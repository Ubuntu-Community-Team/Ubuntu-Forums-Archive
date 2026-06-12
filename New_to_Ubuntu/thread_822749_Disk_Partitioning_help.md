---
title: "Disk Partitioning help"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Moozikku25 on 2008-06-08
Hey guys,

I am very new.  I came across this distro due to much praise about it and that my Windows XP has some unknown stutter problem.  So, please bare with me as I have questions with Disk Partitioning.

Here are my specs:
Dell Inspiron 1300 Laptop
Windows XP Home Edition
40GB HD
1GB RAM
1.5GHz Intel Celeron M

Right now, I am using the LiveCD desktop version.  I tried installing Ubuntu.  I was at the Partitioning part.  I resized the Windows XP and Ubuntu partition using the guided partioning and went through with it. I could not complete the setup process, and canceled right before doing the password/login step, due to time.  When I looked at Windows XP: C Drive I had a about 10GB chopped off have read through the the noobie guides for the disk partitioning. My windows XP now, has a hard drive space of 26.9GB, If I recall correctly. Please look at the screenshot below and help me delete and/or move partitions around.

[[IMG]http://img296.imageshack.us/img296/2710/diskpartitionix7.th.jpg[/IMG]](http://img296.imageshack.us/my.php?image=diskpartitionix7.jpg)

*edit*
Okay it's now up.

So according to the image, both the fat 16 and fat 32 are unmounted. With allocated space.  I seriously don't know if fat 32 is ubuntu's partition? I don't know whats up with the fat 16.  But the ntfs /dev/sda2 is windows xp partition.

Hopefully you guys can help.  Thanks!

---

### Post by mevets on 2008-06-08
to restore your partitions to the way they were in the beginning do the following. boot to the livecd again. dont start the install but instead go to system > administration > partition editor. then delete the small 10gb patition. then expand the windows partition.

---

### Post by Stefanie on 2008-06-08
the first fat16 partition is your Dell utility partition - i have a dell notebook and i have a similar partition. i did not delete it, it may come in useful when you have hardware problems. 

so what i would tho is this: resize the ntfs partition (= windows) to something like 20 GB (right-click the partition, select resize and then drag the right border to the left). This way you'll have 15GB of unallocated space to install ubuntu on. make sure you run the disk defragmenter tool a few times in windows xp before reszing the partition.

after doing the resizing you can use the ubuntu installer, make sure you select "use largest continuous free space" and the new partitions should be created automatically without overwriting your windows, i think - i'm quite new myself so maybe it's better to wait for others to confirm this. (you can find more information on this page: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) ) 

this fat 32 partition, i don't know what it is but it's not ubuntu AFAIK. when you go to places -> computer using the live cd, can you browse the 3.40 GB partition and see what files are in it? If it's a backup partition or something like that you'll probably want to it move to the right get rid of the 7.5 MB of unallocated space.

---

### Post by Moozikku25 on 2008-06-08
> **Stefanie said:**
> the first fat16 partition is your Dell utility partition - i have a dell notebook and i have a similar partition. i did not delete it, it may come in useful when you have hardware problems. 

so what i would tho is this: resize the ntfs partition (= windows) to something like 20 GB (right-click the partition, select resize and then drag the right border to the left). This way you'll have 15GB of unallocated space to install ubuntu on. make sure you run the disk defragmenter tool a few times in windows xp before reszing the partition.

after doing the resizing you can use the ubuntu installer, make sure you select "use largest continuous free space" and the new partitions should be created automatically without overwriting your windows, i think - i'm quite new myself so maybe it's better to wait for others to confirm this. (you can find more information on this page: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) ) 

this fat 32 partition, i don't know what it is but it's not ubuntu AFAIK. when you go to places -> computer using the live cd, can you browse the 3.40 GB partition and see what files are in it? If it's a backup partition or something like that you'll probably want to it move to the right get rid of the 7.5 MB of unallocated space.

Thanks for helping me out, I was about to delete the fat16 partition.  Unfortunately, I don't know what the fat32 partition is.  I went to Places>Computers>Filesystem>dev.  Tried to find sda3, but there was no such thing.  I don't know how to look through it.

*edit*
Well, I went ahead and deleted it, I don't know if it affected any of the windows partition. It could've been a back up of some sort.  But I don't mind because I transfered most of my important files into my iPod.  Anyways, thanks Stefanie and mevet for your help.  If you and/or anyone else has anymore info regarding this topic, please do.

---

### Post by housam on 2008-06-08
Till now you don't have any partitions for ubuntu. If you want to install ubuntu ,just boot from the live cd and open the partition editor as you did in the image you posted. then grab windows partition a little to give ubuntu more space than the 7 GB at the unallocated space.let say 4 GB more.
so we have now 11 GB unallocated space.we need to create 2 new partitions for ubuntu : 10 GB for the root ( / ) ext format. and 1 GB for the swap.
after that commence the installation and when it comes to the partitioning , choose the manual way and assign the root partition manually with the sign (/).

Edit :
After you deleted the Fat32 partition , you don't have to resize the windows partition any more . you just have now about the 11 GB of space needed to create the 2 partitions for ubuntu

---

