---
title: "Help with Dell Inspiron 1100 Screen Resolution"
date: 2006-02-20
forum: Repositories &amp; Backports
---

### Post by DJCollins on 2006-02-20
Hello I just recently installed Unbuntu 5.10 onto my computer and I have having the same problem with everyone else. I am unable to resolve the Screen Resolution, it is stuck on 640X480 at a refresh rate of 60Hz. I have tried reconfig. the xserver, installing 845patch, manually editing the config. file. Any help would be greatly appreciated.

Thank you
DJ

---

### Post by lazychris2000 on 2006-05-07
have you tried booting off a live cd and seeing if that works?  if its good, you can copy the xorg.conf into your /etc/X11 folder.  My fiancee has an inspiron 1100 and i have had to do that everytime we tried to linuxify it.  IMHO, this model does not like to run linux, and will fight you tooth and nail to be winblows only.

---

### Post by test on 2006-05-28
[http://www.ubuntuforums.org/showthread.php?t=183285]("http://www.ubuntuforums.org/showthread.php?t=183285")

---

### Post by durableapostle on 2006-07-16
[http://www.ubuntuforums.org/showthread.php?t=190022]("http://www.ubuntuforums.org/showthread.php?t=190022")

---

### Post by Jack Waugh on 2012-12-11
The Lubuntu 12.04 (Precise Pangolin) live CD works at full screen on my Dell Inspiron 1100.  But, interestingly enough, from the system running live from the CD, there is no /etc/X11/xorg.conf file.  So I'm wondering why this system is able to run full screen and what it would take to make the version of the system that runs from the magnetic disk do the same thing.  Upgrading the BIOS is not in the cards for me because I didn't receive the Win-doze installation media with this machine.

> **lazychris2000 said:**
> have you tried booting off a live cd and seeing if that works?  if its good, you can copy the xorg.conf into your /etc/X11 folder.  My fiancee has an inspiron 1100 and i have had to do that everytime we tried to linuxify it.  IMHO, this model does not like to run linux, and will fight you tooth and nail to be winblows only.

---

### Post by Jack Waugh on 2012-12-12
In answer to my own question, I think I'm on to the answer from [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) .  It seems to be a matter of changing the vga=blah argument in the linux startup via grub.  I tested by changing it manually from grub, and I'm sure there's a way to tell the grub stuff use the right argumet every time it boots.

> **Jack Waugh said:**
> The Lubuntu 12.04 (Precise Pangolin) live CD works at full screen on my Dell Inspiron 1100.  But, interestingly enough, from the system running live from the CD, there is no /etc/X11/xorg.conf file.  So I'm wondering why this system is able to run full screen and what it would take to make the version of the system that runs from the magnetic disk do the same thing.  Upgrading the BIOS is not in the cards for me because I didn't receive the Win-doze installation media with this machine.

---

### Post by lisati on 2012-12-12
A lot has changed in the time from when 6.06 was new to 12.04

Old thread closed.

---

