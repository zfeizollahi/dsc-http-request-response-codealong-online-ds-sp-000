
# HTTP Request/Response Cycle - Codealong

##  Introduction
When developing a Web application as we saw in previous lesson, the request/response cycle is a useful guide to see how all the components of the app fit together. The request/response cycle traces how a user's request flows through the app. Understanding the request/response cycle is helpful to figure out which files to edit when developing an app (and where to look when things aren't working). This lesson will show how this setup works using python. 

## Objectives

You will be able to: 

* Understand and explain the HTTP Request/Response cycle
* Make http requests in Python using the ‘requests’ library

## The `requests` Library in Python

Dealing with HTTP requests could be a challenging task  any programming language. Python with two built-in modules, `urllib` and `urllib2` to handle these requests but these could be very confusing  and the documentation is not clear. This requires the programmer to write a lot of code to make even a simple HTTP request.

To make these things simpler, one easy-to-use third-party library, known as` Requests`, is available and most developers prefer to use it instead or urllib/urllib2. It is an Apache2 licensed HTTP library powered by urllib3 and httplib. Requests is add-on library that allows you to send HTTP requests using Python. With this library, you can access content like web page headers, form data, files, and parameters via simple Python commands. It also allows you to access the response data in a simple way.

![](images/logo.png)

Below is how you would install and import the requests library before making any requests. 
```python
# Uncomment and install requests if you don't have it already
# !pip install requests

# Import requests to working environment
import requests
```


```python
!pip install requests
```

    Looking in indexes: https://yoober8:apeSoocie4eeth1ohZu6gaiCaiW0Shoi@pypi.uberinternal.com/index, https://pypi.python.org/simple
    Requirement already satisfied: requests in /anaconda3/envs/learn-env/lib/python3.6/site-packages (2.19.1)
    Requirement already satisfied: urllib3<1.24,>=1.21.1 in /anaconda3/envs/learn-env/lib/python3.6/site-packages (from requests) (1.23)
    Requirement already satisfied: chardet<3.1.0,>=3.0.2 in /anaconda3/envs/learn-env/lib/python3.6/site-packages (from requests) (3.0.4)
    Requirement already satisfied: idna<2.8,>=2.5 in /anaconda3/envs/learn-env/lib/python3.6/site-packages (from requests) (2.7)
    Requirement already satisfied: certifi>=2017.4.17 in /anaconda3/envs/learn-env/lib/python3.6/site-packages (from requests) (2018.8.13)



```python
# Code here
import requests
```

## The `.get()` Method

Now we have requests library ready in our working environment, we can start making some requests using the `.get()` method as shown below:
```python
### Making a request
resp = requests.get('https://www.google.com')
```


```python
# Code here 
resp = requests.get('https://www.google.com')
```

GET is by far the most used HTTP method. We can use GET request to retrieve data from any destination. 

## Status Codes
The request we make may not be always successful. The best way is to check the status code which gets returned with the response. Here is how you would do this. 
```python
# Check the returned status code
resp.status_code == requests.codes.ok
```


```python
# Code here 
resp.status_code == requests.codes.ok
```




    True




```python
resp.status_code
```




    200



So this is a good check to see if our request was successful. Depending on the status of the web server, the access rights of the clients and availability of requested information. A web server may return a number of status codes within the response. Wikipedia has an exhaustive details on all these codes. [Check them out here](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes).

## Response Contents
Once we know that our request was successful and we have a valid response, we can check the returned information using `.text` property of the response object. 
```python
print (resp.text)
```


