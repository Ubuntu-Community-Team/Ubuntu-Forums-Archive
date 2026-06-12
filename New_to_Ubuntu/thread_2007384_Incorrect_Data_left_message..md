---
title: "Incorrect Data left message."
date: 2012-06-20
forum: New to Ubuntu
---

### Post by Killya on 2012-06-20
Hey!

So ubuntu is installed on C:/ right? Ubuntu keeps giving me the error that there is only xMB left on the system (x is around 40 often) while C:/ still has 32GB. How can I use these 32 gigs?

Ciao!

---

### Post by coffeecat on 2012-06-20
It sounds as though you have a wubi installation, not a conventional Ubuntu installation on its own partition. Did you run the wubi executable within Windows in order to install Ubuntu? If so, look here:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

See the first screenshot there. The default installation size is only 8GB, unless you change that figure at that screen. With wubi, Ubuntu is installed in a virtual partition in the file C:\ubuntu\disks\root.disk. If that's what you did, you only have 8GB immediately available to Ubuntu, and it sounds as though you have filled that up already. You can access other files on the C: partition by opening a Nautilus file browser, selecting "File System" on the left and then opening the host folder.

---

