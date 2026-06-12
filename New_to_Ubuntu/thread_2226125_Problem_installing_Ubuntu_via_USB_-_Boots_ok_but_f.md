---
title: "Problem installing Ubuntu via USB - Boots ok but fails on installation"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by James_Khalid on 2014-05-25
I am a complete newbie, so please bear with me!

* I have an old notebook which had Windows XP
* I was able to successfully install Ubuntu as dual-boot via a USB stick
* After a few weeks, for some reason the Windows XP became corrupted and the notebook crashed every time it tried to load Windows XP. But the Ubuntu option still loaded ok and worked fine.
* I decided to do away with XP completely and start from scratch. 
* I downloaded a fresh copy of Ubunto, created a USB stick and used that to boot into the notebook. It loaded fine. 
* I clicked on the 'install Ubuntu' option, chose the option to erase everything and start a fresh new installation.
* It started to copy the files from the USB stick, but towards the end the whole thing locked up with a screen full of error messages. 
* The last line of the error message was: 
"drm-kms-helper panic occurred switching back to text console".

* Since the whole thing becomes locked, I have to press the on/off button to  re-boot.
* It reboots fine from the USB stick, and I can use the notebook (as I'm doing now writing this help reqquest), but when I try the "intall Ubuntu" it goes through the same process and crashed at the same place with the same error. I have tried all the various options of install again, install alongside, etc. but same results. I have even tried completely formatting the HDD, but same result.

* When I boot from the USB stick and use the "Try Ubuntu" option, everything works and  I can even see that there are many folders and files that have been copied onto the Hard Drive during it's attempted ( but failed) installation..

I would appreciate if anybody could offer some advice and help. 
Thanks
James.

---

### Post by varun6 on 2014-05-25
Hey Khalid, I am also new in ubuntu but I have a suggestion for you. Please try to install new version of ubuntu and delete the old one as I had older version ubuntu 8.04 and last night when i Installed Ubuntu 14.04 with the help of usb,It working fine for me. Because during installation ubutu detected the older version and ask if I want to install new version with the old one or should Ubuntu delete the older version and install the new versio. I opted the second option and Ubuntu 14.04 is working fine for me.

I think this helps.
Regards,
Varun Rawat
Skype id: varunrawat-rajput

---

### Post by mörgæs on 2014-05-25
Hi, welcome to the fora.

Could be a failing hard disk. Are you able to read SMART data from the live boot?

---

### Post by James_Khalid on 2014-05-26
Hi [**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075"), Hi Varun,
I am using the 14.04 LTS version of Ubuntu. As mentioned previously, during installation it is loading large numbers of directories and files onto the HDD, but as the status bar gets near the end the installation fails with the same error messages every time and locks up. It has obviously partly installed Ubuntu since the next time I try and do an install it gives me the options of trying a new install by erasing the one it thinks it's already installed or install alongside it as another copy of Ubuntu. And then it proceeds to the same point everytime before bombing out. Because the whole think locks up (and an led with a lock icon on the Notebook starts flashing), I am unable to scroll back and see any other error messages.

The HDD disk is 160 Gb and after the attempted installation and re-boot via "Try Ubuntu" option it shows approx. 1gb as having been used, meaning virtually all the required files have been copied to the HDD. That to me indicates that there are no  issues in reading/writing to the HDD.

Wierd thing is it had installedOK   previously as dual-boot when I still had Windows XP - before XP became corrupted a few weeks later!

James

p.s I tried downloading and installing Linux Mint (Cinnamon) - same error, same place !!!

---

### Post by Impavidus on 2014-05-26
This is entirely consistent with a failing hard drive. Some sectors of your hard drive, belonging to the Windows partition, failed, corrupting Windows but not affecting Ubuntu. Installing Ubuntu works up to the point when the unpacking of the files has reached the broken sectors on the hard drive, at which point something goes wrong. As computers are deterministic, it always goes wrong at the same point. If the hard drive is indeed failing it's only a matter of time before more sectors break, so you'd better get a new drive if this is the problem. First check the SMART status though, as it could also be a damaged live disk. There must be a tool on the live disk that can read it. Also check the integrity of the live disk.

A fresh install is close to 4GB, so it still had to unpack quite some files before finishing installation.

---

### Post by James_Khalid on 2014-05-26
Don't know how or why, but problem solved, Ubuntu installed successfully.
The only thing I did differently is that at the point it asked whether to erase the disk and make a new installation, I chose the "Something else"  option and split the 160Gb disk into separate 40Gb partitions and instructed the installation process to install on the 2nd partition. 
Only thing I can think of is that any bad sectors were likely to be on the part of the disc in the new 1st partition and by installing Ubuntu on the 2nd partition it by-passed the bad sectors. 
Anyway problem solved.
Thanks to everyone for your various suggestions.

---

### Post by mörgæs on 2014-05-26
I was about to suggest something similar, but good that you found the solution yourself. 
Remeber to have a backup of the most important data.

---

