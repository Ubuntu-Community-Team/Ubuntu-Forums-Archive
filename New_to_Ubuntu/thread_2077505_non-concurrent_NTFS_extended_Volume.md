---
title: "non-concurrent NTFS extended Volume"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by rousy on 2012-10-28
Hi all,

I have just recently started to use Ubuntu from a USB Stick.  

Reasons are two-fold - 
1.  To try a linux operating system without losing any files or existing operating system installed. 
2.  I was hoping I could actually tidy up my two hard drives up and re-partition them easier and without currently losing the dual boot option I have currently for Win2000 and WinXP. 

I have a funny setup and I now realise it's not really fit for purpose so my idea was to back up all my files/data to another 64GB stick (using Ubuntu) and then re-partition both so something more suitable for the operating systems that I will use going forward.

However it's not looking good, this is because of my strange setup - in particular an extended NTFS volume that has been extended using Windows disk Manager in XP this is not being seen by Ubuntu and I'm not so sure there is going to be way I can get Ubuntu to see this as one entity either.

I think there is a command to view the blocks which I have used and this was the only command that showed additional devices on the Hardrive but GPART and other the installed disc utilities available including commands to list the devices I have seen listed in these forums fail to list this particular extended volume and before I start moving partitions and reformatting I'd like to get a copy of that.  

I'd like to think there would be a way of getting the 3 bits together and loading them as one partition/directly/volume - whatever the correct terminology is - entity I would call it but it's not going to be easy if it is possible assearching through the Forums and google but have not seen anything that would help me resolve this problem. 

Gut feeling is that to do what I am wanting to do I might just have to dip my hand in my pocket and purchase something like partition magic - however I'm not even convinced that will work because I am running low on some of my system partition volumes hence another reason for really wanting to sort out my hard drives but currently getting nowhere.  Also it would appear certainly with programs such as Ghost, these need to be installed when you first install the system i.e. on a blank hardrive almost, trying to change things retrospectively is either not possible or requires specialist software like Partition Magic it would seem?

I have uploaded a screenshot from windows PC showing the current setup.  Ubuntu is picking up all the other volumes correctly except the N (Music2) Volume.  

Any help or guidance on this would be greatly appreciated.

Output from lsblk showing the volume in question is shown below and I've figured out that sda2,sda5 and sda6

sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   2.4G  0 part 
&#9500;&#9472;sda2   8:2    0   7.8G  0 part 
&#9500;&#9472;sda3   8:3    0    20G  0 part 
&#9500;&#9472;sda4   8:4    0    10G  0 part 
&#9500;&#9472;sda5   8:5    0    40G  0 part 
&#9492;&#9472;sda6   8:6    0  10.1G  0 part 

root@ubuntu:/home/ubuntu# parted -l
Model: ATA ST3120814A (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  11.5GB  11.5GB  primary  ntfs         boot
 2      11.5GB  33.0GB  21.5GB  primary  ntfs
 3      33.0GB  120GB   87.0GB  primary








Rousy

---

### Post by Mark Phelps on 2012-10-28
In my experience, Windows utilities work better with Windows filesystems; Linux utilities with Linux filesystems.

If the partitions you're looking to clean up are Windows filesystems (NTFS) then you should look into the Mintool Partition wizard.  I believe there is a Boot CD available for free download from their site.

I would burn that to CD, boot from that, and use that to do your partition work.

---

### Post by rousy on 2012-10-29
Thanks Mark, 

I'll look at what you have suggested and other options available from Windows and see how we get on.  

Similar topics on other forums here seem to indicate that Linux Ubuntu can only have 4 primary partitions - I have 4 but one is obviously dynamic and extended.  I'm also reading that linux/ubuntu cannot handle these type of partitions!  

I've also added to my original post the output from linux block and parted commands just in case there is a way to do this - I would have thought there was provided Linux/Ubuntu can somehow understand the Windows dynamic/extended partitions - that at the moment seems to be the stumbling block it doesn't and presumably would require some development.  

Regards

Rousy

---

### Post by Mark Phelps on 2012-10-29
> **rousy said:**
> Thanks Mark, 

I'll look at what you have suggested and other options available from Windows and see how we get on.  

Similar topics on other forums here seem to indicate that Linux Ubuntu can only have 4 primary partitions
NO -- this is a general limit on partitioning that affects Windows as well as Linux.

> I have 4 but one is obviously dynamic and extended.  I'm also reading that linux/ubuntu cannot handle these type of partitions!  
Dynamic Disks are not a good situation.  This generally happens when you already have the 4-partition limit and force the creation of another partition.  Linux can't use Dynamic Disks.

> I've also added to my original post the output from linux block and parted commands just in case there is a way to do this - I would have thought there was provided Linux/Ubuntu can somehow understand the Windows dynamic/extended partitions - that at the moment seems to be the stumbling block it doesn't and presumably would require some development.

As long as you have Dynamic Disks, there are no Linux utilities that will be able to handle the partitioning.

---

