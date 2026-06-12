---
title: "How to make an http connection within a C or C++ program"
date: 2007-12-08
forum: Programming Talk
---

### Post by sshahir on 2007-12-08
Hi,

I am wondering how to make an http connection within a C or C++ program. I have tried to use "wget" Linux command:

> system("wget [http://google.ca/index.html](http://google.ca/index.html) -O- | sh");

but it doesn't work.

I appreciate for any comments or suggestions.

sshahir

---

### Post by yabbadabbadont on 2007-12-08
You will need to use a third party library to get this functionality.  I think that the Boost libraries might offer it, but I've never used it myself.

---

### Post by LaRoza on 2007-12-08
You can use Posix Sockets. [http://beej.us/guide/bgnet/output/html/multipage/index.html](http://beej.us/guide/bgnet/output/html/multipage/index.html)

---

### Post by yabbadabbadont on 2007-12-08
> **LaRoza said:**
> You can use Posix Sockets. [http://beej.us/guide/bgnet/output/html/multipage/index.html](http://beej.us/guide/bgnet/output/html/multipage/index.html)

I thought about suggesting something low level like that, but third party libraries usually provide a much simpler interface.  ;)

---

### Post by Wybiral on 2007-12-08
[LibCURL]("http://curl.haxx.se/libcurl/c/") is a pretty good one.

---

### Post by yabbadabbadont on 2007-12-08
> **Wybiral said:**
> [LibCURL]("http://curl.haxx.se/libcurl/c/") is a pretty good one.

THAT was the one I was trying to remember.  Thanks.  :D

---

### Post by sshahir on 2007-12-08
Thank you all for providing the valuable information. I am going to look at those options. I believe the Internet socket is more robust but time consuming than third party libraries. I am wondering whether any of you guys have used those techniques; if so, please let me know what you recommend.

Thanks,
sshahir

---

