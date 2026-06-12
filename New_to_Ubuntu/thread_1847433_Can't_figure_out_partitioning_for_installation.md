---
title: "Can't figure out partitioning for installation"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by pianoporsche on 2011-09-20
I'm trying to install Ubuntu 11.04 from a CD onto an HP dv6 and can't figure out how to deal with partitioning. A lot of the guides I'm seeing are talking about resizing the Windows partition, but I can't find anything on which partition that would be. The screen in the installation guide gives me this info:

/dev/sda1  ntfs   208 MB (69 MB used)
/dev/sda2  ntfs   624079 MB (30270 MB used)
/dev/sda3  ntfs   15735 MB (13983 MB used)
/dev/sda4  fat32 108 MB (33 MB used)

I have a general grasp on the concept of partitioning the drive to have a Windows partition, an Ubuntu partition, the home partition, and the swap, but I have no idea how to change what I have to that setup. I also saw something about another partition that stores your Ubuntu settings so you can try upgrading without losing your settings, but I'm fuzzy on that as well.

Thank you in advance for your help. I greatly appreciate it.

---

### Post by coffeecat on 2011-09-20
First thing to say is that with a HP machine, they have used up your maximum allowance of four primary partitions, which means that you have to delete one before you can create an extended partition (which is a special type of primary) in which you can create a number of logical partitions. You shouldn't delete either of partition 1 or 2 both of which are needed for Windows to run.

So that I don't have to type all this out again :wink: here are a couple of posts I've made about which of the other two partitions you can delete and what you need to do first. There's some information relevant to the threads they come from and which you don't need, but they should give you an overview.

[http://ubuntuforums.org/showpost.php?p=11214572&postcount=3](http://ubuntuforums.org/showpost.php?p=11214572&postcount=3)

[http://ubuntuforums.org/showpost.php?p=11025958&postcount=11](http://ubuntuforums.org/showpost.php?p=11025958&postcount=11)

Once you've deleted either or both of partitions 3 and 4, the installer will be able to install to the unformatted space, or you can set up a custom partition layout yourself, and someone will be able to help you with that.

**EDIT**: also - sorry to burden you with reading material, but you will find this useful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Read all the links in it. It will give you a good grasp of partitioning basics and give you more confidence with the installer.

---

### Post by pianoporsche on 2011-09-20
Excellent! Thank you very much for all of that. I definitely understand this partitioning business better. I might try a custom scheme sometime down the road, but I think I'll go with the installer's "side by side" method for now.

And hey, I'd rather have an overabundance of info than a lack of it.

Thanks for the help!

---

### Post by coffeecat on 2011-09-21
Good luck with that. Before you install you might want to search the forum for threads about HP DV6 machines. Some people seem to have trouble with them but because there are variants with different hardware configurations, what one user gets may not be relevant to another. I couldn't ask for better Ubuntu compatibility than with my HP Mini, but I've noticed several threads about the DV6.

---

