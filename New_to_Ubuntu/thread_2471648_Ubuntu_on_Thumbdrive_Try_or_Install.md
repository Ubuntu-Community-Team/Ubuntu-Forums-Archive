---
title: "Ubuntu on Thumbdrive Try or Install?"
date: 2022-02-05
forum: New to Ubuntu
---

### Post by gunner169 on 2022-02-05
Installed Ubuntu 20.04.3 LTS on a 16GB thumbdrive as per these instructions: [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows)
System boots great and then Try Ubuntu or Install Ubuntu

Then I'm prompter with Try Ubuntu or Install Ubuntu
"Install" doesn't work as it fails on Installation Type. 
Click on Change - nothing
Click on + and an error pops up: No root file system is defined. Please correct this from the partitioning menu".
New Partition Table is greyed out.
I'm thinking I can't install? 

"Try" makes the mousepad unusable.

Once I get this figured out, onto the next problem of installing Wine.

---

### Post by yancek on 2022-02-05
You need to click on free space in the main installation type window (shown at the link below) and then the + sign or if you have a partition ready, highlight it and click Change.  You should get a new window to change or edit and here you click the drop down arrow and select the "/" root filesystem option in the Use as section.

[https://medium.com/linuxforeveryone/how-to-install-ubuntu-20-04-and-dual-boot-alongside-windows-10-323a85271a73](https://medium.com/linuxforeveryone/how-to-install-ubuntu-20-04-and-dual-boot-alongside-windows-10-323a85271a73)

---

### Post by GhX6GZMB on 2022-02-05
You need to boot your computer from the USB drive.
In the link from Yancek there's a section describing this around halfway down.
Read that section carefully.

---

### Post by ActionParsnip on 2022-02-07
If you are planning to dual boot I suggest you resize your NTFS in Windows. Then reboot a few times to make sure that booting works as expected.
Ubuntu will then see the unpartitioned space and suggest to use it.
As with all big disk changes (and I can't stress this enough)

BACK UP YOUR DATA

The number of people who barf their disks then cry when their data is lost is getting a bit tiresome now

---

### Post by mIk3_08 on 2022-02-07
> **gunner169 said:**
> Installed Ubuntu 20.04.3 LTS on a 16GB thumbdrive as per these instructions: [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows)
System boots great and then Try Ubuntu or Install Ubuntu
Then I'm prompter with Try Ubuntu or Install Ubuntu
"Install" doesn't work as it fails on Installation Type. 
Click on Change - nothing
Click on + and an error pops up: No root file system is defined. Please correct this from the partitioning menu".
New Partition Table is greyed out.
I'm thinking I can't install? 
"Try" makes the mousepad unusable.
Once I get this figured out, onto the next problem of installing Wine.

Hi Here are some of the quick link that might help you in your installation of Linux Ubuntu Operating System.
Please [Click Here]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick") for a Quick Install from USB. This is a quick guide to installing from a USB memory stick.
And Please [Click Here]("https://help.ubuntu.com/community/Installation/FromUSBStick") for Installation from USB - Installing from a USB memory stick (full version).
USB stick + grub - Similar to above but using grub. [Click Here]("https://help.ubuntu.com/community/Installation/FromCForUSBStick")
Installation/iso2usb - Overview: cloning and extraction, tools and a simple 'Do it yourself' extracting method. [Click Here]("https://help.ubuntu.com/community/Installation/iso2usb")
Smart Boot Manager - Installing from a PC which will not boot from a CD. [Click Here]("https://help.ubuntu.com/community/SmartBootManager")
Just follow some installation instructions for more best and accurate results.
Good Luck and Cheers.

---

### Post by gunner169 on 2022-02-10
Yeah, clicked on the window and the + sign. No joy.
Thanks for the link - this is for a laptop with no hard disk.

---

### Post by tea for one on 2022-02-10
[COLOR="#0000FF"]From post 1[/COLOR] - Install" doesn't work as it fails on Installation Type. 
[COLOR="#0000FF"]From post 6[/COLOR] - this is for a laptop with no hard disk

It is not really a surprise that the OS installation failed without a target disk.

Can you provide more details about what you want to do?

---

