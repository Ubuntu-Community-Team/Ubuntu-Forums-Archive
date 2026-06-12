---
title: "cant boot ubuntu or windows"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by hscriber on 2012-09-26
I partitioned my hard drive and installed ubuntu on a separate one from windows 7. I did this from a live usb created using lili. Now when I boot, it goes straight to trying windows, and it gives me windows cant boot, status 0xc0000225, needed device inaccessible. This is the third time I have reinstalled windows and linux, and this happens everytime. Is this fixable, or am I screwing up somewhere?

---

### Post by Bashing-om on 2012-09-26
hscriber;

A high degree of certainty. UEFI or large disks may pose difficulties to be overcome.

see these links and advise:
[http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI](http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI).

[http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise](http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise)

[http://ubuntuforums.org/showthread.php?p=12254717#post12254717](http://ubuntuforums.org/showthread.php?p=12254717#post12254717)
[INDENT]hth <==BDQ

[/INDENT]

---

### Post by hscriber on 2012-09-26
Ok, so I sorted this out be reformatting and reinstalling both systems.  Turns out I had Ubuntu installed in an extended partition of windows recovery.  Stupid mistake.  Now I have a new problem.  I have ubuntu installed on a seperate partition, but don't know how to get to it.  I have no startup screen asking which OS to boot.  I've read a few posts about editing the MBR or installing Grub 2, but none of them tell you how, just to do it.  I'm not great at taking general "oh, just install Grub 2 then....." and actually knowing how to do it.  I need somewhere with a step by step walk through on how to boot ubuntu once it's installed.  Thanks a lot.

---

### Post by sarc on 2012-09-26
If your MBR or GRUB or BIOS has problem, there is a wonderful utility called PLOP boot mamager that will let you boot anything anytime.  It searches for bootable systems and gives you a choice menu.  Worked wonders for me.  Google search, download and burn to disk or USB memory.

---

### Post by Bashing-om on 2012-09-26
You do good work !... In regards to a step by step process on grub ..the issues are many so a "general" howto not feasible. However, specific troubleshooting tutorials are numerous (ubuntu documentation is wonderful, if overwhelming).

These should be enough to resolve your problem, or at least point ya to asking the direct questions ya need to know.
These are step-by-step tutorials. & additional links for more.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#The_terminal_way](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#The_terminal_way)

and my nbr 1 thinking/starting point:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[INDENT]hth <==BDQ

[/INDENT]

---

