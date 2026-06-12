---
title: "dual boot windows xp with ubuntu 11.04"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by Nikki5 on 2012-06-08
hi,
i want to dual boot windows xp along with ubuntu 11.04.i have windows XP installed on my pc.i had earlier installed ubuntu using windows installer but after sometime my windows XP
could not boot,so i formatted my C drive and again installed windows XP through CD.Now i want to install ubuntu 11.04...actually i need it for a project.so can u please suggest me a safer way to install ubuntu 11.04 in a step by step manner(I dont have ubuntu installation cd)and i have space on my E and D drives

---

### Post by wilee-nilee on 2012-06-08
> **Nikki5 said:**
> hi,
i want to dual boot windows xp along with ubuntu 11.04.i have windows XP installed on my pc.i had earlier installed ubuntu using windows installer but after sometime my windows XP
could not boot,so i formatted my C drive and again installed windows XP through CD.Now i want to install ubuntu 11.04...actually i need it for a project.so can u please suggest me a safer way to install ubuntu 11.04 in a step by step manner(I dont have ubuntu installation cd)and i have space on my E and D drives

Just so we are on the same page E and D drives mean nothing here it is all sdXX here.  First X is the HD second X the partition.

Boot the live ubuntu cd and take a screenshot of the gparted partitioner and attach it to a reply with the paperclip in the reply panel.

---

### Post by Frogs Hair on 2012-06-08
Hello and Welcome

If you must have 11.04 and don't want to use Wubi see the links, but you will need to create a disk or usb installation medium.
[http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

Dual Boot: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you can use 12.04 do so because it is supported for 5 years.

---

### Post by Nikki5 on 2012-06-09
Thanks a lot for replying.if i install ubuntu desktop through a cd then will it be permanently installed?and will i get an option to choose the O.S while booting.Thanks in advance:)

---

### Post by Fuzzv on 2012-06-09
Do you have a flash drive? You can use [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable live USB.

---

### Post by Nikki5 on 2012-06-09
i actually bought a cd.i have a usb of 2GB

---

### Post by Nikki5 on 2012-06-09
Thanks a lot for replying.if i install ubuntu desktop through a cd then will it be permanently installed?and will i get an option to choose the O.S while booting.Thanks in advance:)

---

### Post by wilee-nilee on 2012-06-09
> **Nikki5 said:**
> Thanks a lot for replying.if i install ubuntu desktop through a cd then will it be permanently installed?and will i get an option to choose the O.S while booting.Thanks in advance:)

Any install can be removed, so permanently is not quite the correct word, it will be installed. 

Ubuntu uses a boot loader called grub that finds other operating systems and adds them to the grub menu at boot .

---

### Post by holycow131415 on 2012-06-09
If you are just using it for a school project, and will never use it again or want the option to delete easily, just install a virtual machine program. Virtualbox works very well.

---

### Post by TMD on 2012-06-09
I second that. I used VirtualBox when I was trying out Ubuntu. It's free and you can gets it here

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by Nikki5 on 2012-06-10
i dont want it for  a temporary period.so i hav 2 install it via cd only.i have burnt the iso image on cd.can ny1 tell me how to proceed now in a step by step manner?

---

### Post by Nikki5 on 2012-06-10
i am referring the site:  [https://help.ubuntu.com/community/WindowsDualBoot.in](https://help.ubuntu.com/community/WindowsDualBoot.in) this in automatic partitioning how should i slide the dragger to partition so that ubuntu is on a separate partition than windows.

---

### Post by wilee-nilee on 2012-06-10
If it were me I would not use the installer to resize the XP.

I would use a windows based partitioner and move all the files to the front of that XP partition with the partitioner first, then defragg it and run a chkdsk, then resize it. I would make sure the xp is booting and in good shape then install Ubuntu.

I would also be aware of the limitations of primary partitions on a sigle HD, 4 is the max, or 3 and a extended partition for the ubuntu install.

I would not do any of this without having a XP disc as well, and have everything backed up including a clone of XP.

Thats just me though I like to have a full tool chest and travel with ease.;)

---

