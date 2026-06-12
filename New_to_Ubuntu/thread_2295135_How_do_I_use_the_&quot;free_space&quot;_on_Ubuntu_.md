---
title: "How do I use the &quot;free space&quot; on Ubuntu live usb?"
date: 2015-09-16
forum: New to Ubuntu
---

### Post by thrashercharged on 2015-09-16
I've made 2 usb jump drives into Ubuntu 14.04 live usb. One is 32bit, the other is 64bit.  When I look at them with Win7 I see some files and folders. I've attached the screenshots.  The 64bit version has a EFI and UUI folder that the 32 bit one doesn't have, and in both I see a casper-rw file that is huge.  Apparently both usb drives are formatted FAT32, and Win7 tells me that about 1.95 GB of space is used and I've lots of free space.

1.  Briefly, what are these folders and files for?  I'm worried that something might accidentally get deleted/moved when we're working with the USB drives in Win7 and mess up my ability to use the drive to boot into Ubuntu.  Is this a valid worry?

2.  Were should I store my datafiles on these USB drives where both Ubuntu and Win7 can access them?  Do I make a folder?

My goal is to use these USB drives to store data that's accessible both by Ubuntu and Win7, but I wanted to make them Ubuntu Live USBs so I can always boot into Ubuntu when I need/want to.  I would prefer to make separate partitions like I'd do with a HD and make a Linux partition and have NTSF/FAT32 partitions for data, but you can't do that and make a Live USB drive can you?  I made the Live USBs while booted into Ubuntu, and I believe it erases the entire USB drive when it makes it, right?

I've more questions related to this but I'll start another thread.

---

### Post by mastablasta on 2015-09-16
> **thrashercharged said:**
> I've made 2 usb jump drives into Ubuntu 14.04 live usb. One is 32bit, the other is 64bit.  When I look at them with Win7 I see some files and folders. I've attached the screenshots.  The 64bit version has a EFI and UUI folder that the 32 bit one doesn't have, and in both I see a casper-rw file that is huge.  Apparently both usb drives are formatted FAT32, and Win7 tells me that about 1.95 GB of space is 
used and I've lots of free space.

1.  Briefly, what are these folders and files for?  I'm worried that something might accidentally get deleted/moved when we're working with the USB drives in Win7 and mess up my ability to use the drive to boot into Ubuntu.  Is this a valid worry?


you can make multiboot USB using YUMI. some files have to be on USB disk and you shouldn't move them around or remove them.

obviously they contain the system image and are needed to boot the OS. I mean what else would they be? check windows install disk - it will be full of files and folders. same here. I think casper is there for persistance. if you do not have that set than that file is a lot smaller.

Live OS is mean to help you try out the OS and assist with easy install. not as an everyday use, production grade OS. 


> 

2.  Were should I store my datafiles on these USB drives where both Ubuntu and Win7 can access them?  Do I make a folder?


you can just create a folder called DATA and use that to store your data. it will be in FAT32 or NTFS. I have plenty of things on Xubutnu live USB. multiple folders, windows portable apps...
you can also store them at the root of USB (e.g right on E:\ drive)


> 
My goal is to use these USB drives to store data that's accessible both by Ubuntu and Win7, but I wanted to make them Ubuntu Live USBs so I can always boot into Ubuntu when I need/want to.  I would prefer to make separate partitions like I'd do with a HD and make a Linux partition and have NTSF/FAT32 partitions for data, but you can't do that and make a Live USB drive can you?  I made the Live USBs while booted into Ubuntu, and I believe it erases the entire USB drive when it makes it, right?

