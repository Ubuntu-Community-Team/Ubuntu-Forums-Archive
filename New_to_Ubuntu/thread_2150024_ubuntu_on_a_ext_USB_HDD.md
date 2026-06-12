---
title: "ubuntu on a ext USB HDD"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by keith pitts on 2013-05-30
How do i make a bootable ext HDD with ubuntu on it, i don't want to mess with the internal hd on my laptop
keith pitts:P

---

### Post by DuckHook on 2013-05-30
Welcome to Ubuntu and the forums.

To be absolutely sure that I did not overwrite my internal HDD, I took it out of my laptop completely. The installation DVD then just recognized the external HDD that I had attached, and installed Ubuntu with no problems. After reattaching my internal HDD post-install, I can now select either OS through the BIOS.

---

### Post by C.S.Cameron on 2013-05-30
Following is step by step for making a Full install of *buntu 12.04 on a USB hard disk drive.
All partitions except / are optional.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.

Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Insert the target USB drive.
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
Start with an external drive that has been formatted NTFS.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." as large as required.
Location = Beginning.
"Use as:" = "do not use this partition".
Leave "Mount point" blank.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 5000+ megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 5000+ megabytes, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
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
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

