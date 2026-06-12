---
title: "Hard Disk Problem"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by sxytrillian on 2008-06-14
I can't able to view any partitions of my hard disk after installing Ubuntu 8.04.

And in the system menu under administration i can't able to see the option Disk.

so please help me out how to solve this..

---

### Post by FAJALOU on 2008-06-14
You can get into Ubuntu correctly though correct?  What parition are you trying to see, your Windows paritions? or something else?

---

### Post by sxytrillian on 2008-06-14
i didn't install windows. i have freshly installed ubuntu on my 250gb hard disk. now the problem is its not showing any of the partition of my hard disk.

---

### Post by FAJALOU on 2008-06-14
Try installing gparted, normally it is reliable for showing paritions on a harddrive.   After that, you can manually mount the HDD, but one step at a time ;)  ```
sudo apt-get install gparted
``` Should do the trick.  When that is done open it up in System>Administration>Partition Editor.  Can you see the partitions from here?

---

### Post by sxytrillian on 2008-06-14
i got it .

in that its showing unallocated 200 gb.

how can i allocate it to store my files.

i need 2 partitions each 100gb

how can i do that?

please help me..

if i right click that its showing new in that its showing primary partition or extended partition how i want to configure that?

and in file sytem its showing ext2,ext3,fat16,fat32,linuxswap,reiserfs,unformatted in this which one i need to choose.

please guide me.

---

### Post by FAJALOU on 2008-06-14
alrightee cool you are half way there.

Do you have a live cd?  Because the best place to partition is in a live cd environment.  

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

this is a really good tutorial to bring you through all of the steps to do what you want.  After you partition your 200 GB to 100 GB each, you want to format them to ext3 to store your data for ubuntu.  The tutorial does well.  Feel free to write with questions, and AIM works too.  Good luck!

---

### Post by sxytrillian on 2008-06-14
ya i have an Ubuntu live Cd what i want to do with it?

---

### Post by sxytrillian on 2008-06-14
which file system i want to choose for storing video,mp3 files?

---

### Post by FAJALOU on 2008-06-14
you will probably want ext3. Thats what Ubuntu uses.  You should go into the live cd and use it to partition your HDD.  Because partitioning from inside Ubuntu , you could come up with issues.

---

### Post by bluepowder7 on 2008-06-14
personally, i prefer JFS or XFS since they don't waste as much space as ext2 / ext3.  and JFS doesn't seem to need the fsck crap.

---

### Post by impert on 2008-06-14
> Ext3 or third extended filesystem is a journaled file system

From the Wikipedia article "Ext3"

---

