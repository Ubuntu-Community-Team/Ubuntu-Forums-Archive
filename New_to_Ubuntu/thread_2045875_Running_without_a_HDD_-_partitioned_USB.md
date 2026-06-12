---
title: "Running without a HDD - partitioned USB"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by chadwell on 2012-08-22
I am completely new to Linux/Ubuntu.  I have received an old laptop without a hard drive.  I was thinking I can just have this as something to surf the web etc on.

So I'm not too keen on buying a laptop - so I was going to try using a spare 16GB USB stick and partition it and install linux on one of the partitions.

Here is what I did:

Using Gparted - I created 2 FAT32 partitions (one 2GB for the Ububtu install and the remaining 14GB for storage).

I then used one of the tools from pendrive linux to install linux to the 2GB partition.  There was 1GB of persistence.

I booted from USB on the laptop and Ubuntu loaded fine.  Had a few issues with broadcom drivers and wifi but I got this sorted by seraching the web.

The 14GB appears as a usb removeable storage in Ubuntu so I thought this is working great.

I tried to save an image form the web onto the storage, then navigated to it using file system - but the image was not there?

Also - I loaded update manager, and downloaded some 340MB of Ubuntu updates.  While installing these - I ran out of space!

I'm guess my idea wasn't so good after all.


Can anyone explain how to install Ubuntu to a 16GB pen drive, and be able to use the rest of the USB space for storing files etc?

Thanks a lot!

---

### Post by anewguy on 2012-08-22
There are several guides out there for partitioning.  Additionally, I *think* the minimum hard drive partition for Ubuntu (and I'm assuming this is the same for USB flash) is around 5gb.  What I would try (and it's just me):

[LIST]
[*]repartition the flash drive with[LIST]
[*] 1gb persistence
[*]15gb for ubuntu
[/LIST][/LIST]

Since this will be an Ubuntu flash drive, just use the rest of the drive for Ubuntu.  You can create folders inside of your home folder to hold data.

If, however, you want to use the data storage area for both Linux and to share files to a Windows machine, then I would:

[LIST]
[*]repartition the flash drive with[LIST]
[*] 1 gb persistence
[*] 8gb for Ubuntu
[*] 7gb for data storage
[/LIST][/LIST]

---

### Post by chadwell on 2012-08-22
OK I for some reason though that if I installed Ubuntu on a usb stick, that the rest of the storage would be unusable?

Does persistance mean that if you install something then it goes into this part of the storage?  Say I installed GIMP and some other stuff.  Where does it get installed?

I would like it to be the first way where Ubuntu gets all the storage from the usb stick.

---

### Post by C.S.Cameron on 2012-08-22
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

### Post by C.S.Cameron on 2012-08-22
To access  files when booted from the persistent drive look in filesystem/cdrom

---

