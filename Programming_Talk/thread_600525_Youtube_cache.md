---
title: "Youtube cache"
date: 2007-11-02
forum: Programming Talk
---

### Post by chongchongworks on 2007-11-02
Hi,

I did a simple Youtube proxy sever in my course. User set firefox with the IP and Port no of my proxy, then every web request should pass by my proxy. When user browse a website, the proxy writes the content to disk then send them back to browser, so the youtube video will exist in proxy server. 

Until two weeks ago, it worked well, but now it just fail. The index file says 

HTTP/1.0 400 Bad Request
Date: Sat, 27 Oct 2007 02:47:51 GMT
Server: Apache
Cache-Control: no-cache
Content-Type: text/html; charset=utf-8
X-Cache: MISS from nme-pow-pr4.tpgi.com.au
Via: 1.0 nme-pow-pr4.tpgi.com.au:3128 (squid/2.5.STABLE16)
Proxy-Connection: close

but i check the file when it work, it is like

HTTP/1.0 200 OK
Date: Wed, 17 Oct 2007 05:54:48 GMT
Server: Apache
Set-Cookie: use_hitbox=72c46ff6cbcdb7c5585c36411b6b334edAEAAAAw; path=/; domain=.youtube.com
Set-Cookie: user_omniture=3756d44ab2f6fdee26892cc5805390c2dAEAAAAw; path=/; domain=.youtube.com
Set-Cookie: GEO=fcdfa75097a2423d3e62727ce6978c5dcxYAAABBVSx2aSxtZWxib3VybmUsLCwsLC0x; path=/; domain=.youtube.com; expires=Fri, 19-Oct-2007 05:54:48 GMT
Set-Cookie: VISITOR_INFO1_LIVE=QHeaeuTKyMU; path=/; domain=.youtube.com; expires=Sat, 14-Oct-2017 05:54:48 GMT
Set-Cookie: LOCALE_PREFERENCE=86d1d09eefe6b79b4068000ce05518a4dAUAAABlbl9VUw==; path=/; domain=.youtube.com; expires=Sat, 14-Oct-2017 05:54:48 GMT
Cache-Control: no-cache
Content-Length: 72738
Content-Type: text/html; charset=utf-8
X-Cache: MISS from nme-pow-pr7.tpgi.com.au
Via: 1.0 nme-pow-pr7.tpgi.com.au:3128 (squid/2.5.STABLE16)
Proxy-Connection: close
<omitted>

if i replace the index file with the latter, it works, and for other website all fine, only youtube. 

Does anyone know what I should do? I will be very appreciate if someone can give me any idea.

Thanks

---

### Post by Slychilde on 2007-11-04
I think Youtube recently put in some code or something that prevents people from downloading their 'content'.  Youtubedownloader stopped working as did [this]("http://www.techcrunch.com/get-youtube-movie/") page, so I'm guessing that's why your program stopped working.  Also, if you google "youtube download" you'll find that a lot of the sites say they are temporarily down, etc.

Ironic, they steal copyrighted content, but they don't want you to taking it from them. ;)

---

### Post by chongchongworks on 2007-11-05
Thank for your reply.

I did not realise the copyright of youtube. I have seen many tools to download Youtube, so i though it should be free-copyright.

Anyway, fortunately, I have something to explain to my lecturer, that is not the problem of my code, it is the "damn"google make some trick thing for the http request. 

Finally, the result is I cannot get full mark from this "damn" assignment.

---

### Post by evymetal on 2007-11-05
Are you setting your user-agent correctly? So long as you pass the request in exactly the same way as the machine the request originates from I can't see why there should be a problem.

---

