---
title: "alsa modules"
date: 2007-12-09
forum: Packaging and Compiling Programs
---

### Post by ztomic on 2007-12-09
While trying to build alsa modules, using /usr/share/doc/alsa-source/README.Debian as a guide, I get this error using make-kpkg:
```

The UTS Release version in include/linux/utsrelease.h
     "2.6.22-14-generic" 
does not match current version:
     "2.6.22.9" 
Please correct this.
make: *** [modules-image] Error 2

```

Here's what I've done so far:
```

#apt-get install alsa-source
#apt-get install linux-headers-2.6.22-14-generic
#cp -rpL /usr/src/linux-headers-2.6.22-14-generic /tmp
#cd /usr/src
#rm -rf modules/alsa-driver
#tar jxf alsa-driver.tar.bz2
#cd /tmp/linux-headers-2.6.22-14-generic
#sudo make-kpkg modules-image

```
To solve the problem I changed the top level [COLOR="DarkOliveGreen"]Makefile[/COLOR] in /tmp/linux-headers-2.6.22-14-generic/:
```

- EXTRAVERSION = .9
+ EXTRAVERSION = -14-generic

```
The package will then compile.

---

### Post by ztomic on 2007-12-11
bump..
Is there anything that can be done easier?

2 points I am assuming: 1) building the alsa with the wrong headers will not work. 2) upgrading the kernel will break the built alsa modules.

---

