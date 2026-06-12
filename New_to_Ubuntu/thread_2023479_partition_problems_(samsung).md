---
title: "partition problems (samsung)"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by interkin3tic on 2012-07-12
Hi, I'm running windows 7 (64 bit) on a samsung laptop and am having issues with partitions.

I tried installing from the CD.  No option to install side-by-side came up, unlike the instructions, only run within windows (wubi, which I'm not interested in), install only ubuntu, and advanced.

I went to advanced and had little clue as to what I was doing, but there were four partitions in use and showed no "free" space.  The largest one has 75 gb free, but I was unable to figure out how to set aside 20 gb and install ubuntu without erasing the whole partition (D/ in windows, sdev4?)

I shrank the large partition by 20gb in windows and tried installing there, however the installation program says that's unusable, and won't install there.

I'm aware that dynamic vs basic can be an issue, how would I check if my hard drive is setup as "dynamic?"  How would I change it back to basic if this is the problem?

If I need to expand sdev4 again, will I need to repartition it and erase everything on that partition?

---

### Post by oldfred on 2012-07-12
Most new Windows 7 systems use all 4 primary partitions. Post this to see info on partitions from terminal on liveCD:

sudo fdisk -lu

---

### Post by interkin3tic on 2012-07-12
But I'll still have all four partitions in use.  How do I deal with that?

---

### Post by interkin3tic on 2012-07-12
I have 15 gb allocated to a recovery partition, 100mb for system, 100gb for C, and 350 for D.  

The recovery partition says it has 100% free space, which seems odd.

Am I safe in deleting the recovery partition (I have made a windows repair disc) and using that 15 gb partition for ubuntu?

---

### Post by OM55 on 2012-07-12
Hello interkin3tic,

As oldfred mentioned, many of the new systems will use all 4 primary partitions and in essence prevent adding any new partitions. So the Ubuntu Installer did not offer a "side-by-side" option (dual boot) simply because it cannot create a 5th primary partition.

There are several solutions to this situation but I think the most practical and fast solution would be to delete your "recovery" partition. This partition is usually prepared by the computer manufacturer and is used to restore the hard disk to the initial factory setting. However, you can definitely use a different method to do that (I describe it below) and you can even back up this "recovery" partition and possibly restore it in the future, if you really need it.

I recommend using GParted Live in combination with Image for Linux. 
GParted Live This is the "Live" (CD or USB key) version of GParted. You can get it at:
 [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

Image for Linux is a very good image backup program, which you can get at: 
[http://www.terabyteunlimited.com/image-for-linux.htm](http://www.terabyteunlimited.com/image-for-linux.htm)

I recommend to use the CUI-Network (Console User Interface with network support) version and not the GUI (Graphic User Interface) because it is much faster, clear and easy to follow. both CUI and GUI have versions with and without network support, but having the network support gives you the option of backing up/restoring from a network drive as well.

To get ready for this "computer surgery", first prepare each of the above programs on a bootable CD or a bootable USB key (explanations on how to do that are included in each website and there are many postings in this forum with instructions).

Once you burned them to a bootable CD or a bootable USB media, you can boot either one to take the desired action:

- If you want to image backup (or image restore) the entire computer, or just the one of the partition, boot your computer using Image for Linux and follow the instructions. In almost all screens the option you need to select is the suggested default. But only in one screen you may want to change the selection - the question about "OS Direct", switch it to "File direct" (I don't remember the exact wording, but you will see what I mean when you get to that screen).

- If you want to remove or resize partisions, just boot your computer using GParted Live. It is a graphic environment and very easy to select, delete or resize a partition. Your changes will take effect after you "save". Delete action will be very quick but resizing may take time, depends on the size of the partition.

So to sum it up, you can:
1. Use Image for Linux to backup the "recovery" partition to an external USB or network drive, then 

2. Use GParted Live to delete that "recovery" partition and possibly resize the adjacent partition to allow more unused disk space for Ubuntu (it has to be the adjacent partition because partition space has to be continues). 

3. Boot using Ubuntu Live and install Ubuntu. Now the installer will have the ability to suggest a "side-by-side" installation - and you are good to go.

Hope that helps!

---

### Post by oldfred on 2012-07-12
Some good info from om55.

A few links with additional info:
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by Mark Phelps on 2012-07-14
> **interkin3tic said:**
> ... 
Am I safe in deleting the recovery partition (I have made a windows repair disc) and using that 15 gb partition for ubuntu?

Absolutely ... NOT!

The only thing a repair disk will do is let you boot into WinRE in order to restore Boot Loader files;  it is NOT a factory restore disk.

A better solution (that I have used for years) is to do the following:
1) Download and install the free version of Macrium Reflect in your Win7 setup
2) Hook up an external drive and image off your Win7 setup (OS partition and the System Reserved partition)
3) Use the option to create a Linux Boot CD.

NOW ... you have the means to restore Win7 to the state it was in when you made your backup.  You no longer need the Recovery partition -- so you can safely delete it.

---

