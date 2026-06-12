---
title: "Apache use proxy server?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Dissident85 on 2008-05-22
Hi all, I wanted to know if it was possible to get Apache to use a proxy server? I was trying to build a Tor hidden service search engine using the Sphider php search engine script. 

The problem I am having is that Apache try to find the pages on the normal web and not through the tor network. I was thinking if I install provioxy on the server and get Apache to direct it traffic through it, it should solve the problem. 

Dose anyone know how this can be done? Any help would be greatly appreciated. 

Ps: I did post this in a server area of these forums, but I think I worded the question wrong. And I didn’t get any reply’s… [http://ubuntuforums.org/showthread.php?t=803071](http://ubuntuforums.org/showthread.php?t=803071)

---

### Post by Dissident85 on 2008-05-22
bump, Anyone???

---

### Post by spiderbatdad on 2008-05-22
There is a ton of information on this subject on google.
Apache as forward proxy, Reverse proxy. Caching proxy...

[http://httpd.apache.org/docs/2.0/mod/mod_proxy.html](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html)
[http://www.devshed.com/c/a/Administration/Using-Apache-As-A-Proxy-Server/1/](http://www.devshed.com/c/a/Administration/Using-Apache-As-A-Proxy-Server/1/)
[http://www.acm.org/crossroads/xrds7-5/proxy.html](http://www.acm.org/crossroads/xrds7-5/proxy.html)

My understanding is that apache must be compiled with the proxy module...you would need to start from scratch compiling apache correctly with prefixes.

---

### Post by Dissident85 on 2008-05-22
> **spiderbatdad said:**
> There is a ton of information on this subject on google.
Apache as forward proxy, Reverse proxy. Caching proxy...

[http://httpd.apache.org/docs/2.0/mod/mod_proxy.html](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html)
[http://www.devshed.com/c/a/Administration/Using-Apache-As-A-Proxy-Server/1/](http://www.devshed.com/c/a/Administration/Using-Apache-As-A-Proxy-Server/1/)
[http://www.acm.org/crossroads/xrds7-5/proxy.html](http://www.acm.org/crossroads/xrds7-5/proxy.html)

My understanding is that apache must be compiled with the proxy module...you would need to start from scratch compiling apache correctly with prefixes.

Thanks, i did see all that on google... but i thought that was for using apache as a proxy server. not getting apache to use a proxy server. 

but ill have a closer look.

---

### Post by tlerner on 2009-06-18
I too thought it was how to make apache a proxy server.  I do not see how I can make apache USE a proxy server.  I have spent hours on this and cant figure this out and I am probably missing something.  Any help on exactly where to look would be helpful.  I am running my server on Windows XP.  Thanks so much

---

### Post by Tempuser123 on 2010-02-16
**Solution**
Not for Apache in general but for php

See the comment at [http://php.net/manual/en/function.stream-context-get-default.php]("http://php.net/manual/en/function.stream-context-get-default.php")

---

