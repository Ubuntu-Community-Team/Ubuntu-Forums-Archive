---
title: "Safety of Dual Boot?"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by Sly14Cat on 2012-08-07
Hello,
I'm currently running Windows 7 and I wanted to install Ubuntu 12.04. I wanted to partition my drive and have space for each operating system. I just bought a USB (8 gigs) and formatted it as NTFS and put the .iso file on it. My BIOS seem to not give me the option to choose removable media as a boot method (I'm running a fairly new computer so the BIOS are new). I want to shrink the windows portion and format the left space as a simple volume. I want to use that for Ubuntu. I also heard of swap space. How would I go about that? Is there any chance Ubuntu could completely mess up my computer? I can not risk ruining this computer. I understand if something goes wrong with the windows I could just put in the CD and fix it so that's no problem but I just to make sure I'm doing everything right. Here's my plan:

- Insert USB
- Start computer
- Select "Something else" at hard drive menu
- Make the partition for Ubuntu and format it as... (Can someone tell me what to format it as?)
- Make that the primary partition
- Follow through with installation
- Restart computer

If I don't like Ubuntu, I have EasyBCD and I'll write Windows 7 to the MBR and delete the Ubuntu partition and extend the windows partition over it. Does this sound good? Did I make the USB bootable correctly? I would prefer to use Windows Boot Manager instead of Grub but if I can't that's fine. I just want to make sure there's no risks.

Thank You,
Sly14Cat

---

### Post by Jerry N on 2012-08-07
DO NOT use Ubuntu (or gparted) to shrink the NTFS partition that Windows is installed on.  Windows has its own utility - go to the Control Panel, select Administrative Tools, Computer Management, and Disk Management. Right click on the C: drive and select Shrink Volume.  When you shrink the volume free space will be created.  DO NOT DO ANYTHING TO THIS FREE SPACE USING WINDOWS!!!!  Use the tools on the Ubuntu install media to manipulate this free space.
While you are looking at disk management, note how many partitions are shown.  If it is less then 4, you are in good shape.  If it is 4, you will have to decide what partition to delete because you can't have more than 4 primary partitions.  

By the way, make sure your backup of important files is current and be sure you know how to restore Windows from scratch because it is certainly possible to irretrievably damage Windows while you are messing with your computer.  The people most likely to do this are (1) total rank amateurs when it comes to computer diddling and (2) highly experienced experts who tend to forge swiftly ahead, ignoring warnings and anything else that gets in the way.  Embarrassing to say the least!

The ext4 format is just fine for the ubuntu volume.

Jerry

---

### Post by Kalanac on 2012-08-07
I'm pretty sure you need to create a swap partition too.  You can use logical partitions to make 1 partition into 4.

I've not encountered any problems using gparted to shrink the windows partition, but use whatever you feel most comfortable with.  Note that data could be lost so back up whatever is vitally needed.  Running defrag helps by shifting files to the beginning of the partition (where they should be).

There are a lot of opinions on the swap partition and how big it should be.  The rule of thumb is as large as you have RAM.  So 2gig RAM means a 2gig swap partition.  The swap partition will be created automatically by the installer if you use the guided option and will probably be about 4gig.

ext3 or ext4 is fine for the ubuntu partition, again the guided install will do this for you.

Oh!  When you install the boot loader (grub) make sure you install it to the hard drive and not the flash drive.

---

### Post by Sly14Cat on 2012-08-07
Sorry if I didn't make it clear. Yes I would shrink using windows mainly because of fragmentation among other things (Even though I just defragmented but I still would use windows and never gparted). So do I just format the swap as ext 3 or 4? Does it matter if I use 3 or 4?

Yes I currently have 3 partitions (one for the bootloader, one for recovery and the main drive which I will partition).

I'll back up windows to a CD and create a restore point and all my information I'll back up online. So am I going correctly about it? So if I wanted to get rid of Ubuntu I just write Windows 7 to the MBR using Easy BCD? Would I make the swap a logical partition since I can't have more than 4 primary?

You were talking about restoring windows from scratch. How would I do this? Would I use a Windows .iso burned to a CD and follow the instructions and boot from CD in the Windows installer to get windows back (and use the product key that came with my computer)? What's the worst thing that could happen to my computer? I can boot Ubuntu from a CD but my CD's are only 700 mb's big. Is that big enough? They're DVD-R16x.

Thanks for your help so far. I do ask lots of questions.

---

### Post by Paqman on 2012-08-07
> **Sly14Cat said:**
> I just bought a USB (8 gigs) and formatted it as NTFS and put the .iso file on it. 

You need to write the .iso straight to the USB stick, not copy it to an existing filesystem on the stick. [Instructions here]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows").

---

### Post by Paqman on 2012-08-07
> **Sly14Cat said:**
> So do I just format the swap as ext 3 or 4? Does it matter if I use 3 or 4?

Swap space is just swap space, you don't have to format it. But don't worry too much about all this stuff, the installer will take care of it all. Setting up a dual-boot with Windows is a very common way to install Ubuntu, the installer will automate almost all of it.

