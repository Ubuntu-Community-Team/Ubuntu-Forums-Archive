---
title: "Very Small Linux OS?"
date: 2009-01-31
forum: Other OS Talk
---

### Post by Musick Man on 2009-01-31
Hi,

I just got my hands on a old Dell Latitude XPi CD Laptop, running Windows 98. And I dont want windows on it. I was wondering if there is a Linux OS out there that can run on these specs. 

32 MB of Ram
3.02 GB HD

Not sure about the processor speed, but under the System propteries, it says it has a Genuine Intel Pentium processor Intel MMX Technology.

Well, is it possible to get a Linux OS on this, or should I stick with Windows 98 on it. 

Thanks,
Musick Man

---

### Post by cardinals_fan on 2009-01-31
SliTaz is great.  I would **not** recommend running X (even Xvesa) on that machine.  A SliTaz CLI system would work fine.

With all that said, installing SliTaz would be a bit tricky.  I'm not sure if you could boot the live CD with that little RAM.

NetBSD ought to work.

---

### Post by smartboyathome on 2009-01-31
Tiny Core Linux? :)

---

### Post by Twitch6000 on 2009-01-31
[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

TinyCoreLinux should run on that machine.

---

### Post by smartboyathome on 2009-01-31
> **Twitch6000 said:**
> [http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

TinyCoreLinux should run on that machine.

Beat you to it. :p

---

### Post by init1 on 2009-02-01
ttylinux should work fine
[http://www.minimalinux.org/ttylinux/](http://www.minimalinux.org/ttylinux/)

---

### Post by Sorivenul on 2009-02-01
My vote here goes to NetBSD if you are okay without running anything truly "graphical".

If you need a "desktop" TinyCore gets my vote.

Good luck! 

Side note: I wish somebody would give *me* an old computer. Hmm... Maybe for my birthday.

---

### Post by K.Mandla on 2009-02-01
[Crux, awesome and CLI applications]("http://kmandla.wordpress.com/2009/01/29/suddenly-things-make-sense/"). Works for me at [100Mhz/16mb]("http://kmandla.wordpress.com/hardware#FMV-5100"). :D

As a side note, I was once hunting for an XPI CD, but couldn't find one complete and in working condition. Congratulations, if that one is a winner. :)

---

### Post by darrelljon on 2009-02-01
Have you seen the [Operating systems for really, really old computers]("http://ubuntuforums.org/showthread.php?t=575456") thread?

---

### Post by fistfullofroses on 2009-02-01
+1 SliTaz
+1 NetBSD

---

### Post by gjoellee on 2009-02-01
SliTaz

---

### Post by snowpine on 2009-02-01
SliTaz cooking recommends 160mb of ram, so be sure to use one of the 'loram' flavors: [http://slitaz.org/en/get/flavors.html](http://slitaz.org/en/get/flavors.html)

---

### Post by cardinals_fan on 2009-02-01
[BasicLinux]("http://www.volny.cz/basiclinux/") might actually fly on that machine, but it's a bit... different :D

---

### Post by Twitch6000 on 2009-02-01
> **smartboyathome said:**
> Beat you to it. :p

Maybe so,but I gave the link ;).

---

### Post by mohitchawla on 2009-02-02
Puppy ! There were quite a few happy users on the puppy forums, as far as I remember.

---

### Post by maybeway36 on 2009-02-02
For SliTaz you might need to remaster the CD (it normally loads all 25MB to RAM). DSL doesn't load to RAM unless you tell it to and I'm not sure about Puppy.

---

### Post by snowpine on 2009-02-02
SliTaz loram-cdrom is a larger .iso than "regular" SliTaz because it is uncompressed. It runs from the CD rather than loading into ram, so it is suitable for low ram.

Regular Slitaz requires 128mb (stable) or 160mb (cooking).

---

### Post by Neural oD on 2009-02-02
what about dsl - damn small linux - although i haven't come across tiny-core before!

---

### Post by smartboyathome on 2009-02-02
> **maybeway36 said:**
> For SliTaz you might need to remaster the CD (it normally loads all 25MB to RAM). DSL doesn't load to RAM unless you tell it to and I'm not sure about Puppy.

Puppy doesn't load to RAM by default. It only does it if you tell it to, and then only if you have at least 256mbs of RAM.

---

### Post by mikjp on 2009-02-02
> **Musick Man said:**
>   
32 MB of Ram
3.02 GB HD


I have used Slackware 11 and Debian 3 on a Pentium 100 with 40 Mb RAM and 800 Mb HD.

K. Mandla has also some ideas for hardware like yours, see his [blog](http://kmandla.wordpress.com/).

Mikko

---

### Post by maybeway36 on 2009-02-03
I bet you could have Puppy, DSL and SliTaz on there, all booting off the same partiton with frugal installs and GRUB (or GRUB4DOS).

---

