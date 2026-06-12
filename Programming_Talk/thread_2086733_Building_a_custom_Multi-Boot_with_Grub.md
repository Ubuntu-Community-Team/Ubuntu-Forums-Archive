---
title: "Building a custom Multi-Boot with Grub"
date: 2012-11-21
forum: Programming Talk
---

### Post by Pen16 on 2012-11-21
Hello, there has been a project I have been meaning to complete and the Thanksgiving break is the only time I can get it done.  I am having some common newb problems and I was wondering if you Pro java drinkers can help.

I have been trying to create a custom multi-boot using grub.  These are the Teks I've been using;

[http://www.userbytes.com/roll-your-own-multiboot-usb-flash-drive/](http://www.userbytes.com/roll-your-own-multiboot-usb-flash-drive/)
[http://www.linuxforums.org/articles/how-to-create-a-bootable-usb-with-various-utilities-_1661.html](http://www.linuxforums.org/articles/how-to-create-a-bootable-usb-with-various-utilities-_1661.html)

But none explain if there is a way to get more than one Windows distribution to boot from one USB plus all the utilities.

I have Windows 7, XP, and 8 and would like to put them all on my USB because not all people are gonna want the new 8 or even the 7 so I would like to have that option, not only that but the x32, x64 bit distributions as well.

The second link talks about a single XP and utilities working properly but does not elaborate on adding more Windows. (Is this even possible or am I reaching too far)

I have downloaded Grub legacy from here; [ftp://ftp.gnu.org/gnu/grub/](ftp://ftp.gnu.org/gnu/grub/)
Do I first put the windows files on the base USB and then drop the Grub files on the same location and then add ISO's and utilities while adding them to the grub boot menu.

I have started this task but left the windows by the wayside until I can find a proper answer and this is what i have built on the Grug4dos menu on the USB.
> 
color blue/black yellow/blue
timeout 120

title Hiren's Boot Disk ver 15.1
kernel /memdisk
initrd /HBCD/boot.gz

title Ultimate Boot CD for Windows
map (hd0,0)/UBCD.iso

So I have the Hirens boot disc file structure on the base USB on top of the Grub4dos files but since this does not boot from a USB, I was wondering what file I have Grub us to boot this.  Or how I can add it properly.

I believe all the ISO files should be easy to add to the USB, I just need some help with the ones that aren't an image.

---

### Post by oldfred on 2012-11-21
Windows will not boot from a removeable device. It is licensed for one computer only. I have installed the Windows 7 repair ISO to flash and then added grub2 to boot it and additional ISO on another partition.

There are a lot of scripts that automate the process. I started & still do it manually. But I use grub2.

       These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

    
       MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
    
this is from another hard drive, but flash drive is almost identical except for path.
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by Pen16 on 2012-11-23
Wow, thank you for the help. This is everything I need.

I appreciate the time you took to reply, thank you again.

---