> So if I wanted to get rid of Ubuntu I just write Windows 7 to the MBR using Easy BCD? 

After deleting it's partition, yes.

> Would I make the swap a logical partition since I can't have more than 4 primary?

If you like. By default the installer will do it that way.

> You were talking about restoring windows from scratch. How would I do this? Would I use a Windows .iso burned to a CD and follow the instructions and boot from CD in the Windows installer to get windows back (and use the product key that came with my computer)? 

Yep. You can get the .iso images from Microsoft.


> What's the worst thing that could happen to my computer?

The worst you could do would be accidentally wipe your Windows install.


> I can boot Ubuntu from a CD but my CD's are only 700 mb's big. Is that big enough? They're DVD-R16x.

That's fine, Ubuntu is designed to fit on a single CD.

---

### Post by Sly14Cat on 2012-08-07
Wow thanks very much for all that useful information. I think I'll go though with it now by installing from CD. I'll notify the community if I have any problems.

Thank You,
Sly14Cat.

---

### Post by oldfred on 2012-08-07
Some examples of installing.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

If you have a Windows repairCD:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Sly14Cat on 2012-08-08
I burned Ubuntu to a disk. Do I need a special .iso burning program or can I just burn it using windows like any other cd?

---

### Post by oldfred on 2012-08-08
Usually the default in Windows just copies one large ISO file not like the installers that create a bootable CD or USB with many smaller files. See instructions on Ubuntu download site:

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by I2k4 on 2012-08-08
Have to say, this reads like a weird exercise in "how hard can I make this easy thing?"  I'm no techie, I made a Live USB, booted it, there was an installation icon on the desktop, clicked it and one of the regular install options was dual booting with Windows, it was brainless for me and it has worked great for about a year now.  

The one thing I had been unaware of is that GRUB takes over the normal Windows boot set up and apparently can be difficult to get rid of if a user wants to go back to pure Windows - for the time being it's a non-issue because I quite like the dual boot.

---

### Post by Sly14Cat on 2012-08-08
Sorry if it seems I'm making a hard thing out of a easy thing :P
But I need to make sure 100% I don't fry my computer. Thank you for the advice you gave, I used a new CD and burned the disk image instead of just dragging and dropping it and it treats the CD just like a factory made one as you can see here the CD picture is replaced with the Ubuntu logo...
[IMG]http://i45.tinypic.com/2i5fuo.jpg[/IMG]

Sorry I know I ask this question *way* too much but are you 100% sure that but putting this disk in and starting it there's no risk to hurting the computer (besides user made mistakes)?

Thank you for bearing with me :)

---

### Post by SantaFe on 2012-08-08
I just installed Xubuntu 12.04 LTS using the first partition option "Install Linux beside Windows 7".  I had no problems at all, besides the fact that when you boot back into Win 7 the first time, it's ole Chkdsk time.  But after it's done Win 7 boots just fine, and so does Xubuntu. 

I DID however, make one backup of my system before installing using Macrium Reflect in case it did mess up.  And after everything was set up I did another backup with all partitions checked (Windows & Linux).  Figured if it messed up I'd at least have a fresh Xubuntu 12.04 & a stale Win 7 one. :D

And yes, the FIRST thing I did after doing all that was to insert the recovery DVD & reboot & restore using the second backup file.  By gum it worked. ;)

---

### Post by oldfred on 2012-08-08
Boot liveCD and see if it works ok for your hardware. Try a few things. 

The main thing to be somewhat careful of is mounting your existing Windows partition and accidentally deleting or moving something vital. The NTFS drive shows all the Windows hidden files & folders what Windows normally tries to protect you from. Otherwise liveCD will only make changes if you install it.

Many new systems have all four primary partitions used, so use gparted to look at drive and run this from a terminal to list partitions. sudo may not be required in liveCD, but if it asks for password just hit enter, Ubuntu has no password on liveCD. 

sudo fdisk -lu

---

### Post by Sly14Cat on 2012-08-09
I decided that I'm going to do wubi as a trial first. When you first boot after installing wubi, does it boot you straight into Ubuntu?

---

### Post by oldfred on 2012-08-09
Wubi is just a file in the Windows NTFS partition. It adds an entry to the Windows boot loader, so Windows will give you a menu, then grub's menu appears. 

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)


Another alternative if you do not want to repartition is just to buy a 8GB or larger flash drive and use it.
HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by Sly14Cat on 2012-08-19
Hello,
So today finally tried out the CD and it works.
I just wanted to know what to format the Ubuntu space as (sda 2,3 etc.)?
I'm getting The official Ubuntu book 6th ed and I'll be one of the first to get 7th ed when the library orders them.

Sorry if it seems like I'm gravedigging here...

---

### Post by oldfred on 2012-08-19
Windows usually uses 2 partitions. One is the hidden boot/repair and the other is your main install or c: "drive" which is really a partition. Often vendors use two also, so then all 4 primary partitions are used. You have to delete on of those and make an extended partition which is just a container for many logicals. Linux works fine from logical partitions where Windows has to boot from a primary partition.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

