---
title: "dokuwiki stalls on install"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by mevets on 2008-09-26
I tried installing wiki software. On the installation of dokuwiki, it went to configure and then stalled indefinitely. I killed the process and tried to run sudo dpkg --configure -a. This went to reconfigure dokuwiki again but the configure process just stalls in the same place.

Output
```
steve@steve-laptop:~$ sudo dpkg --configure -a
Setting up ewiki (1.02-6ubuntu1) ...

Setting up dokuwiki (0.0.20070626b-1) ...
X_LOADTEMPLATEFILE /var/lib/dpkg/info/ucf.templates ucf

```

---

### Post by jamesrl on 2008-09-26
From [https://bugs.launchpad.net/ubuntu/+source/dokuwiki/+bug/216980]("https://bugs.launchpad.net/ubuntu/+source/dokuwiki/+bug/216980"):
> 
I had the same problem, but still managed to install it: stop apache before install, launch install process, hit return a few times till the end.
After that start apache and go to: [http://localhost/dokuwiki](http://localhost/dokuwiki)

and you should see your new wiki.


---

