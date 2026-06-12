---
title: "[SOLVED] How to read linux xfs partition from windows?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by bhadotia on 2008-08-21
I tried googling for the answer to the above question and came acroos many tutorials that showed how to install tools on windows so that linux filesystem partitions,  such as ext2/3/4 and rieserfs can be accessed from windows. But no tutorial on how to do it with xfs without installing a linux virtual machine on windows. The thing is I use windows only for a few spwcific purposes and have only a 9.5 GB partition (the only NTFS partition on my machine) allocated to it. So that I cannot afford to install a linux virt machine because that would waste valuable disk space and is redundant.
Many articles said that support for xfs on windows was non-existent and many others pointed to a site link ([www.crossmeta.com](www.crossmeta.com))  which has expired. The link they said had windows drivers that enabled xfs r/w support.

So can anyone help me in this regard.

Many thanks in advance.

---

### Post by Znupi on 2008-08-21
You searched the wrong thing :-). I searched for "ext3 driver windows" and came across [http://www.fs-driver.org/](http://www.fs-driver.org/) . I've been using it ever since and it works like a treat :-) Good luck!

---

### Post by philinux on 2008-08-21
[http://polishlinux.org/linux/ext3-reiserfs-xfs-in-windows-thanks-to-colinux/](http://polishlinux.org/linux/ext3-reiserfs-xfs-in-windows-thanks-to-colinux/)

If I were in the same position I'd use ext3 on Linux and use the fs-driver in windows to read it.

---

### Post by bhadotia on 2008-08-21
> **Znupi said:**
> You searched the wrong thing :-). I searched for "ext3 driver windows" and came across [http://www.fs-driver.org/](http://www.fs-driver.org/) . I've been using it ever since and it works like a treat :-) Good luck!
Actually I did searched the right thing. The link you gave contains drivers for the ext2/3 and not xfs. I think I mentioned in the original post also that I had come acroos many such tools and drivers for the ext2/3/4 and rieserfs but none for the xfs.

---

### Post by bhadotia on 2008-08-21
> **philinux said:**
> [http://polishlinux.org/linux/ext3-reiserfs-xfs-in-windows-thanks-to-colinux/](http://polishlinux.org/linux/ext3-reiserfs-xfs-in-windows-thanks-to-colinux/)

If I were in the same position I'd use ext3 on Linux and use the fs-driver in windows to read it.
I have already come across that. I told you that I cannot afford to install a virtual machine on windows.

---

### Post by philinux on 2008-08-21
I think the answer is there is not a way to read xfs from windows.

Unless someone else has an answer.

Could you shrink another partition and give windows just enough to run a vm?

---

### Post by bhadotia on 2008-08-21
> **philinux said:**
> I think the answer is there is not a way to read xfs from windows.

Unless someone else has an answer.

Could you shrink another partition and give windows just enough to run a vm?
I could not do that (though I tried). My partitioning scheme does not permit me to do that.
Here is what my fdisk -l gives:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000837a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1276    10249438+   7  HPFS/NTFS
/dev/sda2            5110        9729    37110150   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3            1277        1312      289170   83  Linux
/dev/sda4            1313        5109    30499402+  8e  Linux LVM

```
I have also  attached a screen-shot of the gparted window.
The problem is self evident: I cannot just shrink my /boot which is already some 200 MB.

---

### Post by philinux on 2008-08-21
Ok just get gparted, from the live cd, to shrink your data partition by 1 to 2 gig, whatever a vm needs and expand your windows partition by the same amount. 

Backup first and you're good to go. 

Or back up your data partition as it's only using 3 gig and reformat to ext3 then problem solved. Unless your mad keen on xfs.

Whats on sda4?

---

### Post by Znupi on 2008-08-21
Is there some specific reason for using xfs instead of ext3? I think the best thing you could do is to reformat /dev/sda2 to ext3 (or /dev/sda4, if you can) and use that. You can do it in two steps to keep your data (resize and create a new ext3 partition, move the data to the new partition, delete the old partition and expand the new one).

---

### Post by bhadotia on 2008-08-22
> **philinux said:**
> Ok just get gparted, from the live cd, to shrink your data partition by 1 to 2 gig, whatever a vm needs and expand your windows partition by the same amount. 
 
Backup first and you're good to go. 
 
Or back up your data partition as it's only using 3 gig and reformat to ext3 then problem solved. Unless your mad keen on xfs.
 
Whats on sda4?
/dev/sda4 is the partiton for the lvm. It contains my logical volumes for the / , /home , and swap.
 
I was trying to avoid not using xfs (or trying to avoid using est3) because I read somwhere that xfs is the highest performing filesystem around. Well I guess I'll have to copy all my /data to my /home and then reformat it to ext3 and also give some 5 or 6 gigs more to wiindows.
Thanks for the help guys.
 
I would be interested in your opinions regarding the different filesystems.
Also some guidance on resolving the ownership issues once I have access to the linux partition from windows would be great. I can use google but some practical advice would be good.

---

### Post by Archmage on 2008-08-22
Unfortunatly the Microsoft devloper are not able to make a XFS driver, therefore you can't read XFS under Windows.

However you can read and write NTFS under Linux.

---

### Post by philinux on 2008-08-22
As Mr.Spock would say, fascinating. :lolflag:

[http://en.wikipedia.org/wiki/File_system#Further_reading](http://en.wikipedia.org/wiki/File_system#Further_reading)
[http://www.osnews.com/story/69](http://www.osnews.com/story/69)
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

Extract from the last link.
> OVERALL CONCLUSION

These results replicate previous observations from Piszcz (2006) about reduced disk capacity of Ext3, longer mount time of ReiserFS and longer FS creation of Ext3. Moreover, like this report, both reviews have observed that JFS is the lowest CPU-usage FS. Finally, this report appeared to be the first to show the high page faults activity of ReiserFS on most usual file operations.

While recognizing the relative merits of each filesystem, only one filesystem can be install for each partition/disk. Based on all testing done for this benchmark essay, **XFS appears to be the most appropriate filesystem to install on a file server for home or small-business needs** :

    * It uses the maximum capacity of your server hard disk(s)
    * It is the quickest FS to create, mount and unmount
    * It is the quickest FS for operations on large files (>500MB)
    * This FS gets a good second place for operations on a large number of small to moderate-size files and directories
    * It constitutes a good CPU vs time compromise for large directory listing or file search
    * It is not the least CPU demanding FS but its use of system ressources is quite acceptable for older generation hardware 

While Piszcz (2006) did not explicitly recommand XFS, he concludes that "Personally, I still choose XFS for filesystem performance and scalability". I can only support this conclusion. 

---

### Post by Znupi on 2008-08-22
> **bhadotia said:**
> Also some guidance on resolving the ownership issues once I have access to the linux partition from windows would be great. I can use google but some practical advice would be good.

What ownership issues? From windows you can read/write any file on the Linux partition, no matter what Linux user it belongs to. I hope I got your question right.

---

### Post by bhadotia on 2008-08-22
> **philinux said:**
> As Mr.Spock would say, fascinating. :lolflag:

.
Whose Mr. Spock?

---

### Post by Archmage on 2008-08-22
> **bhadotia said:**
> Whose Mr. Spock?

[IMG]http://upload.wikimedia.org/wikipedia/en/4/4c/SpockVulcan.jpg[/IMG]

---

### Post by bhadotia on 2008-08-22
Guys , I have a problem I have reformatted the /data to ext3 and shrunk it by 5 gigs. But I'm unable to expand /windows. I got the ntfs progs , so thats not the problem. But the thing is that when I select the resize option the only operation I am able to perform is shrinking(screen-shot). /windows is /dev/sda1 and /data is sda2 so I should be able to expand sda1 after shrinking sda2 (isn't it?).

Any idea on whats wrong or what am I doing wrong?

Also if I'm able to install programs on sda2 in windows after installing the drivers then I'm good even if sda1 cannot be expanded. So, Znupi please confirm if I can do that.

---

### Post by Znupi on 2008-08-22
The reason why you can't enlarge your Windows partition is because you have to move all the other partitions to the right before enlarging it, but I don't recommend that.

Well, I never tried installing programs, but since you have read and write support, I don't see why it wouldn't work. The partition appears in My Computer just as any other partition :).

---

### Post by bodhi.zazen on 2008-08-22
Side track : performance on so called benchmarks are not the best way to select a file system. Other considerations include features on the file system and, as in your case, compatibility with other OS.

Keep in mind benchmarks are quite artificial. I mean, how often is it that a desktop user creates then deletes 10,000 files ?

Personally I have tried all the file systems and do not see much difference in day to day speed or performance.

See also :

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939) 

[http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

---

### Post by bhadotia on 2008-08-22
> **Znupi said:**
> Well, I never tried installing programs, but since you have read and write support, I don't see why it wouldn't work. The partition appears in My Computer just as any other partition :).

All the programs I installed were successful excet for jre which generated an install error (something regarding update patch) but that also nevertheless installed.


Thanks for the links bodhi. They look quite educative I'll go through them when I get the time.

---

### Post by agnitio on 2009-05-08
apparently has drivers I downloaded them, I however do not have a spare drive to install xp for a test yet
[http://www.driver-fix.com/driverdetective.php?t=Windows%20Xfs%20Driver](http://www.driver-fix.com/driverdetective.php?t=Windows%20Xfs%20Driver)

---

### Post by bhadotia on 2009-05-29
> **agnitio said:**
> apparently has drivers I downloaded them, I however do not have a spare drive to install xp for a test yet
[http://www.driver-fix.com/driverdetective.php?t=Windows%20Xfs%20Driver](http://www.driver-fix.com/driverdetective.php?t=Windows%20Xfs%20Driver)

Thanks for the info agnitio.

Although I am using only ext3/4 now, I don't think that the program will be able to find drivers for the xfs. We'll just have to wait for someone using windows along with linux (on xfs) to confirm this.

---

### Post by jbizcocho on 2010-02-04
> **bhadotia said:**
> Thanks for the info agnitio.

Although I am using only ext3/4 now, I don't think that the program will be able to find drivers for the xfs. We'll just have to wait for someone using windows along with linux (on xfs) to confirm this.

I came across this thread and was curious to know if you ever found a suitable XFS driver for windows.  I use probably the same linkstation device you have.  It is a great device but I didn't want to think about windows recovery options when and if it fails.  I looked at the driver detective thing but the website seems a bit... cheap commercial, think "but that's not all." so I wanted to know before I installed something on my system I'd have to remove from Linux to get off.
Thanks

---

### Post by ingva2r on 2012-09-10
> **bhadotia said:**
> I tried googling for the answer to the above question and came acroos many tutorials that showed how to install tools on windows so that linux filesystem partitions,  such as ext2/3/4 and rieserfs can be accessed from windows. But no tutorial on how to do it with xfs without installing a linux virtual machine on windows. The thing is I use windows only for a few spwcific purposes and have only a 9.5 GB partition (the only NTFS partition on my machine) allocated to it. So that I cannot afford to install a linux virt machine because that would waste valuable disk space and is redundant.
Many articles said that support for xfs on windows was non-existent and many others pointed to a site link ([www.crossmeta.com](www.crossmeta.com))  which has expired. The link they said had windows drivers that enabled xfs r/w support.

So can anyone help me in this regard.

Many thanks in advance.
Maybe its will be of use for anybody:
You could use colinux for it - it allows to run linux kernel on windows machine thus have native support of XFS

---

