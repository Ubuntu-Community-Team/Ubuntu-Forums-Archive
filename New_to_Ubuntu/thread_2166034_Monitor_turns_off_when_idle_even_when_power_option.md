---
title: "Monitor turns off when idle even when power options are set otherwise"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by moltenicee on 2013-08-07
My Dell monitor, attached to my laptop running Xubuntu 13.04 goes into standby mode in regular intervals (~10 minutes) when I do not move the mouse or type (usually when listening to music or watching videos.)

This is purely a software issue because my monitor does not have any powersaving functionality, and before I installed xubuntu, I was running Linux Mint and was able to turn off any display dimming/switching off.

Here are screenshots of any relevant power settings:

Screensavers turned off:

[[IMG]http://www.zimagez.com/miniature/screenshot-08072013-122028pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-08072013-122028pm.php")

Unchecked screensaver on startup:

[[img]http://www.zimagez.com/miniature/screenshot-08072013-122209pm.php[/img]](http://www.zimagez.com/zimage/screenshot-08072013-122209pm.php)

Power saving disabled:

[[img]http://www.zimagez.com/miniature/screenshot-08072013-122307pm.php[/img]](http://www.zimagez.com/zimage/screenshot-08072013-122307pm.php)

[[img]http://www.zimagez.com/miniature/screenshot-08072013-122338pm.php[/img]](http://www.zimagez.com/zimage/screenshot-08072013-122338pm.php)
(same settings for "On Battery")

I would greatly appreciate your help.

---

### Post by lego11 on 2013-08-07
Hi,
Could you provide your video card information?
Were you running Linux Mint with Nvidia/Ati's drivers installed?
Thanks

---

### Post by moltenicee on 2013-08-07
Hey, thanks for the reply.

I have an ASUS N53JF-XE1 laptop from 2011 with an Nvidia 425M. It has Nvidia Optimus, so I installed primusrun using this [http://www.webupd8.org/2012/11/primus-better-performance-and-less.html](http://www.webupd8.org/2012/11/primus-better-performance-and-less.html) (I did the same on Linux Mint.)

---

### Post by lego11 on 2013-08-07
Hi,
Are you using the monitor as a mirror of the internal screen, or as a 2nd screen? I cannot help you further since this is not my cup of tea :(

---

### Post by moltenicee on 2013-08-07
Never mind, I fixed it. Turns out enabling "PolicyKit" in startup fixed the issue and also fixed some issues with updates that I was having.

I appreciate your effort.

/request close

---

