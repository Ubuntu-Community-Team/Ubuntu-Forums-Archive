---
title: "linux 2.6.39 rc6 released"
date: 2011-05-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-04
Here is the release announcement:

[https://lkml.org/lkml/2011/5/3/553](https://lkml.org/lkml/2011/5/3/553)

According to it the release does not contain anything special.

---

### Post by Harry33 on 2011-05-06
Now the 2.6.39 rc6 is in Launchpad and soon in repos too.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/2.6.39-1.6](https://launchpad.net/ubuntu/oneiric/+source/linux/2.6.39-1.6)

---

### Post by rubenverweij on 2011-05-06
Has the high power consumption issue Phoronix posted about already been fixed in this version?

---

### Post by dino99 on 2011-05-06
the changelog says:  not yet

---

### Post by VinDSL on 2011-05-06
Working fine...  ;)

```

vindsl@Zuul:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"

vindsl@Zuul:~$ uname -a
Linux Zuul 2.6.39-020639rc6-generic #201105050905 SMP Thu May 5 09:12:03 UTC 2011 i686 i686 i386 GNU/Linux

vindsl@Zuul:~$ unity --version
unity 3.8.12

vindsl@Zuul:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
vindsl@Zuul:~$ 

```

---

