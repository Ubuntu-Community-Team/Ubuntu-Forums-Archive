---
title: "Help with Python"
date: 2009-07-30
forum: Programming Talk
---

### Post by CrazyMonkeyFox on 2009-07-30
**_The Task:_**
A URL would be given at the CLI, or possibly read in from a file. The program would then ideally, check all pages of the site for a javascript script that should be embedded in it. ( In the case of dynamic pages only one instance would be necessary but I'm not sure this would be possible.) The program would return a list of pages that the script wasn't on or in teh case of none, a message bout that.

_**Ideas:**_
1. Using urlopen and read() from urllib2 to open the source and look for the script physically.
2. Using getheader from httplib to look for a header created by the script.

_**Problems:**_
1. Using urlopen and read() would be very time consuming, use up alot of memory, and in the case of a site with dynamic pages it messes stuff up.
2. Ive tried using this but it only returns the initial header info. Using the addon "live-headers" I found that the script sends a get request much later.

```

http://t.********.com/ie/****_ie/bmv13.js 
 
GET /ie/****_ie/bmv13.js HTTP/1.1 
Host: t.********.com 
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12 
Accept: */* 
Accept-Language: en-us,en;q=0.5 
Accept-Encoding: gzip,deflate 
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7 
Keep-Alive: 300 
Connection: keep-alive 
Referer: http://www.****.ie/ 
 
HTTP/1.x 200 OK 
Date: Thu, 30 Jul 2009 14:47:31 GMT 
Server: Apache/2.2.8 (FreeBSD) mod_ssl/2.2.8 OpenSSL/0.9.7e-p1 PHP/5.2.5 mod_fastcgi/2.4.6 
Last-Modified: Wed, 24 Sep 2008 11:07:49 GMT 
Etag: "916d0-631-457a24b732b40" 
Accept-Ranges: bytes 
Content-Length: 1585 
Connection: close 
Content-Type: application/javascript 

```**_Note:_**
This request is sent much later then the initial header request. The 4 asterixes (****) would be a variable by the way. The longer string of asterixes are just for privacy.

I am wondering purely in pseudo-code terms how to approach this particular program as I like a challenge. If I have left out any information please let me know.

Thanks in advance,
CMF

---

### Post by unutbu on 2009-07-30
This is not very elegant, but perhaps this could work:

[PHP]#!/usr/bin/env python
from urllib2 import urlopen
f=urlopen('http://www.python.org')
chunk='the sky is so blue'
while chunk != '':
    chunk=f.read(10000)  # Read in only the first 10000 bytes
    # Check for javascript[/PHP]

See "21.6.21 Examples" in [http://docs.python.org/library/urllib2.html#module-urllib2](http://docs.python.org/library/urllib2.html#module-urllib2)

---

### Post by smartbei on 2009-07-30
Unless you have absolute huge websites, reading the whole website should not be a memory problem. Even if it is 1mb (which is a lot for a html page), you should not have any memory issues. Of course, you can also use unutbu's suggestion, but then you need to watch out for the stirng you are searching for being split between two chunks.

---

### Post by CrazyMonkeyFox on 2009-08-04
> **smartbei said:**
> Unless you have absolute huge websites, reading the whole website should not be a memory problem. Even if it is 1mb (which is a lot for a html page), you should not have any memory issues. Of course, you can also use unutbu's suggestion, but then you need to watch out for the stirng you are searching for being split between two chunks.

I was kind of referring to the whole thing that for sites with 1000+ pages, it'd possibly strain memory wise, I'm no expert I just thought it would. Its seems that for the most part all the solutions would be time consuming, hence why I suggested the header method, but can't get it to work. Unutbu's method seems good, but once again very time consuming.

Thanks and keep the suggestions coming, for the mean time I should mess around with whats been given.

Regards, 
CMF.

---

### Post by benj1 on 2009-08-04
> **CrazyMonkeyFox said:**
> I was kind of referring to the whole thing that for sites with 1000+ pages, it'd possibly strain memory wise, I'm no expert I just thought it would. Its seems that for the most part all the solutions would be time consuming, hence why I suggested the header method, but can't get it to work. Unutbu's method seems good, but once again very time consuming.

Thanks and keep the suggestions coming, for the mean time I should mess around with whats been given.

Regards, 
CMF.

i would have thought your bottleneck would be your bandwidth,
you could have a look into threading then you could down load a page and then search for javascript while downloading the next page, that way you wouldn't have to store all pages in memory.

---

