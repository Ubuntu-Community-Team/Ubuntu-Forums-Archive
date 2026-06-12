---
title: "Dual boot Problem"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by arunachalamev on 2008-05-01
Hi all,
I just now entered into the world of open source.
and Unbuntu really made me crazy.

So i downloaded the latest version of Unbuntu 8.04 and installed into my system.Now iam facing some problem with it, which is described below.

My hard disk capacity : 250 GB IDE
I have partioned the drive in manner below.
1. Drive C: 40 GB NTFS Win Xp installed
2. Drive D: CDROM 
3. Drive E: 100 GB NTFS  Movies, songs, etc
4. Drive F: 40  GB NTFS for Back up
5.          20  GB Linux Swap
6.          40  GB Linux Ext3


I have successfully installed the ubuntu in Linux Ext3 partion.
When i booted it first time and GRUB menu flashed and i entered into Ubuntu. I was really happy that i installed it properly.

Again i rebooted the system and entered into Win XP from GRUB screen without any prob.

However the problem started thereafter, again i restarted my system, unfortunately GRUB menu flashes with the ERROR 17 and its not booted to any OS either Win xp or Ubuntu.

Inorder to loginto Win XP, i tried repairing it using Win Xp CD. I have restored my MBR and able to log into Win XP now.

But i was unable to log into my Favorite "UBUNTU" since i was not able to get GRUB screen.

Could anyone of u provide me the solution for it.
Eagerly awaiting for it.

Cheers,
Arun

---

### Post by iSplicer on 2008-05-01
Namaste Arun, and welcome to Ubuntu.

First of all, you dont need a 20GB swap partition. 2GB is enough.

Did you do anything in Xp that could have caused this problem?

---

### Post by arunachalamev on 2008-05-01
Hi iSplicer,
When i partioned it, i didnt actually understand Linux Swap space.

After installation,  i was browsing through the forum to solve the issue, i came to know that 2Gb is enough for Swap.

ok..now into the issue.
I didnt do anything in the windows.

i think, i just want to install only the boot loader now and configure it to understand both WinXp and Ubuntu.

Pls let me know how to do the same

Cheers,
Arun

---

### Post by El King on 2008-05-01
Run the live cd and do the steps mentioned here
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

This will restore ur grub into ur MBR again

---

