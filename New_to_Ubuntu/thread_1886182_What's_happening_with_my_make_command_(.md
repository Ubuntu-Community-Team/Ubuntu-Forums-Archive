---
title: "What's happening with my make command :("
date: 2011-11-24
forum: New to Ubuntu
---

### Post by ASH.AT on 2011-11-24
[B]Hello Ubuntus;

since i started using Ubuntu ( i was using  windows :S ), each time i try to compile any package i get errors with make command, now i'm trying to compile MadWifi 0.9.4 and my kernel is 2.6.38-8-generic...

I changed into the madwifi dir and just  typed :

```
sudo make
```but sadly i got:

./kernelversion.c:13:30: fatal error: linux/utsrelease.h: No such file or directory
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH.  Stop.

i so on MadWifi's website that this release can patch my wireless card to use injection only if my kernel is above 2.6.28, mine are 2.6.38

so what's happening :'(

p.s: i used gnome to unpack the package, u know "extract here", don't know if it really cares

Thanks guys
[/B]

---

### Post by ptrakk on 2011-11-24
i think you need your kernel headers and source in a certain folder. something like apt-get install linux-headers linux-source. i dunno what the package is but you can find them using synaptic

---

### Post by sandyd on 2011-11-24
> **ASH.AT said:**
> [B]Hello Ubuntus;

since i started using Ubuntu ( i was using  windows :S ), each time i try to compile any package i get errors with make command, now i'm trying to compile MadWifi 0.9.4 and my kernel is 2.6.38-8-generic...

I changed into the madwifi dir and just  typed :

```
sudo make
```but sadly i got:

./kernelversion.c:13:30: fatal error: linux/utsrelease.h: No such file or directory
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH.  Stop.

i so on MadWifi's website that this release can patch my wireless card to use injection only if my kernel is above 2.6.28, mine are 2.6.38

so what's happening :'(

p.s: i used gnome to unpack the package, u know "extract here", don't know if it really cares

Thanks guys
[/B]
why don't you just use the deb package?
[http://www.marlow.dk/site.php/tech/madwifi](http://www.marlow.dk/site.php/tech/madwifi)

---

### Post by ASH.AT on 2011-11-25
[B]Thanks guys, i think both of you talked about the same thing, the link provided the same info about installing kernel headers in the requirements section... So i guess there's nothing wrong in my make command :)
[/B]

---

