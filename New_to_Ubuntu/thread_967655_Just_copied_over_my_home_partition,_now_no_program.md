---
title: "Just copied over my home partition, now no programs"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by peejaroni on 2008-11-02
Hey everyone,
I'm moving from one install (hardy) to another (Ibex). In order to preserve all my settings and such I copied over my /home folder. All my settings showed up on my new computer, but I want to be able to use the dozens of programs I had obtained over the last while. I know most programs are stored in the /usr directory, but I am pretty sure it is a bad idea to just copy and paste that willy-nilly. Is there an easier way to get all my programs back other than installing them all again or copying my /usr?
Thanks!

---

### Post by The Cog on 2008-11-02
You will have to install them all. In Linux, programs get broken up and scattered around lots of different places on the hard disk. Madness to me, but that's the way it is. If you copied / you may well have to fix up the hardware config such as disk, sound, video. It'll be quicker to install the odd program again instead.

---

### Post by ugm6hr on 2008-11-02
Copying the /usr/bin will not work - your apps are for Hardy, not Intrepid.

This is probably the easiest way to create a list of apps: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

They all need to be downloaded again from the Intrepid repo.  This only works for apps from the repo.

---

### Post by scorp123 on 2008-11-02
> **The Cog said:**
>  In Linux, programs get broken up and scattered around lots of different places on the hard disk. Madness to me ... This has nothing to do with "madness". And I am not even trying to imitate Leonidas from that "300" movie here (Madness? This isn't madness. This is Linux ...!). You may want to read about the "Filesystem Hierarchy Standard" (FHS):
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Things get "broken up" according to that standard, e.g. config files should go to /etc, system-essential binaries relevant for the boot process go to /bin, if they should be accessed only by the "root" account they should go to /sbin .. if they are not really relevant for the system and purely optional they should go to /opt, and so on.

If you understand this system it makes perfect sense, especially if your system is partitioned accordingly.

Having to gather those packages again is no big deal at all if you know the names of the package. See the link that was posted before: You simply tell system "B" to install the same packages that system "A" had ... voila, you have the same set of packages again on both systems. That's the advantage of having package managers: You simply don't have to and don't want to bother about hunting down single files in /etc, /usr/bin, /opt and wherever else the files were put .... you lean back and let the package manager do that. ;)

---

