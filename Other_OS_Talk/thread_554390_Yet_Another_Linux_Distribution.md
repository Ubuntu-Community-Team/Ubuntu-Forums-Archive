---
title: "Yet Another Linux Distribution"
date: 2007-09-18
forum: Other OS Talk
---

### Post by fistfullofroses on 2007-09-18
I have been trying to create my own Linux distribution for a while, mainly for use on my own personal machines. I know that Gentoo and Slackware and several other distributions allow for high customization but that is not what I am looking for. I know of Linux from scratch and plan upon using it. I also know of the Live CD tool kits that have been made available. My main question lies in this: are there any tools available to make an installer? or is that something I would need to program on my own? Also, are there any tools out there that are better suited to my tasks than LFS, and LiveCD tool kits?

---

### Post by init1 on 2007-09-19
> **fistfullofroses said:**
> I have been trying to create my own Linux distribution for a while, mainly for use on my own personal machines. I know that Gentoo and Slackware and several other distributions allow for high customization but that is not what I am looking for. I know of Linux from scratch and plan upon using it. I also know of the Live CD tool kits that have been made available. My main question lies in this: are there any tools available to make an installer? or is that something I would need to program on my own? Also, are there any tools out there that are better suited to my tasks than LFS, and LiveCD tool kits?
There are a number of projects that allow one to make Live CDs. They include BootCD, Linux Live, and Live Helper.
```

apt-get install bootcd
bootcdwrite

```
Creates a Live CD from your system. This only works in debian, and not in Ubuntu.

[http://www.linux-live.org/](http://www.linux-live.org/)

[http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/](http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/)
Edit: 
Live Helper is the best. Follow the instructions in the last link. I am using the Live CD I made, and I like it a lot.

---

### Post by fistfullofroses on 2007-09-20
I have used Live Helper. It wasn't exactly what I am looking for. But, it is good for making variants of Debian. What I want is to create a system that is extremely compact that I can use on all of my machines, in live form, or through install. Debian Live really doesn't allow for this (if it does please correct me). My other constraint is that I do not want to have any distros customized file hierarchy, or any distro's package system.

---

### Post by igknighted on 2007-09-20
> **fistfullofroses said:**
> I have used Live Helper. It wasn't exactly what I am looking for. But, it is good for making variants of Debian. What I want is to create a system that is extremely compact that I can use on all of my machines, in live form, or through install. Debian Live really doesn't allow for this (if it does please correct me). My other constraint is that I do not want to have any distros customized file hierarchy, or any distro's package system.

I think you can accomplish this with Fedora's revisor app.  Basically it gives you a choice of everything in the Repos to put a checkmark next to, and once you have selected what you want it double checks the dependencies and puts that stuff on the liveCD.  You could make it as heavy or light as you want.  I am fairly sure that you can put anaconda on there to install from the liveCD as well.

---

### Post by fistfullofroses on 2007-09-20
Does it allow me to go in and modify everything in the base system?

---

### Post by igknighted on 2007-09-20
> **fistfullofroses said:**
> Does it allow me to go in and modify everything in the base system?

If you mean modify the actual programs, no (well, unless you download the SRPMs and rebuild them into your own repo...).  If you mean select individually every package that goes on the CD, then (to my knowledge), yes.  I selected a metapackage when I used it to add the base KDE system, but I believe that *everything* you want you have to add yourself, including the base system.

---

### Post by init1 on 2007-09-20
> **fistfullofroses said:**
> Does it allow me to go in and modify everything in the base system?
You can do that in Live-Helper. There's config file you can edit so that it will give you a chroot during the process. You can then install what you want in addition to adding anything outside of the repos/editting files. You may not be able to mount anything in the chroot though. A USB drive might work.

---

### Post by fistfullofroses on 2007-09-20
I have used live-helper. My issue there is that I cannot get rid of the debian configuration and files. I cannot really install a non-debian kernel, or a non-debian Xserver or anything else.

---

### Post by RAV TUX on 2007-09-21
I highly advise you use rPath's rBuilder, but even better then that you can set up a developers environment and set up exactly what you want.

I have tried them all and rBuilder will be the best place to start, again for more advanced building and customization that you are referring to consult the wiki there on setting up a developers environment.

Have fun and let me know if you need any advice.

---