```python
# Code here 
print(resp.text)
```

    <!doctype html><html itemscope="" itemtype="http://schema.org/WebPage" lang="en"><head><meta content="Search the world's information, including webpages, images, videos and more. Google has many special features to help you find exactly what you're looking for." name="description"><meta content="noodp" name="robots"><meta content="text/html; charset=UTF-8" http-equiv="Content-Type"><meta content="/logos/doodles/2019/bb-kings-94th-birthday-6492993740603392-l.png" itemprop="image"><meta content="B.B. King&#8217;s 94th Birthday" property="twitter:title"><meta content="B.B. King&#8217;s 94th Birthday! #GoogleDoodle" property="twitter:description"><meta content="B.B. King&#8217;s 94th Birthday! #GoogleDoodle" property="og:description"><meta content="summary_large_image" property="twitter:card"><meta content="@GoogleDoodles" property="twitter:site"><meta content="https://www.google.com/logos/doodles/2019/bb-kings-94th-birthday-6492993740603392-2xa.gif" property="twitter:image"><meta content="https://www.google.com/logos/doodles/2019/bb-kings-94th-birthday-6492993740603392-2xa.gif" property="og:image"><meta content="825" property="og:image:width"><meta content="460" property="og:image:height"><meta content="https://www.google.com/logos/doodles/2019/bb-kings-94th-birthday-6492993740603392-2xa.gif" property="og:url"><meta content="video.other" property="og:type"><title>Google</title><script nonce="8pRUqs3g20ZK1gentjmv/w==">(function(){window.google={kEI:'PMx_Xb23Jobr-wSNsJyQAg',kEXPI:'0,1353746,5663,731,223,510,246,819,3151,379,206,905,112,53,1431,577,2,37,87,10,713,226,94,18,233,306,166,46,32,2329595,329498,1294,12383,4855,32691,15248,867,12163,6381,3335,2,2,6801,364,3319,5505,224,2218,5942,1119,2,578,728,2432,1361,284,4039,3700,1267,774,2250,1407,1413,1924,1146,9,1963,6197,668,1050,1808,1478,7,1,2,488,2044,5766,1,3144,5295,2016,38,623,297,873,1217,1364,1611,2729,7,1558,1097,315,91,2,631,1140,2,1261,837,1810,5636,620,2884,18,319,1118,864,38,1153,975,1,369,2777,519,400,992,509,778,6,109,2687,967,48,553,25,1279,1042,1170,202,168,157,3,68,1184,327,513,324,193,1466,8,48,158,662,2620,818,109,151,52,1135,1,3,2063,606,1839,184,595,1182,143,377,361,141,184,1261,747,61,158,97,113,44,207,1,1,894,327,1284,16,84,336,82,2283,142,1639,608,245,228,1339,29,700,501,557,669,2425,133,521,433,1395,498,5,437,66,225,592,523,1002,1276,602,507,240,108,291,133,4,856,207,1,907,425,957,2874,4,284,408,470,1,5,1,25,49,267,348,42,9,112,2,149,385,429,34,58,469,417,262,344,105,2,375,79,157,292,18,211,323,33,475,56,441,179,134,109,104,128,490,498,1340,84,135,53,5,495,847,2,607,464,5891798,1874,1154,5997344,282,2799686,4,1572,549,333,444,1,2,80,1,900,581,11,304,1,8,1,2,2132,1,1,1,1,1,414,1,748,141,59,726,3,7,563,1,3653,134,4,1,73,18906231,3397042,1662865',authuser:0,kscs:'c9c918f0_PMx_Xb23Jobr-wSNsJyQAg',kGL:'US',kBL:'7eXu'};google.sn='webhp';google.kHL='en';google.jsfs='Ffpdje';})();(function(){google.lc=[];google.li=0;google.getEI=function(a){for(var b;a&&(!a.getAttribute||!(b=a.getAttribute("eid")));)a=a.parentNode;return b||google.kEI};google.getLEI=function(a){for(var b=null;a&&(!a.getAttribute||!(b=a.getAttribute("leid")));)a=a.parentNode;return b};google.https=function(){return"https:"==window.location.protocol};google.ml=function(){return null};google.time=function(){return(new Date).getTime()};google.log=function(a,b,e,c,g){if(a=google.logUrl(a,b,e,c,g)){b=new Image;var d=google.lc,f=google.li;d[f]=b;b.onerror=b.onload=b.onabort=function(){delete d[f]};google.vel&&google.vel.lu&&google.vel.lu(a);b.src=a;google.li=f+1}};google.logUrl=function(a,b,e,c,g){var d="",f=google.ls||"";e||-1!=b.search("&ei=")||(d="&ei="+google.getEI(c),-1==b.search("&lei=")&&(c=google.getLEI(c))&&(d+="&lei="+c));c="";!e&&google.cshid&&-1==b.search("&cshid=")&&"slh"!=a&&(c="&cshid="+google.cshid);a=e||"/"+(g||"gen_204")+"?atyp=i&ct="+a+"&cad="+b+d+f+"&zx="+google.time()+c;/^http:/i.test(a)&&google.https()&&(google.ml(Error("a"),!1,{src:a,glmm:1}),a="");return a};}).call(this);(function(){google.y={};google.x=function(a,b){if(a)var c=a.id;else{do c=Math.random();while(google.y[c])}google.y[c]=[a,b];return!1};google.lm=[];google.plm=function(a){google.lm.push.apply(google.lm,a)};google.lq=[];google.load=function(a,b,c){google.lq.push([[a],b,c])};google.loadAll=function(a,b){google.lq.push([a,b])};}).call(this);google.f={};var a=window.location,b=a.href.indexOf("#");if(0<=b){var c=a.href.substring(b+1);/(^|&)q=/.test(c)&&-1==c.indexOf("#")&&a.replace("/search?"+c.replace(/(^|&)fp=[^&]*/g,"")+"&cad=h")};</script><style>#gbar,#guser{font-size:13px;padding-top:1px !important;}#gbar{height:22px}#guser{padding-bottom:7px !important;text-align:right}.gbh,.gbd{border-top:1px solid #c9d7f1;font-size:1px}.gbh{height:0;position:absolute;top:24px;width:100%}@media all{.gb1{height:22px;margin-right:.5em;vertical-align:top}#gbar{float:left}}a.gb1,a.gb4{text-decoration:underline !important}a.gb1,a.gb4{color:#00c !important}.gbi .gb4{color:#dd8e27 !important}.gbf .gb4{color:#900 !important}
    </style><style>body,td,a,p,.h{font-family:arial,sans-serif}body{margin:0;overflow-y:scroll}#gog{padding:3px 8px 0}td{line-height:.8em}.gac_m td{line-height:17px}form{margin-bottom:20px}.h{color:#36c}.q{color:#00c}.ts td{padding:0}.ts{border-collapse:collapse}em{font-weight:bold;font-style:normal}.lst{height:25px;width:496px}.gsfi,.lst{font:18px arial,sans-serif}.gsfs{font:17px arial,sans-serif}.ds{display:inline-box;display:inline-block;margin:3px 0 4px;margin-left:4px}input{font-family:inherit}a.gb1,a.gb2,a.gb3,a.gb4{color:#11c !important}body{background:#fff;color:black}a{color:#11c;text-decoration:none}a:hover,a:active{text-decoration:underline}.fl a{color:#36c}a:visited{color:#551a8b}a.gb1,a.gb4{text-decoration:underline}a.gb3:hover{text-decoration:none}#ghead a.gb2:hover{color:#fff !important}.sblc{padding-top:5px}.sblc a{display:block;margin:2px 0;margin-left:13px;font-size:11px}.lsbb{background:#eee;border:solid 1px;border-color:#ccc #999 #999 #ccc;height:30px}.lsbb{display:block}.ftl,#fll a{display:inline-block;margin:0 12px}.lsb{background:url(/images/nav_logo229.png) 0 -261px repeat-x;border:none;color:#000;cursor:pointer;height:30px;margin:0;outline:0;font:15px arial,sans-serif;vertical-align:top}.lsb:active{background:#ccc}.lst:focus{outline:none}</style><script nonce="8pRUqs3g20ZK1gentjmv/w=="></script></head><body bgcolor="#fff"><script nonce="8pRUqs3g20ZK1gentjmv/w==">(function(){var src='/images/nav_logo229.png';var iesg=false;document.body.onload = function(){window.n && window.n();if (document.images){new Image().src=src;}
    if (!iesg){document.f&&document.f.q.focus();document.gbqf&&document.gbqf.q.focus();}
    }
    })();</script><div id="mngb"> <div id=gbar><nobr><b class=gb1>Search</b> <a class=gb1 href="https://www.google.com/imghp?hl=en&tab=wi">Images</a> <a class=gb1 href="https://maps.google.com/maps?hl=en&tab=wl">Maps</a> <a class=gb1 href="https://play.google.com/?hl=en&tab=w8">Play</a> <a class=gb1 href="https://www.youtube.com/?gl=US&tab=w1">YouTube</a> <a class=gb1 href="https://news.google.com/nwshp?hl=en&tab=wn">News</a> <a class=gb1 href="https://mail.google.com/mail/?tab=wm">Gmail</a> <a class=gb1 href="https://drive.google.com/?tab=wo">Drive</a> <a class=gb1 style="text-decoration:none" href="https://www.google.com/intl/en/about/products?tab=wh"><u>More</u> &raquo;</a></nobr></div><div id=guser width=100%><nobr><span id=gbn class=gbi></span><span id=gbf class=gbf></span><span id=gbe></span><a href="http://www.google.com/history/optout?hl=en" class=gb4>Web History</a> | <a  href="/preferences?hl=en" class=gb4>Settings</a> | <a target=_top id=gb_70 href="https://accounts.google.com/ServiceLogin?hl=en&passive=true&continue=https://www.google.com/" class=gb4>Sign in</a></nobr></div><div class=gbh style=left:0></div><div class=gbh style=right:0></div> </div><center><br clear="all" id="lgpd"><div id="lga"><a href="/search?ie=UTF-8&amp;q=B.B.+King&amp;oi=ddle&amp;ct=119275757&amp;hl=en&amp;kgmid=/m/01w60_p&amp;sa=X&amp;ved=0ahUKEwi9xaDR9NXkAhWG9Z4KHQ0YByIQPQgD"><img alt="B.B. King&#8217;s 94th Birthday" border="0" height="220" src="/logos/doodles/2019/bb-kings-94th-birthday-6492993740603392-l.png" title="B.B. King&#8217;s 94th Birthday" width="391" id="hplogo"><br></a><br></div><form action="/search" name="f"><table cellpadding="0" cellspacing="0"><tr valign="top"><td width="25%">&nbsp;</td><td align="center" nowrap=""><input name="ie" value="ISO-8859-1" type="hidden"><input value="en" name="hl" type="hidden"><input name="source" type="hidden" value="hp"><input name="biw" type="hidden"><input name="bih" type="hidden"><div class="ds" style="height:32px;margin:4px 0"><input style="color:#000;margin:0;padding:5px 8px 0 6px;vertical-align:top" autocomplete="off" class="lst" value="" title="Google Search" maxlength="2048" name="q" size="57"></div><br style="line-height:0"><span class="ds"><span class="lsbb"><input class="lsb" value="Google Search" name="btnG" type="submit"></span></span><span class="ds"><span class="lsbb"><input class="lsb" id="tsuid1" value="I'm Feeling Lucky" name="btnI" type="submit"><script nonce="8pRUqs3g20ZK1gentjmv/w==">(function(){var id='tsuid1';document.getElementById(id).onclick = function(){if (this.form.q.value){this.checked = 1;if (this.form.iflsig)this.form.iflsig.disabled = false;}
    else top.location='/doodles/';};})();</script></span></span></td><td class="fl sblc" align="left" nowrap="" width="25%"><a href="/advanced_search?hl=en&amp;authuser=0">Advanced search</a><a href="/language_tools?hl=en&amp;authuser=0">Language tools</a></td></tr></table><input id="gbv" name="gbv" type="hidden" value="1"><script nonce="8pRUqs3g20ZK1gentjmv/w==">(function(){var a,b="1";if(document&&document.getElementById)if("undefined"!=typeof XMLHttpRequest)b="2";else if("undefined"!=typeof ActiveXObject){var c,d,e=["MSXML2.XMLHTTP.6.0","MSXML2.XMLHTTP.3.0","MSXML2.XMLHTTP","Microsoft.XMLHTTP"];for(c=0;d=e[c++];)try{new ActiveXObject(d),b="2"}catch(h){}}a=b;if("2"==a&&-1==location.search.indexOf("&gbv=2")){var f=google.gbvu,g=document.getElementById("gbv");g&&(g.value=a);f&&window.setTimeout(function(){location.href=f},0)};}).call(this);</script></form><div id="gac_scont"></div><div style="font-size:83%;min-height:3.5em"><br><div id="prm"><style>.szppmdbYutt__middle-slot-promo{font-size:small;margin-bottom:32px}.szppmdbYutt__middle-slot-promo a.ZIeIlb{display:inline-block;text-decoration:none}.szppmdbYutt__middle-slot-promo img{border:none;margin-right:5px;vertical-align:middle}</style><div class="szppmdbYutt__middle-slot-promo" data-ved="0ahUKEwi9xaDR9NXkAhWG9Z4KHQ0YByIQnIcBCAQ"><a class="NKcBbd" href="https://www.google.com/url?q=https://www.youtube.com/watch%3Fv%3DJTb4wUZhBRA&amp;source=hpp&amp;id=19013808&amp;ct=3&amp;usg=AFQjCNGf6vhBbWrvAderiFcmyo2cEO2jiw&amp;sa=X&amp;ved=0ahUKEwi9xaDR9NXkAhWG9Z4KHQ0YByIQ8IcBCAU" rel="nofollow">Go behind-the-scenes of today&#8217;s Doodle</a><span> celebrating the King of the Blues</span></div></div></div><span id="footer"><div style="font-size:10pt"><div style="margin:19px auto;text-align:center" id="fll"><a href="/intl/en/ads/">Advertising Programs</a><a href="/services/">Business Solutions</a><a href="/intl/en/about.html">About Google</a></div></div><p style="color:#767676;font-size:8pt">&copy; 2019 - <a href="/intl/en/policies/privacy/">Privacy</a> - <a href="/intl/en/policies/terms/">Terms</a></p></span></center><script nonce="8pRUqs3g20ZK1gentjmv/w==">(function(){window.google.cdo={height:0,width:0};(function(){var a=window.innerWidth,b=window.innerHeight;if(!a||!b){var c=window.document,d="CSS1Compat"==c.compatMode?c.documentElement:c.body;a=d.clientWidth;b=d.clientHeight}a&&b&&(a!=google.cdo.width||b!=google.cdo.height)&&google.log("","","/client_204?&atyp=i&biw="+a+"&bih="+b+"&ei="+google.kEI);}).call(this);})();(function(){var u='/xjs/_/js/k\x3dxjs.hp.en_US.CqKx7coWtKw.O/m\x3dsb_he,d/am\x3dHhZsAg/d\x3d1/rs\x3dACT90oFMjf3G2i6qraPPdavAZsbh53V5OQ';setTimeout(function(){var a=document.createElement("script");a.src=u;google.timers&&google.timers.load&&google.tick&&google.tick("load","xjsls");document.body.appendChild(a)},0);})();(function(){window.google.xjsu='/xjs/_/js/k\x3dxjs.hp.en_US.CqKx7coWtKw.O/m\x3dsb_he,d/am\x3dHhZsAg/d\x3d1/rs\x3dACT90oFMjf3G2i6qraPPdavAZsbh53V5OQ';})();function _DumpException(e){throw e;}
    function _F_installCss(c){}
    (function(){google.spjs=false;google.snet=true;google.em=[];google.emw=false;})();(function(){var pmc='{\x22JnTczA\x22:{},\x22Qnk92g\x22:{},\x22RWGcrA\x22:{},\x22U5B21g\x22:{},\x22YFCs/g\x22:{},\x22YQeDTA\x22:{},\x22ZI/YVQ\x22:{},\x22d\x22:{},\x22mVopag\x22:{},\x22sb_he\x22:{\x22agen\x22:false,\x22cgen\x22:false,\x22client\x22:\x22heirloom-hp\x22,\x22dh\x22:true,\x22dhqt\x22:true,\x22ds\x22:\x22\x22,\x22ffql\x22:\x22en\x22,\x22fl\x22:true,\x22host\x22:\x22google.com\x22,\x22isbh\x22:28,\x22jsonp\x22:true,\x22msgs\x22:{\x22cibl\x22:\x22Clear Search\x22,\x22dym\x22:\x22Did you mean:\x22,\x22lcky\x22:\x22I\\u0026#39;m Feeling Lucky\x22,\x22lml\x22:\x22Learn more\x22,\x22oskt\x22:\x22Input tools\x22,\x22psrc\x22:\x22This search was removed from your \\u003Ca href\x3d\\\x22/history\\\x22\\u003EWeb History\\u003C/a\\u003E\x22,\x22psrl\x22:\x22Remove\x22,\x22sbit\x22:\x22Search by image\x22,\x22srch\x22:\x22Google Search\x22},\x22ovr\x22:{},\x22pq\x22:\x22\x22,\x22refpd\x22:true,\x22rfs\x22:[],\x22sbpl\x22:24,\x22sbpr\x22:24,\x22scd\x22:10,\x22sce\x22:5,\x22stok\x22:\x22srpaiiHCy6C2XR2VQsQKNI4EZmU\x22,\x22uhde\x22:false}}';google.pmc=JSON.parse(pmc);})();</script>        </body></html>


