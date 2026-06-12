---
title: "forgot password/messed up grub/cannot install new software"
date: 2016-07-11
forum: New to Ubuntu
---

### Post by jake682 on 2016-07-11
old newbie. 3 months ago i installed ubuntu 14 on laptop as sole os. all functional and ok.
problem 1. forgot the password. i accessed the recovery menu in grub to renew it and instead messed it up. 
now when i click on root in the recovery menu the following appears:
"Give root password for maintenance (or press Control -D to continue):_"
The last white lower case line just flashes and does not accept any keyed instruction. I also managed in the recovery menu to change grub from read only to read and write, (is this important).

problem 2. i thought to install ubuntu 16.04 and just start afresh. Having burned the file to dvd i cannot boot from it as i cannot change the boot order without installing grub-customizer, which i cannot do as i have no password to authenticate.

 not being able to add or remove software, is not so cool. your help is appreciated.

---

### Post by grahammechanical on 2016-07-11
Re-install is the best option. To install Ubuntu in the first place you needed to enter the BIOS/UEFI setting utility to change a setting to load an OS from DVD disc or USB stick. You need to do the same again.

Grub-Customizer will only change the boot order of Grub. It does not change the settings in the BIOS/UEFI settings utility. A motherboard user guide for that motherboard will help. Download a PDF version from the manufacturer's web site.

Also, when you switch on the computer the motherboard should display a screen that tells you what key to press to enter the BIOS/UEFI settings utility. All this takes place before Grub is loaded.

Regards

---

### Post by jake682 on 2016-07-16
The challenge was to how to access the bios/uefi,  as gnu grub had replaced it. I could find no way into the bios to change the boot order to ODD (dvd drive).
The solution: 
1. insert the dvd with burnt iso image. 
2. switch off the machine.
3. A. while holding down the zero key "0" (not the letter "o"), B. switch the machine on.
 
Re-install process began, with the option to delete the mess i'd made of the first installation.
P.S. write down your passwords and put them in a place you will REMEMBER AND DO NOT FORGET.

The exasperation of becoming intimate with Ubuntu is superseded by the exhilaration of success.

---

### Post by Bucky Ball on 2016-07-16
Hi old newbie. You won??? Fantastic! You got your head around that pretty quick and with little help from us so you're on the 'buntu learning curve. You'll be driving it like a pro in no time. :)

To help others, please use 'Thread Tools' at the top of the thread to mark the thread as solved (see the second link in my signature at the bottom of this post if any confusion).

Good luck and enjoy.

---

