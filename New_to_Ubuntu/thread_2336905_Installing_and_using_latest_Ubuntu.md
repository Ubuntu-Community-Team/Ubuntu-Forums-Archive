---
title: "Installing and using latest Ubuntu"
date: 2016-09-12
forum: New to Ubuntu
---

### Post by ranmac1948 on 2016-09-12
Hi, I am a newbee to Linux but not to computers. I have worked on computers since 1982 and have therefore been through the gamut of msdos and all versions of windows except 2000.
I have been on the insider program for windows 10 for over a year now and it is due to my frustrations with it that I decided a few days ago to learn Linux.
I am having major problems with the installation of the latest Ubuntu program version 16.04.1 LTS.
I initially tried installing it on my desktop computer which had windows10 installed. I partitioned the 1TB hard drive so that I could install Ubuntu on a new partition. I also have windows 7 installed on another 1TB hard drive and I have a further 1TB hard drive which I use to backup my drives. I have a further external 1TB hard drive which I also use for backups. I built the desktop machine in 2009 and it has hardware upgrades as required. I tell you this information for what comes next.
I printed off all instructions to complete the installation and instructions for dual boot. I have produced many iso installation disks in the past so I am very familiar with this operation. I produced the iso disk (both 32 and 64bit) and installed Ubuntu as per instructions but the program failed and the computer locked up at the same point near the end of the install in both 32 and 64bit installs. I could only restart my computer using ctrl-alt-delete. When it restarted I found that I was unable to load windows 7, 10 or access my backup disks for restore, This is an engineers nightmare situation as windows 7 and 10 had lost their MBR. I managed to repair the situation and decided to install Ubuntu on a separate (external) ssd connected to my laptop using a usb3 port. Note: I upgraded the laptop last year and fitted 8gb of ram, a faster processor and a 250gb ssd.
I loaded Ubuntu into the external ssd after having to restore windows 7 on the internal hard disk after it had been overwritten by the Ubuntu software during the first install. I told the install program to install it to the external hard drive but it also overwrote the windows 7 installation. I therefore "pulled" the internal ssd while Ubuntu was being installed. The program installed and I thought all was ok. When I removed the iso disk and restarted the laptop the software went into a continuous loop of: Broadcom base code P2.1 V10 7,5 PXE- E61 media test failure check cable. Broadcom UNDI PXE-2,1 V1.0.9. I am uncertain what this means so perhaps you can enlighten me.
I have a further problem in that I find the setup instructions for windows dual boot  a little confusing.
I am very interested in learning Linux Ubuntu and just need a little help to get me on my way. 
Thank you in advance for your help.
Randall McDonald

---

### Post by QIII on 2016-09-12
Hello!

Not to sound gruff, but please do not ask for support via email.  You asked your question here.  Please have the courtesy to continue the discussion here. This is a community effort and a community resource, not a compilation of individual questions and answers.  Asking here and having a private conversation elsewhere robs the community of valuable information.

Thanks. 

Cheers!

---

### Post by ian-weisser on 2016-09-12
If you just want to learn Linux without risky installs, VMs are one good option.

Check your hardware to ensure your components are supported: [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/) . Look on the TOP RIBBON for the hardware and component databases.

If Ubuntu overwrote your MBR (MBR on Win 10? On an EFI system?) then perhaps your instructions are old. Recent implementations of UEFI and Windows FastBoot (deliberately) make Linux installation more complicated than it used to be.

---

### Post by oldfred on 2016-09-12
If your system is from 2009, you probably only have BIOS, not the newer UEFI.
And with BIOS you have the old MBR partitioning with 4 primary partition limit. Many Windows systems use all 4 primary partitions. The Ubuntu installer then only can overwrite the current system as that is the only option you are giving it. You have to create at least one primary partition to use as an extended partition. Then you can have an unlimited number of logical partitions.