So this returns a lot of information which by default is not really human understandable due to data encoding, HTML tags and other styling information that only a web browser can truly translate. In later lessons we'll learn how we can use **_Regular Expressions_**  to clean this information and extract the required bits and pieces for analysis. 

## Response Headers
The response of an HTTP request can contain many headers that holds different bits of information. We can use `.header` property of the response object to access the header information as shown below:

```python
# Read the header of the response - convert to dictionary for displaying k:v pairs neatly
dict(resp.headers)
```


```python
# Code here 
dict(resp.headers)
```




    {'Date': 'Mon, 16 Sep 2019 17:54:04 GMT',
     'Expires': '-1',
     'Cache-Control': 'private, max-age=0',
     'Content-Type': 'text/html; charset=ISO-8859-1',
     'P3P': 'CP="This is not a P3P policy! See g.co/p3phelp for more info."',
     'Content-Encoding': 'gzip',
     'Server': 'gws',
     'X-XSS-Protection': '0',
     'X-Frame-Options': 'SAMEORIGIN',
     'Set-Cookie': '1P_JAR=2019-09-16-17; expires=Wed, 16-Oct-2019 17:54:04 GMT; path=/; domain=.google.com; SameSite=none, NID=188=uTSc5m1NCc_w9EvhgFQ2DOUeomQ3ef8KGfv6y1dio9svp-AtWtMrJHoiIpTHHAZQIJl3YDVf-B6_nQeZe2QVvT3xAB0IwJucG_HcHW2ZEiDyZa1n7NZMHQvU3vX7fDsSU8xTrsrgoPp7dLDN-bAuxALKJLl4AIQIUlY5qIlEaZQ; expires=Tue, 17-Mar-2020 17:54:04 GMT; path=/; domain=.google.com; HttpOnly',
     'Alt-Svc': 'quic=":443"; ma=2592000; v="46,43,39"',
     'Transfer-Encoding': 'chunked'}



