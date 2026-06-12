---
title: "Thwarted before I begin"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by punstress on 2012-04-07
I want to install ubuntu on a partition I will make on my Windows 7 laptop. I didn't get very far! I went to download but I don't know what category my architecture falls into. 

My processor is Intel Core i3 CPU M380 @ 2.53 GHz. 64-bit. 

1. Which version do I download?

2. How big of a partition do I need?

3. So once I make the partition, do I then download the files while in a Windows partition, then will I be able to choose the new partition to install ubuntu?

Thanks everyone.

---

### Post by oldfred on 2012-04-07
You can download the ISO in Windows and make a CD or bootable USB. I only use USB flash drive or even hard drive to boot ISO now as I have burned coasters and I always burned backups, repairCDs and other systems just to have ways to boot. Now with USB flash drives it is reuseable. If using CD always burn at slowest speed you can.

When you say version, which are you asking about. Use 64bit if you have 3GB or more of RAM, and the standard Desktop version. But all the other versions are different GUIs which you can try later if you like.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Do not make partitions in Windows as it may convert to dynamic partitions which is a one-way conversion and dynamic does not work with Linux. But use the Windows tools to shrink the Windows partition if you need to make it smaller.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Also what video card do you have? That can have some issues that you need to set parameters to get it to boot.

---

### Post by PhantomTurtle on 2012-04-07
1. 64-bit since your processor supports it. However if you do not have more than 3GB RAM you might not see a big performance boost.
2. I usually like to do half and half when I dual boot. I would give it at least a 15GB partition. Also keep in mind that you would have to make a swap partition, so you need allocate extra space for that excluding the space for the Ubuntu partition.
3. Download the iso and burn it to a cd or make a live USB. Boot into the cd or USB and you can install using that.

Additionally if you don't know how to shrink your Windows partition here's a tutorial: [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/").

---

### Post by jwbrase on 2012-04-07
> **punstress said:**
> I want to install ubuntu on a partition I will make on my Windows 7 laptop. I didn't get very far! I went to download but I don't know what category my architecture falls into. 

My processor is Intel Core i3 CPU M380 @ 2.53 GHz. 64-bit. 

1. Which version do I download?

Go with the latest version, 64-bit. You may want to wait a few weeks until 12.04 comes out, though.

---

### Post by uRock on 2012-04-07
I have a 64bit system which works perfectly fine with 64bit ubuntu and 2GB RAM.

---

### Post by punstress on 2012-04-07
I guess I was looking in the wrong place before. I was presented with these choices:

Installing Ubuntu 11.10 from the Alternate CD
Here you can find information on how to install Ubuntu from the Alternate CD. The Alternate CD provides more advanced installation options than the standard Desktop CD, which is the recommended method of installing Ubuntu. For instructions on how to use the Desktop CD, see the Graphical Install page on the Ubuntu community documentation site.

To view the guide for the Alternate CD, choose the architecture of your computer from the list below.

Intel x86
AMD64 & Intel EM64T
IBM/Motorola PowerPC
Sun SPARC
HP PA-RISC
Intel IA-64

And I didn't know which of those to choose. Now I see there is a plain old 64 bit version.

> **punstress said:**
> I want to install ubuntu on a partition I will make on my Windows 7 laptop. I didn't get very far! I went to download but I don't know what category my architecture falls into. 

My processor is Intel Core i3 CPU M380 @ 2.53 GHz. 64-bit. 

1. Which version do I download?

2. How big of a partition do I need?

3. So once I make the partition, do I then download the files while in a Windows partition, then will I be able to choose the new partition to install ubuntu?

Thanks everyone.

---

### Post by uRock on 2012-04-07
Use the AMD64 image.

---

### Post by punstress on 2012-04-07
Why should I make a CD, can't I just download straight to my computer?? I have no idea what you were going on about in most of your post, sorry.

I use Partition Wizard to resize my partitions. I don't know what video card and I am new to Win7; nothing is found easily.

> **oldfred said:**
> You can download the ISO in Windows and make a CD or bootable USB. I only use USB flash drive or even hard drive to boot ISO now as I have burned coasters and I always burned backups, repairCDs and other systems just to have ways to boot. Now with USB flash drives it is reuseable. If using CD always burn at slowest speed you can.

When you say version, which are you asking about. Use 64bit if you have 3GB or more of RAM, and the standard Desktop version. But all the other versions are different GUIs which you can try later if you like.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Do not make partitions in Windows as it may convert to dynamic partitions which is a one-way conversion and dynamic does not work with Linux. But use the Windows tools to shrink the Windows partition if you need to make it smaller.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Also what video card do you have? That can have some issues that you need to set parameters to get it to boot.

---

### Post by uRock on 2012-04-07
> **punstress said:**
> Why should I make a CD, can't I just download straight to my computer?? I have no idea what you were going on about in most of your post, sorry.

I use Partition Wizard to resize my partitions. I don't know what video card and I am new to Win7; nothing is found easily.

The links explain how to install ubuntu. You will have to create a CD or LiveUSB in order to install. You will have to restart your system and boot from the CD or USB. Please take the time to read the documentation linked by **[COLOR="Red"]oldfred[/COLOR]**.

---

### Post by oldfred on 2012-04-07
If you do not understand partitions and how systems work the wubi version may be better to start with. It is like the liveCD but allows updates and runs inside a file on your Windows NTFS partition. It is meant for new users who want an extended test over just using liveCD. 

Linux is not a program you run in Windows. And even the wubi install which can be installed & deleted like a program is not, but boots into another system, Ubuntu.

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

