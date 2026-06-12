---
title: "How To Resize your Ext3 Ubuntu partition with the Install Disk"
date: 2005-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Herman on 2005-12-18
I installed Ubuntu 5.10 on a 5Gb EXT3-partition, I left the other 35Gb for Windows.
 0 -> 34,xx Gb NTFS
 34,xx -> 35 Gb SWAP
 35 Gb -> 40 Gb EXT3
  Now, i want to resize/move my linux-partition (by shrinking the ntfs-partition). I can shrink the ntfs and move the swap with partition magic 6.0, but it can't resize EXT3-partitions. I cannot find a program that can move and resize my ext3-partition.
  So is it possible to make my linux-partition bigger without having to reinstall the whole thing?

This is a question that gets asked reasonably often, so I have been using my old test computer to find the easiest (I think), way to do this. You can help me test it more, I'm sure other people would already know how to do this, but it's a new one to me, and I haven't seen this method being described by anyone else yet. Maybe it's something that's was known, and has since been forgotten. So it is still experimental, you have been warned: back up your data first!!!:roll:
1.This works for ext3, but not for reiserfs. 
2.You can copy to another partition of equal size or greater, but not to a smaller one, using this method.

The basic plan is this: I have a 30.0 GB disk, with Windows on 24.0 GB, and a 1.0 GB swap, with Ubuntu on the last 5.0 GB. I will shrink Windows to 5.0 GB,delete the swap, make a temporary 5.0 GB partition for Ubuntu, (equal size or just a wee, tiny, bit bigger, in the free space I made by shrinking WIndows), copy the Ubuntu partition to the temporary one, delete the 5.0 GB Ubuntu partition, make a new partition for Ubuntu that is larger, (up to 19.0 GB) and copy the data from the temporary partition back into the new, larger one. Then, I make a new 1.0 GB swap area. After that, I delete the temporay partition, so there is room to grow Windows back again by 5.0 GB.  So I'll finish with Windows on 10.0 GB, a 1.0 GB swap, and 19.0 GB for Ubuntu.

1.  I used QTParted for shrinking my Windows (FAT32 filesystem). I have no data in it (test computer), but most people will need to remove a lot of data and defrag first. You'll still have all your files and settings and software, just remove music and pictures maybe, copy to CDs to put in again later on. I don't know anything about shrinking and re-sizing NTFS filesystems. Do at your own risk. (Everything is at your own risk-even waking up in the morning!). I shrunk my Windows down to 5.0 GB. Make a note of which side of Ubuntu your swap is on. If you want to delete your swap later on, make a new swap before finishing the same side as the old swap used to be. (eg, on the Windows side of Ubuntu, or on the opposite side).
2. I inserted a Ubuntu install CD and re-started my computer.
3. Carry on as if intending to perform a new install until '[!!] partition disks' is reached, then choose 'Manually edit partition table'.
4. Select the 1.0 GB swap partition first if it is on the Windows side of Ubuntu, and delete the partition,  to make even more room.
5. I Selected  my 20 GB free space, and pressed 'enter'
6. I chose: 'create a new partition', and typed in 5.0 GB for my new partition's size. I'm making mine 'primary', but it probably doesn't matter. Location for the new partition: beginning of the available space.
7. 'You are editing partition #3 (or some other number) sign appears, I choose 'copy data from another partition, and press 'enter'. Then 'Yes' on the confirmation panel, which appears next.
8. A new panel appears and asks me to choose which partition I want to copy the data from. I choose my old Ubuntu partition.
 'please wait... creating ext3 file system for partition #3 progress bar'.
 A progress bar 'copying partition' will display for quite some time. (5 or ten minutes or so).
9. A new 'editing partition #3' (or whatever number) sign is shown when the data transfer is complete.
 It shows the following details: 'file system:ext3,'Format the partition?':  yes, format it, mount point / ,options: defaults, bootable: off, size: 5.0 GB, 
Important: Change 'Format the partition' to: 'no, keep existing data.', then select  'done setting up the partition'..
10. On the partition table panel, which shows next, I pick 'finish partitioning and write changes to disk', then 'yes' for the confirmation panel.
11.'You have not made a swap area' sign might appear if you deleted your swap already, like I did.  Ignore it and press No, (continue without one).
10. Red warning screen 'Not installing to unclean target' (continue). (Don't be scared).
11. Red warning screen 'Installation step failed' (continue). (Don't worry about it).
12. In the Ubuntu Installer main menu again, scroll down to 'abort the installation'. (you must  re-boot to make the partitioner 'unmount' the newly created temporary partition, it wants to do a new clean install on it, and will reformat it and erase everything  pretty darn quck if you try to continue without re-booting).
13.'Your system may be left in an unusable state', exit anyway.('Yes').

14. Re-boot with the install CD once again, repeat all the preliminary questions and progress bars.
15. When you get to [!!] partition disks again, choose 'manually edit partition table', again.
16.select old 5.0 GB Ubuntu partition, and delete the partition.
17. select 20.0 GB free space,How to use this free space: create a new partition. New partition size: 19.0 GB,  partition type: primary (depending on your situation)
location for the partition:  the end of the free space. (this depends on where the swap area used to be before, if it is still on the other side, you wouldn't have needed to delete it like I did to mine earlier, but since mine was between Windows and Ubuntu, I was able to get an extra GB of free space by deleting the swap temporarily, and need to leave room for it to go back in again now.
18. 'You are editing partition#2 (or whatever number) no existing file system....', Choose 'copy data from another partition again, and: 'Yes', write changes to disk in the confirmation screen.
19 Choose your temporary 5.0 GB partition to copy the data from.
20. please wait... creating ext3 file system for partition #2 (progress bar).
21 Please wait... copying partition progress bar, (for another five or ten minutes... )
22. A new 'editing partition #2' (or whatever number) sign is shown when the data transfer is complete.
 It shows the following details: 'file system:ext3,'Format the partition?':  yes, format it, mount point / ,options: defaults, bootable: off, size: 5.0 GB.
Important: Change 'Format the partition' to: 'no, keep existing data.',
 then, change the 'bootable flag: from 'off' to 'on', and then, 'done setting up the partition'..
23. select the remaining 1.0 GB free space, 'create a new partition', new partition size: (leave as 1.0 GB), 'partition type': logical, Use as: swap area.
24. 'You are editing partition #5...' choose 'done setting up the partition'.
25.The new partition table shows all the partitions again, select your temporary partition, and 'delete the partition'.
26. Check the partition table again, if it all looks okay, then 'finish partitioning and write changes to disk. ('Yes' on the confirmation screen too).
27.  Red warning screen 'Not installing to unclean target' (continue), ( it's okay, really!).
28. Red warning screen 'Installation step failed' (continue) ( Be brave).
29.In the Ubuntu Installer main menu again, scroll down to 'abort the installation'.
30.'Your system may be left in an unusable state', exit anyway.('Yes').
31. Very quicky remove your Ubuntu install CD before it has time to re-boot. 
32. It should,(unless you hold it by pressing your 'pause' key), reboot into Ubuntu. (Mine did!)  Hooray!!!
33. After checking to be sure all is well, you may at some future time, at your leisure, do something with the remaining 5.0 GB 'free space, such as creating a FAT32 logical for sharing, or simply (in my case) expand Windows back with QTParted to fill the gap.
> 

---

