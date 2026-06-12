---
title: "No Beuno installation."
date: 2008-11-28
forum: New to Ubuntu
---

### Post by twiz86 on 2008-11-28
Hi,

I have been running ubuntu for about 2 weeks now and just now setup an account on these forums. These forums have been extremely helpful and I would like to thank all those out there that provide better support for free than any "pay" service out there. 

I have my ubuntu setup on my laptop and everything but bluetooth works so I think I will live to fight another day as far as that is concerned.

However, now I am branching out and installing ubuntu on my laptop out in the loft. Its an Acer sempron 1.8ghz, 60gb, 512 ram machine. not too good not too bad.

My problem is this. I get an error at about 69% that says it cannot copy such and such file and shows me a list of reason why it may be failing such as: cr-rom is faulty(well i got this far..hmmm.), cd is scratched or dirty...i just burnt it.

I would like to know if there is a different way of installing ubuntu be it easier or harder, and how to do it.

I know you are all volunteers and do this for free so i dont expect an answer for a while and will continue to try to install it off the cd but i do thank you for you responses.

---

### Post by Michael.Godawski on 2008-11-28
> **Installation using the Alternate CD**

 If your computer is not able to run the standard Desktop installation CD, you can use an *Alternate installation CD* instead. The Alternate CD also allows more advanced installation options which are not available with the Desktop CD. 

[LIST]
[*]If you have an **x86 computer**, and want to install Ubuntu 7.04 "Feisty Fawn" see [Installation/I386]("https://help.ubuntu.com/community/Installation/I386"). Most people have an x86 computer. 
[*]If you have an **AMD 64-bit computer**, and want to install Ubuntu 6.06 see [Installation/AMD64]("https://help.ubuntu.com/community/Installation/AMD64"). 
[*]If you have a **PowerPC (Apple Mac)** computer, and want to install Ubuntu 5.10 "Breezy Badger" see [Installation/PowerPC]("https://help.ubuntu.com/community/Installation/PowerPC"). 
[*]If you have a **SPARC** computer, such as an UltraSPARC T1 (Niagara), and want to install Ubuntu 6.06.1 see [Installation/Sparc]("https://help.ubuntu.com/community/Installation/Sparc"). 
[*]If you have a **Sony Play****Station 3**, and want to install Ubuntu 7.10 see [PlayStation_3]("https://help.ubuntu.com/community/PlayStation_3"). 
[/LIST]
 
**Installation without a CD**

 The documents listed below provide instructions for installing Ubuntu without using a CD or CD-ROM drive. 

[LIST]
[*][SmartBootManager]("https://help.ubuntu.com/community/SmartBootManager") - Installing from a PC which will not boot from a CD. 
[*][Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick") - Installing from a USB memory stick. 
[*][Installation/FromCForUSBStick]("https://help.ubuntu.com/community/Installation/FromCForUSBStick") - Similar to above but using *grub*. 
[*][Installation/WithFloppies]("https://help.ubuntu.com/community/Installation/WithFloppies") - Installing without a CD drive over a network. 
[*][Installation/FromHardDriveWithFloppies]("https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies") - Installing without a CD drive or network capabilities from a hard drive. 
[*][Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows") - Installing from Windows without using floppies, a CD, or any other removable media. 
[*][Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux") - Installing using a spare partition from an existing Linux system to house the Ubuntu CD image. 
[*]See also the network installation options below
[/LIST]


I would burn another CD and use the Alternate installer now. If this installation also get stuck, try one of the above mentioned installation methods. I have not tried them out so I cannot tell you which one is easier. Perhaps someone other can...

---

### Post by steveneddy on 2008-11-28
Try this link:

[http://www.linux-on-laptops.com/acer.html](http://www.linux-on-laptops.com/acer.html)

---

### Post by twiz86 on 2008-11-28
You know what, I apologize...must of been the drugs as a kid. I am running an averatec laptop. not an acer. (wow this guy doesnt even know what kind of computer he has, what an idiot)

Hehe there, i said it for you

btw, thanks for the quick replys.

---

### Post by a0u on 2008-11-28
Hello, and welcome to the forums.

> **twiz86 said:**
> 
My problem is this. I get an error at about 69% that says it cannot copy such and such file and shows me a list of reason why it may be failing such as: cr-rom is faulty(well i got this far..hmmm.), cd is scratched or dirty...i just burnt it.
First, do an integrity check to see whether the CD is corrupted - you should see an option in the menu after you boot from the live CD.

> **twiz86 said:**
> 
I would like to know if there is a different way of installing ubuntu be it easier or harder, and how to do it.

As others have mentioned, you may want to give the [alternate install CD]("http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate") a try.  Note that it is text-based, but the procedure should be less resource-intensive on older hardware.

Also, when you have downloaded the *.iso images, compare [md5 checksums]("https://help.ubuntu.com/community/HowToMD5SUM") for extra precaution.

---

### Post by twiz86 on 2008-11-28
Ok. after two hours of attempting to install from the alt cd i keep getting errors saying this is corrupt or that is corrupt. ive burned 3 different cd's...one in windows, one in linux at 4x and one at 8x. Same error on all of them. I cant do the network install because i have no floppy drive. 

Any ideas?

Thank you
:popcorn:

---

### Post by a0u on 2008-11-28
> **twiz86 said:**
>  I cant do the network install because i have no floppy drive.

Perhaps you mean the [minimum install CD]("https://help.ubuntu.com/community/Installation/MinimalCD")?  A floppy is not needed for that.
Note that a minimum install only provides the CLI base system.  To get the full Ubuntu desktop, you would need to enter this terminal command afterwards:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by twiz86 on 2008-11-28
oh sweet. that could have saved me alot of time. i must be blind...thanks

---

### Post by twiz86 on 2008-11-28
ok, sweet. that worked. thank you muchos

---

