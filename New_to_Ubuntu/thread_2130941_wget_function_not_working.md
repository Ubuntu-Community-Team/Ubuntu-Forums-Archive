---
title: "wget function not working"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by kiritisai on 2013-03-31
I use a proxy server and the apt-get function is working properly,
I have edited the files /etc/environment and /etc/bash.bashrc and /etc/apt/apt.conf as per one of the forums present .. but still the wget function shows the following error. 
Error parsing proxy URL [http://username:password@server.in:port/:](http://username:password@server.in:port/:) Bad port number.

would be very helpful if u could help
lol!! that emoticon means ':' and a 'p'

---

### Post by schragge on 2013-03-31
> **kiritisai said:**
> I have edited the files /etc/environment and /etc/bash.bashrc and /etc/apt/apt.conf as per one of the forums present .. but still the wget function shows the following error. 
```
Error parsing proxy URL [http://username:password@server.in:port/:](http://username:password@server.in:port/:) Bad port number.
```
It says *Bad port number*, so check the port number you put into http_proxy/ftp_proxy variables in */etc/bash.bashrc*. Also check */etc/wgetrc* and *~/.wgetrc* as settings there override environment variables defined in shell startup scripts.

---

### Post by coldcritter64 on 2013-03-31
> **kiritisai said:**
> ....
lol!! that emoticon means ':' and a 'p'
:)   using noparse tags, eg. [noparse][noparse]<your-post-details>[/noparse][/noparse], around the line containing : and p in your editor, will stop the forum bbcode reading those details. It can give some funny results in posts otherwise :p

---

