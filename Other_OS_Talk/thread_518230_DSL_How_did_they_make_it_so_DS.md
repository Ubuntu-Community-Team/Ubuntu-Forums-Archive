---
title: "DSL: How did they make it so DS?"
date: 2007-08-05
forum: Other OS Talk
---

### Post by init1 on 2007-08-05
I was wondering, how did they make DSL so small? It comes with everything I need, but takes up less space.

---

### Post by shynko on 2007-08-05
yes it is small ,but a big part of it comes from  using an outdated kernel version 2.4       I think??? also using apps that are small and less resource intensive such as using abiword instead of open office. and midget programmers lol

---

### Post by cobrn1 on 2007-08-05
The bigger brother version, DSL-N (not DSL) has the 2.6 kernel (2.6.12 at last look) and a few other mod-cons. It's only 95Mb, not bad really. That said, I find it to be a absolute pain to use, but if you find it ok then full steam ahead!

---

### Post by tgalati4 on 2007-08-05
Well, it's not exactly outdated.  They are using the latest 2.4 kernel available.  It's just that the 2.6 kernel has support for newer hardware that wouldn't work on older machines that DSL is targeted for.

I have DSL running on a P1, 166 MHz laptop and desktop.  They run fine with uptimes measured in months.  It makes a decent server platform.  What's interesting is that you can take a lot of binary code from Ubuntu and just bring it over and it runs on DSL.  Now you have to have configuration files and libraries available, but anything not in the DSL repository can be compiled to run under DSL.  You just have to manually satisfy the dependencies because there is not a default package manager.

That said, you can install apt-get and use dpkg to force packages and sometimes you will get a working application.

DSL also doesn't have extensive logging in /var/log, so when things break, you don't have info to troubleshoot.

With 128 MB of RAM you can run completely in RAM and if your hardrive is borked in an old machine, just run it from the CD.  You can save your settings on a USB stick and you won't need to reboot for months.

I started using DSL as a curiosity to revive some old garage-ware.  Now I use it for downloading distros, storing music and media, playing podcasts, and running steam servers.

Ubuntu tends to be painful on a PII, 300 MHz machine, but DSL will fly on it.

---

### Post by darksong on 2007-08-05
I always had problems with DSL on my machines, it never configures the internet/lan or sound - and it stops responding after a few minuets.

Like some people dont get vista to work, i can't get DSL :D

---

### Post by init1 on 2007-08-05
> **tgalati4 said:**
> Well, it's not exactly outdated.  They are using the latest 2.4 kernel available.  It's just that the 2.6 kernel has support for newer hardware that wouldn't work on older machines that DSL is targeted for.

I have DSL running on a P1, 166 MHz laptop and desktop.  They run fine with uptimes measured in months.  It makes a decent server platform.  What's interesting is that you can take a lot of binary code from Ubuntu and just bring it over and it runs on DSL.  Now you have to have configuration files and libraries available, but anything not in the DSL repository can be compiled to run under DSL.  You just have to manually satisfy the dependencies because there is not a default package manager.

That said, you can install apt-get and use dpkg to force packages and sometimes you will get a working application.

DSL also doesn't have extensive logging in /var/log, so when things break, you don't have info to troubleshoot.

With 128 MB of RAM you can run completely in RAM and if your hardrive is borked in an old machine, just run it from the CD.  You can save your settings on a USB stick and you won't need to reboot for months.

I started using DSL as a curiosity to revive some old garage-ware.  Now I use it for downloading distros, storing music and media, playing podcasts, and running steam servers.

Ubuntu tends to be painful on a PII, 300 MHz machine, but DSL will fly on it.
DSL has apt. You need to activate it in the menu. 
DSL is so fast I can use it in qemu :D. I installed it to a qcow image and dillo runs fine. Firefox is sluggish though.

---

### Post by shynko on 2007-08-06
I wonder what the fastest boot and login times have  been on dsl

---

### Post by fistfullofroses on 2007-08-07
Another way that the size was maintained was to use older versions of common programs and utilities.  Then for rather large apps, make them use alternate smaller libraries. Some of the apps were even straight up hacked to make them smaller.

---

### Post by cobrn1 on 2007-08-07
Also, alot of really useful utilities have been ripped out, ie, make isn't there and a few others I tried to use... (in fairness, even quite large live CDs, ie, the Zenwalk live cd at about 300Mb doesn't have make, but it's a real bugger if you need to compile stuff)

---

### Post by init1 on 2007-08-07
> **fistfullofroses said:**
> Another way that the size was maintained was to use older versions of common programs and utilities.  Then for rather large apps, make them use alternate smaller libraries. Some of the apps were even straight up hacked to make them smaller.
That makes sense. DSL even has busybox. Maybe they put a lot of apps into there. XWOAF (x windows on a floppy) contains X, JWM, a file manager, text editors, a web browser, and maybe more on one floppy. That is even more amazing.

---

### Post by Frak on 2007-08-07
Think how fast [Menuetos]("http://www.menuetos.net/") would run if it were on a thumb drive :)
THAT!! my friends is Damn Small.
100% Assembly, the images, browsers, game, and all.

---

### Post by init1 on 2007-08-08
> **Frak said:**
> Think how fast [Menuetos]("http://www.menuetos.net/") would run if it were on a thumb drive :)
THAT!! my friends is Damn Small.
100% Assembly, the images, browsers, game, and all.
I does run on a pen drive! I tried it using memdisk. It's the same way knoppix runs freedos on the livecd. And yes, that is indeed that is truly damn small. Not to mention damn fast also. 
```

apt-get install syslinux mtools lilo
fdisk (first partition of usb drive is fat32, with boot flag)
lilo -M (give it a new mbr)
syslinux -sf (drive is not mounted, do it on the first partition, not the whole disk)
copy the zipped files in

```
I'll post the files later.

---

