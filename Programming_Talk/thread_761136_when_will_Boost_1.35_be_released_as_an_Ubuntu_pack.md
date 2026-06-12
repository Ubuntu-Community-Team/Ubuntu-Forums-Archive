---
title: "when will Boost 1.35 be released as an Ubuntu package?"
date: 2008-04-20
forum: Programming Talk
---

### Post by jmartrican on 2008-04-20
I noticed that the Ubuntu package for Boost 1.35 is not out yet.  Boost 1.35 came out in late March.  Does anyone know the turnaround time for new releases to be packaged for Ubuntu?

---

### Post by mssever on 2008-04-20
Maybe it's in Hardy already, though I don't know since I'm not running Hardy yet.

In general, Ubuntu doesn't upgrade packages within a given release. So whatever version is included in Gutsy will remain in Gutsy. Exceptions are for security fixes, some bug fixes, and occasional backports if there's sufficient interest to justify a backport.

Additionally, Ubuntu packages come from Debian, and I don't know how long it takes Debian to update. The Debian website should tell you the current version in Debian unstable.

---

### Post by WW on 2008-04-21
Looks like hardy has 1.34: [http://packages.ubuntu.com/search?keywords=libboost&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=libboost&searchon=names&suite=hardy&section=all)

---

### Post by 6174 on 2008-04-21
Coincidentally I just researched this myself as there is a function I want to use out of 1.35 in one of my programs.

From what I can tell, Ubuntu is pretty much following what Debian does on this package, particularly since the people listed as maintainers overlap. Hardy still has 1.34.1. Sid (Debian's development branch) also has 1.34.1 The Debian maintainers are currently trying to work out how to add 1.35 with the minimum potential of breaking programs that depend on Boost. You can read more about what they are doing in the corresponding Debian bug ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=473752](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=473752)).

---

### Post by Zdravko on 2008-04-21
I want to use Boost 1.35 too. If Ubuntu does not allow me to use it, I won't use Ubuntu! :(

---

### Post by mssever on 2008-04-21
> **Zdravko said:**
> I want to use Boost 1.35 too. If Ubuntu does not allow me to use it, I won't use Ubuntu! :(

You can, of course, compile it yourself until Debian gets it packaged properly; then you can grab Debian's pakage and build it under Ubuntu and your Ubuntu will support it.

---

### Post by gladandong on 2008-07-07
I have also waited it for a long time.

---

### Post by weirdfox on 2008-07-14
There is some deb file made for intrepid now and they work with Hardy.

You can grab them here :
[https://launchpad.net/ubuntu/intrepid/+source/boost1.35/](https://launchpad.net/ubuntu/intrepid/+source/boost1.35/)

Here's a quick route (for 1.35.0-5):
```
wget http://launchpadlibrarian.net/14813106/libboost1.35-doc_1.35.0-5_all.deb http://launchpadlibrarian.net/14813108/libboost1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813133/libboost-wave1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813134/libboost-wave1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813131/libboost-thread1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813132/libboost-thread1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813129/libboost-test1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813130/libboost-test1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813127/libboost-system1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813128/libboost-system1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813125/libboost-signals1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813126/libboost-signals1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813123/libboost-serialization1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813124/libboost-serialization1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813121/libboost-regex1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813122/libboost-regex1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813117/libboost-program-options1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813118/libboost-program-options1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813115/libboost-iostreams1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813116/libboost-iostreams1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813113/libboost-graph1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813114/libboost-graph1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813111/libboost-filesystem1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813112/libboost-filesystem1.35-dev_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813109/libboost-date-time1.35.0_1.35.0-5_i386.deb http://launchpadlibrarian.net/14813110/libboost-date-time1.35_1.35.0-5_i386.deb
sudo dpkg -i libboost*.deb
rm libboost*.deb

```

If the install show some unmet dependencys, just complete setup with :
```

sudo apt-get install -f

```

good luck !

---

### Post by MickePicke on 2008-08-10
> **weirdfox said:**
> There is some deb file made for intrepid now and they work with Hardy.

You can grab them here :
[https://launchpad.net/ubuntu/intrepid/+source/boost1.35/](https://launchpad.net/ubuntu/intrepid/+source/boost1.35/)

Here's a quick route (for 1.35.0-5):
...

If the install show some unmet dependencys, just complete setup with :
...

good luck !

Thanks! 
I made it install without any dependency problems by installing libicu-dev and adding [http://launchpadlibrarian.net/14813110/libboost-date-time1.35-dev_1.35.0-5_i386.deb](http://launchpadlibrarian.net/14813110/libboost-date-time1.35-dev_1.35.0-5_i386.deb).

---

### Post by StOoZ on 2008-08-10
I installed it from source, and it works like a charm , just read the docs how to install and link the stuff...

---

