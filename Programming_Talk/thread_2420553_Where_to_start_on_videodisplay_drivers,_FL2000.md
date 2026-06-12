---
title: "Where to start on video/display drivers, FL2000"
date: 2019-06-06
forum: Programming Talk
---

### Post by safetycaptain on 2019-06-06
Hi' i'd like to create a display driver for the FL2000. 

If anyone is familiar with the flow of data from Xorg to a buffer fed to a device that causes lights..... I would love to try my hand at this.

---

### Post by TheFu on 2019-06-06
GPU developers don't hangout here.
I would start there: [https://github.com/FrescoLogic/FL2000](https://github.com/FrescoLogic/FL2000) , but it appears that code hasn't been worked on in years and won't work with any supported version of Ubuntu.

---

### Post by safetycaptain on 2019-06-07
I've gotten the kernel module compiled and installed, I've also got Linus Torvalds smiling on a vga display off to the side of my cluttered desk. ([https://bitbucket.org/mgulin/fl2000_show_static/src/master/](https://bitbucket.org/mgulin/fl2000_show_static/src/master/)) 
So I know I have a few things to better understand
Xorg, Display managers, really the entire X system, I've got a small overview of compiling kernel modules ( [https://github.com/FrescoLogic/FL2000](https://github.com/FrescoLogic/FL2000)) but now i need to figure out who's in charge or producing data , the video buffer, the management... etc

---

### Post by safetycaptain on 2019-06-07
[https://www.x.org/wiki/DeveloperStart/](https://www.x.org/wiki/DeveloperStart/)
Jackpot, I'll keep a thread here on what i learn along the way. 

[IMG]https://www.x.org/wiki/guide/xorg.svg[/IMG]

Next step, ddx

---

### Post by safetycaptain on 2019-06-07
[https://cgit.freedesktop.org/~jbarnes/xf86-video-intel/](https://cgit.freedesktop.org/~jbarnes/xf86-video-intel/)

---

### Post by safetycaptain on 2019-06-07
[https://www.x.org/wiki/Development/Documentation/HowVideoCardsWork/](https://www.x.org/wiki/Development/Documentation/HowVideoCardsWork/)

Sadly the intro to writing a video driver is broken [https://www.x.org/wiki/Development/Documentation/XorgVideoHOWTO/](https://www.x.org/wiki/Development/Documentation/XorgVideoHOWTO/)

---

