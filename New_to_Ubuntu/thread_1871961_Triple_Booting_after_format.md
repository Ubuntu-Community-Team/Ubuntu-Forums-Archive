---
title: "Triple Booting after format"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by 1childish1 on 2011-10-29
Hello! First off, I want to say that I am a complete newbie with Ubuntu and I don't really know much about it. I also didn't know if this was the right section to put this thread in (I was struggling between Absolute Begnner Talk and Installing & Upgrading).

I want to have Win 7, Ubuntu 11.10 and BackTrack 5 in my hard drive (after formatting it).
My question is if this is a good idea and if it is possible. Also, if anyone can tell me which one should I install first and how much disk space should I use for each (will be using mostly Win 7 and Ubuntu).
A tutorial (if any) would be a lot of help!

Reason for doing this is I want to learn how to use Ubuntu, I need Win 7 for school and I use BackTrack 5 for curiosity (I don't want to be using the Live CD all the time). I have searched about installing BackTrack 5's components (apps and stuff) into Ubuntu, but I found that this is not recommended and quite impossible (for me that is).

Thank you!!

_Computer Info:_

Sony VAIO VGN-NW270F laptop
Windows 7 sp1 x64
Intel Core 2 Duo CPU @2.20 GHz each
4GB of RAM
290 GB HDD

---

### Post by MG&amp;TL on 2011-10-29
Hello! I would think this:

1. Install Windows. Windows does not always play nice with other operating systems when it installs.

2. Install Ubuntu. Ubuntu is a little more stable than BT (IMO). Select the 'install alongside windows 7' option on the installer.

3. Bit of variance here. You want a hard drive install because the CD is slow. How about a USB? My USB distros boot in around twice the time that the HDD ones do, so I would suggest a USB. Use Unetbootin and select the backtrack release in the drop-down at the top. I say this because three partitions can be a bit of a pain, and there are currently some issues (on some hardware) with HDD installs of backtrack kernel-panicking. (for instance on my VAIO.) See here: [http://www.pskl.us/wp/?p=630]("http://www.pskl.us/wp/?p=630")

If you do want a HDD install, insert the BT cd and resize the partitions to accomadate BT.

---

### Post by Blaqksheep on 2011-10-30
Have a look at your partition tree before you proceed.  There might be hidden or irremovable partitions and HDDs can only support 4 primary partitions.

---

### Post by MG&amp;TL on 2011-10-30
Indeed you are right, but linux can be installed to a logical partition, see here:

[http://ubuntuforums.org/showthread.php?t=282018]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by MG&amp;TL on 2011-10-30
Basic Ubuntu/Linux information: [http://psychocats.net/ubuntu/index.php]("http://psychocats.net/ubuntu/index.php")

---

### Post by 1childish1 on 2011-10-30
Thank you everyone for your answers!! I think I'll just do a dual boot instead (Ubuntu and Windows) seeing that it can have a kernel panic (which I have yet to learn about)...

> **MG&TL said:**
> 

You want a hard drive install because the CD is slow. How about a USB? My USB distros boot in around twice the time that the HDD ones do, so I would suggest a USB. Use Unetbootin and select the backtrack release in the drop-down at the top. I say this because three partitions can be a bit of a pain, and there are currently some issues (on some hardware) with HDD installs of backtrack kernel-panicking. (for instance on my VAIO.) See here: [http://www.pskl.us/wp/?p=630](http://www.pskl.us/wp/?p=630)

If you do want a HDD install, insert the BT cd and resize the partitions to accomadate BT.

Well, not because it is slow (it isn't), it's just that I am a bit lazy carrying around the CD, but I think I'll do the USB instead since it is much easier for me to carry it around with me...

> **Blaqksheep said:**
> 

Have a look at your partition tree before you proceed.  There might be  hidden or irremovable partitions and HDDs can only support 4 primary  partitions.     

Need to learn about partitions... All I know is that I have 3 primary partitions (Recovery [7.90 GB] || System, Active, Primary [100 MB] || Boot, Page File, Crash Dump, Primary [290 GB])

> **MG&TL said:**
> 

Indeed you are right, but linux can be installed to a logical partition, see here:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

I'll see about that... but I first need to know about my partitions...


> **MG&TL said:**
> 

Basic Ubuntu/Linux information: [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Will have a look at this!! Thanks!!

---

