---
title: "More disck space to Ubuntu."
date: 2012-07-25
forum: New to Ubuntu
---

### Post by Sarys on 2012-07-25
So I have dual booted win 7 (92bg) and Ubuntu (25gb) but I still have 100 gb NTFS partition unused. Reason for that I that user called Winux(user?) told me to do so. He said I should use that to share data between Win and Linux but laiter he said I should use it as backup. (I don't think it's good idea to backup data to the same drive) So I thouhg that maybe I should get rid of it. So I want to give most of that data to Linux. (or at least some of it) But not sure how to do that without harming anything. And should I give the data to root or home?

---

### Post by ikt on 2012-07-25
> **Sarys said:**
> So I have dual booted win 7 (92bg) and Ubuntu (25gb) but I still have 100 gb NTFS partition unused. Reason for that I that user called Winux(user?) told me to do so. He said I should use that to share data between Win and Linux but laiter he said I should use it as backup.

If you dual boot with windows you'll want the NTFS drive there so you can access the data from within windows. If you don't dual boot windows then yeah, just pop in a live cd and run gparted and delete the NTFS partition and stretch the linux partition out.

---

### Post by Sarys on 2012-07-25
> **ikt said:**
> If you dual boot with windows you'll want the NTFS drive there so you can access the data from within windows. If you don't dual boot windows then yeah, just pop in a live cd and run gparted and delete the NTFS partition and stretch the linux partition out.

You mean if I have two windows os then delete? Since I find that confusing.

---

### Post by NikTh on 2012-07-25
Hi , 
its better to give space in your /home partition , as in home you store big files usually. 
you must reformat 100GB Ntfs patition (of course you will lose everything you have there) to ext4 "filesystem with journal". 

The safe way is to add later an entry to /etc/fstab and mount permanently this new formatted partition , so you can store thing there. 
The risky way is to boot from a LiveCD and try to unite two partitions (/home and new partition)   , so after reboot space will be added to your /home. 

**Do you have separate /home partition ? **

Thanks

---

### Post by lukeiamyourfather on 2012-07-25
If I understand correctly the original poster wants to use both Windows and Linux but has spare disk space on the Windows partition that needs to be accessible from Linux. There are a few ways to do this. The easiest would be to just mount the NTFS partition from Windows while running Linux. Symbolic links could be used to make this more transparent to the user. The downside is the filesystem wouldn't be Linux native and might introduce problems (for example if Windows is hibernated instead of shutdown it'll jack things up).

If you shrink the Windows partition I'd suggest doing it from Windows, not Linux. After shrinking it there should be some free space. In order to extend the partition that Linux is installed on the space has to be contiguous on the disk, my guess is this is not the case. A new partition could be created using the free space and then mounted in Linux as a Linux native filesystem (like ext4).

If the free space and the Linux partition are contiguous then you could just expand the partition. Regardless of what you do make sure to backup anything you don't want to lose to another hard disk or machine. Even experienced users can make simple but catastrophic mistakes like accidentally formatting the wrong partition.

---

### Post by Sarys on 2012-07-25
Just tell me Why I have the 100 gb NTFS anyway?

---

### Post by FatFrog on 2012-07-25
There is no real reason for there to be a spare NTFS partition unless you really want it there. 

You could mount the NTFS partition in Ubuntu for use to share files between both OS. I'm a multibooter and I have a partition that stores all of my stuff so I can have at it whenever I need. If you don't want to do that, then you could always create an ext4 partition with a utility like gparted and mount it for use with Ubuntu only...

---

### Post by lukeiamyourfather on 2012-07-25
> **Sarys said:**
> Just tell me Why I have the 100 gb NTFS anyway?

We can't answer that. In general NTFS partitions are for Windows. If there's nothing on it or you don't want Windows anymore than format it to whatever you want.

---

### Post by oldfred on 2012-07-25
I also have a shared NTFS data partition from when I used XP. I still have my Firefox & Thunderbird profiles, all photos, and all data from XP in it. I had to run a .bat file to move some data out of Windows as some applications always defaulted to their own location. Made it easy to share as I have several Ubuntu installs and XP all using same data. But now I do not boot XP and all new data goes into a shared ext3 formated partition. Backup is on anther drive and most important data to DVDs. If you backup to NTFS by file, you lose permissions & ownership, but if just data you can relatively easily reset.

May be best to post screenshot from gparted to see you exact layout to offer best suggestions on changes. Or run thi and post output.

sudo fdisk -lu

---

### Post by Petro Dawg on 2012-07-25
I have successfully resized partitions from live cd using gparted on my Win/Ubuntu dual boot setup, its fairly straight forward and the route I would suggest.

As far as to where to put the space, it depends, if you still want to download some large programs and you are running low on root space then add it to root, else add it to home, or split it to 20 to root and 80 to home for a safe balance.

---

