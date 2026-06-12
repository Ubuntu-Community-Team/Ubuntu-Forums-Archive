---
title: "ubuntu on usb w/&quot;persistence&quot; is awful slow anyway to make it faster?"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by urez2beat on 2013-04-28
Hello Everyone! My name is urez2beat and I'm sick of Windows and switvhing to Ubuntu 13.04.  have it installed on a 4Gb 
flash drive using Unetbootin. I also have a "persistence " file and it runs slow as all get out. i was told that it would, due to 
fact that I'm writing and reading from the same usb flash drive and that's the way it is. Now I know that with Linux there's is a way to have a persistence file and keep the speed up as well. Unfortunetly being a total newbie to Linux I am just not exactly sure what would have to do to insure good speed. For example is it possible to keep the persistence file on say a seperate flash drive or something like that since it makes sense that reading and writing from the same flash drive would be 
obviously a slow process any help by anyone with this would be soooooooo much appreciated Sincerely Urez2beat

---

### Post by zemega on 2013-04-28
I would suggest doing a full install into a USB. You will need 2 USB, 1 to load ISO and Unetbootin, and the other is the installation target. I believe this way is better than using persistence. There were discussions on the type of USB drive before, and some of the brand are not good in doing persistence or full installation. Sandisk line works well, I have installed 13.04 on a Sandisk USB drive, and run it on an old Acer Aspire ZG5, and it works fast. 4GB is not enough really, you need at least 8GB, go for 16 or 32 GB if you can. Your computer/desktop/laptop plays an important role as well. Try to use USB 2.0 port at least, it will be faster on USB 3.0. Maybe you can utilise i394, or external SATA. Doing external installation on external HDD works the same way as well, and its definitely faster. 

Graphics card can cause you some problem. Nvidea is a common problem, particularly if its old. 

There are other type of *buntu, such Xubuntu, and Lubuntu. Xubuntu is lighter than Ubuntu, and Lubuntu is the lightest. Its not fancy looking if that is your concern.

There's no problem in reading/writing from the same USB, what matters is you read/write speed. If you use old drive with 3.0 MB/s write, that is way slower that the phased out 5400 rpm HDD. Try getting new one that is fast, if your USB speed is slow. Again, Sandisk brand has been proven to work well with full installation.

Try giving out your spec, whether its a desktop or laptop.

---

### Post by C.S.Cameron on 2013-04-28
A Full install boots faster than a persistent install, once booted they seem about the same.
The make of flash drive seems to make a difference. I am having good results with a Sandisk Cruzer Fit.
USB3 seems to be speedy and USB3 HDD's are pretty quick.

---

### Post by urez2beat on 2013-04-29
Okay not really sure what you mean by"2 usb's one to load ISO AND uNETBOOTIN AND ONE AS TARGET" KINDA VAGUE LEAVE A LOT OF ROOM FOR "NEWBIE" INTERPRETATION!!!!LOL of just exactly due you mean by that!!! but thanks I think you were trying to help!!!! Urez2beat

---

### Post by zemega on 2013-04-29
Well, lets be clear then. You will need 2 USB drive. One to house the Unetbootin. One to house the Ubuntu, or to install the Ubuntu in it. Turn off your computer. Enter your BIOS. disable your harddisk (you can enable it back later).  Set your boot to primary USB. Turn off your computer. Plug in the USB containing Unetbootin. Turn on the computer, if things go well, you will get to select Try Ubuntu. Pick that and run Ubuntu. Plug in the USB drive  you want to install Ubuntu. Then click the Install Ubuntu on the desktop.  The installer will then install Ubuntu on the target USB drive. Automatically, the swap size will be 4GB, so 16GB will be better than 8GB. If you want to change this, you need to customise during install. After installation, you can enable your harddisk back.  By setting your primary boot to USB, you will boot into Ubuntu first. Note that is doesnt work really well if you have several USB  drives plugged in at the same time during booting your computer.

---

### Post by C.S.Cameron on 2013-04-29
Following is step by step how to install 12.04 on a 8GB flash drive:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language.
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue.

At "Installation type" select "Something else".
Continue

Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "+".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "+".
Select "Primary", "New partition size ..." = 4500 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then 

OK.

(Optional swap space, allows hibernation)
Click "free space" and then "+".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning 

and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".

Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a 

password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you 

are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You may do an update-grub later.

---

