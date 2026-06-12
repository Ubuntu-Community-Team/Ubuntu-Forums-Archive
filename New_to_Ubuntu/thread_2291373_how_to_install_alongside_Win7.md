---
title: "how to install alongside Win7"
date: 2015-08-19
forum: New to Ubuntu
---

### Post by flex567 on 2015-08-19
I would liike to install Ubuntu 14.04 alongside win 7 but I can't - I get the message that Ubuntu didn't detect any other OS ? How can I install ubuntu alongside Win7? I already have win7 installed, I am posting this from Win7.

[[img]http://i.imgur.com/njeXqBJ.jpg[/img]](http://imgur.com/njeXqBJ)

---

### Post by grahammechanical on 2015-08-19
You do not give us any information about your machine or the partitions (what Windows calls drives) or whether it is a BIOS or UEFI boot system. That limits the advice that can be given. So, I will take a guess.

In Windows find a utility that shows you the partition layout of the hard disk. A screen shot posted here would be useful.

But it is my guess that the partitions are labelled "Primary" and that there are 4 of them. With a BIOS boot system using the msdos partition table there can only be 4 Primary partitions. And with the allocation of 4 possible primary partitions already used up the Ubuntu installer is offering you the only thing it can offer and that is to Erase disk and Install Ubuntu. It cannot offer to Install alongside because it needs 2 partitions for the installation of Ubuntu and there is no place to create them.

I am not suggesting that you choose the Erase disk option but what will happen, apart from deleting Windows and all your data, is that the Installer will create a new partition table using 2 primary partitions. One primary partition will hold Ubuntu. The other primary partition will be a special primary partition called an Extended partition. In the extended partition the installer will create a Logical partition to be used as a swap partition. And that will leave 2 primary partition allocations still available. And that is something the suppliers who pre-install Windows do not do.

Having one of the 4 possible primary partition slots as an Extended partition allows us to get around the 4 primary partition limit because we can create any number of logical partitions inside the Extended partition. And that means we can put the 2 necessary Ubuntu partitions in the Extended partition as Logical partitions if we want to.

But this is only a guess and it is not based an any evidence. So I will not suggest what you need to do.

Regards.

---

### Post by mastablasta on 2015-08-20
> **grahammechanical said:**
> 
But it is my guess that the partitions are labelled "Primary" and that there are 4 of them. With a BIOS boot system using the msdos partition table there can only be 4 Primary partitions. And with the allocation of 4 possible primary partitions already used up the Ubuntu installer is offering you the only thing it can offer and that is to Erase disk and Install Ubuntu. It cannot offer to Install alongside because it needs 2 partitions for the installation of Ubuntu and there is no place to create them.

this is very likely the case, but not necessarily. once you are sure you do not have 4 primary and still get that message you can install using manual partitioning. you do that by creating a root "/" partition (format as ext4) and a /swap partition formatted as swap in the size of your ram or double the size of RAM if you are low on RAM. GRUB is place on disk where computer boots from. it replaces windows boot loader.

if you do have 4 primary partitions the easiest path is to backup your data (maybe create a disk image using the free RedoBackup or Clonezilla) or backup just the data (if you have windows install disk). then use min partition wizard tool and convert one of the primary partitions to secondary/extended. for example I had a hidden boot partition so I left that as primary and changed the system partition C into secondary and created unformatted free disk space from it. when "toying" with partitions it's best to defragment the drive at least two times before you start.

---

### Post by flex567 on 2015-08-20
I don't think I have 4 primary partitions. 
[IMG]http://i.imgur.com/JrAFP34.png[/IMG]
Is it still posible to install ubuntu alongside win7 without formating the entire drive and how can I do it?
Maybe I should try Ubuntu 15.10?

---

### Post by flex567 on 2015-08-20
I tried to install Ubuntu and I choose "Something else" and I saw this screen. What should I do next, I don't want to format my entire drrive. Apperantly ubuntu dosn't see win7. 
[IMG]http://i.imgur.com/berSPJL.jpg[/IMG]

---

### Post by Mark Phelps on 2015-08-20
Do NOT use the Ubuntu installer to shrink the Win7 OS partition.  Doing that risks filesystem corruption, and if that happens, Win7 may then be unbootable -- making it very hard to fix.

Instead, use the Minitool Partition Wizard to shrink the "C:" partition to make some room for Ubuntu.  40GB should be more than enough.  Do NOT create a partition in the empty space, but leave it as is.

Then, when you use the Something Else option, you will be able to create the Linux filesystem partitions you need in the unallocated space.

---

### Post by flex567 on 2015-08-20
Right now my mini tool partition looks like this: 
[img]http://i.imgur.com/9Cq6Wy1.png[/img]

And when I try to install Ubuntu and chose "something else" I see this. So what should I do next?
[img]http://i.imgur.com/WGFSwgW.jpg[/img]

---

### Post by sotiris2 on 2015-08-20
Something is very wrong. Ubuntu sees the whole disk (1000204 MB ~=  1TB) as free space. Do post a screenshot from the actual windows7 disks tool.

---

### Post by Deep_Peasant on 2015-08-20
> **sotiris2 said:**
> Something is very wrong. Ubuntu sees the whole disk (1000204 MB ~=  1TB) as free space. Do post a screenshot from the actual windows7 disks tool.

Yes and, his System Reserved is set to active & boot, not his C: drive?

Start Windows, 
run
diskmgmt.msc

---

### Post by sotiris2 on 2015-08-20
System Reserved is flagged as boot on my working win7 install too, that's normal afaik.

---

### Post by flex567 on 2015-08-20
[img]http://i.imgur.com/0qg0WG7.png[/img]

---

### Post by Deep_Peasant on 2015-08-20
> **sotiris2 said:**
> System Reserved is flagged as boot on my working win7 install too, that's normal afaik.

Back, I checked my Windows, diskmgmt, the System Reserved is not set to boot in my system.
I have,
Reserved: System, Active, Primary Partition.
C: Boot, Swap, Crashdump, Primary Partition

Perhaps  he is using bitlocker, reinstalls of windows or even tried the windows  10 upgrade, that completely messes up the disk with hidden partitions.
Can't make head or tails of it with third party programs like he uses.

*edit*
That I recognize ;), hmm, looks good?

*edit2*
I have had hell myself, something I remember now, when you are booting the ubuntu disc or usb, do you get the option Eufi boot and/or legacy boot?
In one mode it saw my drive as empty like you have (you have legacy btw.)
Running out of ideas, make a new ubuntu disc/usb with a fresh iso with [lili]("http://www.linuxliveusb.com/")

---

### Post by flex567 on 2015-08-20
So what should I do next?

---

### Post by oldfred on 2015-08-20
Are you leaving Windows hibernated?
Or does it need chkdsk? I would just run chkdsk a couple of time to make sure. It always needs a chkdsk after a resize.
The Linux NTFS driver will not mount NTFS that needs chkdsk or is hibernated. Windows 8 is always hibernated with its fast startup setting. But with Windows 7 it should only be hibernated if you turned it on.

---

### Post by flex567 on 2015-08-21
I ran the chkdsk and after that I ran the Ubuntu 14.04 disk and It was same as before. 

After that I created bootable usb from 15.04 and it gave me the option to install it alongside win7

---

### Post by cariboo on 2015-08-21
I'd suggest using the Something else option in the Ubuntu installation partitioning section.Use the unallocated area of the hard drive to create a root / and a swap partition, then just do the normal installation.

---

### Post by flex567 on 2015-08-21
I already installed ubuntu. It is installed by default to unnalocated space.

---