The content of the headers is our required element. You can see the key-value pairs holding various pieces of  information about the resource and request. Let's try to parse some of these values using the requests library:

```python
print(resp.headers['Date'])  # Date the response was sent
print(resp.headers['server'])   # Server type (google web service - GWS)
```


```python
# Code here 
print(resp.headers['Date'])  # Date the response was sent
print(resp.headers['server'])
```

    Mon, 16 Sep 2019 17:54:04 GMT
    gws


## Try `httpbin`
`httpbin.org` is a popular website to test different HTTP operation and practice with request-response cycles. Let's use httpbin/get to analyze the response to a GET request. First of all, let's find out the response header and inspect how it looks. 

```python
r = requests.get('http://httpbin.org/get')

response = r.json()  
print(r.json())  
print(response['args'])  
print(response['headers'])  
print(response['headers']['Accept'])  
print(response['headers']['Accept-Encoding'])  
print(response['headers']['Host'])  
print(response['headers']['User-Agent'])  
print(response['origin'])  
print(response['url'])  
```


```python
# Code here 
r = requests.get('http://httpbin.org/get')

response = r.json()  
print(r.json())  
print(response['args'])  
print(response['headers'])  
print(response['headers']['Accept'])  
print(response['headers']['Accept-Encoding'])  
print(response['headers']['Host'])  
print(response['headers']['User-Agent'])  
print(response['origin'])  
print(response['url'])  
```

    {'args': {}, 'headers': {'Accept': '*/*', 'Accept-Encoding': 'gzip, deflate', 'Host': 'httpbin.org', 'User-Agent': 'python-requests/2.19.1'}, 'origin': '207.231.170.7, 207.231.170.7', 'url': 'https://httpbin.org/get'}
    {}
    {'Accept': '*/*', 'Accept-Encoding': 'gzip, deflate', 'Host': 'httpbin.org', 'User-Agent': 'python-requests/2.19.1'}
    */*
    gzip, deflate
    httpbin.org
    python-requests/2.19.1
    207.231.170.7, 207.231.170.7
    https://httpbin.org/get


Let's use `requests` object structure to parse the values of headers as we did above. 

```python
print(r.headers['Access-Control-Allow-Credentials'])  
print(r.headers['Access-Control-Allow-Origin'])  
print(r.headers['CONNECTION'])  
print(r.headers['content-length'])  
print(r.headers['Content-Type'])  
print(r.headers['Date'])  
print(r.headers['server'])  
```


```python
# Code here 
print(r.headers['Access-Control-Allow-Credentials'])  
print(r.headers['Access-Control-Allow-Origin'])  
print(r.headers['CONNECTION'])  
print(r.headers['content-length'])  
print(r.headers['Content-Type'])  
print(r.headers['Date'])  
print(r.headers['server']) 
```

    true
    *
    keep-alive
    183
    application/json
    Mon, 16 Sep 2019 18:36:38 GMT
    nginx


## Passing Parameters in GET
In some cases, you'll need to pass parameters along with your GET requests. These extra parameters usually take the the form of query strings added to the requested URL. To do this, we need to pass these values in the `params` parameter. Let's try to access information from `httpbin` with some user information. 

Note: The user information is not getting authenticated at `httpbin` so any name/password will work fine. This is merely for practice. 

```python
credentials = {'user_name': 'FlatironSchool', 'password': 'learnlovecode'}  
r = requests.get('http://httpbin.org/get', params=credentials)

print(r.url)  
print(r.text)  
```


```python
# Code here 
credentials = {'user_name': 'FlatironSchool', 'password': 'learnlovecode'}  
r = requests.get('http://httpbin.org/get', params=credentials)

print(r.url)  
print(r.text) 
```

    http://httpbin.org/get?user_name=FlatironSchool&password=learnlovecode
    {
      "args": {
        "password": "learnlovecode", 
        "user_name": "FlatironSchool"
      }, 
      "headers": {
        "Accept": "*/*", 
        "Accept-Encoding": "gzip, deflate", 
        "Host": "httpbin.org", 
        "User-Agent": "python-requests/2.19.1"
      }, 
      "origin": "207.231.170.7, 207.231.170.7", 
      "url": "https://httpbin.org/get?user_name=FlatironSchool&password=learnlovecode"
    }
    


