---
title: "gcc-4.0 in broken packages list"
date: 2006-02-15
forum: Repositories &amp; Backports
---

### Post by lalitpatel on 2006-02-15
Hi All,

I was trying to install xchm manually. All went fine (hopefully).
I can run xchm. 

But when I start Synaptic Packet Manager, it says that there are a few
broken packages. :(

There is **gcc-4.0** in the broken packages list, when I try to fix it, It says
that:

```

47 packages will be held back and not upgraded
261 packages will be removed :cry: 
Warning: 1 essential package will be removed.
832 MB of extra space will be freed

``` 

Please help.
I use Ubuntu 5.10

---

### Post by anirban.sam on 2006-02-15
first remove all broken packages completely & reinstall

or try,

sudo apt-get update , then

sudo upgrade --fix-missing

---

### Post by lalitpatel on 2006-02-15
Hi Anirban,

Thanks for the information, but, there is gcc-4.0 in the broken packages 
when I try to reinstall gcc-4.0, it says that 281 other packages will be removed.
Thats where I am stuck up. If I try to fix gcc-4.0 and then everthing else is messed
up then its bad :(

Regards,
Lalit

---

### Post by lalitpatel on 2006-02-15
-- Message deleted --

---

