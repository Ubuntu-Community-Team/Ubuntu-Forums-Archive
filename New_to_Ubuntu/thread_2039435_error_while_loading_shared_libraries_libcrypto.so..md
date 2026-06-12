---
title: "error while loading shared libraries libcrypto.so.0.9.8"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by C00kie88 on 2012-08-08
hi all,
 
I have installed Ubuntu version 12, with squid and dansguardian installed. So far is working great. I love it... Big achievement for me since i'm a linux newbie.
My problem is:
 
I'm trying to install sawmill software for log/reporting purpose (trial version) to see how it looks like, but i received the error as below when i run the software.
./sawmill: error while loading shared libraries: libcrypto.so.0.9.8: cannot open shared object file: no such file or directory. :(
 
Am i missing any packages?
 
Please help
 
Thank you

---

### Post by ubudog on 2012-08-08
Hi there & welcome to the forums.  

Try installing this package:
```
sudo apt-get install libssl0.9.8
```

Best,
ubudog

---

### Post by C00kie88 on 2012-08-09
Thank you so much...
 
It works now 
 
:)

---

### Post by ubudog on 2012-08-09
Glad that worked!  :)

Be sure to mark the thread as solved using the "Thread Tools" dropdown at the top of the page.

---

