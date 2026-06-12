---
title: "can't compile mplayer"
date: 2010-09-16
forum: Packaging and Compiling Programs
---

### Post by masterdrark on 2010-09-16
hello everyone im new to linux an ubuntu forums...
im in the process of learning does everything works in linux and im trying to build the mplayer package.
so i started it simple by ./configure --enable-gui
all good so far but in the 'make' i had a problem
```

libmpcodecs/ad_realaud.o: In function `preinit':
ad_realaud.c:(.text+0x83c): undefined reference to `dlopen'
ad_realaud.c:(.text+0x856): undefined reference to `dlsym'
ad_realaud.c:(.text+0x86b): undefined reference to `dlsym'
ad_realaud.c:(.text+0x880): undefined reference to `dlsym'
ad_realaud.c:(.text+0x895): undefined reference to `dlsym'
ad_realaud.c:(.text+0x8aa): undefined reference to `dlsym'
libmpcodecs/ad_realaud.o:ad_realaud.c:(.text+0x8bf): more undefined references to `dlsym' follow
libmpcodecs/ad_realaud.o: In function `preinit':
ad_realaud.c:(.text+0x984): undefined reference to `dlclose'
ad_realaud.c:(.text+0xb31): undefined reference to `dlerror'
libmpcodecs/vd_realvid.o: In function `uninit':
vd_realvid.c:(.text+0x377): undefined reference to `dlclose'
libmpcodecs/vd_realvid.o: In function `init':
vd_realvid.c:(.text+0x8c4): undefined reference to `dlopen'
vd_realvid.c:(.text+0x8de): undefined reference to `dlsym'
vd_realvid.c:(.text+0x8f3): undefined reference to `dlsym'
vd_realvid.c:(.text+0x908): undefined reference to `dlsym'
vd_realvid.c:(.text+0x91d): undefined reference to `dlsym'
vd_realvid.c:(.text+0x958): undefined reference to `dlsym'
libmpcodecs/vd_realvid.o:vd_realvid.c:(.text+0x96d): more undefined references to `dlsym' follow
libmpcodecs/vd_realvid.o: In function `init':
vd_realvid.c:(.text+0x9e6): undefined reference to `dlclose'
vd_realvid.c:(.text+0xb80): undefined reference to `dlerror'
loader/elfdll.o: In function `ELFDLL_dlopen':
elfdll.c:(.text+0x3b): undefined reference to `dlopen'
elfdll.c:(.text+0xc5): undefined reference to `dlopen'
loader/elfdll.o: In function `ELFDLL_LoadLibraryExA':
elfdll.c:(.text+0x280): undefined reference to `dlopen'
elfdll.c:(.text+0x3a4): undefined reference to `dlclose'
elfdll.c:(.text+0x4af): undefined reference to `dlopen'
libmpcodecs/vd_xanim.o: In function `uninit':
vd_xanim.c:(.text+0xa9a): undefined reference to `dlclose'
libmpcodecs/vd_xanim.o: In function `init':
vd_xanim.c:(.text+0xbbc): undefined reference to `dlopen'
vd_xanim.c:(.text+0xbd7): undefined reference to `dlsym'
vd_xanim.c:(.text+0xbe0): undefined reference to `dlerror'
vd_xanim.c:(.text+0xc13): undefined reference to `dlclose'
vd_xanim.c:(.text+0xee9): undefined reference to `dlerror'
vd_xanim.c:(.text+0x1261): undefined reference to `dlclose'
collect2: ld returned 1 exit status
make: *** [mencoder] Error 1

```
i tired to google it a bit but i had no luck at all = \ nothing helpful 
any solution to this?

---

### Post by mc4man on 2010-09-16
You haven't mwntioned what mplayer source you're using and what ubuntu release.

If using a current svn then maybe clean your source, run svn up and try again.
(I wouldn't enable the gui, just build the cli mplayer and use a frontend such as gnome-mplayer or smplayer, available in ubuntu repo's.

If on lucid (10.04) you may wish to use or at least refer to this guide on building a svn mplayer
(similar guides avail. in same sub forum for older ubuntu releases

[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

---

### Post by masterdrark on 2010-09-16
thank you for your quick answer
im using ubuntu 10.4 lucid
and im trying to build mplayer from the official source..
downloaded the tar from [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
the binaries are from there too

---

### Post by MadCow108 on 2010-09-17
do you have all build dependencies installed?
sudo apt-get build-dep mplayer

the missing functions are in the dynamic loading library libdl.
It is included in libc6 package in ubuntu.

>apt-file search libdl.so
libc6: /lib/libdl.so.2
libc6-dev: /usr/lib/libdl.so

>nm --dynamic /usr/lib/libdl.so | grep dlopen
0000000000000eb0 T dlopen

if this is installed and it does not work this indicates a problem in the mplayer build (a missing -ldl flag)

---