Also Windows 10 whether UEFI or BIOS uses fast start up which really is just always on hibernation. Since that leaves all NTFS partitions it sees mounted, the Linux NTFS driver does not correctly see those NTFS partitions and can lead to overwriting them. Make sure fast start up is off in Windows 10.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

If you have more than one drive, you need to use Something Else install option and on partitioning screen choose to install grub2's boot loader to MBR of that drive. All auto install options overwrite MBR of sda or first drive.

       
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 
    
       
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by Geoffrey_Arndt on 2016-09-13
It's always useful on a 1st post to include the full specs of your system.   Especially important is the media system (intel, nvidia or ati/amd), if system is uefi/bios or legacy/bios and to include a screen print of your disk partition layout.   This is a smart thing to do "before" attempting the install/setup of a multi-boot system.   I perused Linux forums for nearly 6 months and read at least 20-30 user threads about multi-boot setup, disk partitioning, etc.    I thought I had a decent computer background before I started - - but found I had a LOT of gaps in that knowledge.

Also helpful would be a link to the actual instructions you used.

In summary, as he so often does, OldFred has created a useful reply post to serve as a starting point for checking what steps to look at to fix.   The fast/quick start (always on hibernation) is the 1st thing that has to be addressed, and I always get nervous when a user with multi OS's & partitions uses the "install alongside" option in the installer versus the "something else" option (which is really better labeled - "custom install").

---

### Post by mastablasta on 2016-09-13
> **ranmac1948 said:**
>  I therefore "pulled" the internal ssd while Ubuntu was being installed. 

do that before you do the install and all should go smooth.

if you can boot into live session, the boot repair tool has the option to create a bootinfo summary. [URL="https://help.ubuntu.com/community/Boot-Repair"][SIZE=2]https://help.ubuntu.com/community/Boot-Repair
[/SIZE][/URL]
create it and post it here. it should displays your setup for the rest to see. 

single OS install is really easy. dualboot (or multiboot) is a bit harder with UEFI, but very easy with MBR. multiboot of various linux distros is easy for the most part. installing it in virtualbox is really easy: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)


you just need to have enough ram for it.

---

### Post by Bucky Ball on 2016-09-13
> **Geoffrey_Arndt said:**
> It's always useful on a 1st post to include the full specs of your system.

Welcome. It is also useful to use paragraphs and punctuation. You do your chances of support no favours by posting a 'wall of text' with no paragraphs. Probably cuts a third of potential helpers out right there as they take one look and move on (I'm not willing to attempt it personally as I already have a bit of a headache!). There are also those with vision issues to consider who can't do much with 'black blobs' of text.

Good luck. ;)

---

### Post by coldraven on 2016-09-13
Hi and welcome to the forum. 
As mentioned above you might want to consider Virtual Machines, it's so easy even i can do it :)
Get VirtualBox from here: [https://www.virtualbox.org/](https://www.virtualbox.org/)

Get any number and flavour of ready-made VBox images here: [https://virtualboxes.org/images/](https://virtualboxes.org/images/)

Top tip: if you run a Linux server in VirtualBox use PuTTY to connect to it from your Windows host.

Another method would be to buy a second-hand laptop and use that for your experiments. I was just given a couple of Toshiba Satellite Pros an A200 and an A300.
 I kept Windows XP on them just long enough to update the BIOS then overwrote the whole drive with Ubuntu 16.04. They work perfectly and can be bought for peanuts!
Ubuntu, Xubuntu or Lubuntu can transform old kit into something that's modern, usable and secure.

---

### Post by leunam12 on 2016-09-13
> **ranmac1948 said:**
> ...the software went into a continuous loop of: Broadcom base code P2.1 V10 7,5 PXE- E61 media test failure check cable. Broadcom UNDI PXE-2,1 V1.0.9. I am uncertain what this means so perhaps you can enlighten me.
Your computer cannot find the boot device. Most likely it means the computer is trying to  boot from a disk that doesn't have any boot information. You have to do some research and learn to use the option "something else", it will give you more control of what gets installed where, that way you don't mess up your previous installations.

---