### Post by Nikki5 on 2012-06-10
thanks wilee-nilee but I have burnt the iso image on a CD.I am able to boot from the CD.I tried to install Ubuntu 12.04 alongside windows.everything was working fine.resizing the partitions was done,installation started....it showed various features ubuntu has then it started retrieving files.while retrieving suddenly screen went blank.i tried 2-3 times but the same thing is happening again and again.i spent my whole day but not getting the solution :(please help me...I also checked whether iso file is proper using Winmd5sum.it shows same values on comparing hashes.please help....

---

### Post by wilee-nilee on 2012-06-10
> **Nikki5 said:**
> thanks wilee-nilee but I have burnt the iso image on a CD.I am able to boot from the CD.I tried to install Ubuntu 12.04 alongside windows.everything was working fine.resizing the partitions was done,installation started....it showed various features ubuntu has then it started retrieving files.while retrieving suddenly screen went blank.i tried 2-3 times but the same thing is happening again and again.i spent my whole day but not getting the solution :(please help me...I also checked whether iso file is proper using Winmd5sum.it shows same values on comparing hashes.please help....

Your problem is really outside my area of knowledge.

---

### Post by Kundan Negi on 2012-06-10
U can download pendrivelinux from [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
Install it in ur Windows XP and put ur PC in USB Boot mode.Proceed as indicated in the installer.Choose the correct options and it will install Ubuntu in ur harddisk free space.It will not erase ur Windows XP. A Grub boot loader will be installed for dual boot purpose and u can choose between Ubuntu or Windows XP for booting.:P

---

### Post by Nikki5 on 2012-06-10
Thanks Kundan,but i have a flashdrive of only 2GB.will it work?

---

### Post by Bartender on 2012-06-10
I've tried building flash drive installers [several times]("http://ubuntuforums.org/showthread.php?t=1914974").  Have tried a few more times after the above thread.  

Failed several times, success once.  

Many thumb drives won't take the data properly, so you can spend hours on this and it won't work and you don't know if it's operator error, bad data, or a flash drive that simply will not work.

If you've got a CD, and you're pretty sure it's working, try again.  This time unplug the PC from the internet.  I recently had an install of 12.04 fail when it was connected to the 'net.  I wiped the drive and tried again with Ethernet cable unplugged.  12.04 installed.  I updated it afterwards.

It's very hard to give someone step-by-step instructions via the forums.  Too many variables.

You said you reinstalled XP.  So, I have a suggestion.  This involves starting over from scratch again.  Download [GParted]("http://gparted.sourceforge.net/livecd.php") LiveCD.  Create a bootable CD from the .iso.  You can use ImgBurn on a Windows PC.  I call the resulting disc a GPLCD, because it's too long to type that all out every time :)

Boot from the GPLCD.  Wipe out all partitions.  Create a **primary ntfs** partition on the "front" (the left-hand side) of the HDD.  Make it the size that you want for XP.  With a GPLCD disc, you have to "Apply" the task, otherwise it won't actually do it.  You'll see what I mean when you get to that step.  Watch a YouTube video or two and you'll understand.

Get out of GPLCD, plop your Windows XP install CD in the tray, restart the PC.  The XP installer will **only see** the primary ntfs partition that you created.  It will **ignore** the rest of the HDD.  Install XP to that partition.  

This is much more trouble-free than installing XP to the whole disc, then trying to squish it down.    

When you've got XP running, boot from the GPLCD disc again, or go into XP's Administrative Services.  What we need to know is how many partitions you have.  Hopefully you'll only have one or two primary partitions.  You were asked for this info earlier (Post #2) but you never responded.

If XP is running, and you have three (hopefully less) primary partitions, then boot into the GPLCD again and create one extended partition from the blank (it's called unallocated) space remaining on the HDD outside of the XP install.  Apply the task.  Get out of GPLCD, put the Ubuntu install CD in and reboot.

Unlike Windows, Ubuntu doesn't need a primary partition.  You can install Ubuntu to the extended partition you just created.  The Ubuntu installer has changed over the years so I'm really not sure if it will automagically see the extended partition and ask you if you want it to go there, or if you will have to go into manual mode and direct it to install to the extended partition.

(Side note: Is XP working now?  Or is the PC non-functional?  If you can get into XP, tell us how many partitions you have.  A screenshot would be helpful.)

So, Reader's Digest:

1) We need to know how many partitions you have now if XP is functional.
2) Download latest stable GPLCD, use Windows and ImgBurn to create the disc.
3) Boot from GPLCD, annihilate all partitions.  We want one big unallocated space front-to-back.
4) Create a primary, ntfs partition on the left-hand side of the GPLCD "map".  This partition will be used by Windows installer, so make it the size you want for XP.  Apply, get out of GPLCD.
5) Install Windows XP.  It will install to the ntfs section only.
6) Find out for sure how many partitions have been installed by your XP CD.  Hopefully two or less.  And hopefully no extended partition.
7) Go back in with GPLCD, create an extended partition out of the remaining unallocated space on HDD.  Reboot with Ubuntu install CD.  Install Ubuntu with no internet connection.

If all of that goes to plan (what are the chances?) you should have a functional dual-boot.  And GRUB messes with the MBR so if you just rip Ubuntu out XP won't boot.  That can be fixed, but you need to be prepared for that challenge if you remove Ubuntu later.

---

### Post by Nikki5 on 2012-06-10
Thanks a lot Bartender.my windows xp has 3 partitions:C,D&E.My ubuntu is installed.ur idea of closing the net connection while copying worked.thank u:)

---

