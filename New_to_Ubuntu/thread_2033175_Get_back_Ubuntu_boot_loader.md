---
title: "Get back Ubuntu boot loader"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by thomsebastin on 2012-07-25
I had Ubuntu 12.04..i installed pclos as a dual boot ..now i've pclos boot loader shown up..even though i'm able to boot to my ubuntu,my old boot loader would make me feel home..how can i get it back?

---

### Post by Shadius on 2012-07-25
Might need to update GRUB by doing: 
```
sudo update-grub
```

or reinstalling GRUB: 
[Reinstalling GRUB]("https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2")

or maybe Boot-Repair would be the easiest way. Check my signature for the link.

---

### Post by thomsebastin on 2012-07-25
> **Shadius said:**
> Might need to update GRUB by doing:```
sudo update-grub
``` or reinstalling GRUB:Reinstalling GRUB or maybe Boot-Repair would be the easiest way. Check my signature for the link. Thanx Bro..i'll try that n get back to you asap.

---

### Post by oldfred on 2012-07-25
You have to boot into Ubuntu and reinstall grub to sda (or whichever drive you boot from).

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

Grub2 does remember where it installed, so on major updates it may reinstall to the MBR.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by thomsebastin on 2012-07-27
> **oldfred said:**
> You have to boot into Ubuntu and reinstall grub to sda (or whichever drive you boot from). #reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):sudo fdisk -l#if it's "/dev/sda" then just run:sudo grub-install /dev/sda#If that returns any errors run:sudo grub-install --recheck /dev/sdasudo update-grub Grub2 does remember where it installed, so on major updates it may reinstall to the MBR. #To see what drive grub2 uses see this - grub-pc/install_devices:sudo debconf-show grub-pc Yes it was on /dev/sda ..so the problem s resolved..thanx a lot @shadius,@overdrank.

---

