---
title: "How to add Windows 7 in GRUB bootloader"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by Dhiraj1 on 2012-09-08
I dont have windows 7 in my grub bootloader..and i selected UBUNTU as my default OS.Now i cant boot Windows 7.:mad::mad:
Pls tell me how to add windows 7 in grub menu.
I also tried to changing the 40_custom file but it is read only so i cant change.
Help I am using UBUNTU 12.04 LTS

---

### Post by Jakin on 2012-09-08
Try using yannbuntu (boot-repair) via a live CD/USB to reinstall the GRUB, and fix any errors :)

---

### Post by Dhiraj1 on 2012-09-08
> **Jakin said:**
> Try using yannbuntu (boot-repair) via a live CD/USB to reinstall the GRUB, and any errors :)
i dont have any CD/DVD of UBUNTU!!

---

### Post by NikTh on 2012-09-08
> **Dhiraj1 said:**
> I dont have windows 7 in my grub bootloader..and i selected UBUNTU as my default OS.Now i cant boot Windows 7.:mad::mad:
**Pls tell me how to add windows 7 in grub menu.**
I also tried to changing the 40_custom file but it is read only so i cant change.
Help I am using UBUNTU 12.04 LTS

Hi, 

First of all , open a terminal (ctrl+alt+t combo keys) and do this 
```
sudo update-grub
```Then you can install a package that will allow you to modify your grub-bootloader . Its easy to use. 

Open a terminal (ctrl+alt+t combo keys) and apply bellow commands 

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update 
sudo apt-get install grub-customizer

```Open grub-customizer and change your settings according to your preferences.

And here is a great **how-to** for grub-customizer : [http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134) , to take advantage all of the features.

Thanks

---

### Post by Dhiraj1 on 2012-09-08
Hey Nikth Bro,
When i try to install grub customizer ,it says package not available,!!!:mad:

---

### Post by NikTh on 2012-09-08
> **Dhiraj1 said:**
> Hey Nikth Bro,
When i try to install grub customizer ,it says package not available,!!!:mad:

Hey , 

did you copy-paste the commands from here to your terminal ? 

Please give the results of 

```
sudo udpate-grub
``` 

Thanks

---

### Post by anewguy on 2012-09-08
+1.  update-grub should pick up any OS's on the disk and they should then be available in the boot menu.  I do have one question, thought:

Does:
> i selected UBUNTU as my default OS

mean that in the installation you told it to use the entire disk for ubuntu, not dual install for dual boot?  If so, then you probably don't have a partition with Windows installed on it now.  Boot up ubuntu, go to disk utility, and see what partitions are defined.  Do a screen print of this and attach it back in a reply here.  Don't do anything is in disk utility - just display, print screen and exit.

---

