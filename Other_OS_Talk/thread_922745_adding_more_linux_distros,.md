---
title: "adding more linux distros,"
date: 2008-09-17
forum: Other OS Talk
---

### Post by ontherooftop on 2008-09-17
I have windows xp with ubuntu dual booted with wubi, and I have 
ubuntu set up really good with compiz, but I wanna explore linux
more, whats another good linux distro and how would I triple boot.

---

### Post by smoker on 2008-09-17
try something different like fedora, or opensuse. if you set up a partition for the new distro, it should amend grub to give you the choice from boot, though, if i am correct, with wubi, you will have a grub option of your new distro and windows, and when you pick windows, will then have the option of windows or ubuntu (wubi), as listed in the windows boot.ini file.

---

### Post by kk0sse54 on 2008-09-17
First off check out distrowatch.com ,no one can tell you what's the best OS to install and it really depends on what you are looking to get out of that OS. As for triple booting check out this thread it might help [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by smartboyathome on 2008-09-17
In addition to the above, try installing Ubuntu without wubi. Many distros don't have the luxury which wubi provides, and triple booting is usually pretty successful with GRUB (used on 99% of Linux distros by default).

---

### Post by kk0sse54 on 2008-09-17
> **smartboyathome said:**
> In addition to the above, try installing Ubuntu without wubi. Many distros don't have the luxury which wubi provides, and triple booting is usually pretty successful with GRUB (used on 99% of Linux distros by default).

...except Slackware :lolflag:

---

### Post by felipeborges on 2008-09-17
> **C!oud said:**
> ...except Slackware :lolflag:

:lolflag:

hahahaha

Debian! xD

---

### Post by smartboyathome on 2008-09-17
> **C!oud said:**
> ...except Slackware :lolflag:

Slackware is why I said "used by 99% of Linux distros". Slackware is the other 1%. :p

---

### Post by cardinals_fan on 2008-09-17
> **smartboyathome said:**
> Slackware is why I said "used by 99% of Linux distros". Slackware is the other 1%. :p
That's the only thing I don't like about Slack.  LILO is revolting...

---

### Post by Tux Aubrey on 2008-09-18
> Slackware is the other 1%

I had no idea their market share had risen so dramatically. :popcorn:

Re triple booting:

I agree that it is possible and usually easy to set up but keeping track of which version of grub is booting has driven me absolutely crazy on several occasions.  Kernel updates have thrown me into meltdown.

Why not set up a VM (VirtualBox or VMware or Qemu) and try out other distros that way?

If you really want to learn about Linux, go with one of the lightweight distros - the fully-featured ones are too easy and polished.  Or even try [INX]("http://inx.maincontent.net/") - it is specifically tailored for learning command line gymnastics and won't bust your monthly download limit.

---