I am not sure what you are up to with your drives, but easiest way to mess around with the OS and to try out stuff is virtualbox. if you need a folder with shared data then you just create that. : [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

you can also do proper install on USB - again it depends what you want to do. and also why you are using USB. I use it to install the OS and to be able to troubleshoot other PC's (multiboot with light os like Xubuntu, a virus cleaner, imaging OS, pen testing OS... is good for that).

I've attached my junk on Xubuntu USB I use as fall back (on e of fallbacks if I need a live OS).

---

### Post by yancek on 2015-09-16
Looking at your image, I see that the casper-rw is a file.  This is for persistence and is a file and files are limited to 4GB when using FAT32, see the pendrivelinux link below.

  [http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)

The other folders/files you see are the standard for an Ubuntu Live CD.  You should be able to create another partition on the flash drive although you may need to shrink the current if you only have one partition.  You could then make another partition for data.  You can't do this from inside the flash, but need to use a different flash drive or DVD.  Then create a data partition.  You would then need to create a mount point on the UUI flash drive and put an entry in the /etc/fstab for your newly created partition.

---

### Post by JKyleOKC on 2015-09-16
> **thrashercharged said:**
> Win7 tells me that about 1.95 GB of space is used and I've **lots of free space**.
That "free space" reported by Win7 is most probably your entire set of Linux files. Windows fails to recognize the partition codes used by other systems, and reports only "free space" rather than admitting it doesn't know what's there!

---

### Post by thrashercharged on 2015-09-16
> [COLOR=#000000]you can make multiboot USB using YUMI. some files have to be on USB disk and you shouldn't move them around or remove them.  [/COLOR][COLOR=#000000]obviously they contain the system image and are needed to boot the OS. I mean what else would they be? check windows install disk - it will be full of files and folders. same here. I think casper is there for persistance. if you do not have that set than that file is a lot smaller. [/COLOR][COLOR=#000000]Live OS is mean to help you try out the OS and assist with easy install. not as an everyday use, production grade OS. [/COLOR]

Thanks for the info about YUMI and Casper - yes, I wanted persistance.  I understand these files must be system images, similar to a Win install disk.

> [COLOR=#000000]I am not sure what you are up to with your drives... [/COLOR][COLOR=#000000]you can also do proper install on USB - again it depends what you want to do. and also why you are using USB. [/COLOR]

My goal is to have bootable Linux USB jump drives with data that's accessible either with Win or Linux, so I can go to any computer, plug in my USB, and either use whatever OS it's currently running to surf the web and access my files, or if necessary, boot into Ubuntu with my USB jump drive and work out of Ubuntu.  I thought making a Live OS was the only way to do this, are you saying that I can do a "proper" install of Ubuntu/Linux on the USB and better accomplish my goals (as opposed to doing a Live OS)?  I understand the Live OS is really meant for trying out the OS and not for everyday use.  My intention is for temporary use of a public computer, etc if for some reason the OS on that computer isn't suiting my needs.

> [COLOR=#000000]you can just create a folder called DATA and use that to store your data. it will be in FAT32 or NTFS.[/COLOR]

Ok, I made a DATA folder using Win7 on my LiveOS USB on the root.  I then booted into Ubuntu using that LiveOS USB.  I don't see my DATA folder?  

Also, while booted in Ubuntu from the LiveOS USB, I used LibreOffice Writer and wrote a doc.  I tried to "SaveAs" onto my HD (which has a NTSF partition that's visible in Ubuntu as a folder named "MSDRIVE", I assume because that's what I named that volume in Win7) but I was not able to find MSDRIVE while in LibreOffice Writer to save the file to.  I also don't see the DATA folder I made on the USB drive.  So I did the only thing I could, which is save the file to where it wanted, which was "/home/ubuntu/documents/".

Ok fine, but when I boot up in Win7, I'm not able to find my file on that USB drive.   "/home/ubuntu/documents/" doesn't exist.  If I boot up in Ubuntu using my other HD (I have one physical Win7 bootable HD and another physical Ubuntu bootable HD) I'm also not able to find that file on the USB drive.

So to summarize my questions:

1.  Is there a better way than making a LiveOS to have a Ubuntu bootable USB drive that can be used to store data that's accessible with either Win or Linux? 
2.  If I boot with an Ubuntu LiveOS USB, how can I access this DATA folder I made on the USB drive root?  I can't find it.
3.  If I boot with an Ubuntu LiveOS USB, I can see that my NTFS partition on my HD is mounted and I can access it while doing OS stuff, but in LibreOffice, I can't find that NTFS partition to save files to. Why and how to resolve this?
4.  If I boot with an Ubuntu LiveOS USB and save a file to "/home/ubuntu/documents/", once I'm not booted with that LiveOS (and booted with Win7 or Ubuntu from another HD) I cannot find that folder or that file on that USB drive.

Thanks for the help!

---

### Post by thrashercharged on 2015-09-16
I see 2 more replies came in as I was typing my reply!

> [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG][COLOR=#000000] Originally Posted by [/COLOR]**thrashercharged**[COLOR=#000000] [/COLOR][[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13357113#post13357113")[COLOR=#000000][I]Win7 tells me that about 1.95 GB of space is used and I've **lots of free space**.

[/I]
[/COLOR]
[COLOR=#000000]That "free space" reported by Win7 is most probably your entire set of Linux files. Windows fails to recognize the partition codes used by other systems, and reports only "free space" rather than admitting it doesn't know what's there![/COLOR]

My 32bit LiveOS USB is a 4GB drive - doing a "Properties" on it reports 1.96 GB of used space and 1.75 GB free.
My 64bit LiveOS USB is a 16GB drivve - it reports 1.95 GB used space and 12.9 GB free.

So I don't think that free space is my entire set of Linux files?

> [COLOR=#000000]Looking at your image, I see that the casper-rw is a file. This is for persistence and is a file and files are limited to 4GB when using FAT32...  [/COLOR][COLOR=#000000]The other folders/files you see are the standard for an Ubuntu Live CD. You should be able to create another partition on the flash drive although you may need to shrink the current if you only have one partition. You could then make another partition for data. You can't do this from inside the flash, but need to use a different flash drive or DVD. Then create a data partition. You would then need to create a mount point on the UUI flash drive and put an entry in the /etc/fstab for your newly created partition.[/COLOR]

Ok, this obviously isn't the easiest way (making another partition) to store data, but if simply making a DATA folder on the root of the LiveOS drive doesn't work I guess I'll have to pursue this avenue!

---

### Post by sudodus on 2015-09-16
Windows can only read the first partition in a USB pendrive, and it must be a microsoft file system (FAT32 or NTFS or exFAT).

Linux can read any partition in a USB pendrive, but it cannot manage exFAT (except with some special tools).

Often the tools to create USB boot drives use a FAT32 partition. So your best bet is to create a persistent live drive. You can use a casper-rw file to store the data you want to persist, but it is better to use a casper-rw partition to do it. It will not be limited by the max file size of FAT32, 4 GB.

If you use mkusb, you can create a persistent live system from the Ubuntu family operating systems. You will be prompted to select the percentage of the available drive space for persistence, and the rest of it will be in a FAT32 partition and available to Windows (and exchange of data between Windows and Ubuntu).

If you save documents from Ubuntu into 'Documents' it will be stored in a linux file system, which Windows cannot (does not want to) read. So you must save things to be shared with Windows in the FAT32 partition (which is also the first partition). See this link and links from it.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

An alternative is to have two pendrives, one for the operating system and one for data, but it is not very convenient.

---

### Post by oldfred on 2015-09-16
I do not use Windows anymore, so do not put a Windows FAT32 or NTFS partition first on flash drives.
I have either full installs, or a grub only install and ISO files in folders that I can directly boot. Then I can have multiple installs on one flash drive. I did this before or about the same time as most of the auto scripts were created. And I had learned grub for standard boot, so made sense to also use grub for ISO.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

It now makes a difference whether UEFI or BIOS.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode
[http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)

How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images
[http://ubuntuforums.org/showthread.php?t=2276498](http://ubuntuforums.org/showthread.php?t=2276498)
Bootable UEFI USB Key
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

---

### Post by thrashercharged on 2015-09-16
> [COLOR=#000000]Windows can only read the first partition in a USB pendrive[/COLOR]

I only have 1 partition AFAIK.

> [COLOR=#000000]If you use mkusb, you can create a persistent live system from the Ubuntu family operating systems. You will be prompted to select the percentage of the available drive space for persistence, and the rest of it will be in a FAT32 partition and available to Windows (and exchange of data between Windows and Ubuntu).[/COLOR]

I used Startup Disk Creator to make my LiveOS USB drives, and I believe I was prompted to select how much space I wanted for persistence? I gave it 1GB, and it was my understanding that the rest would be "free space" available for exchanging data between Window and Ubuntu.  Is this not correct?  Do I have to use mkusb instead of Startup Disk Creator to do this?

> [COLOR=#000000]If you save documents from Ubuntu into 'Documents' it will be stored in a linux file system, which Windows cannot (does not want to) read. So you must save things to be shared with Windows in the FAT32 partition (which is also the first partition).[/COLOR]

I figured that something like that was going on, but it appears that when I save documents from [COLOR=#000000]Ubuntu into 'Documents', not only does it only appear in Linux, but apparently it only appears when you boot into the Linux that it's a part of?  That is, it's not visible when I boot into Linux from another installation?

[/COLOR]I looked more closely at what I'm experiencing and I've determined this:

1.  I made a "DATA" folder (FAT32) on the root of my LiveOS USB pendrive using Win7.  If I boot into a permanent installation of Ubuntu off a fixed HDD and insert this USB pendrive, I can access this DATA folder.  
2.  While booted into Ubuntu from my permanent installation off the HDD, if I run LibreOffice I can save files onto this DATA folder and onto a NTFS partition on that HDD.
3.  If I boot into Ubuntu using this LiveOS USB pendrive, I no longer see the "DATA" folder on this pendrive, but I can still see/access the NTFS partition on my HDD.
4.  While booted into Ubuntu off this LiveOS, if I run LibreOffice I cannot access/see either the "DATA" folder or the NTFS HDD partition.  Hence my only option for saving a file is into "Documents" in the Linux file system.
5.  Apparently I can only access this "Documents" folder while booted into the Linux OS that this folder is a part of.  i.e., I cannot see it from Windows obviously, but even if I boot into Ubuntu off the HDD I cannot see this folder.  So what I'm seeing is that it's pointless to make a file in LibreOffice while booted into a LiveOS, as I cannot save to any drive outside of the Linux file system, and if I'm booted into another copy of Linux, I can't get to this file, so essentially nothing I do under a LiveOS boot (in LibreOffice at least) is transferable to the outside world?  That just doesn't seem right, there must be something I'm not understanding.
6.  If 5. is really the way it is, then I don't see much of a point in booting off a LiveOS is there? Sure, it's fine for troubleshooting a system or running some diagnostic stuff and surfing the web, but you really wouldn't be able to use LibreOffice to do any work would you?

---

### Post by sudodus on 2015-09-16
> **thrashercharged said:**
> > [COLOR=#000000]Windows can only read the first partition in a USB pendrive[/COLOR]

I only have 1 partition AFAIK.

OK
> 
[QUOTE][COLOR=#000000]If you use mkusb, you can create a persistent live system from the Ubuntu family operating systems. You will be prompted to select the percentage of the available drive space for persistence, and the rest of it will be in a FAT32 partition and available to Windows (and exchange of data between Windows and Ubuntu).[/COLOR]

I used Startup Disk Creator to make my LiveOS USB drives, and I believe I was prompted to select how much space I wanted for persistence? I gave it 1GB, and it was my understanding that the rest would be "free space" available for exchanging data between Window and Ubuntu.  Is this not correct?  Do I have to use mkusb instead of Startup Disk Creator to do this?
[/QUOTE]
Yes, it is correct. If persistence works for you already, it may be OK. But 1 GB is not much, if you want to use it for a longer time, and install some programs. If you run out of space in the casper-rw file, the persistence will be corrupted. So at least with the 16 GB pendrive you should have more space for persistence, maybe around half of the available drive space.
> 
[QUOTE][COLOR=#000000]If you save documents from Ubuntu into 'Documents' it will be stored in a linux file system, which Windows cannot (does not want to) read. So you must save things to be shared with Windows in the FAT32 partition (which is also the first partition).[/COLOR]

I figured that something like that was going on, but it appears that when I save documents from [COLOR=#000000]Ubuntu into 'Documents', not only does it only appear in Linux, but apparently it only appears when you boot into the Linux that it's a part of?  That is, it's not visible when I boot into Linux from another installation?
[/QUOTE]
No, that description is not correct. A live or installed linux system can read the files written by another live or installed linux system with one exception: if the system is encrypted. But you must identify and mount the partition and directory path, where the files were written. Then you can find them with a file browser.
> 
[/COLOR]I looked more closely at what I'm experiencing and I've determined this:

1.  I made a "DATA" folder (FAT32) on the root of my LiveOS USB pendrive using Win7.  If I boot into a permanent installation of Ubuntu off a fixed HDD and insert this USB pendrive, I can access this DATA folder.  
2.  While booted into Ubuntu from my permanent installation off the HDD, if I run LibreOffice I can save files onto this DATA folder and onto a NTFS partition on that HDD.
3.  If I boot into Ubuntu using this LiveOS USB pendrive, I no longer see the "DATA" folder on this pendrive, but I can still see/access the NTFS partition on my HDD.

Well, it is there, but it is a system folder and mounted with another name, maybe /cdrom. You can identify it as the first partition on the pendrive, so maybe **/dev/sdb1** or **/dev/sdc1** depending of which other drives are mounted (/dev/sda is probably your internal drive).

When running live only that partition will be mounted read-only, you can read but not write there. When running persistent live, that partition will be mounted read-write, you can read and write there.

```
df
```

If you want help to identify the FAT32 partition, please post the output of the **df** command. While you are doing this, I suggest that you run another command too and post the output from it.

```
sudo lsblk -fm
```

> 
4.  While booted into Ubuntu off this LiveOS, if I run LibreOffice I cannot access/see either the "DATA" folder or the NTFS HDD partition.  Hence my only option for saving a file is into "Documents" in the Linux file system.

Either something is wrong, or it is there but you are not finding it.
> 
5.  Apparently I can only access this "Documents" folder while booted into the Linux OS that this folder is a part of.  i.e., I cannot see it from Windows obviously, but even if I boot into Ubuntu off the HDD I cannot see this folder.  So what I'm seeing is that it's pointless to make a file in LibreOffice while booted into a LiveOS, as I cannot save to any drive outside of the Linux file system, and if I'm booted into another copy of Linux, I can't get to this file, so essentially nothing I do under a LiveOS boot (in LibreOffice at least) is transferable to the outside world?  That just doesn't seem right, there must be something I'm not understanding.
6.  If 5. is really the way it is, then I don't see much of a point in booting off a LiveOS is there? Sure, it's fine for troubleshooting a system or running some diagnostic stuff and surfing the web, but you really wouldn't be able to use LibreOffice to do any work would you?

I'm using these kinds of systems side by side. I'm even testing the versions during the development cycle, and I can assure you, that they can read "each other's files". Please check if your installed system is encrypted! If that is the case, it ***should*** be impossible to read it.

---

### Post by yancek on 2015-09-16
> 3.  If I boot into Ubuntu using this LiveOS USB pendrive, I no longer  see the "DATA" folder on this pendrive, but I can still see/access the  NTFS partition on my HDD.

When you boot the persistent Ubuntu on the flash drive, you can see the DATA file you created in windows by looking in the /cdrom folder which is in the / of the filesystem.  You can also access it from /media/cdrom but that is just a link.  The Libre Office solution might be the same, when you save try to navigate to the /cdrom folder.

I don't know what Documents folder you are referring to.  Is this when booted to the persistent Ubuntu?

 > So what I'm seeing is that it's pointless to make a file in LibreOffice  while booted into a LiveOS, as I cannot save to any drive outside of the  Linux file system, 

Copy to the second partition you created, if you created one.  Simply create a mount point (directory) on the persistent Ubuntu, then an entry in the /etc/fstab file while you are booted into it.  You're going to run out of space quickly as your Ubuntu with the casper-rw persistent file is less than 2GB so about 1GB for persistence.  Of course, if you do this, even if you format it as vfat or ntfs, windows won't see it.  That's not a Linux/Ubuntu problem, that's microsoft.  Interestingly enough, if I create a second partition on a flash drive and format it ntfs, I can see it, read it and write to it from Linux but it is not recognized at all in windows 7.

If you have a second partition created, it should be available in the persistent Ubuntu under /media/ubuntu and you may not need to create a mount point, particularly if it is already using a UUID for the partition.  

You might be better off doing a normal install, at least on the larger flash drive as long as you don't install proprietary drivers such as for graphics.

---

### Post by yancek on 2015-09-16
I had an empty 8GB flash, booted an installed Ubuntu system, opened GParted and created an ntfs partition as the first partition on the flash of about 6GB.  Then I created a second vfat partition with the remaining space.  I used unetbootin to put Peppermint 5 (Ubuntu derivative) on the flash.  When I opened unetbootin, it showed sdc2 which was the vfat partition and I installed the Peppermint Live CD there, creating a small persistent file.  Rebooted and the flash drive booted to Peppermint successfully.

While booted to the persistent flash, I checked the /cdrom folder in the / of the filesystem and the casper-rw persistent file was there.  The ntfs partition on sdc1 I created was available under /media/peppermint showing as its UUID.  I created several folders in different places and re-booted to test and the folders were there on reboot. 

I booted windows 7 and under Computer saw the first partition of the flash drive as Drive H, created a folder on the partition.  Rebooted the flash drive and the folder I created on windows was available under /media/peppermint.   As expected, the second partition formatted FAT32 was not available.

I don't use pendrivelinux but I would expect this to work with it.  Because of windows inability to read other than the first partition on a flash drive, doing a full install of Ubuntu to a second partition and using the first partition as ntfs/vfat would work.

---

### Post by thrashercharged on 2015-09-18
Sorry for the delay - I've just had the chance to get back to working on this.

> If you want help to identify the FAT32 partition, please post the output of the **df** command. While you are doing this, I suggest that you run another command too and post the output from it.


Ok - attached.

Right now I'm booted into my LiveOS Persistant Ubuntu and the attached is the response I get for the df and sudo lsblk -fm commands.

sda is my encrypted Win7 drive - I do not expect nor want to have Ubuntu do anything with this drive!
sdb is my 16GB USB jump drive.  I assume it's named UUI - I don't recall naming it that but whatever... perhaps it was named that from the factory or did Ubuntu do that when I made it a LiveOS?
sdc is my 2nd HDD with a 20GB ext4 partition (with Ubuntu 14.04 installed) and a 374GB NTFS partition named MS_drive

Following advice given on this forum, I was able to find the "DATA" folder I made, apparently it's mounted under both /cdrom and /media/cdrom.  I was also able to find my "MS_drive" NTFS folder under /media/ubuntu.

HOWEVER, when I open LibreOffice and try to "Save As" to either /cdrom/DATA or /media/cdrom/DATA I get the error message "Error saving the document Untitled1: /cdrom/DATA/untitled1.odt does not exist.  Note this is when I'm booted into my LiveOS USB and I'm trying to save to that "DATA" folder which is on that LiveOS USB.  So I'm still not understanding how to use LibreOffice to save a file onto that "DATA" folder on my LiveOS USB.

My files are not encrypted AFAIK.

---

### Post by sudodus on 2015-09-18
Is there persistence now? In that case the loop1 device is the loop mounted casper-rw file.

Does it work to create files in /cdrom manually?

You can check the file permissions with the following two commands.

```
ls -l /
ls -l /cdrom
```

It is easier to read the output if you copy and paste the text from the terminal window to the edit box of a reply window, and then click the red button 'Advanced', mark the pasted text and click on the **#** icon above the editing window to put it within CODE tags.

If you can create files manually, but not with LibreOffice, there might be a check, that you are not allowed to write onto CDROM (actually a bug, when it is used with a pendrive). But the problem might also be permissions, which will be shown by the output of those two commands.

---

### Post by sudodus on 2015-09-18
Edit: I tested in a similar setup (made by the Ubuntu Startup Disk Creator), and /cdrom is mounted read/write, but it is owned by root (the superuser), so you need superuser privileges to write there unless you change the permissions, which is hard with system partitions.

So it is possible to use **/cdrom** (copy files that are created elsewhere), not very convenient but possible.

```
sudo cp file /cdrom
```

I can check later, if systems made with other tools work in the same way, or if they are easier to use.

---

### Post by yancek on 2015-09-18
> sdb is my 16GB USB jump drive. I assume it's named UUI - I don't recall naming it that but whatever... 

I expect that was done because you used the UUI, universal usb installer but it's not relevant to anything.

The /media/cdrom is just a link to /cdrom.  So if you save a file to /cdrom it will show in /media/cdrom and vice versa.

> Error saving the document Untitled1: /cdrom/DATA/untitled1.odt does not exist

I'm not sure why you get that error.  I have a similar setup with a flash drive with a LiveCD with persistence of Peppermint Linux, derivative of Ubuntu.  Can't save anything to /cdrom/DATA as a normal user.  Didn't have Libre Office installed but using the text editor gedit, I was able to save when logged in as root.  So in a terminal:  sudo gedit and then just click File/Save As  and it saves.  I navigate to the /cdrom/DATA directory and the file is there.

The owner:group for /cdrom is root:root, same obviously for /cdrom/DATA.  Trying to change owner I get 'operation not permitted'.  Is 'DATA' actually 'DATA' or is it Data or data as that will make a difference.  I doubt you will be able to save anything to /cdrom/DATA from windows.

---

### Post by thrashercharged on 2015-09-18
> You can check the file permissions with the following two commands.

 	Code:
 	ls -l /
ls -l /cdrom


```
ubuntu@ubuntu:~$ ls -l /
total 48
drwxr-xr-x   2 root root  2955 Jul 22  2014 bin
drwxr-xr-x   1 root root  4096 Sep 18 16:26 boot
drwxr-xr-x  15 root root  4096 Jan  1  1970 cdrom
drwxr-xr-x  16 root root  4380 Sep 18 16:25 dev
drwxr-xr-x   1 root root  4096 Sep 18 16:26 etc
drwxr-xr-x   1 root root  4096 Sep 15 00:12 home
lrwxrwxrwx   1 root root    33 Jul 22  2014 initrd.img -> boot/initrd.img-3.13.0-32-generic
drwxr-xr-x  26 root root   899 Jul 22  2014 lib
drwxr-xr-x   2 root root    43 Jul 22  2014 lib64
drwx------   2 root root 16384 Sep 14 23:30 lost+found
drwxr-xr-x   1 root root  4096 Sep 15 13:46 media
drwxr-xr-x   2 root root     3 Apr 10  2014 mnt
drwxr-xr-x   2 root root     3 Jul 22  2014 opt
dr-xr-xr-x 245 root root     0 Sep 18 16:24 proc
drwxr-xr-x  21 root root   338 Jul 22  2014 rofs
drwx------   1 root root  4096 Sep 18 09:31 root
drwxr-xr-x  22 root root   720 Sep 18 16:26 run
drwxr-xr-x   2 root root  4885 Jul 22  2014 sbin
drwxr-xr-x   2 root root     3 Jul 22  2014 srv
dr-xr-xr-x  13 root root     0 Sep 18 16:24 sys
drwxrwxrwt   5 root root   140 Sep 18 16:32 tmp
drwxr-xr-x   1 root root  4096 Jul 22  2014 usr
drwxr-xr-x   1 root root  4096 Jul 22  2014 var
lrwxrwxrwx   1 root root    30 Jul 22  2014 vmlinuz -> boot/vmlinuz-3.13.0-32-generic
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ ls -l /cdrom
total 1051276
-rwxr-xr-x 1 root root        134 Sep 14 19:24 autorun.inf
drwxr-xr-x 3 root root       4096 Sep 14 19:24 boot
drwxr-xr-x 2 root root       4096 Sep 18 16:26 casper
-rwxr-xr-x 1 root root 1073741824 Sep 18 16:33 casper-rw
drwxr-xr-x 2 root root       4096 Sep 16 08:51 DATA
drwxr-xr-x 3 root root       4096 Sep 14 19:27 dists
drwxr-xr-x 3 root root       4096 Sep 14 19:27 EFI
drwxr-xr-x 2 root root       4096 Sep 14 19:27 install
-r-xr-xr-x 1 root root      32768 Sep 14 19:27 ldlinux.sys
-rwxr-xr-x 1 root root      18092 Apr  4  2012 license.txt
-rwxr-xr-x 1 root root      21426 Sep 14 19:24 md5sum.txt
drwxr-xr-x 2 root root       4096 Sep 14 19:27 pics
drwxr-xr-x 4 root root       4096 Sep 14 19:27 pool
drwxr-xr-x 2 root root       4096 Sep 14 19:27 preseed
-rwxr-xr-x 1 root root        231 Sep 14 19:24 README.diskdefines
drwxr-xr-x 2 root root       4096 Sep  7 01:36 $RECYCLE.BIN
drwxr-xr-x 2 root root      12288 Sep 14 19:27 syslinux
-rwxr-xr-x 1 root root      49070 Jan 15  2015 Uni-USB-Installer-Copying.txt
-rwxr-xr-x 1 root root      19261 Jun 26 12:58 Uni-USB-Installer-Readme.txt
drwxr-xr-x 2 root root       4096 Aug 31 23:26 uui
-rwxr-xr-x 1 root root    2551408 Sep 14 19:24 wubi.exe
 

```

Ok - here it is, I dont' know how to decipher whether I have permissions or not?

---

### Post by thrashercharged on 2015-09-18
> sdb is my 16GB USB jump drive. I assume it's named UUI - I don't recall naming it that but whatever...
I expect that was done because you used the UUI, universal usb installer but it's not relevant to anything.
The /media/cdrom is just a link to /cdrom.  So if you save a file to /cdrom it will show in /media/cdrom and vice versa.


Thanks for explaining that. So if /media/cdrom is just a link, does that mean /media/ubuntu/MS_drive is also a link too? 
If so, where's the real MS_drive folder? 

> Error saving the document Untitled1: /cdrom/DATA/untitled1.odt does not exist
			
I'm not sure why you get that error.  I have a similar setup with a
 flash drive with a LiveCD with persistence of Peppermint Linux, 
derivative of Ubuntu.  Can't save anything to /cdrom/DATA as a normal 
user.  Didn't have Libre Office installed but using the text editor 
gedit, I was able to save when logged in as root.  So in a terminal:  
sudo gedit and then just click File/Save As  and it saves.  I navigate 
to the /cdrom/DATA directory and the file is there.


I just tried the same using gedit while booted into my LiveOS Ubuntu and get the same results as you - file saves and is there.
But I still can't ssave anything to /cdrom/DATA using LibreOffice.

> The owner:group for /cdrom is root:root, same obviously for /cdrom/DATA.
  Trying to change owner I get 'operation not permitted'.  Is 'DATA' 
actually 'DATA' or is it Data or data as that will make a difference.  I
 doubt you will be able to save anything to /cdrom/DATA from windows.

'DATA' is really 'DATA'. I made that folder using Win7 and put it on the root of this LiveOS USB and I am able to save to it in Win7.

---

### Post by thrashercharged on 2015-09-18
> Edit: I tested in a similar setup (made by the Ubuntu Startup Disk  Creator), and /cdrom is mounted read/write, but it is owned by root (the  superuser), so you need superuser privileges to write there unless you  change the permissions, which is hard with system partitions.

So it is possible to use **/cdrom** (copy files that are created elsewhere), not very convenient but possible.

 	Code:
 	sudo cp file /cdrom


So let me see if my understanding is correct:

I made this folder named "DATA" on the root of my LiveOS USB using Win7.  When I boot into Ubuntu using this LiveOS, I can find this "DATA" folder mounted under /cdrom.  gedit can find and write to that folder, but since it is owned by the root (the SU), I'll need SuperUser privlieges to write there using LibreOffice (and possibly other applications) unless I change the permissions, which is possible using that sudo cp file /cdrom command but I'll have to run that command everytime I boot using this LiveOS?

My goal is to have a LiveOS with a FAT32 folder that is accessible in both Ubuntu (when I boot with this LiveOS) and Win7 and Ubuntu (when I boot off a HDD) - this FAT32 folder (my "DATA" folder) will be used to transfer files I make while booted with this LiveOS to other computers.  Am I to understand there's not really a good way to accomplish this?  (Other than changing permissions for the /cdrom folder every time I boot with the LiveOS?

I'm not complaining (well, I'm a bit disillusioned if this is the case), just trying to figure out how to best accomplish my goal!  If my understanding is correct, is this a bug that will be fixed, or is this just the way it is?

---

### Post by sudodus on 2015-09-18
> **thrashercharged said:**
> ```
ubuntu@ubuntu:~$ ls -l /
total 48
drwxr-xr-x   2 root root  2955 Jul 22  2014 bin
drwxr-xr-x   1 root root  4096 Sep 18 16:26 boot
[COLOR="#FF0000"]drwxr-xr-x  15 root root  4096 Jan  1  1970 cdrom[/COLOR]
drwxr-xr-x  16 root root  4380 Sep 18 16:25 dev
drwxr-xr-x   1 root root  4096 Sep 18 16:26 etc
drwxr-xr-x   1 root root  4096 Sep 15 00:12 home
lrwxrwxrwx   1 root root    33 Jul 22  2014 initrd.img -> boot/initrd.img-3.13.0-32-generic
drwxr-xr-x  26 root root   899 Jul 22  2014 lib
drwxr-xr-x   2 root root    43 Jul 22  2014 lib64
drwx------   2 root root 16384 Sep 14 23:30 lost+found
drwxr-xr-x   1 root root  4096 Sep 15 13:46 media
drwxr-xr-x   2 root root     3 Apr 10  2014 mnt
drwxr-xr-x   2 root root     3 Jul 22  2014 opt
dr-xr-xr-x 245 root root     0 Sep 18 16:24 proc
drwxr-xr-x  21 root root   338 Jul 22  2014 rofs
drwx------   1 root root  4096 Sep 18 09:31 root
drwxr-xr-x  22 root root   720 Sep 18 16:26 run
drwxr-xr-x   2 root root  4885 Jul 22  2014 sbin
drwxr-xr-x   2 root root     3 Jul 22  2014 srv
dr-xr-xr-x  13 root root     0 Sep 18 16:24 sys
drwxrwxrwt   5 root root   140 Sep 18 16:32 tmp
drwxr-xr-x   1 root root  4096 Jul 22  2014 usr
drwxr-xr-x   1 root root  4096 Jul 22  2014 var
lrwxrwxrwx   1 root root    30 Jul 22  2014 vmlinuz -> boot/vmlinuz-3.13.0-32-generic
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ ls -l /cdrom
total 1051276
-rwxr-xr-x 1 root root        134 Sep 14 19:24 autorun.inf
drwxr-xr-x 3 root root       4096 Sep 14 19:24 boot
drwxr-xr-x 2 root root       4096 Sep 18 16:26 casper
-rwxr-xr-x 1 root root 1073741824 Sep 18 16:33 casper-rw
drwxr-xr-x 2 root root       4096 Sep 16 08:51 DATA
drwxr-xr-x 3 root root       4096 Sep 14 19:27 dists
drwxr-xr-x 3 root root       4096 Sep 14 19:27 EFI
drwxr-xr-x 2 root root       4096 Sep 14 19:27 install
-r-xr-xr-x 1 root root      32768 Sep 14 19:27 ldlinux.sys
-rwxr-xr-x 1 root root      18092 Apr  4  2012 license.txt
-rwxr-xr-x 1 root root      21426 Sep 14 19:24 md5sum.txt
drwxr-xr-x 2 root root       4096 Sep 14 19:27 pics
drwxr-xr-x 4 root root       4096 Sep 14 19:27 pool
drwxr-xr-x 2 root root       4096 Sep 14 19:27 preseed
-rwxr-xr-x 1 root root        231 Sep 14 19:24 README.diskdefines
drwxr-xr-x 2 root root       4096 Sep  7 01:36 $RECYCLE.BIN
drwxr-xr-x 2 root root      12288 Sep 14 19:27 syslinux
-rwxr-xr-x 1 root root      49070 Jan 15  2015 Uni-USB-Installer-Copying.txt
-rwxr-xr-x 1 root root      19261 Jun 26 12:58 Uni-USB-Installer-Readme.txt
drwxr-xr-x 2 root root       4096 Aug 31 23:26 uui
-rwxr-xr-x 1 root root    2551408 Sep 14 19:24 wubi.exe
 

```

Ok - here it is, I dont' know how to decipher whether I have permissions or not?

The user **root** owns the directory /cdrom and only root can write there. So you need elevated permissions to write there. LibreOffice does not run with elevated permissions and should not run like that either. Instead you should save files in the ordinary file system (for example the directory Documents) and after that copy the file(s) to /cdrom with

```
cd
cd Documents
sudo cp file1.odt file2.odt /cdrom
```

---

### Post by yancek on 2015-09-18
> So if /media/cdrom is just a link, does that mean /media/ubuntu/MS_drive is also a link too? 
If so, where's the real MS_drive folder? 

I don't think /media/ubuntu/MS_drive is a link.  If you look at the folder icon, it will have a small black arrow which indicates it is a link.  The real MS_drive folder is on your other hard drive.  What you see when booted to the Live CD on the usb drive is a mount point which gives you access to that folder.

 >  unless I change the permissions, which is possible using that sudo cp  file /cdrom command but I'll have to run that command everytime I boot  using this LiveOS?

I don't think you will be able to change permissions.  When I was booted to the flash with Ubuntu, I got 'operation not permitted' for /cdrom and obviously and sub-directories.  You can run Libre Office as a user and save it somewhere and then copy it to the /cdrom with the sudo cp command.  You're trying to do something this system was not designed to do.  It's basically and installer and a method to test the operating system.  Your expectations are unrealistic.  Part of the problem is that windows chooses not to recognize Linux filesystems so that if you save a file on Ubuntu or any other Linux system, it won't be possible to boot windows and copy it from that partition.  Why, because windows can't read a Linux filesystem.  Linux can read and write to windows filesystems however.

There isn't any simply way I can think of.  If you have a 32GB drive, you could not an actual install of Ubuntu using about a 10GB partition and use the first 20+GB for a FAT32 or ntfs partition.  This should work on multiple computers if you do NOT install proprietary drivers.  You can install Ubuntu to the second partition, install it's bootloader to the mbr.  You are still going to have to copy anything you create on Ubuntu to the FAT32 or ntfs partition and that is because windows can't read/write to a Linux filesystem.  You could also install Ubuntu as a Live CD to a second partition and leave the first as FAT32 or ntfs but you will have the same circumstance.  This just isn't something a Live CD even with persistence was designed to do and basically, if windows could read from a Linux filesystem, your problem would be solved but it can't and I seriously doubt it ever will.  It's not that they can't do it, it's that they don't want to.

My statement above about not being able to write to the DATA was in error as you know.  Actually it is the opposite.  From windows you can create anything and delete anything.  Good luck with it.

---

### Post by Geoffrey_Arndt on 2015-09-18
MS does also present a solution for this - - using their cloud storage (azure).   Like Dropbox and other cloud solutions it can run in both platforms, and each pc can save and retrieve files that are secure and synced.   The user can also use other cross-platform programs like 7zip to compress/encrypt (AES256) those folders/files prior to upload.    Another solution that can yield the same results (shared data) is SAMBA (which is 100% free).    You can even insert a 64 or 128 usb flash card into a wireless printer with SD slots (like Epson Workforce 645).   Samba takes a bit more work (to initially setup), but no cost.   Cloud is more flexible, but you pay for that (fairly modestly if someone is not a "media hoarder").   

Above may not be a solution in the "form" OP was looking for, but it does answer the basic need (using different methods).

---

### Post by yancek on 2015-09-19
> MS does also present a solution for this - - using their cloud storage  (azure).   Like Dropbox and other cloud solutions it can run in both  platforms, and each pc can save and retrieve files that are secure and  synced.   The user can also use other cross-platform programs like 7zip  to compress/encrypt (AES256) those folders/files prior to upload.     Another solution that can yield the same results (shared data) is SAMBA  (which is 100% free).    You can even insert a 64 or 128 usb flash card  into a wireless printer with SD slots (like Epson Workforce 645).    Samba takes a bit more work (to initially setup), but no cost.   Cloud  is more flexible, but you pay for that (fairly modestly if someone is  not a "media hoarder").   

The problem with 'cloud' is in the case of the OP, he may need a computer which has no access to the internet.  You also have to have complete trust in the provider.  Also there is the cost?  Using Samba, if he is just using computers on his own network that would work.  Maybe he needs to write a document on a university or work computer or a computer at a public library.  If he is just wanting data on the flash that he can view/save from both windows/Linux the explanations above will work.  Running LibreOffice as root will allow him to save to the directory he wants but I don't think that's a good idea.  Simplest and safest is to write/save ass a user and then copy as root.

---

### Post by sudodus on 2015-09-19
> **yancek said:**
> ... Simplest and safest is to write/save as a user and then copy as root.

+1

---

### Post by mystics on 2015-09-19
> **yancek said:**
> The problem with 'cloud' is in the case of the OP, he may need a computer which has no access to the internet.

A reasonable concern for certain people, but I think that unless someone specifies as such, using the cloud is very good advice. 

> Also there is the cost?

Both Google and Microsoft offer 15 GB of free storage. That means each one is offering more free storage than either of the OP's USB drives have. So I don't think cost should be a concern here.

> Maybe he needs to write a document on a university or work computer or a computer at a public library.

At least in my experience, you can still access your cloud storage from these devices. The only concern is making sure you log out of whatever accounts you were in and make sure to never save passwords. But if you're failing to do either of those on public computers, giving someone access to your cloud storage is the least of your concerns. Besides, it isn't like you can't easily steal a USB drive.

But really, I don't think the OP has to treat this as an either/or situation. If they have multiple GB of free space left on a USB, then they should take advantage of that. And with various cloud storage options, they have dozens of GB of storage space made available freely across many companies. Treating this as either/or is just telling the OP to not take advantage of the resources made available to them, which limits the usefulness of any advice we give.

---

### Post by JKyleOKC on 2015-09-19
Would not these two commands solve his problem more easily?
> sudo chgrp -R ubuntu /cdrom/DATA
sudo chmod -R 0775 /cdrom/DATA
The first, of course, would recursively change group ownership of the DATA folder and all its current content from "root" to "ubuntu," which appears to be the group to which his persistent installation belongs. The second would then change permissions from "drwxr-xr-x" to "drwxrwxr-x" allowing him to write and to edit anything stored there.

This still would not make Windows capable of accessing those files, but that problem appears to have been solved already...

---

### Post by sudodus on 2015-09-19
I think the problem is that /cdrom is a system partition with FAT32, so the ownership and permissions are set by the system, and cannot be changed afterwards. After reading your post, *JKyleOKC*, I tested it, and I'm sorry, but it did not work for me.

Some other persistent live systems are configured in such a way, that it works directly to write to the first partition. The first partition has a FAT32 file system, and it is used during boot, but it is not locked, when you have logged into linux. Make a ***persistent live system*** with [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb), and the first partition will be owned by the user, so there are no problems to read from and write to it.

---

### Post by yancek on 2015-09-19
> Both Google and Microsoft offer 15 GB of free storage

With the history of Google and microsoft, feel free to trust them.  I certainly don't.  A cloud option might be good for some but, for whatever reason the OP had specific requirements that he was trying to use and I think it was the protability.  He could carry an external drive around with an OS on it, or a notebook or laptop but that's not what he was asking.

> I think the problem is that /cdrom is a system partition with FAT32, so  the ownership and permissions are set by the system, and cannot be  changed afterwards. After reading your post, *JKyleOKC*, I tested it, and I'm sorry, but it did not work for m  

I also tested a persistent Ubuntu flash and was unable to change permissions or owner:group using sudo. 

I had the same results as the OP with LibreOffice.  Saving a file will save it to /home/ubuntu.  I had a 524MB persistent file.  When I clicked Save in Libre Office and selected it the file was also saved to /home/ubuntu.  If instead I select filesystem as the location, I can navigate to the /cdrom/data directory and click save and get a message that it doesn't exist.  Using a terminal and sudo, I could copy the file from /home/ubuntu to /cdrom/data successfully.  As a test, I opened libreoffice using sudo and was able to save a file directly to /cdrom/data.

---

### Post by oldfred on 2015-09-19
I am finding when I directly boot live ISO with grub, not only are ownership & permissions and issue, but live installer's default userID is 999, where all standard installs use 1000 as first or default user.

---

### Post by mystics on 2015-09-19
> **yancek said:**
> With the history of Google and microsoft, feel free to trust them.  I certainly don't.  A cloud option might be good for some but, for whatever reason the OP had specific requirements that he was trying to use and I think it was the protability.  He could carry an external drive around with an OS on it, or a notebook or laptop but that's not what he was asking.

From my experience, a lot of people, even more technologically knowledgeable ones, still seem to overlook the potential to use cloud storage for more than just collaberation. Even if they know of things like Google Drive, USB drives have for years been the default way of moving around files and are still often the first thing people reach for, and the number of "Well why didn't I think of that!" moments I've had with friends who I told to use cloud storage is staggering. So unless someone specifically says they don't want to use cloud storage (which the OP didn't do), I think it is reasonable to assume that they overlooked that possibility.

And I'm not saying people shouldn't help the OP with the original request. I just don't think we should completely overlook other options to help the OP reach the desired end goal.

---

### Post by sudodus on 2015-09-20
> **oldfred said:**
> I am finding when I directly boot live ISO with grub, not only are ownership & permissions and issue, but live installer's default userID is 999, where all standard installs use 1000 as first or default user.

It depends how you implement the 'grub-n-iso' method. Doing it with [mkusb](https://help.ubuntu.com/community/mkusb) works, such that the first partition will be easily accessed because it will be owned by the default user of the live system (as I described in my previous post). Doing it with my 'original grub-n-iso method' according to [this link (post #6 and following)](http://ubuntuforums.org/showthread.php?t=2259682) will also work, but a beginner might prefer mkusb.

Edit: Yes, the default user in live sessions is 999, with the verbose name 'ubuntu' in Ubuntu, 'lubuntu' in Lubuntu etc and 'qwerty' in LXLE :-) But it does not prevent using the first partition when that user owns it, because you are logged in as that user.

---

### Post by thrashercharged on 2015-09-21
I'm the OP - sorry I was busy all weekend away from the internet - I'm surprised at all this traffic on this thread over the weekend!

@Sudodus recommended:
> The user **root** owns the directory /cdrom and only root can write  there. So you need elevated permissions to write there. LibreOffice does  not run with elevated permissions and should not run like that either.  Instead you should save files in the ordinary file system (for example  the directory Documents) and after that copy the file(s) to /cdrom with

     Code:

     cd
cd Documents
sudo cp file1.odt file2.odt /cdrom

I tried that but was unsuccessful.  I made a file "Checking Ubuntu Version.docx" using LibreOffice while booted into my LiveOS and saved it into /Home/Documents.  Following the above advice, here's what I get:

ubuntu@ubuntu:~$ cd Documents
ubuntu@ubuntu:~/Documents$ sudo cp Checking Ubuntu Version.docx Checking Ubuntu Version.docx /cdrom
cp: cannot stat ‘Checking’: No such file or directory
cp: cannot stat ‘Ubuntu’: No such file or directory
cp: cannot stat ‘Version.docx’: No such file or directory
cp: cannot stat ‘Checking’: No such file or directory
cp: cannot stat ‘Ubuntu’: No such file or directory
cp: cannot stat ‘Version.docx’: No such file or directory
ubuntu@ubuntu:~/Documents$ 

Apparently I can't have spaces in my filenames when using Terminal to move files?

I'm aware of Cloud Storage, but I'd prefer a solution that doesn't require Internet access.  Firstly, I may not have internet access (in a car, out in the woods, at an oilfield, miles from land, etc.) and if I can get WiFi, it's sometimes a pain as you need the password (which could change daily if you're at a workplace - especially if you're a vistor at that workplace). And if you're in a public place, you need to know which WiFi source is the one you want (the legit one - you don't want to accidentally hook into someone's Pineapple WiFi).

>  					[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **oldfred** 					[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13359181#post13359181") 				
 				I am finding when I directly boot live ISO with  grub, not only are ownership & permissions and issue, but live  installer's default userID is 999, where all standard installs use 1000  as first or default user.
 			 		 	 It depends how you implement the 'grub-n-iso' method. Doing it with [mkusb]("https://help.ubuntu.com/community/mkusb")  works, such that the first partition will be easily accessed because it  will be owned by the default user of the live system (as I described in  my previous post). Doing it with my 'original grub-n-iso method'  according to [this link (post #6 and following)]("http://ubuntuforums.org/showthread.php?t=2259682") will also work, but a beginner might prefer mkusb.

Edit: Yes, the default user in live sessions is 999, with the verbose  name 'ubuntu' in Ubuntu, 'lubuntu' in Lubuntu etc and 'qwerty' in LXLE :smile: But it does not prevent using the first partition when that user owns it, because you are logged in as that user.

Sorry, I'm not understanding how the default user being 1000 or 999 is important?  So are y'all saying that I should be making my LiveOS USB using mkusb instead of the "default" way that seems to be built into Ubuntu (Sorry I can't remember or find that app now as apparently it's not available in the LiveOS I'm booted with now, and only in Ubuntu when I boot into it with a HDD).

So if I make a LiveOS using mkusb it'll make the first partition accessable because it'll be owned by the default user, so then I can save a file into home/documents as long as I don't have spaces in the filename, and then I can copy from that folder into a NTFS partition using sudo cp commands?

I understand it's not Linux's fault that MS chooses not to recognize Linux partitions, and I am by no means a MS lover - I'm just a computer user that's trying to use my laptop as a tool and unfortunately most of my apps need to run under Win7 because that's what my corporate employer chooses use.  And no, I don't work in the computer industry obviously - we do engineering and manufacturing.  I decided I needed to give Linux a try and decided it would be nice to make all my USB jump drives Linux bootable (instead of just being all data) so I can have a way to use any PC I come across and boot into a OS setup in a way I'm familiar with, do my work and save files that I can then access from Win7.

This really seems to be a very reasonable goal (to be able to easily use all my free space on a USB drive in both Win7 and Linux) and be bootable into Linux.  I'd say a lot of folks would want to do this, and frankly I'm surprised I seem to be the first post trying to do this after all these years!  So are my options using a LiveOS to make it using mkusb and copy the files, or not using LiveOS and making a permanent Ubuntu installation on a USB?  If the later, what's the simplest way (step by step) to do this?

Thanks for all the advice and discussion!

---

### Post by sudodus on 2015-09-21
> **thrashercharged said:**
> 
I tried that but was unsuccessful.  I made a file "Checking Ubuntu Version.docx" using LibreOffice while booted into my LiveOS and saved it into /Home/Documents.  Following the above advice, here's what I get:

```
ubuntu@ubuntu:~$ cd Documents
ubuntu@ubuntu:~/Documents$ sudo cp Checking Ubuntu Version.docx Checking Ubuntu Version.docx /cdrom
cp: cannot stat ‘Checking’: No such file or directory
cp: cannot stat ‘Ubuntu’: No such file or directory
cp: cannot stat ‘Version.docx’: No such file or directory
cp: cannot stat ‘Checking’: No such file or directory
cp: cannot stat ‘Ubuntu’: No such file or directory
cp: cannot stat ‘Version.docx’: No such file or directory
ubuntu@ubuntu:~/Documents$ 
```

Apparently I can't have spaces in my filenames when using Terminal to move files?

Please use [noparse]```
tags
```[/noparse] around input to and output from the terminal window to make it easier to read :-)

File names with spaces and some other characters, that have a special meaning in the shell must be quoted. (It is the same in Windows command line)

```
sudo cp "file with spaces in the name.docx" /cdrom
```
> 
...

So are y'all saying that I should be making my LiveOS USB using mkusb instead of the "default" way that seems to be built into Ubuntu (Sorry I can't remember or find that app now as apparently it's not available in the LiveOS I'm booted with now, and only in Ubuntu when I boot into it with a HDD).

So if I make a LiveOS using mkusb it'll make the first partition accessable because it'll be owned by the default user, so then I can save a file into home/documents as long as I don't have spaces in the filename, and then I can copy from that folder into a NTFS partition using sudo cp commands?

I understand it's not Linux's fault that MS chooses not to recognize Linux partitions, and I am by no means a MS lover - I'm just a computer user that's trying to use my laptop as a tool and unfortunately most of my apps need to run under Win7 because that's what my corporate employer chooses use.  And no, I don't work in the computer industry obviously - we do engineering and manufacturing.  I decided I needed to give Linux a try and decided it would be nice to make all my USB jump drives Linux bootable (instead of just being all data) so I can have a way to use any PC I come across and boot into a OS setup in a way I'm familiar with, do my work and save files that I can then access from Win7.

This really seems to be a very reasonable goal (to be able to easily use all my free space on a USB drive in both Win7 and Linux) and be bootable into Linux.  I'd say a lot of folks would want to do this, and frankly I'm surprised I seem to be the first post trying to do this after all these years!  So are my options using a LiveOS to make it using mkusb and copy the files, or not using LiveOS and making a permanent Ubuntu installation on a USB?  If the later, what's the simplest way (step by step) to do this?

Thanks for all the advice and discussion!

I'm not sure all of us say that you should use mkusb. I do, I made it work that way ;-)

If you use standard Ubuntu, you need to add the universe repo. (It is already active in the community flavours Lubuntu, Xubuntu ...).

```
sudo add-apt-repository universe
```

You need the mkusb PPA, and after that update the list of current versions of the available packages. Finally you install mkusb.

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter to accept it
sudo apt-get update
sudo apt-get install mkusb
```

See this link for more details [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by yancek on 2015-09-21
Doing a normal install to a drive is explained at the Ubuntu site below.  In your case, you will need to take care that you have the right device to install to so you don't overwrite your internal drive on the computer you are using.  You can find that with the command:  sudo fdisk -l(Lower Case Letter L in the command)  This will output drive/partition information and you should be able to find the flash drive as the size of the drive(s) will be reported.  This should work if you do not install proprietary graphics drivers.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

A more detailed explanation with a lot of other useful info is at the site below:

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

> I'd say a lot of folks would want to do this, and frankly I'm surprised I  seem to be the first post trying to do this after all these years!

You're not, I've seen other similar posts at other forums also.  I think it would be very useful but I expect those of us who do are in the small minority.   I expect it's an incredible amount of work to create something like this so I think the demand would have to be pretty high for someone to do it.

---

### Post by JKyleOKC on 2015-09-21
> **thrashercharged said:**
> 
Sorry, I'm not understanding how the default user being 1000 or 999 is important?

It's something that most users never need to know, but in situations such as you've encountered can be quite critical.

Since the choice of a User Name is up to the user and can be anything the user wants (my usual choice on my own machines is just two letters, my initials), the actual file system assigns a number when it creates the user profile, and all internal reference, permission checking, and so on, uses that number instead of the actual name. The number zero is always reserved for the super user or "root" and a block following that is reserved for "system users" created to keep various processes from trampling on each others' areas. Finally, the rest of the number range up to 65535 is used for "standard" users.

In Ubuntu and its various flavors, the system range is 1 to 999 and the first standard user is always 1000 (many other distributions such as Mandrake or Red Hat use 500 rather than 1000 as the dividing line, which sometimes leads to serious permissions problems when migrating from one distro to another).

Thus the difference between 999 and 1000 means that when you store a file as "user 999" via the flash drive, you're NOT the owner of it when using the hard-disk installation where you are user 1000. And a little-publicized feature of the permission system is that when a user doesn't have permission to read a file or a folder, read attempts sometimes report that the target doesn't exist.

In your case, it was absence of the quote marks that caused the message, but I often encounter the other case when browsing through systems I've imported via flash drives. Many years ago I used a Red Hat variant, and sometimes need to browse through very old files from that era.

Undoubtedly more than you really wanted to know, but I hope it helps a bit to make you more comfortable with the system!

---

### Post by Paulgirardin on 2015-09-21
> **yancek said:**
> With the history of Google and microsoft, feel free to trust them.  I certainly don't.  A cloud option might be good for some but, for whatever reason the OP had specific requirements that he was trying to use and I think it was the protability.  He could carry an external drive around with an OS on it, or a notebook or laptop but that's not what he was asking.


Use MEGA - 50Gb of encrypted storage free.
Until the US govt succeeds in their efforts to destroy the company

---

### Post by Geoffrey_Arndt on 2015-09-22
> **thrashercharged said:**
> I've made 2 usb jump drives into Ubuntu 14.04 live usb. One is 32bit, the other is 64bit.  When I look at them with Win7 I see some files and folders. I've attached the screenshots.  The 64bit version has a EFI and UUI folder that the 32 bit one doesn't have, and in both I see a casper-rw file that is huge.  Apparently both usb drives are formatted FAT32, and Win7 tells me that about 1.95 GB of space is used and I've lots of free space.

1.  Briefly, what are these folders and files for?  I'm worried that something might accidentally get deleted/moved when we're working with the USB drives in Win7 and mess up my ability to use the drive to boot into Ubuntu.  Is this a valid worry?

2.  Were should I store my datafiles on these USB drives where both Ubuntu and Win7 can access them?  Do I make a folder?

My goal is to use these USB drives to store data that's accessible both by Ubuntu and Win7, but I wanted to make them Ubuntu Live USBs so I can always boot into Ubuntu when I need/want to.  I would prefer to make separate partitions like I'd do with a HD and make a Linux partition and have NTSF/FAT32 partitions for data, but you can't do that and make a Live USB drive can you?  I made the Live USBs while booted into Ubuntu, and I believe it erases the entire USB drive when it makes it, right?

I've more questions related to this but I'll start another thread.

***************************

When you create a live Linux usb-flashstick you can make it persistent or not.   In either case, the default file system is fat32 which is useable by Ubuntu and Windows immediately.   To share data, all that's needed is to create a new folder (and subfolders) for your application data on the flash-stick.   That data then will not interfere with your live linux system files.   So, no issue re messing up the live media.  No need for separate partiitons in the first place.

I believe the total space (less the OS reserved space) as expressed via a properties view - - is fully accessible for writing data (via such apps as LibreOffice, etc.).   If that's not the case, I'm not aware of that limitation.  

The use of persistence on the live install is for expansion of the live-OS (adding new programs, etc.).   Data can be added to the physical drive (usb-stick) via windows or linux.   So, I'm not fully understanding what the issue is with respect to the OP's original goal.   Windows doesn't concern itself with permissions (that's why malware writers love it).   And the files saved via Linux apps should have the correct ownership assigned if using most standard live usb creator apps.     Seems simple but maybe I'm missing something.

---

### Post by sudodus on 2015-09-22
@ Geoffrey_Arndt

Please try, and you will find out how it works in different cases :-)

---

### Post by Geoffrey_Arndt on 2015-09-22
Sudodus, . . . ok, fair enough  ;)   .   In my case, I just haven't seen a scenario yet with a static or a dynamic live linux usb-stick where I could not save "beaucoup" data from any app.   Is there a known-limitation . . a restriction on creating recursive directories in the free space of a live flash-stick?  (in other words, I just right-clicked nautilus to create the Folder "Test101" - - - where I pasted a 450 GiB iso image).

[IMG][IMG]http://i.imgur.com/0E7GMJbl.png[/IMG][/IMG]


My main concern about _regular use_ of this method (versus a dual boot, or using Virtual Box) is the "seeming" lack of security with ID-Less login and permission-less file system (fat32).   Just doesn't seem at all secure.

---

### Post by yancek on 2015-09-22
> where I pasted a 450 GiB iso image).

Your image shows a 16GB volume so I'm not sure how you got a 450GB iso file on it, typo or a miracle?

There are limitations with a FAT32 filesystem.  If using a casper-rw "file", the limit is 4GB.  If using a partition, there is no limit but, as I understand this partition would need to be a Linux filesystem.  I haven't tried with a windows filesystem so I'm basing this on what I've read.

The problem in this instance is that the OP wants to access data from windows and Linux.  Windows won't read a Linux filesystem so a Linux partition won't help.  Another problem is the inability of windows to access other than the first partition on a flash drive.  One solution for what the OP wants is to create two partitions, partition one being an ntfs in his case 26GB and the remaining 6GB of his 32GB flash drive a FAT32 and use unetbootin (or possibly other software) to put the Ubuntu Live CD on the second partition with a casper-rw file.  Also, with a 32GB or larger flash drive, a normal install to the second partition with the first partition ntfs would work.

---

### Post by Geoffrey_Arndt on 2015-09-22
> **yancek said:**
> Your image shows a 16GB volume so I'm not sure how you got a 450GB iso file on it, typo or a miracle?

There are limitations with a FAT32 filesystem.  If using a casper-rw "file", the limit is 4GB.  If using a partition, there is no limit but, as I understand this partition would need to be a Linux filesystem.  I haven't tried with a windows filesystem so I'm basing this on what I've read.

The problem in this instance is that the OP wants to access data from windows and Linux.  Windows won't read a Linux filesystem so a Linux partition won't help.  Another problem is the inability of windows to access other than the first partition on a flash drive.  One solution for what the OP wants is to create two partitions, partition one being an ntfs in his case 26GB and the remaining 6GB of his 32GB flash drive a FAT32 and use unetbootin (or possibly other software) to put the Ubuntu Live CD on the second partition with a casper-rw file.  Also, with a 32GB or larger flash drive, a normal install to the second partition with the first partition ntfs would work.

Hello Yancek . . . hopefully the OP hasn't abandoned this thread, as I think his goal is doable . . . 

So first, for the first time in almost 2 years, I'm logged in to Windows 7 to test out our hypothesis (at least for this hardware & software setup).   Anyway, here's what I'm seeing:

>   re the 16 GB volume and the file I copied into "Test 101" . . . my typo.   The iso is 450 meg or abouts (Partition Magic Live image),

>   the usbv3 flash-stick has only the standard fat32 (default) file system (although the live session use a linux file system),

>   In a standard (installed) Linux session (Ubuntu 15.04 on a Galago Ultra Pro running Unity) . . . the usb folder and contents are viewable, editable.   The file system is FAT32 . . . so it's a cross-platform device,

>   On a persistent Linux Live USBv3 Flash-Stick (Xubuntu 15.04) - the Thunar file manager can access, read, write, delete etc. the Test 101 Folder & contents.   It mounts at /media/cdrom (all iso folders including Test101 are visible there),

>   On Windows 7 (man is this thing slow on a Lenovo H410 desktop) - - the Live USBv3 Flash-Stick is mounted (on my system as drive H and all folders within the ISO level are visible and editable). 

**************************************************************************************** 

Using this setup, there is no need to do partitioning, or think about windows access to the first or second partition - - it's a moot point (not applicable).   

So, if the OP can replicate this basic setup, his goal seems doable.   Am I off-track (wouldn't be the first time)?? - - just let me know and I/we can test further.

---

### Post by thrashercharged on 2015-09-23
> [COLOR=#000000]Hello Yancek . . . hopefully the OP hasn't abandoned this thread, as I think his goal is doable . . . [/COLOR]

No I haven't abandoned this thread!  I'm just reading and soaking in all this info and suggestions and trying it out when I get the chance - I haven't yet had the chance to try the latest.  I have to say I am surprised that there isn't an easier solution as my goal seems fairly reasonable and I would've thought a majority of Windows users wanting to try out Linux, or experienced Linux users that still need to work under Windows for various reasons would need to be have a shared area on a USB drive to save files so they're easily accessible from both OS.  

Thanks for all the responses and suggestions!

---

### Post by Geoffrey_Arndt on 2015-09-23
An additional thought:   if the OP is really serious about using flash media in the way described . . . I think it's still entirely too "clunky".     While I have not personally done an actual install to a usb-flashstick, it seems that would offer a lot of advantages to running a "Live USB" for this type of steady use.    That way, you can update the install, and use all the standard Linux tools and permissions systems.   Even just the proper use of sudo is enhanced by valid user ID of the initial user.  
 
On that note, my next mini-project will be to replace my live xubuntu 15.04 with the next version "Wiley Werewolf" with a full install.   Should be fun!:lolflag:

**EDIT**:   oh Thrasher . . . just saw your latest post!   Glad your still here.    But . . . . be careful about certain "assumptions" you still have about your need and the solutions presented so far.   There are "multiple" ways to do almost anything in Linux.   For example,  you can still save your spreadsheet (or whatever file) to a network (samba) shared folder.   That's kind of the standard and we really haven't talked about that at all yet.   One of the new standards, is simply to login to your cloud service, and upload the files there.   Other tools like FTP still exist too.    So, the bottom line, experienced Linux admins know how to do what you're wanting (experience and training matter).   Our responses are all predicated by the way you seem to want to achieve your goal.    (by the way, the actual install of Ubuntu to a Flash stick is something to think about).

---

### Post by sudodus on 2015-09-23
> **thrashercharged said:**
> No I haven't abandoned this thread!  I'm just reading and soaking in all this info and suggestions and trying it out when I get the chance - I haven't yet had the chance to try the latest.  I have to say I am surprised that there isn't an easier solution as my goal seems fairly reasonable and I would've thought a majority of Windows users wanting to try out Linux, or experienced Linux users that still need to work under Windows for various reasons would need to be have a shared area on a USB drive to save files so they're easily accessible from both OS.  

Thanks for all the responses and suggestions!

Now you know about several alternatives. When you decide which way to continue, let us know, and you can get detailed tips along that way.

---

### Post by sudodus on 2015-09-23
> **Geoffrey_Arndt said:**
> An additional thought:   if the OP is really serious about using flash media in the way described . . . I think it's still entirely too "clunky".     While I have not personally done an actual install to a usb-flashstick, it seems that would offer a lot of advantages to running a "Live USB" for this type of steady use.    That way, you can update the install, and use all the standard Linux tools and permissions systems.   Even just the proper use of sudo is enhanced by valid user ID of the initial user.  
...

Many people use installed systems in USB drives. It works well, but frequent writes might cause the pendrive to fail unless the system is changed to avoid some of them:

Add the mount option noatime for the root partition into /etc/fstab

Turn off journaling for the file system (also for the root partition).

If a home partition is also created, I think it should be treated the same way.

Avoid running several applications or open many tabs in a browser at the same time, so that you do not use swap (except in rare cases).

-o-

For portability you should avoid installing proprietary drivers. But if you intend to use it in one computer, it is OK.

-o-

See also this link [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by yancek on 2015-09-23
>    On a persistent Linux Live USBv3 Flash-Stick (Xubuntu 15.04) - the  Thunar file manager can access, read, write, delete etc. the Test 101  Folder & contents.   It mounts at /media/cdrom (all iso folders  including Test101 are visible there),

On the persistent flash drive I used, created with unetbootin the /media/cdrom was simply a link to /cdrom which is in the / of the persistent filesystem.  And yes, from a Linux or windows system, you can make changes to and write/save to /cdrom.  Trying to save a file to /cdrom while booted into the persistent flash drive requires root privileges.  On the system created with unetbootin, it is not possible to change the permissions/owner:group of /cdrom.

One of the problems the OP discussed was while booted to the persistent flash drive, writing and trying to save a LibreOffice file to /cdrom so it was accessible from another Linux or windows system did not work as a user but would as root, using sudo to open libreoffice or a text editor.  With an installed system, this would be easily doable as a user and since windows only sees the first partition, the need for that partition to be FAT32 or ntfs and Ubuntu installed to the second partition.

>   On a persistent Linux Live USBv3 Flash-Stick (Xubuntu 15.04) - the  Thunar file manager can access, read, write, delete etc. the Test 101  Folder & contents.   It mounts at /media/cdrom (all iso folders  including Test101 are visible there), 

On the system I tested, the results were the same as those posted by the OP.  While booted to the persistent flash drive, I could not create a file under /cdrom or save a file as a user but could do so as root.  Again, it was also not possible to change owner:group or permissions of /cdrom or sub-directories.  When I tried, I got "operation not permitted".  Maybe it makes a difference as to how the flash was created.

---

### Post by Geoffrey_Arndt on 2015-09-23
Have good news and bad news re further testing for change, save cababilities via a Live USB Flash-stick . . . . Yancek is absolutely right.   I could do a copy operation, but it was apparently outside the live session, and although the data was accessible - the owner of the Test 101 folder (and it's files) is still root.  Therefore save (back to the usb stick) didn't really work well at all.   So, I'm wrong about using this method (live persistent usb flash-stick sessions) as a standard way to do what the OP wants.

As Yancek and others have said, there should be more flexibility (e.g., capability) by doing a full-install to the flash-stick versus the live operation.

And lastly, just an additional comment for trashercharged . . . . each day, in many thousands of organizations worldwide, there are millions of files exchanged between Windows & Linux domains (servers, desktop workstations, etc.).   *Literally millions*.   And virtually none use any type of usb method for file exchange.    The standard when I was still productively employed in IT was Samba and a couple other network tools (with Samba being safest).   Cloud technology is now a major player also.   So, while a fully installed version of Ubuntu on a stick may do what you want, you're still better off (in a business setting), learning more about how Samba and the Cloud work for sharing.

Thanks Yancek - I learned a few more things about Live Linux options the past couple days   ](*,)](*,). . am looking forward to Wiley Werewolf on a sandisk usbv3 16 GiB nano size stick.!

---

### Post by yancek on 2015-09-23
Using a single FAT32 partition is the most limited option.  In the scenario the OP posted, trying to save a file with a text editor or libre office can be done but not to the /cdrom directory which is viewable from another Linux or windows system.  It would be necessary to copy/move it using sudo to the /cdrom directory.

On the flash drive I created with the first partition as an ntfs and the second a persistent Live CD, it was possible to directly save a file to the first (ntfs) partition as a normal user without the necessity of having to copy using sudo.  I used Peppermint Linux, an Ubuntu derivative and the ntfs partition was available on boot under /media/peppermint/UUID, the UUID for the windows partition.  This partition would then be viewable from the persistent flash as well as another Linux or windows install so this is a better option than a single FAT32 partition.  The limitation would be that if using the persistent flash, anything you wanted to share with another windows system would need to go to the ntfs partition.

---

### Post by sudodus on 2015-09-23
If you use the tool mkusb and make a persistent live USB drive, the first partition will be available automatically for file transfer with Windows, because it will be mounted with the standard user (of the live system) as the owner. The method you describe, yancek, will work too (but it will need some 'manual operations').

Let us wait for the OP to decide which way to continue (persistent live or installed system), and help along that way :-)

---

### Post by thrashercharged on 2015-09-25
I'm the OP.  Let me see if my understanding thus far is correct.

1. If I make a persistent live, doing it with "Startup Disk Creator" like I did, it doesn't make the first partition available automatically for file transfers with Windows.  To do this I would use mkusb instead?  This is because Startup Disk Creator makes a Linux 1st partition while mkusb makes either a FAT32 or NTFS first partition?

2. If don't have a first partition that's usable by Windows, I can save my files to home/documents, then go to Terminal and do the 

```
sudo cp file1.odt file2.odt /cdrom
``` commands and transfer the file to a folder that Windows can see.

(Sorry for the italics, cut and pasted those sudo commands in which were in italics and I can't turn italics off now!  Highlighting and toggling the I doesn't work!)

3. I can forgo the persistent live and make an installed Linux system on the USB.  I haven't tried that yet but I intend to.  Can someone summarize how to do this?  What's the negatives for not making a persistent live and doing this?  This would seem to be my best solution as I'm not "trying out" Ubuntu and do intend on sticking with it when I use that USB to boot.

Sorry I don't respond very quickly as I'm making this bootable USB in my free time.  Frankly, I'll continue to be a Windows user for my work stuff as that's what the corporate world provides and most of the apps I run are Windows apps (yes I know about Wine and do use it for LTSpice, but I can't count on Wine working 100% for all engineering programs, esp the data acquisition stuff like AVL Concerto, ETAS Inca, or even MATLAB Simulink so for the most part I'm stuck with Win7).  Also, as I mentioned, the Cloud solution doesn't always work for me as I don't always have internet service if I'm out in the boonies or I'm a visitor at someone's facility and don't have access to their secure network. I'm really just looking to boot anybody's computer I get my hands on with my USB into a OS I'm familiar with (either because I don't have the Windows password to that password because I'm a visitor at that facility, or that company's IT dept has put security and restrictions on it that I don't understand, etc.) and do some work that I'll later have to be able to open under Win7.  So why don't I just use my own Win7 laptop to do this?  It's sometimes either unavailable as it's collecting data and physically not available (as in another room/location) or my corporate IT dept has put something on it that where it needs to communicate with the "mother ship" (as in hardwired at the office) to do God knows what and if I'm not in the office the processor is running near 100% and the speed is about that of a 1st gen IBM XT 8086 machine (yes I had one - with real floppys!).  Under those circumstances, I really would like to boot into another OS with the USB.

---

### Post by oldfred on 2015-09-25
Pros & cons of persistence install over direct install to flashdrives -  See posts by C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by sudodus on 2015-09-25
> **thrashercharged said:**
> I'm the OP.  Let me see if my understanding thus far is correct.

1. If I make a persistent live, doing it with "Startup Disk Creator" like I did, it doesn't make the first partition available automatically for file transfers with Windows.  To do this I would use mkusb instead?  This is because Startup Disk Creator makes a Linux 1st partition while mkusb makes either a FAT32 or NTFS first partition?

Yes, it works with mkusb. The first partition is a FAT32 partition, and it is not owned by root. It is mounted so that it is owned by the default user, and you are running as that user, so you are allowed to write there.
> 
2. If don't have a first partition that's usable by Windows, I can save my files to home/documents, then go to Terminal and do the 

```
sudo cp file1.odt file2.odt /cdrom
``` commands and transfer the file to a folder that Windows can see.


Only the first partition can be used by Windows and must be a Microsoft file system, either FAT32 or NTFS. The reason to copy files (in this case file2.odt and file2.odt) with sudo is to be able to write to the first partition in cases, when it is owned by root (when created with the Startup Disk Creator).
> 

(I removed the italics)

3. I can forgo the persistent live and make an installed Linux system on the USB.  I haven't tried that yet but I intend to.  Can someone summarize how to do this?  What's the negatives for not making a persistent live and doing this?  This would seem to be my best solution as I'm not "trying out" Ubuntu and do intend on sticking with it when I use that USB to boot.

You do this like you would install into an internal disk drive. It is easier to avoid mistakes, if you disconnect your internal drive while doing it. Otherwise you might write something to the internal drive by mistake, for example the bootloader. Avoid proprietary drivers, if you want the pendrive's system to be portable between different computers.

See also the links in *oldfred's* post.
> 
Sorry I don't respond very quickly as I'm making this bootable USB in my free time.  Frankly, I'll continue to be a Windows user for my work stuff as that's what the corporate world provides and most of the apps I run are Windows apps (yes I know about Wine and do use it for LTSpice, but I can't count on Wine working 100% for all engineering programs, esp the data acquisition stuff like AVL Concerto, ETAS Inca, or even MATLAB Simulink so for the most part I'm stuck with Win7).  Also, as I mentioned, the Cloud solution doesn't always work for me as I don't always have internet service if I'm out in the boonies or I'm a visitor at someone's facility and don't have access to their secure network. I'm really just looking to boot anybody's computer I get my hands on with my USB into a OS I'm familiar with (either because I don't have the Windows password to that password because I'm a visitor at that facility, or that company's IT dept has put security and restrictions on it that I don't understand, etc.) and do some work that I'll later have to be able to open under Win7.  So why don't I just use my own Win7 laptop to do this?  It's sometimes either unavailable as it's collecting data and physically not available (as in another room/location) or my corporate IT dept has put something on it that where it needs to communicate with the "mother ship" (as in hardwired at the office) to do God knows what and if I'm not in the office the processor is running near 100% and the speed is about that of a 1st gen IBM XT 8086 machine (yes I had one - with real floppys!).  Under those circumstances, I really would like to boot into another OS with the USB.

I'll try my best to help you get a portable system on you USB pendrive. It might be worthwhile for you to try both a persistent live system and an installed system, and after serious testing of both, you will find what is the best for you.

Finally, pendrives may fail without warning. There is a shorter number of write cycles before failure compared to hard disk drives and SSDs. It is also easy to unplug them before the content is synced (buffers flushed), which will corrupt the file system.  So you need a ***good backup*** routine for all your important personal files (where the result of your work resides).

---

