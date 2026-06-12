---
title: "Chainloading GRUB 2 and LILO"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by tb75252 on 2011-09-08
I am just trying to teach myself some more Linux, hence please bear with me as I am still quite inexperienced.

I have a desktop PC with two Linux distributions installed:  Ubuntu 11.04 and Slackware 13.37.  Both are 32-bit.

A few pieces of information:
* Ubuntu is installed on partitions /dev/sda1 (root) and /dev/sda5.
* Slackware is installed on partitions /dev/sda3 (root) and /dev/sda7.
* The boot loader installed is GRUB 2 (Ubuntu) and it is installed in the MBR of the hard drive (/dev/sda).
* The boot loader that comes with Slackware (LILO) is installed in the superblock of Slackware's root partition (/dev/sda3).

I have been trying to find a way to insert a chainloader command in GRUB 2 custom file (called "40_custom" and available in the /etc/grub.d subdirectory of Ubuntu).  The idea is to boot up the computer, GRUB 2 displays on the screen, I get to choose whether I want to start up Ubuntu or Slackware from the menu.  If I choose to start up Slackware, then GRUB 2 would invoke LILO and LILO would start up Slackware.

So far I have not been able to get this done.  GRUB 2 is perfectly able to startup Ubuntu, but I get errors with the chainloading solutions that I have tried for Slackware.  Partially because most of the examples that I could find on the Internet pertain to the syntax used in GRUB Legacy (the one that still uses file /boot/grub/menu.lst for customizations).

Anyhow, I am looking for some sort of chainloading solution for Slackware as outlined above.

Does anyone know how to do it?

---

### Post by MG&amp;TL on 2011-09-08
I'm a newb, but I have been fishing around in GRUB for ages-is it not possible to remove LILO from the partition, and tell it where to look for the partitions?

And does not 'update-grub' pick it up? What kind of errors?

Although I understand that you can install GRUB on Slackware?

---

### Post by YesWeCan on 2011-09-08
I haven't tried this before myself but I imagine you'd want something like this. I just modified mine for Windows:
```
menuentry "Slackware (on /dev/sda3)" {
        insmod part_msdos
        set root='(hd0,3)'
        chainloader +1
}

```

---

### Post by ajgreeny on 2011-09-08
I am not sure why you want to, or need to chainload from grub to lilo when grub2 should find the slackware OS and add it to the grub menu when you run ```
sudo update-grub
```in ubuntu.

That is one of the joys of grub2; that it finds and adds any OS to its menu automatically with no further input from you.

---

