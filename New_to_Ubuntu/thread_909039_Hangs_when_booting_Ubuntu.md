---
title: "Hangs when booting Ubuntu"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Just Tom on 2008-09-03
Hey guys,

I've seen a lot of posts with a similar problem to mine but their solutions never seem to work for me. I bought a new laptop (LG R405-A) a few weeks ago and Vista has me about to shoot myself so I wanted to dual-boot Ubuntu to get away from it and learn to use Linux.

The problem I'm having is that when I try to boot the computer into Ubuntu I get a line 'Running local boot scripts' and then it just hangs there with a useless cursor. I've tried installing it already and it installed fine (wouldn't load any graphics so it was a text-based installer) but got stuck on the first boot the same way as if I run off the Live CD. Others have had this problem and fixed it by changing settings with their graphics before running the Live CD or installing and some have replaced their graphics cards but the options they had I can't find and I don't really want to have to change my graphics card right now (ATI Radeon Xpress 1300M).

I've also bailed out on Ubuntu already and tried installing Fedora instead. I didn't get any problems installing or anything (text installer again, though) but when I went to boot it gave me a text login / password so I tried root and it just took me to a regular command line. I've tried startx there but it failed and brought me back to the same point.

Does my graphics card not work with Linux or something? Please help me and bear in mind that I have no knowledge of how to use Linux. Thank you.

---

### Post by overdrank on 2008-09-03
> **Just Tom said:**
> Hey guys,

I've seen a lot of posts with a similar problem to mine but their solutions never seem to work for me. I bought a new laptop (LG R405-A) a few weeks ago and Vista has me about to shoot myself so I wanted to dual-boot Ubuntu to get away from it and learn to use Linux.

The problem I'm having is that when I try to boot the computer into Ubuntu I get a line 'Running local boot scripts' and then it just hangs there with a useless cursor. I've tried installing it already and it installed fine (wouldn't load any graphics so it was a text-based installer) but got stuck on the first boot the same way as if I run off the Live CD. Others have had this problem and fixed it by changing settings with their graphics before running the Live CD or installing and some have replaced their graphics cards but the options they had I can't find and I don't really want to have to change my graphics card right now (ATI Radeon Xpress 1300M).

I've also bailed out on Ubuntu already and tried installing Fedora instead. I didn't get any problems installing or anything (text installer again, though) but when I went to boot it gave me a text login / password so I tried root and it just took me to a regular command line. I've tried startx there but it failed and brought me back to the same point.

Does my graphics card not work with Linux or something? Please help me and bear in mind that I have no knowledge of how to use Linux. Thank you.

Hi and wlecome, some of the newer graphics cards can have some issues with Ubuntu. If you still have Ubuntu installed and can boot into recovery mode which is usually the second choice from the grub then you can try and use the xfix option to correct the graphics.

---

### Post by Dougie187 on 2008-09-03
You could also go to ati's website and see if they have a linux driver available for the card.

---

### Post by Just Tom on 2008-09-05
I just checked the ATI driver lists and they have drivers for Linux for a Radeon X1300 series so I guess that includes mine (Radeon Xpress 1300M) and they're just curring Xpress down to X to save space.

I uninstalled Ubuntu a few weeks ago and would much prefer running the Live CD before reinstalling so is there any way to get the Live CD to use the driver I've found? I never get a useful command prompt line or anything where I could try the xfix idea.

I guess my next option will be to reinstall and try the restore mode though I'm a total noob with Linux so when I get in I won't really know what to do (which is why the Live CD is a much nicer option to me).

---

### Post by knix on 2008-09-05
I believe Xpress is just a mobile X (I could be wrong there).

Anyhow (you can do this on the cd) download and install the driver. Then (if you're root) ```
nano /etc/X11/xorg.conf
``` (use ```
sudo nano /etc/X11/xorg.conf
``` if not).Then, modify ypur xorg.conf to use the fglrx driver (should appear ```
Driver    fglrx
``` in section Device.
Then save and exit. press Ctr+Alt+backspace to restart X server.


Edit: I just found this - use method 2
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

I assume you're trying hardy

---

