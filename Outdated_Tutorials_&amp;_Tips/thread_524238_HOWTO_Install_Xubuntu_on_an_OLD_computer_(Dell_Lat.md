---
title: "HOWTO: Install Xubuntu on an OLD computer (Dell Latitude LM, but applies to others)"
date: 2007-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by 0graham0 on 2007-08-12
**HOW A FEEBLE-MINDED NEW USER WAS STILL ABLE TO INSTALL XUBUNTU ON A COMPUTER WITH BIOS UNABLE TO BOOT FROM CD, AN INSTALLATION THAT FAILED TO INSTALL GRUB OR LILO AND A BOOT THAT ENDED WITH NO GUI.**

Hi all, thought I would just chronicle the 3-day long process it took me to install Xubuntu 7.04 on an old Dell Latitude LM, with a 133 mhz pentium 1 processor, 40 mb RAM and swappable Floppy/CD-ROM drives. I upgraded the harddrive to 6 GB, however a minimum install may be possible with the 2 GB drive that came with it? 

The good news: I got the system to work in the end...the bad news: I needed a separate computer to make bootdisks and an external floppy drive. (If you don't have an external floppy drive info on using a boot disk with usb cd drivers and installing off a usb cd here: [http://ubuntuforums.org/showthread.php?t=244918](http://ubuntuforums.org/showthread.php?t=244918))

The worst news of all: With 40 MB Ram Xubuntu was unbearably slow, and I immediatly ditched Xubuntu on this computer. However, don't be too discouraged it may have ran so slow because I installed the entire Xubuntu-Desktop package, and there are other more stripped down versions you can try (See Section 6 for more info!)!

I take little to no credit for figuring out how to do all these things, it was mostly thanks to various web documents and members of the UbuntuForums community. (Thank you so much everyone who helped...) Thus, this is really more of an amalgamation of other how-tos and not so much an original document. I have tried to list the sources I used to solve each problem, both to credit those sources, and so that those of you having similar problems can easily find out more.

Note: I will list links for referenced files at the end of section...
[B]
SECTION 1. ACQUIRE A XUBUNTU INSTALL DISK...CHECK MD5!
[/B]
I first needed a CD to use for the install. I used the Xubuntu 7.04 i386 Alternative Install CD image and burned to CD with Nero Burning Rom. I never checked the md5 of the downloaded iso, and even though the installer's CD integrity check found no problems, a faulty download may have led to many of the problems i encountered. I guess I learned the hard way to always check the md5 of your cd image before trying an install!
[B][U]
Referenced Files can be found at:[/U][/B]

Xubuntu Alt. Install CD - [http://xubuntu.com/get](http://xubuntu.com/get)

**SECTION 2. BOOTING TO CD WITH A FLOPPY (OR MAYBE FROM DOS?)**

Next I had to figure out how to boot to the CD, even though the computers BIOS only allowed me to boot to a floppy or a hard drive.

METHOD 1: USING A BOOT DISK AND LINLD.COM

Since I had no operating system installed on my computer, and I only had a swappable floppy/cd drive, I found no way to boot into linux except by obtaining an external floppy drive.

a. Using another computer I created a boot disk (for this method I used a windows 98 boot disk)

b. I needed to add linld.com onto the boot disk so I could load the installer cd linux kernel. 

c. To simplify the process of telling linld.com where to look for the linux kernel I created a .bat in notepad. I opened notepad and typed ```
linld image=d:\install\vmlinuz initrd=d:\install\initrd.gz "cl=root=/dev/ram boot=install ramdisk_size=1048576 devfs=mount,dall"
``` (This assumes that your cd drive is mounted as D: and you are using the 7.04 install cd where the kernel is located in \install\.) I then save the file as Xubuntu.bat to the floppy as well.

d. Next I inserted the floppy into the external SCSI floppy drive i had hooked up to the Dell Latitude LM, made sure the Xubuntu install cd was in the swappable CD drive, and started up the computer. I made sure the BIOS was set to "Boot from Floppy" (for a Latitude LM you just hit F2 at startup to access the bios).

e. When the Windows 98 disk asked if I wanted to boot with cdrom support, I typed 1 (for yes) and pressed enter. (Sometimes the boot disk wouldn't boot. I made another boot disk with a different floppy and it worked fine. That is, it worked fine most of the time...sometimes it wouldn't boot up and then all I would have to do is manually shut down the computer and restart).

f. Once presented with the command prompt all I had to do was type "Xubuntu" and the install CD loaded up. If this fails, perhaps theres is an error in the .bat file you created. Maybe try manually entering the same line of code, but changing the location of the CD drive (E:, F: etc.)
[B][U]
Referenced Files can be found at:[/U][/B]

Windows 98 Bootdisk - [http://bootdisk.com/bootdisk.htm](http://bootdisk.com/bootdisk.htm)
Linld.com - [http://port.imtp.ilyichevsk.odessa.ua/linux/linld/](http://port.imtp.ilyichevsk.odessa.ua/linux/linld/)
**_Source:_** 
Adapted from "How to Install from an Unbootable CD" [http://ubuntuforums.org/showthread.php?t=244918](http://ubuntuforums.org/showthread.php?t=244918) and "Install Ubuntu with Loadlin" - [http://ubuntuforums.org/showthread.php?p=1971521#post1971521](http://ubuntuforums.org/showthread.php?p=1971521#post1971521)

AN IMAGINED METHOD 2: LOADING LINLD.COM FROM WITHIN WINDOWS

I haven't tested this method but I assume it would work along similar lines (let me know if it doesn't and I will get rid of this section)

a. Boot up the computer with the Xubuntu Alt. Install cd in the drive. 

b. Follow instructions b. and c. above, but just save linld.com and xubuntu.bat to a directory on your hard drive.

c. Restart the computer in MSDOS mode, navigate to the directory holding Xubuntu.bat and linld.com and load Xubuntu.bat (you just need to type "Xubuntu").

**_Referenced files can be found at:_**

Linld.com - [http://port.imtp.ilyichevsk.odessa.ua/linux/linld/](http://port.imtp.ilyichevsk.odessa.ua/linux/linld/)

**_Source:_**
How To Install with an Unbootable CD - [http://ubuntuforums.org/showthread.php?t=244918&highlight=linld](http://ubuntuforums.org/showthread.php?t=244918&highlight=linld)
Install Ubuntu with Loadlin - [http://ubuntuforums.org/showthread.php?t=37432&highlight=install+floppy](http://ubuntuforums.org/showthread.php?t=37432&highlight=install+floppy)


**SECTION 3. RUN THE XUBUNTU INSTALLER**

I had previous experience installing Ubuntu so I didn't run into that many problems within the alternative installer. My first install was greatly aided with the manual available at [https://help.ubuntu.com/7.04/installation-guide/](https://help.ubuntu.com/7.04/installation-guide/) (for the Dell it would be the i386 manual). First I made sure to select the ext3 file system add on for the partition manager. Setting partitions really depends on your hard drive but for the 6 GB drive I had I just made a 5 GB ext3 partition to mount as root (/) making sure to have the bootable flag on, and a 1 GB swap partition. I also had no internet connection so all those prompts were irrelevant. The installation returned no errors until it reached the Grub installer...and that was when:

**SECTION 4. GRUB FAILS TO INSTALL / BOOTING INTO XUBUNTU WITHOUT GRUB**

Near the end of the install when the GRUB and LILO tried to install, I recieved the message "GRUB/LILO failed to install to /target/" I choose to "Continue Installation without a Bootloader." The install finished fine but I was left unable to boot directly into Ubuntu. Here's how I got Ubuntu to boot...it may be possible to skip directly to the next section, and install grub using the "start emergency shell" mode in the xubuntu installer, but I never tested that method.

1. First you need a SUPERGRUBDISK boot disk. (I made this on another computer. I wrote the image to floppy with Rawrite for windows.)

2. Boot to the disk and at the first menu type "C" to enter the command line.

3. If your Ubuntu install is on the first partition and you only have one hard drive just type these lines of code at the grub prompt:
```
root (hd0,1)
kernel /vmlinuz root=/dev/sda2 
initrd /initrd.img
boot
```This is for a serial drive, if you have an IDE drive replace sda2 with hda2. If your install is in a different partition/drive, please refer to the sources below for more info.

**_Referenced Files can be found at:_**

SuperGrubDisk (Scroll Down for Floppy) - [http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)
RaWrite for Windows - [http://www.chrysocome.net/rawwrite](http://www.chrysocome.net/rawwrite)

**_Source:_**

SuperGrubDisk Homepage - [http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org)
SuperGrubDisk Documentation - [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) SuperGrub Disk Forums - [http://forjamari.linex.org/forum/forum.php?forum_id=235](http://forjamari.linex.org/forum/forum.php?forum_id=235) 

**SECTION 5. INSTALLING GRUB ONCE UBUNTU IS LOADED**

So I found myself with Ubuntu booting, and finally I was presented with a command line. I logged in, made sure the install cd was in the cd drive and then entered the following code to install grub:

```
sudo mount /cdrom
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install grub
sudo grub-install /dev/hda
sudo update-grub
```

**_Source: _**
Switch from LILO to GRUB - [http://xpt.sourceforge.net/techdocs/nix/disk/boot/boot06-Grub/index.html#_How_to_switch_from_LILO_to_GRUB](http://xpt.sourceforge.net/techdocs/nix/disk/boot/boot06-Grub/index.html#_How_to_switch_from_LILO_to_GRUB)
[B]
SECTION 6. AND THEN...I HAD NO GUI?
[/B]
Turns out I must have had a faulty install disk, cause X never was installed...Again, I made sure the install cd was in the drive and entered the code below to install X. NOTE: X RAN EXTREMELY SLOW because I only had 40 mb RAM. I don't know if it would have run better if I did a base install using a seperate set of code, which I will also provide.

Full Install of X:
```
sudo apt-cdrom add
insert cdrom and press enter
sudo apt-get install xubuntu-desktop
```

Basic Install:
```
sudo apt-cdrom add
insert cdrom and press enter
sudo apt-get install xorg xface4
```
[B][U]
Source: [/U][/B]
Xubuntu Doesn't Load GUI - [http://ubuntuforums.org/showthread.php?t=523343](http://ubuntuforums.org/showthread.php?t=523343)

----

Well that was it. Feel free to let me know if any of the information is erroneous, helpful, unfollowable, or needs editing. Thanks again to everyone who provided the help that kept me from tearing my hair out!

Graham

**_Oh and one last source: _**
[http://ubuntuforums.org/showthread.php?t=522474](http://ubuntuforums.org/showthread.php?t=522474) which kind of jumps around from issue to issue over the entire process. Special thanks to merlinus!

---

