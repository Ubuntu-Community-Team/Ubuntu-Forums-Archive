---
title: "Can't install grub-hd0 - fatal error with 8.04"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Stochastics on 2008-04-25
Hi, 

I have downloaded and burned the CD with Ubuntu 8.04 (i checked the md5sum and all is correct) but when i try to install it, at the end of installation, it says fatal error with grub-hd0 can't install...anyone has this problem ? I have a dual-boot with Windows XP.

Thanks

---

### Post by calibre97 on 2008-04-26
Can't help but I can commiserate. I downloaded Ubuntu 8.04 and also get all the way through install until the fatal error with can't install grub to hd0.

Here's the twist, though:
I HAD Kubuntu 8.04 RC working just fine.

My setup:
HP Pavilion dv5035nr with 1 74GB harddrive partitioned thusly:
System Commander in the MBR as boot loader
30GB Windows XP MCE SP2
31GB extended partition
    20GB as TrueImage Security Zone
    11GB NTFS Partition with a 5GB TrueCrypt file
12GB ext3 Partition (where I'm trying to install Ubuntu)
1GB Swap space at the end

With this exact same setup, I was able to install Kubuntu RC 2 weeks ago. I updated but started seeing problems and wanted to check out Gnome anyway so I blew away the Kubuntu partition during the Ubuntu install and went through the installer and then WHAM, right into the wall where Grub fails to install. Kubuntu was able to replace System Commander with Grub and I was able to re-set it all but this time no joy.

I'm just about done downloading the DVD for Ubuntu 8.04 so I'll try that and failing that, I'll try the Kubuntu release CD (KDE 3.5).

---

### Post by ipburbank on 2009-03-29
I also have this problem. It may be a problem with the graphics card, because for me after the error it tells me that the display has shut down 6 times in the last 90 seconds. I am using a graphics card I didn't have last time, and it worked then. My graphics card is the geforce 9800 GX2 if it makes a difference.

~please, this is really annoying! - Istvan.

---

