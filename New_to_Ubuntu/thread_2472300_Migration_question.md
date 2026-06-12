---
title: "Migration question"
date: 2022-02-23
forum: New to Ubuntu
---

### Post by patrick1945 on 2022-02-23
Hello everyone.  I am planning to migrate from Windows 11 to Ubuntu.  One question currently prevents me from migrating.  namely: Does Ubuntu recognize a Windows storage pool and can I associate it with Ubuntu?

---

### Post by Frogs Hair on 2022-02-23
Moved to ***New to Ubuntu. ***

---

### Post by TheFu on 2022-02-23
> **patrick1945 said:**
> Hello everyone.  I am planning to migrate from Windows 11 to Ubuntu.  One question currently prevents me from migrating.  namely: Does Ubuntu recognize a Windows storage pool and can I associate it with Ubuntu?

Linux needs native file systems to work. NTFS or any of the FAT-based file systems don't work.  If a "Windows storage pool" is a specific MSFT advanced volume manager, I don't know. Usually, there is a way to read those things, but may not be a way to write there.  It is always best to use a native file system and volume management for the OS running.

Could you mean to say *Windows Storage Spaces*?  Those appear to be what we call Linux Software-RAID. There are multiple different methods under Linux to get that.  

Linux supports LVM2, which is the Logical Volume Manager very similar to what Veritas, Solaris, AIX and HP-UX have provided for decades. LVM is a checkbox option during the install. That's for volume management, the file system placed onto the Logical Volumes is up to you - i.e. your choice, but if you don't have a specific need for a specific native file system, choose ext4.

Ubuntu has some support for ZFS. That support has been getting better and better. While many people use it for their boot and OS needs, I wouldn't suggest it at this time.  ZFS is great for data storage and merges both volume management AND a file system, so it is probably less effort to learn, but it is a completely different way to handle storage. Most Windows users will have their mind blown by ZFS.

As for SW-RAID on Linux, LVM, mdadm and ZFS all support multiple RAID levels. Each option has pros and cons, but it is your choice which you want. There are other methods that data hoarders use which aren't as proven, but some people swear by.  I'm old school and my data is too important to trust with "new" software that doesn't have 5+ yrs of no data loss due to bugs.  And backups are still required. They are more important than RAID, since sometimes the only fix for some RAID situations is to wipe the array, rebuild it from scratch and restore from a backup version.

---

### Post by MAFoElffen on 2022-02-24
I'll look in the morning on on of my Machines that has Linux and a Windows Storage pool. Off the top of my head, I do not think it does.

---

### Post by Impavidus on 2022-02-24
I don't know about Windows storage pools. But maybe you can answer the question yourself if I tell you a bit.

Network file sharing between Windows and Ubuntu works, either Windows server and Ubuntu client or Ubuntu server and Windows client. The server accesses the filesystem used for storage, translates it to some networking protocol and the client only has to understand the networking protocol. Maybe there are some features that don't work, but for most use cases it's good enough.

Directly accessing a hard drive formatted for the other operating system is harder. Windows has no support for Ubuntu filesystems and Ubuntu has only partial support for Windows filesystems. Reading works, writing usually works, repairing doesn't work and Windows filesystems can only be used to store simple data files, where no ownership or permissions are required. When you move to more complex storage methods (LVM, dynamic partitions, fancy filesystems), it gets harder.

---

### Post by MAFoElffen on 2022-02-24
Back... Didn't see it. Couldn't mount it successfully. Checked into the Why...

