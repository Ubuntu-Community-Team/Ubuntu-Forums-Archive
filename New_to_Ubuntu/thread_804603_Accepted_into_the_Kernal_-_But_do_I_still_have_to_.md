---
title: "Accepted into the Kernal - But do I still have to compile a driver for the raid array"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by DoubleR on 2008-05-23
My Highpoint 3510 RocketRaid adapter card does not seem to be available to the 8.04 install.  I have a RAID 1 array created using the adapter card BIOS.  After starting up the live CD install and when I get to the format disk, the array nor the individual drives are identified by Linux.  

No single disk is available to install Linux on this box.  I have another RAID 0 array established with windows operating system installed on it.  This array is attached to the motherboard SATA controller and is based on Intel ICH9 chip set. On this array the drives are recognized individually on this IC9 driven array during the Ubuntu install and as expected not as an array.  No support for Linux that I have found for this chipset but not the point of this question

The RocketRAID Linux support information provides the following. 

"All RocketRAID products have support for major Linux distributions and include open source drivers and the RocketRAID 3000 series of SATA hardware RAID controllers were recently accepted into the main Linux kernel."

What does it mean that it is accepted into the main kernel?  Other vendor information reports for operating systems: GPL   Licensed Linux Open Source Driver into Kernel 2.6.25.  I though it would mean that Ubuntu would recognize this card natively during the install like any other IDE or SATA disk controller.

The vendor driver disk and support page do not list drivers for the Ubuntu distribution although it does include other distributions. They do list an open source driver.  Do I have to compile the open source driver into Ubuntu some how during the installation? [FONT=Arial]  If this is the case, pointing me in the direction of some reference  or instructional material relevant to my effort to install Ubuntu would be greatly appreciated.
[/FONT]

---

### Post by DoubleR on 2008-05-23
I miss read the kernel rev level for Ubuntu. So the issue is Ubuntu is rev level 2.16.24. Rocket Raid is in the next Kernel rev level. So I need to use the generic open source driver supplied by rocketRAID to install Ubuntu on this raid array. 

I would greatly appreciate point in the right direction to read up on how to do this

---

