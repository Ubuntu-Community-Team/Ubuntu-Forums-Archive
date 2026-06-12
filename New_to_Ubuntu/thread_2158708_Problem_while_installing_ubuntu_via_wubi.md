---
title: "Problem while installing ubuntu via wubi"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by Vegeto Tr7 on 2013-06-30
Hio

I've been facing this problem quite a few times before as well (long back though)
whenever i download an ISO of ubuntu and install via wubi, it automatically starts DOWNLOADING a whole new ISO file... 
i was finally able to install using cmd function to run wubi (while internet is off), but still was a headache. what could be the reason?

---

### Post by vanadium on 2013-06-30
Wubi is not officially supported in the latest Ubuntu version, due to issues with its developpement.

---

### Post by coffeecat on 2013-06-30
> **Vegeto Tr7 said:**
> whenever i download an ISO of ubuntu and install via wubi, it automatically starts DOWNLOADING a whole new ISO file... 

Put the ISO file in the same folder as the wubi.exe executable and the wubi installer will use the saved ISO rather than download another one. Make sure that the release version of both wubi.exe and ISO match. This, of course, only works for 12.10 and earlier for the reason given by vanadium. More on wubi here:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Frogs Hair on 2013-06-30
If you want to trial run Ubuntu with Wubi 12.04 and 12.10 are the only options left and 12.10 installer can be down loaded from the bottom of the page at the link.  [http://nz.releases.ubuntu.com/12.10/](http://nz.releases.ubuntu.com/12.10/)

---

