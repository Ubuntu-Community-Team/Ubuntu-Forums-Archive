---
title: "Linux 2.6.39 rc7 released"
date: 2011-05-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-11
The kernel 2.6.39 rc7 may very well be the last rc.
This means we may next week have the release version here.

Here is the announcement:
[https://lkml.org/lkml/2011/5/9/552](https://lkml.org/lkml/2011/5/9/552)

More info here:
[http://www.phoronix.com/scan.php?page=news_item&px=OTQyMw](http://www.phoronix.com/scan.php?page=news_item&px=OTQyMw)

---

### Post by dino99 on 2011-05-11
still not there in kernel-ppa/mainline/

---

### Post by Harry33 on 2011-05-12
> **dino99 said:**
> still not there in kernel-ppa/mainline/

OK now this rc7 is in Launchpad and soon in official repos of Oneiric.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/2.6.39-2.7](https://launchpad.net/ubuntu/oneiric/+source/linux/2.6.39-2.7)

---

### Post by dext on 2011-05-12
from what i read on the kernel.org mailing list i believe there is something missing in this Kernel that will be fixed in the .40 kernel . i'll see if i can fetch that a lil later

---

### Post by DougieFresh4U on 2011-05-12
Sorry for the 'simple' question, but I would like to know which 
would be the latest/newer kernel:
2.6.39-1
or
2.6.39-rc7
The first one not being an rc and it came through via updates the other day.
Some one please educate me :)

---

### Post by tekstr1der on 2011-05-12
> **DougieFresh4U said:**
> Sorry for the 'simple' question, but I would like to know which 
would be the latest/newer kernel:
2.6.39-1
or
2.6.39-rc7
The first one not being an rc and it came through via updates the other day.
Some one please educate me :)

2.6.39 RC7 is packaged as 2.6.39-2.7 and is the newest version found here:

[https://launchpad.net/ubuntu/+source/linux/2.6.39-2.7](https://launchpad.net/ubuntu/+source/linux/2.6.39-2.7)

2.6.39-1.6, the one you've got installed, is RC6 from last week.

---

### Post by dext on 2011-05-12
from post **#4** read this about the 2.6.39 kernel [http://lkml.indiana.edu/hypermail/linux/kernel/1105.1/00888.html](http://lkml.indiana.edu/hypermail/linux/kernel/1105.1/00888.html)

---

### Post by VinDSL on 2011-05-13
> **dino99 said:**
> still not there in kernel-ppa/mainline/
It's in there now...  :D

```

vindsl@Zuul:~$ uname -s -r && unity --version && cat /etc/lsb-release && /usr/lib/nux/unity_support_test -p
[B][COLOR="Red"]Linux 2.6.39-020639rc7-generic
unity 3.8.12[/COLOR][/B]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="**[COLOR="Red"]Ubuntu oneiric (development branch)[/COLOR]**"
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    **[COLOR="LimeGreen"]yes[/COLOR]**
Not blacklisted:          **[COLOR="LimeGreen"]yes[/COLOR]**
GLX fbconfig:             **[COLOR="LimeGreen"]yes[/COLOR]**
GLX texture from pixmap:  **[COLOR="LimeGreen"]yes[/COLOR]**
GL npot or rect textures: **[COLOR="LimeGreen"]yes[/COLOR]**
GL vertex program:        **[COLOR="LimeGreen"]yes[/COLOR]**
GL fragment program:      **[COLOR="LimeGreen"]yes[/COLOR]**
GL vertex buffer object:  **[COLOR="LimeGreen"]yes[/COLOR]**
GL framebuffer object:    **[COLOR="LimeGreen"]yes[/COLOR]**
GL version is 1.4+:       **[COLOR="LimeGreen"]yes[/COLOR]**

Unity supported:          **[COLOR="LimeGreen"]yes[/COLOR]**
vindsl@Zuul:~$ 

```

---

### Post by zika on 2011-05-13
> **VinDSL said:**
> It's in there now...  :DJust for _i386...

---

### Post by VinDSL on 2011-05-13
> **zika said:**
> Just for _i386...
Yeah, that's strange!

For a while, all they had was amd64.

Anyway, that should be the last rc.  Hopefully the final will include them both.

---

### Post by tekstr1der on 2011-05-13
> **zika said:**
> Just for _i386...

64-bit builds can found here...
[https://launchpad.net/ubuntu/+source/linux/2.6.39-2.7/+build/2500205](https://launchpad.net/ubuntu/+source/linux/2.6.39-2.7/+build/2500205)

---

### Post by zika on 2011-05-13
> **tekstr1der said:**
> 64-bit builds can found here...
[https://launchpad.net/ubuntu/+source/linux/2.6.39-2.7/+build/2500205](https://launchpad.net/ubuntu/+source/linux/2.6.39-2.7/+build/2500205)Mainline has been completed...

---

