---
title: "Two Hard Drives, what now.......?"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by RickFAA on 2013-03-05
I had 8.04LTS from April 2008 till 2 weeks ago.  Did a upgrade(?) to 12.04LTS.
This was easy and worked great!  
Have 2 hard drives – (Not Windows!)
            One with 37GB (/ , boot,  Extended(1.8M), Swap(1.8M))
            One with 250GB (Extended(1GB), Swap(1GB), unallocated(228GB))

Q1:	Why/how do I have 2 swap(s) ?
Q2:	Would like to add each swap (if I need both!) to 2GB.  Easy?
Q3:	Could the 250GB be unallocated first, extended next and swap last?
            (Or leave let there?)
Q4:	Would like to move(?) /home from the 37GB to a partition in the 250GB?
	With a extra partition for /data.
Q5:	Don't no what is in the 250GB extended – (194Mb of ????).  Is it 'right' to
	'format' the  drive first?  (My Ubuntu OS and boot is in the 37GB)

Thanks!
RickFAA

---

### Post by tgalati4 on 2013-03-05
Q1 One swap could have been created under 8.04 and the second under 12.04.  Run the *free* command in a terminal to see how much swap is really detected.
Q2 You can keep both swaps (if they are shown in free) or delete one and increase the other to 2GB.
Q3 Can't answer.  Don't know what is on that 1st (1GB) partition.
Q4 You can leave home where it is and create a symbolic link to point to your second drive, after you format/partition/arrange it the way you want.
Q5 Depends on Q3.  Boot up and explore the second drive and see what is on it.

---

### Post by fantab on 2013-03-06
> **RickFAA said:**
> 
Q1:    Why/how do I have 2 swap(s) ?
Q2:    Would like to add each swap (if I need both!) to 2GB.  Easy?
Q3:    Could the 250GB be unallocated first, extended next and swap last?
            (Or leave let there?)
Q4:    Would like to move(?) /home from the 37GB to a partition in the 250GB?
    With a extra partition for /data.
Q5:    Don't no what is in the 250GB extended &#8211; (194Mb of ????).  Is it 'right' to
    'format' the  drive first?  (My Ubuntu OS and boot is in the 37GB)

If I were you, I would start fresh. I would format both the Hard Drives clean (after BACKING UP all the important DATA) with Gparted provided in the Ubuntu LiveCD/USB. I would Delete all the partitions and re-create them **as I want them**, for instance:
/dev/sda1 : 16 GB Primary "/" 
/dev/sda2 : 16 GB Primary "Free" (In case in future I want to install another Verison of Ubuntu or another Distro)
/dev/sda2 : remaining GB for SWAP

/dev/sdb1 : 200 GB Primary "/home" (or "Linux Ext4 without any mountpoint)
/dev/sdb2 : 50 GB Primary Linux_Ext4.

When Installing Ubuntu I would, rather than use 'automatic' disk management, I'd use "Something Else" option to manually select Ubuntu install targets. I like to keep things simple.

You must also, seriously consider using LVM file system since you are using only Linux. Follow the links below to learn more:
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[http://ubuntuforums.org/showthread.php?t=1782296](http://ubuntuforums.org/showthread.php?t=1782296)
[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

---

