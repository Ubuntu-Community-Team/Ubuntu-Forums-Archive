---
title: "Problem partitioning drive while installing Heron"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by panand178 on 2008-05-12
I've been using Gutsy along with Windows XP and was just waiting to try out the Heron. 

Since installing XP after installing Ubuntu is a pain with having to re-install grub and all I decided to re-install my XP as well (Which I've already done and lost my grub successfully :)).

I had also decided that I'd go in for a fresh install of Heron rather than upgrading from Fiesty. Now when I tried out the live CD and the installation went fine till the time I had to choose the HDD partition on which to install Heron. In Fiesty the partition editor showed my current partitions and I could just delete a partition or break a current partition into 2 without loosing my data. However in Heron all it shows is my whole HDD (250 GB IDE) and it does not show my current partitions. It's the same thing when I tried the manual mode too. 

What I would ideally like to do is format the root partition that I've been using for Fiesty and install Heron there. Could anyone tell me how do I proceed from here. I have loads of data on my other partitions and can't really afford to take a risk of loosing it. 

Thanks in advance!

---

### Post by phidia on 2008-05-12
You need to be sure which partition you want to install on. 
Open a terminal and type fdisk -l that should show your disks and partitions. Is you need to alter anything I recommend cfdisk, and to install heron use the alternate cd as it allows more options during install.

---

### Post by dstew on 2008-05-12
Did you boot the live CD, and install from there, or did you use the "Install inside Windows" choice?

---

### Post by panand178 on 2008-05-13
*fidsk -l* did not give any results. Do I have to do a *sudo fdisk -l*? But even i can see my partiotions how do I select it since the installer itself is not showing any of my partitions to choose from?

---

### Post by panand178 on 2008-05-13
I am booting from the *Live CD* and the *Install from Windows *option.

---

### Post by bodhi.zazen on 2008-05-13
yes you have to sudo fdisk -l

I advise you defragemnt windows first, then I like to partition the hard drive prior to running the installer.

Fire up the live CD and run gparted. Often you need to manage the partitions in two steps. First resize the windows partition -> apply changes. Then make partitions for ubuntu -> apply changes.

Then, lase run the installer and select manual partitioning.

---

### Post by az on 2008-05-13
> **panand178 said:**
> n Fiesty the partition editor showed my current partitions and I could just delete a partition or break a current partition into 2 without loosing my data. However in Heron all it shows is my whole HDD (250 GB IDE) and it does not show my current partitions. It's the same thing when I tried the manual mode too. 


If you run the Feisty desktop cd, do you still get the same result?  Did installing windows delete your other partitions, too?

You can recover lost partitions using parted or testdisk.

see [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by panand178 on 2008-05-18
> **az said:**
> If you run the Feisty desktop cd, do you still get the same result?  Did installing windows delete your other partitions, too?

You can recover lost partitions using parted or testdisk.

see [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Sorry I couldn't check out your reply for a few days. I tried running the Gutsy installer today and I am facing the same problem there too. I cannot see my partitions in the Gutsy installer also.

Now I guess the only way left for me is to format my entire hard disk. However i have over 70 GB of data that I need to backup before I can do that. I need to figure out where I am going to transfer the data temporarily while I format my hard drive.

Is there any other way for me to install any ubuntu flavor without having to format my entire hard drive? Also now I can't even log into my Gutsy since my grub is lost. :(

---

### Post by dstew on 2008-05-18
> Is there any other way for me to install any ubuntu flavor without having to format my entire hard drive? You should never have to format your whole drive as long as there is space available. You should always be able to resize a partition to make room for Ubuntu. The only exception would be a hard drive that had errors on it, or a corrupt partition table. But, since you can run Windows fine, that is not your problem. It must have something to do with your way of using the partitioner software, or a bug in the partitioner software that is specific to your system.

Also, there is something I don't understand. You said:> I am booting from the Live CD and the Install from Windows option.I don't think there is an option to install from Windows when you boot the CD. There _*is*_ an option to "Install Inside Windows" when you *open* the CD in Windows, but not when you *boot* it. Could it be that you have really opened the CD in Windows, and are mistaking the installation screen for a partitioner screen? If you can, post a sceenshot.

---

### Post by panand178 on 2008-05-19
> **dstew said:**
> You should never have to format your whole drive as long as there is space available. You should always be able to resize a partition to make room for Ubuntu. The only exception would be a hard drive that had errors on it, or a corrupt partition table. But, since you can run Windows fine, that is not your problem. It must have something to do with your way of using the partitioner software, or a bug in the partitioner software that is specific to your system.

Also, there is something I don't understand. You said:I don't think there is an option to install from Windows when you boot the CD. There _*is*_ an option to "Install Inside Windows" when you *open* the CD in Windows, but not when you *boot* it. Could it be that you have really opened the CD in Windows, and are mistaking the installation screen for a partitioner screen? If you can, post a sceenshot.

Oops! I meant "I am booting from the Live CD and **NOT** the Install from Windows option." :)

I don't think it could be a problem with a bug in the partitioner software since the Gutsy Live CD which ran perfectly well in November refuses to detect my partitions now. My guess is a corrupt partition table. My 250 GB is split into two NTFS partitions and 3 ext3 partitions excluding the swap (which is around 1 GB). Is there a possibility that Windows is running fine because an ext3 partition is what got corrupted which windows does not detect anyways. On another note I use [explore2fs]("http://www.chrysocome.net/explore2fs") to access my ext3 partitions from inside windows(if i need to copy files from my ext3 partitions to windows without having to reboot to Ubuntu). I am still able to access all my Linux partitions and copy files from there without any problem. Will a corrupt partition allow me to do that?

Anyways what I am trying to do now is backup all my data on a friends external Hard drive (I've already initiated this process btw), delete all my current partitions, install windows again and then try to install Heron. Hope it works this time.

---

### Post by panand178 on 2008-06-01
Just to let you guys know, I have finally managed to install Heron and I should say I am really impressed. It has solved some of the problems I was facing with Fiesty. For example, in Fiesty my system used to hang if I tried a drag drop inside mozilla or akregator. I had [posted]("http://ubuntuforums.org/showthread.php?t=616375") that issue long back however no one seemed to know the solution to issue then. In Heron, that problem seems to have gotten sorted out. I will let you all know any additional comments/concerns I have in a few days! :guitar:

---