No. The filesystem of "Windows Storage Spaces" is ReFS. There is not a free OpenSource Solution that I see yet, which it came out with Windows Server 2012. But: (commercial) [https://www.paragon-software.com/business/refs-linux/#oem](https://www.paragon-software.com/business/refs-linux/#oem)

But realistically, on the Windows side, Microsoft had *'announced'*  dropping support for ReFS back before 9/2017... Which means eventually  it is planned to go away from the MS Windows World. So even for Windows,  you should have a plan on what you are going to do before that does  happen. So your remark on that "Stopping you from migrating", should be  changed to adapt to what is current and upcoming.

And at the end of this article, Microsoft has already disabled the ability to create new Storage Spaces after a certain update, that has already happened about 4-5 years ago... [https://www.guidingtech.com/71672/reasons-why-microsoft-removing-refs-window/](https://www.guidingtech.com/71672/reasons-why-microsoft-removing-refs-window/)

---

### Post by mIk3_08 on 2022-02-24
> **patrick1945 said:**
> Hello everyone.  I am planning to migrate from Windows 11 to Ubuntu.  One question currently prevents me from migrating.  namely: Does Ubuntu recognize a Windows storage pool and can I associate it with Ubuntu?
For me, that was long time go as far as I remember I'm using with ms win 7 at that time. I always accept that I learn computing using ms windows. But now I already migrated to Linux Ubuntu. Before I use a dual boot of ms win7 and Linux Ubuntu Operating System. What I did was just to empty my partition drive d. and made it unallocated and there I installed my Linux Ubuntu Operating System. That time my disk was into mbr (Master Boot Record) disk that was easy for me to add the Linux Ubuntu Operating System then. That was before I don't know now. I think you should know the installation settings from the BIOS/UEFI configuration to setting up boot device and etc. You should familiarize those things before you go and take risk. Don't worry about encountering errors/fails on the Linux Ubuntu Operating System once installation is done or even from the start of installation the Linux Ubuntu Forum Community  are wiling to help you. They were expert on this. So Good Luck Cheers.

---

### Post by rsteinmetz70112 on 2022-02-24
The first question is why do you need to access this storage?

Apparently there is a way to access ReFS from Linux.
Paragon ReFS for Linux.
 How it works and what you need to install it I have no idea.
Their website has this 
> Paragon ReFS for Linux is the first completely free driver for Linux with the ability to read and write data from ReFS volumes
But doesn't say how to obtain this software or much about licensing.
[https://www.paragon-software.com/home/refs-linux/?x-aff=cj](https://www.paragon-software.com/home/refs-linux/?x-aff=cj)

---

### Post by MAFoElffen on 2022-02-24
> **rsteinmetz70112 said:**
> Apparently there is a way to access ReFS from Linux.
Paragon ReFS for Linux.
 How it works and what you need to install it I have no idea.
Their website has this 

But doesn't say how to obtain this software or much about licensing.
[https://www.paragon-software.com/home/refs-linux/?x-aff=cj](https://www.paragon-software.com/home/refs-linux/?x-aff=cj)

When I checked into it, it was not under their Free, nor Home User Sections, it was under Commercial/Business. So highly thinking it is non-free. 

Installs as a Kernel Module, so each time a Kernel Updates...

Windows does not support the creation of any new "Storage Spaces" and they snuck in a Windows Update that turned off the creation of storage spaces to 'disabled' on all of their flavors of the Windows OS that previously supported it. They can still read the ones that are there, but it's life/existence is very numbered.

I feel that, even for the sake of his existing or upgraded Windows OS, that he needs to plan on migrating that data to something and somewhere else. It is abandoned and upsupported by it's own creator. I am faced with this same real-world obstacle with mine. I had been working with it on my own, albiet I work mostly in Linux... And didn't even realize it was disabled on mine!!!

My own choices are to migrate my data to another shared storage source, so that I can use the data between systems. What his decision will be, is based on his own preferences and circumstances.

---

### Post by mastablasta on 2022-02-25
> **TheFu said:**
> Linux needs native file systems to work. NTFS or any of the FAT-based file systems don't work. .

some clarification here. you can use NTFS or FAT to store data (i have old windows disks attached with data on them), but OS has to be installed on EXT4, BTRFS ... or any other supported file system. 

note that you can not repair NTFS partition from Linux, but various windows repair tools can be loaded at boot to do it, if necessary.

---

