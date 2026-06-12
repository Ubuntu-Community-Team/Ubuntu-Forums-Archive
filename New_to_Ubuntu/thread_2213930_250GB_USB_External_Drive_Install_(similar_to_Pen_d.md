---
title: "250GB USB External Drive Install (similar to Pen drive Possible?)"
date: 2014-03-29
forum: New to Ubuntu
---

### Post by randy9 on 2014-03-29
Hello All,
I'd like to install Xubuntu on an External 250GB Lacie Drive. 

If I open windows, try a install that way, it won't let me boot up to that drive. HOWEVER,  if I install as if a "Pen Drive" (using these insytructions)> [http://www.pendrivelinux.com/put-xubuntu-10-04-on-a-flash-drive-with-windows/#more-4189](http://www.pendrivelinux.com/put-xubuntu-10-04-on-a-flash-drive-with-windows/#more-4189)  
it DOES work....but it only allowcates a few GB of space (can't expand it to full external dive capacity (wiped drive) . 

Is there a way to install on a USB Drive I can boot directly into. Assuming this is a boot loader issue I have to trick to see before Bios hands off to Windows (via the F12 option?). 

Would going into Bios (disablining all ut USB drive work?). IF so, how can I install to this drive without the "Hooks" into Windows?

I gues what I"m asking, is there a way to install to the USB without having the "Main" drive involved in the install?
Thank you!

---

### Post by fantab on 2014-03-29
What Windows version do you have? Is it preinstalled Windows8?

---

### Post by C.S.Cameron on 2014-03-30
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

### Post by monkeybrain20122 on 2014-03-30
I never remove the hard drive. Just make sure that you install the bootloader in the target drive, default will be in the intetrnal drive. The option for where to install bootloader is at the bottom of the partition table screen (when you choose how to install: along existing os, wipe drive, something else)

But then that is just me, it is more likely for me to lose the screw so I can't put the hard drive back in than for me to install the bootloader in the wrong drive. :)

---

