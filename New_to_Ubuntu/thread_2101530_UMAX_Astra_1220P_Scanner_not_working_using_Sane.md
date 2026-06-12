---
title: "UMAX Astra 1220P Scanner not working using Sane"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by tlhIngan on 2013-01-04
I've seen a few threads here about getting UMAX Astra 1220P scanners to work on Ubuntu 12.04 using Sane.
The advise there is to download Sane 1.0.18 from the developper's website and install it. I did this, but it doesn't work. xsane cannot detect any scanner.
I've posted to those other threads to inquire about any progress people may have made, but the only responses were from moderators closing the thread.

Has anybody had any success installing Sane? The developper's instructions are a little too generic for a Linux noob.
I'm running Lubuntu 12.04, the scanner connects to a parallel port. It worked fine under Windows.

---

### Post by squakie on 2013-01-04
A lot of parallel port scanners won't work with Linux.  Things to try:

be sure you are a member of the "scanner" group

try running sane as super user (sudo sane) to see if there is a permissions problem


Things to know:

you would probably need the parport module is loaded

if you are using a hybrid parallel adapter - one that requires a driver in Windows - then you probably will not get the adapter itself to work in Linux.

if you are using something like a parallel to USB adapter so you can plug your parallel scanner in via a cable to a USB port, it may not be possible to get the adapter to work

---

### Post by tlhIngan on 2013-01-05
The parallel port itself works, my printer uses that port without any issues. It's an actual parallel port right off the motherboard.
I'll look into those other things you suggested.
Thanks!

---

### Post by tlhIngan on 2013-01-05
I added myself to the scanner group.
libieee1284 is installed.
sudo umax_pp got the scanning head to turn on and twitch.

What am I missing?

---

### Post by DuckHook on 2013-01-05
> **tlhIngan said:**
> What am I missing?

Try installing [this]("http://sourceforge.net/projects/umax1220p/") driver.

---

### Post by tlhIngan on 2013-01-05
Okay, I'm now getting an output file from umax_pp.
It's gibberish, but it's a start.

xsane still isn't finding any scanners though.
What am I looking for now?
Configuration?

[Scanner output file]("http://www.francescorp.com/Pictures/out.pnm")

---

### Post by mips on 2013-01-05
Check your bios as I know you can also set the parallel port to different 'modes'. Just a stab in the dark.

---

### Post by tlhIngan on 2013-01-05
I'll give it a shot, but this scanner was working fine under windows on this pc.

---

### Post by squakie on 2013-01-05
You have to remember Linux is a different animal - and somebody/company wrote the driver for Windows.  Do be sure your parallel port is set up correctly, though I assume that since you did get something back that may not be the problem - it may still be the Linux driver.

---

### Post by tlhIngan on 2013-01-05
Tried ECP, EPP and ECP+EPP modes for the parallel port (from the BIOS), nuthin. I reinstalled Windows on a spare hard drive and I'm scanning from there and then fetching the files in Lubuntu. It's annoying, but it works.
I always called this PC a dinosaur (specs in my signature), but I guess parallel ports are from the time the Earth cooled. If anybody ever figures this out in a simpler way than (in)sane, PM me.

---

### Post by kurt18947 on 2013-01-05
It seems that some "legacy" hardware support is not very good in linux.  Floppy drives, and 'winmodems' come to mind.  Perhaps parallel ports scanners is another.   All manufacturers are compelled to support windows.  Most do not feel the same need to support linux.  Much hardware support in linux is provided by users, not by manufacturers.  I do try to support manufacturers who support linux and let them know I do - and why.

---

### Post by tlhIngan on 2013-01-06
I hear ya. There's just so much involved in getting a parallel port scanner working, I'm just not at that level yet linux-wise.
Maybe someday I'll figure this out.
I believe the (in)sane interface worked on older releases of Ubuntu, it's probably just a matter of finding the part that got removed from Ubuintu along the way and now prevents this package from working on more recent releases of Ubuntu.

---

### Post by squakie on 2013-01-06
> **tlhIngan said:**
> I hear ya. There's just so much involved in getting a parallel port scanner working, I'm just not at that level yet linux-wise.
Maybe someday I'll figure this out.
I believe the (in)sane interface worked on older releases of Ubuntu, it's probably just a matter of finding the part that got removed from Ubuintu along the way and now prevents this package from working on more recent releases of Ubuntu.


I don't really think so.  I've used Ubuntu for many years - including back when I had a Umax Astra 1200P.  It never worked with Linux.

---

### Post by mips on 2013-01-06
[http://manpages.ubuntu.com/manpages/hardy/man5/sane-umax_pp.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/sane-umax_pp.5.html)
[http://umax1220p.sourceforge.net/](http://umax1220p.sourceforge.net/)
[http://forums.linuxmint.com/viewtopic.php?f=49&t=1879](http://forums.linuxmint.com/viewtopic.php?f=49&t=1879)

---

### Post by tlhIngan on 2013-01-06
> **mips said:**
> [http://manpages.ubuntu.com/manpages/hardy/man5/sane-umax_pp.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/sane-umax_pp.5.html)
[http://umax1220p.sourceforge.net/](http://umax1220p.sourceforge.net/)
[http://forums.linuxmint.com/viewtopic.php?f=49&t=1879](http://forums.linuxmint.com/viewtopic.php?f=49&t=1879)

That last link has some information I've been missing.
Thanks!

---

### Post by tlhIngan on 2013-01-06
argh!
That guy from Linux Mint was dancing between 2 different versions of Sane!
He didn't specify which version he finally got it working with!
I registered on that board and sent him a message.

---