## HTTP POST method 

Sometimes we need to send one or more files simultaneously to the server. For example, if a user is submitting a form and the form includes different fields for uploading files, like user profile picture, user resume, etc. Requests can handle multiple files on a single request. This can be achieved by putting the files to a list of tuples in the form (`field_name, file_info)`.


```python
import requests

url = 'http://httpbin.org/post'  
file_list = [  
    ('image', ('fi.png', open('images/fi.png', 'rb'), 'image/png')),
    ('image', ('fi2.jpeg', open('images/fi2.jpeg', 'rb'), 'image/png'))
]

r = requests.post(url, files=file_list)  
print(r.text)  
```


```python
# Code here  
url = 'http://httpbin.org/post'  
file_list = [  
    ('image', ('fi.png', open('images/fi.png', 'rb'), 'image/png')),
    ('image', ('fi2.jpeg', open('images/fi2.jpeg', 'rb'), 'image/png'))
]

r = requests.post(url, files=file_list)  
print(r.text)
```

    {
      "args": {}, 
      "data": "", 
      "files": {
        "image": "data:image/png;base64,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"
      }, 
      "form": {}, 
      "headers": {
        "Accept": "*/*", 
        "Accept-Encoding": "gzip, deflate", 
        "Content-Length": "40790", 
        "Content-Type": "multipart/form-data; boundary=42ffccad6ca833378f5043314b6c7c56", 
        "Host": "httpbin.org", 
        "User-Agent": "python-requests/2.19.1"
      }, 
      "json": null, 
      "origin": "207.231.170.7, 207.231.170.7", 
      "url": "https://httpbin.org/post"
    }
    


This was a brief introduction to how you would send requests and get responses from a web server, while totally avoiding the web browser interface. Later we'll see how we can pick up the required data elements from the contents of the web page for analytical purpose. 

## Summary
In this lesson, we provided an introduction to the `requests` library in python. We saw how to use the get method to send requests to web servers, check server status, look at the header elements of a web page and how to send extra parameters like user information. 
