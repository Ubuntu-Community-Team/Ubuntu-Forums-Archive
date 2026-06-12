---
title: "[SOLVED] screwed up grub (again)"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by medic8ted on 2008-09-29
So I decided to try Fedora 9.  Installed beautifully.  Until reboot when grub menu only showed "Fedora" and "other".  Bad news, now I can only get to Fedora and "other" is winXP.  I believe when grub installed, I put on hd0,0.  Here's the condensed version of my partitions.
hd0,0 (sda1) dell partition...windows and fedora mbr?
hd0,1 (sda2) windows xp
hd0,2 (sda3) hardy 8.04 root
hd0,3 (sda4) extended partition
hd0,4 (sda5) fedora 9 root
hd0,5 (sda6) swap
Any way to get grub moved so all OS's are on same MBR or get rid of the fedora installed grub or am I in for a long night of backing up, reformatting, and reinstalling.  I don't mind formatting, but reinstalling win xp is not my idea of a good time.  It's only there for a few things wine won't run.

---

### Post by LowSky on 2008-09-29
This should fix everything
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by fourthofjuly on 2008-09-29
check this thread out...

[http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub]("http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub")

---

### Post by kansasnoob on 2008-09-29
[http://docs.fedoraproject.org/install-guide/fc6/en/sn-bootloader-others.html](http://docs.fedoraproject.org/install-guide/fc6/en/sn-bootloader-others.html)

---

### Post by hyper_ch on 2008-09-29
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by medic8ted on 2008-10-01
> **kansasnoob said:**
> [http://docs.fedoraproject.org/install-guide/fc6/en/sn-bootloader-others.html](http://docs.fedoraproject.org/install-guide/fc6/en/sn-bootloader-others.html)
Finally had to reinstall windows MBR then format and reinstall Hardy.  Super grub Disk wouldn't boot from cd (burn issue?) or pendrive, and after multiple attempts to install grub from live cd and alternate install cd, error after error after error on grub reinstall.  Maybe if I get Fedora 9 working with my wireless I may get away from Ubuntu.  I end up having to reinstall every time something goes bad, instead of it "just working" I "just get errors" while attempting simple tasks.  Its almost like windows, its been idiot-proofed so much, if you know what you're doing, you're screwed.

---

