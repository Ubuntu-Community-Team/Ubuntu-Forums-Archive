---
title: "Partition advice sought for new install"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by ian49 on 2014-07-11
I'm just about to install 64-bit Ubuntu (14.04) on a brand new desktop pc which has a 120Gb SSD as the primary drive and a 2Tb Seagate as secondary. There is 8Gb RAM.

It's probably not relevant but I'm later going to be running Windows 7 as a virtual machine via VMWare.

I only want to have 3 partitions: root, swap and home but I'm unsure what size to set for the root and swap partitions. In addition, since I've only ever previously run Ubuntu on a laptop with a single HD, I'm unclear as to how to use the secondary 2Tb drive. IOW, should I put home on the 2Tb drive instead?  Hopefully, there's a recommended approach I can take that makes the most sense so if anyone can offer advice I'd really appreciate it.

---

### Post by yancek on 2014-07-11
The largest partition should be for the /home or if you choose, a data partition.  Some people prefer to keep all their personal data such as movies, music, photos on their /home partition, others create a separate data partition or partitions.  It's just a matter of personal preference and you can always create additional partitions after install.  With 8GB of RAM, you may never use a swap partition but with the drive sizes you have, a 2GB swap should suffice.  Is the secondary 2TB an internal or external drive?

Take a look at the posts in this thread just below your which has some specific advice for the same situation.

[http://ubuntuforums.org/showthread.php?t=2233586](http://ubuntuforums.org/showthread.php?t=2233586)

---

### Post by ian49 on 2014-07-11
> **yancek said:**
> The largest partition should be for the /home or if you choose, a data partition.  Some people prefer to keep all their personal data such as movies, music, photos on their /home partition, others create a separate data partition or partitions.  It's just a matter of personal preference and you can always create additional partitions after install.  With 8GB of RAM, you may never use a swap partition but with the drive sizes you have, a 2GB swap should suffice.  Is the secondary 2TB an internal or external drive?

Take a look at the posts in this thread just below your which has some specific advice for the same situation.

[http://ubuntuforums.org/showthread.php?t=2233586](http://ubuntuforums.org/showthread.php?t=2233586)

The secondary 2TB is an internal drive. Is there a recommended size for the root partition? The one on my laptop is 10GB. So, would it make sense to create the following partitions:

SSD (120GB):
root:  10(?) GB
swap:  2 GB
data:  the rest

HDD (2TB)
/home: 2TB

I was thinking I could use the data partition on the SSD for work in progress and then when finished with move it over to Home. Should I create the data partition as Ext4?

---

### Post by oldfred on 2014-07-11
I prefer 20 or 25GB for / (root). I do have my /home inside / and use separate data partition and my / is about 11GB used of the 25GB.
I also have two / partitions on SSD, one current install and one next install. Plus I have several / partitions on hard drive just to test or experiment with things where I do not want to modify working install.

I like to keep every drive as a bootable system, so want at least once reasonable current install on every drive.
Data partitions should be ext4 except perhaps in unusual cases. Most tests show ext4 to be best for general use. 

But every user has somewhat different needs and there is no one totally correct solution. Even my own optimal partition plan is usually outdated a year later, but after a couple of years I get a new hard drive and start all over.

---

### Post by ian49 on 2014-07-11
Thinking about it further I might be better advised to put /home on the SSD after all and have my Win 7 virtual machine installed there. That way both Ubuntu and Win 7 will be on the primary drive and I can use the secondary drive purely for data storage.

Perhaps 15GB might be enough for my root as I don't think I'll be installing that much in the way of addition software etc. That would give me:

SSD (120GB):
root:  15GB
home:  105GB (of which perhaps 50GB will be a VM)

HDD (2TB): data

Thanks to you both for responding.

---

### Post by erind on 2014-07-11
My setup looks like so:

SSD - 90GB, Main OS:
[LIST]
[*]**/home** is inside **/ **- one partition,  and I backup my **/home** in a separate DATA partition (disk). My *Virtual_Directory* is inside */home*, where I keep the most used VMs, the other ones go in another disk. From an efficiency standpoint you can tell the difference when one VM runs from a SSD drive. 
[*]Swap: 2.5GB, on SSD too. 
[/LIST]

HDD (1TB):  DATA, separate disk.

---

### Post by mooreted on 2014-07-11
/dev/sda1       103G    /
/dev/sdb1       939G   /mnt/Backup

I have pretty much the same setup. I just let Ubuntu automatically partition the SSD so home and root are all on the same partition.

I put my Windows 7 VM on the 1TB secondary drive because it takes up about 20GB of space and I want my games to run on the SSD. Windows boots faster on the SSD, of course, but it takes up a lot of room.

---

### Post by ian49 on 2014-07-12
I just thought of another questions. If I'm running both Ubuntu and the Win 7 VM on the primary SSD is  there a  way they could both access files in the same partition on the secondary  drive or would they need to have separate partitions formatted  accordingly (msdos for Ubuntu and NTFS for Win 7)?

---

### Post by oldfred on 2014-07-12
MBR(msdos) is how a drive is partitioned. gpt is the newer way to partition drives.
NTFS or ext4 are formats of a partition. Linux reads NTFS just fine, I used it with a shared XP install for years and still have it but do not use Windows anymore.
Not sure of any special issues with VM as I do not use that.

---

### Post by ian49 on 2014-07-12
> **oldfred said:**
> MBR(msdos) is how a drive is partitioned. gpt is the newer way to partition drives.
NTFS or ext4 are formats of a partition. Linux reads NTFS just fine, I used it with a shared XP install for years and still have it but do not use Windows anymore.
Not sure of any special issues with VM as I do not use that.

Thanks for responding. Looks like MBR/NTFS it is then.

---

### Post by oldfred on 2014-07-12
Actually if just Linux, gpt is preferred whether you use BIOS or UEFI to boot.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

But with gpt you have to have an efi partition for UEFI boot and/or a bios_grub partition for BIOS boot. I have both on my SSD as I planned on moving it to a newer computer. The efi partition should be first on drive, bios_grub can be anywhere on drive.

---

### Post by stalkingwolf on 2014-07-12
as hdd space is really not an issue and you did mention using a virtual machine id make my /at least 20-25 gb. it is a pain when you run out.

---

