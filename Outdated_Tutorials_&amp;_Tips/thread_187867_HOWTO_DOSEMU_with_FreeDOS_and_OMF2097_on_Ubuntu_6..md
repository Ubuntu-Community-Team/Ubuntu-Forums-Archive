---
title: "HOWTO: DOSEMU with FreeDOS and OMF:2097 on Ubuntu 6.06"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by niraj on 2006-06-03
Hi all, I've just written a guide to set up One Must Fall: 2097 (old 1994 DOS game) on Ubuntu 6.06 (or any other debian distros for that matter) The guide covers installing DOSEMU, FreeDOS for DOSEMU, Xfonts for DOSEMU and then installing OMF:2097 in DOS, and customizations for DOSEMU. It can be found here:

[http://niraj.cubicsnow.com/omfuniverse.tk/guides/2097linux/2097linux.htm]("http://niraj.cubicsnow.com/omfuniverse.tk/guides/2097linux/2097linux.htm")

Hope someone finds this useful, it's my first HOWTO :)

---

### Post by Laterix on 2006-06-03
[QUOTE=niraj]
Hope someone finds this useful, it's my first HOWTO :)[/QUOTE]
Thanks, have to try this when I get home! One must fall is a classic. It was one of my favourite beat'em up games.

---

### Post by UbuWu on 2006-06-03
You could also use dosbox, which is in the ubuntu repositories, so easy to install, and which in my experience has always performed better than dosemu.

---

### Post by UbuWu on 2006-06-03
Btw. dosbox, freedos and xfont are also only an apt-get away both in Debian and Ubuntu, that would make your howto a lot simpler.

---

### Post by niraj on 2006-06-04
You're welcome :) Thanks for the comments. I wasn't aware that those were both available in the repositories. I'll do a little checking to see if they're the same and then update my guide if they are.

If someone is interested in One Must Fall, you can visit [my fansite]("http://www.omfuniverse.tk/") for pretty much everything to do with it :)

Also, I'm running it on a 366MHz Pentium II with 64MB of RAM (Xubuntu). It runs really nice. I wouldn't dream of running DOSBox on a system like that. Unless DOSBox's Linux performance is way better than it's Windows counterpart. I also run DOSBox on a 2.7GHz Windows XP machine with 1GB of RAM, and it doesn't run too well. At least not when considering the hardware difference.

---

### Post by gmc on 2006-06-04
Looks like dosemu from the repositories is a wee bit broken...

```

$ dosemu
ERROR: Unable to open console to evaluate the keyboard map.
Please specify your keyboard map explicitly via the $_layout option

```

G

---

### Post by niraj on 2006-06-05
Yeah, the .debs I'm using are like that as well. Probably easily fixed in the configuration.

---

### Post by dtfinch on 2006-06-05
I think there's more than one problem with the dosemu in the repositories.

After specifying the $_layout option, it got further, but bailed after outputting the following errors:
ERROR: cpu exception in dosemu code outside of VM86()!
trapno: 0x0e  errorcode: 0x00000004  cr2: 0x468a5b2d
eip: 0x468a5b2d  esp: 0xbfbdffb5  eflags: 0x00210282
cs: 0x0073  ds: 0x007b  es: 0x007b  ss: 0x007b
Page fault: read instruction to linear address: 0x468a5b2d
CPU was in user mode
Exception was caused by non-available page
ERROR: Fault handler re-entered! signal=11 _trapno=0xE
ERROR: cpu exception in dosemu code outside of VM86()!
trapno: 0x0e  errorcode: 0x00000004  cr2: 0x468a5b23
eip: 0x0805f160  esp: 0x083dd860  eflags: 0x00210202
cs: 0x0073  ds: 0x007b  es: 0x007b  ss: 0x007b
Page fault: read instruction to linear address: 0x468a5b23
CPU was in user mode
Exception was caused by non-available page

xdosemu bails earlier saying the vga font is missing, even though I had installed the xfonts-dosemu package.

As far as I can tell the dosemu in the repositories is 100% nonfunctioning, or I missed something.

After fiddling with it for a while longer, I uninstalled the dosemu packages from the repository, downloaded the official rpm, installed it with alien, and it all worked.

In the past I've found that Duke Nukem 3D plays well on dosemu.

EDIT: I ran into the above problems before reading this howto, which is why I didn't try the debian debs after the ubuntu debs didn't work.

---

### Post by niraj on 2006-06-11
I was told once that the dosemu in the repositories don't work, but that was back when Breezy Badger was new. I thought it would have been fixed by now... Anyway, I suggest you try the files in my guide and see if that works for you. It seems to have worked for a few people including myself.

---

### Post by jISh on 2006-07-12
How can I install this now? None of the package versions from Debian repos work. they all require a different version of libc6 when I try to install them.

---

