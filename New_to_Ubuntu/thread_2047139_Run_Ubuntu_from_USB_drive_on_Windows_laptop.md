---
title: "Run Ubuntu from USB drive on Windows laptop"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by mrdet7 on 2012-08-24
Here's what I want to accomplish, hopefully someone can give me a step by step:
I have a Windows laptop that I want to run Ubuntu on. The computer is used for business during the day, but I want it to run as a 'netbook' type of machine in the evenings.

Requirement 1:
I want to be able to put in the usb key, reboot, and have it load Ubuntu instead of Windows.

Requirement 2:
I do not need access to the main machine hard drive, but I would like access to the remaining space on the USB drive. (In trying to do this in the past, the Ubuntu image loaded on an 8GB thumbdrive, but the unused portion was unavailable for use. I could not even properly update Ubuntu, without getting a message that there was no more drive space.

Requirement 3:
I need wireless connectivity; this has operated very erratically in my past attempts, ie works but then doesn't after reboot.

Requirement 4:
I want to retain my customization settings after rebooting

Dell Latitude E6400
Dell Wireless 1397 (Broadcomm43xx?)

---

### Post by NikTh on 2012-08-24
Hi , 
well you have 2 options  to accomplish what you want. 

1 . Install Ubuntu (regular installation) to a Usb thumb drive (I do not recommend this). 
Run Ubuntu from a Live CD and carefully install it to the Usb thumb instead of HDD. You will have an Ubuntu installed and running in almost any machine , and you can use all the space of Usb thumb. 
Why I not recommend ? 
Cuz thumb drives have a limited cyrlce of read-writes. It is for sure that some day thumb drive will fail . Depends on tolerance of thumb drive how soon . 

2. You can create a LiveUsb Ubuntu session with persistent space. Usb will remain in Fat32 (natural filesystem) and persistent space will give you the option to store your setting , so not lose them on reboot. This way thumb drive will live longer (with the natural file system). The only negative here is that you cannot upgrade the kernel (cuz of initrams-tools) and the persistent space is limited to 4GB. (with usb-creator program). Maybe another way exists to make the persistent even larger but I don't know it. 

If you want details , post here , or search here (in forums) somewhere are good tutorials about.

Thank you

---

### Post by mrdet7 on 2012-08-24
Thanks for your quick response; I'm still kind of partial to your option 1. I did try it once, but the system would not boot to the thumb drive in that case, even when I told the system to. In my attempts at your option 2, system would boot to USB drive no problem, just had other issues.

---

### Post by NikTh on 2012-08-24
> **mrdet7 said:**
> Thanks for your quick response; I'm still kind of partial to your option 1. I did try it once, but the system would not boot to the thumb drive in that case, even when I told the system to

1. Check if grub installed correctly. Grub must installed to usb thumb drive and not to internal HDD. You must do that by hand . System always install grub to first hdd /dev/sda.

2. Check your BIOS cofiguration. Maybe another option instead of Usb exists that allows you to boot from Usb thumb. (Like Usb-hdd). 

Thank you.

---

### Post by C.S.Cameron on 2012-08-25
It is true that flash drives have limited writes, tyhe minimum figure used is 10000.
If you do the math you will find that it would take years to write to every block 10000 times on a 16GB drive.
Just figure how long it takes to write 16GB of data, (1 hour +), then multiply that by 10000.
Some tests suggest their life is more like 100000000 writes.

See: [http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

Following is step by step how to install 12.04 on a 8GB flash drive:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.
(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system", (
And "Mount point" = /windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

