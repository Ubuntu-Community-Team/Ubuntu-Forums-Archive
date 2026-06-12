---
title: "Install Ubuntu &amp; Xubuntu on same machine?"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by Digitalscribbler on 2014-02-27
Can you install more than one type of Ubuntu on the same computer? I have the regular Ubuntu, but was wondering if I could install another type, like Xubuntu? If so, I'm assuming I'd create a third partition. Thanks. 

My current specs:
-Dual boot/install: Ubuntu 13.10, 64-bit; Windows 7
-HDD: 500GB
-Memory: 4GB DDR3
-Hardware: Aspire One 722

---

### Post by carl4926 on 2014-02-27
Yes
If you want you can install the Xubuntu meta package and use it in your existing Ubuntu install. 
You can reduce the possibility of desktop crossover clutter by only using Xubuntu under a different username.

I never do it that way but I'm sure other will confirm they do.


Or
As I do, install in a separate partition/s

---

### Post by Bucky Ball on 2014-02-27
DON'T install xubuntu-desktop in Ubuntu. If you want to try the desktop environment, install xfce4, log out, choose 'xfce session' from the 'Sessions' pop up.

Yea, sure, install as many as you like. I have about four installs and Win7. You need to be smart about the way you share data though. I keep all my data on one partition and put symlinks to it in the /home directory of each install. There are other ways. If you already have a separate /home partition, just make sure it is enabled to 'Use' but NOT format. Same with /swap. That way, the new install will consider them to be ITS /home and /swap partitions. 

Neat, huh? Good luck. ;)

PS: Also, if you are not installed with EFI, you have a limit of four partitions (primary or extended) per physical drive. This can be overcome using a large extended partition into which you can put as many logical partitions as you like. Ubuntu will happily live on a logical partition inside an extended partition. Also neat.

(PS: Why not stick a testing version of 14.04 LTS on a partition while you're there? Then you can just move operations to that when it gets stable after release and help the community by reporting any bugs you find in the [***Ubuntu+1***]("http://ubuntuforums.org/forumdisplay.php?f=427") forum at the same time. ;))

---

### Post by Digitalscribbler on 2014-02-27
Thanks. I'll install it as a separate partition and let you know if I have any more questions or problems. Thanks again!

---

### Post by monkeybrain20122 on 2014-02-27
You can, but one system should take care of boot so in the other you should install the bootloader not in the drive, but the partition where the second system (not control boot) lives (e.g sda4 instead of sda) This is because *buntu doesn't have the option of not installing bootloader.

P.s I don't really see the point of having two *buntus on different partitions, if you want to dual boot, try a different distro. If you just want to try out xfce Buckyball's idea of installing xfce4 and switch session makes a lot more sense.

---

