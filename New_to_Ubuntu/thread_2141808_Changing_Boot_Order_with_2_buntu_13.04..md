---
title: "Changing Boot Order with 2 *buntu 13.04."
date: 2013-05-03
forum: New to Ubuntu
---

### Post by jmate24 on 2013-05-03
I have 2 *buntu installations on one disk. Ubuntu 13.04 was installed first and the second that was installed after is Lubuntu 13.04
I would like to kill Lubuntu (wipe it) and have Ubuntu as my only OS. Because I am getting an 128 GB SSD and am going to try both Windows 7 XD and then Ubuntu 13.04 :D.
How do I change the boot order in Ubuntu 13.04 using the command:

```
sudo update-grub
```

So that I will boot to Ubuntu instead of Lubuntu? So that if I like Ubuntu better than Windows on the SSD then I will try and shrink down and move the Ubuntu partitions (just the /home folder I doubt it will work with the / partition) so that I can dd (copy) the Ubuntu Install from the 1 TB platter HDD to the 128 GB SSD.
I know that I will have to backup my data and I have a hard drive to do so. There is about 110 GB of data on my home partition that I have to save and I would like to save the / partition if at all possible so that I do not have to reinstall. 

But if there is a way to put the / partition and the swap on the 128 GB SSD and have the /home partition stay on the 1 TB HDD with out having to reinstall I would like to know. And I know that it would help others to know this as well.

P.S.

Please do not make it verry complicated.

---

### Post by oldfred on 2013-05-03
Boot into Ubuntu and run this to put Ubuntu's grub2 boot loader into the MBR.

 sudo grub-install /dev/sda
sudo update-grub

If you use dd you have to do major changes as you also copy UUID. You cannot have duplicate UUID mounted on same system, so you have to change UUID, reinstall grub, and edit fstab. 
dd is also not the fastest way to copy as it also copies empty space.

I would move /home on hard drive to a separate partition or my preferred solution move all data to a separate partition. And then do a full install in the SSD, using existing /home or mount all you data using links or bind into /home. All you user settings are in /home so you can easily copy into new /home or if using old /home you will automatically have them.

      
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]https://help.ubuntu.com/community/Partitioning/Home/Moving

[/URL] Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]
[/URL]

---

### Post by fantab on 2013-05-03
In the above post#2, oldfred, has pretty much answered all your questions...However,

If you are open to reinstalling then I'd suggest go for it after you get your SSD. This will be cleaner and simpler way of doing things. Ubuntu WILL run better than Windows. If you are planning to Dual-Boot Windows & Ubuntu, then I suggest you install both on SSD and Keep your DATA on HDD. Don't go for separate /home partition for Ubuntu instead create a simple Linux partiton ext4, or if you like to share your DATA between Windows and Ubuntu then NTFS partition. 

Here's what I suggest:
_SSD 128GB_:
Windows Partition on SSD about 75GB
Ubuntu partition on SSD with "/" of about 25GB (This will be plenty for Ubuntu minus DATA)
Linux partition ext4 on SSD of about 25GB (leave it free for now, if you want to install another Ubuntu versio or another Distro then this will come in handy).

_HDD 1TB_:
4GB SWAP (If you like to "Hibernate" your computer then the SWAP size should be equal to or greater than your RAM in GiB, not GB).

Either:
1TB minus SWAP NTFS partition to share DATA between Windows and Linux

Or:

1TB minux SWAP ext4 Linux partition to keep your DATA for Linux only

Or:
TWO partitions, one NTFS and another ext4.

---

### Post by oldfred on 2013-05-03
+1 on fantab's suggestions.

One more suggestion, if you want to have another way to boot. I like to have an operating system on every drive, even one that really is just a data drive. That way if one drive fails you have another way to boot. 

Ubuntu needs a bit more space (10 to 25GB) than Knoppix but since I know Ubuntu I install it one every drive. But I really like this bloggers reasons.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

