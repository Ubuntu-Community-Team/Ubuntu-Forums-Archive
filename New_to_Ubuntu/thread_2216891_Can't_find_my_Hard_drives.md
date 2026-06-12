---
title: "Can't find my Hard drives"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by McCai on 2014-04-14
I trued the disk utility it doesn't see the  dditional drives
I have Ubunto on  a 1TB  drive and now I am trying to copy  the files and data from old NTFS and FAT32 drives.

My Bios sees the drives

I don't even know what a HD is designated as in Ubunto so I'm a little lost but using the disk utility I can see the 1TB drive and the optical CD/DVD just fine

How to  get Ubunto to see the other hard drives?

---

### Post by 7sbaV8Kt5PTh on 2014-04-14
Hello, McCai.

The best way to see what has been partitioned is to use the command "fdisk -l" to list the partitions.  Look for one that says "no valid partition", this will be your new drive.

Read the section carefully, it should say "/dev/sdb", which is the physical volume.  Once you add a partition to it, you can format it, and it will show up as "/dev/sdb1" which you can mount.

---

### Post by McCai on 2014-04-14
You have confused me.  You are talking about partitions and formatting and all I want to do is to get data from an older IDE drive and copyu it to my 1TB drive.  Is it necessary to access the partitions to do this 
Is Fdisk in ubuntu the same thing as it is in DOS?
I just want to see the drive and get at the   files on it.

When I enter "sudo Fdisk -l"  I get this  and  no "/dev/sdb":


   OMITTED-System-Product-Name:~$ sudo fdisk -l 
 [sudo] password for OMITTED:  
 

 WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted. 
  
 
 Disk /dev/sda: 1000.2 GB, 1000204886016 bytes 
 255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x00000000 
  

    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1               1  1953525167   976762583+  ee  GPT 
  
 
 Disk /dev/mapper/cryptswap1: 17.1 GB, 17116954624 bytes 
 255 heads, 63 sectors/track, 2081 cylinders, total 33431552 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x55810c0d 
  
 
 Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table 
 OMITTED@OMITTED-System-Product-Name:~$




Now about identifyinig a hard drive  are they /dev/sda and dev/sdb and dev/sdc  with a b c d e f g etc., the  designations?
What about when I'm in the  Home Folder? Would other drives appear there?  If so what would the icon and designation be?

---

### Post by coffeecat on 2014-04-14
Your output is showing that your Ubuntu system can only see your 1TB hard-drive. 

Tell us more about these other "drives". You say IDE and that your BIOS can see them. Have you plugged them straight into the motherboard via an IDE connector? Or have you put them in a USB enclosure and plugged them in via USB? Either way, Ubuntu is not seeing them.

As a general principle, you don't need disk utility to see NTFS and FAT32 partitions whether they are on the main drive or on secondary or USB drives. If they are on partitions on internal hard-drives you simply click on them in the left pane of the file manager and they are mounted read-write. If USB, they are automounted as soon as you plug them in. In your case something is not happening, but you need to provide more information.

---

### Post by 7sbaV8Kt5PTh on 2014-04-14
McCai,  I'm sorry for the confusion, I was trying to help determine if the drives were even listed, and then whether the OS understood the formatting.  From your posting, it appears that ti only sees the one TB drive.  

CoffeeCat is heading you down the correct path.

---

