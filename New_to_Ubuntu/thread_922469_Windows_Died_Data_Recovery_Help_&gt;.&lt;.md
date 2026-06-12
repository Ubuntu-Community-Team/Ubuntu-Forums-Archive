---
title: "Windows Died Data Recovery Help &gt;.&lt;"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Ericthegreat on 2008-09-17
I always keep a backup but some of my files that got finished right before Windows Died were not backed up and i also cannot get onto my backup drive Because of this error "Cannot Mount Volume" Details says its in use or w/e and that i can force it at my own risk. So how can i get back onto both of my drives? Is there a high chance i will screw my drives by forcing them; Would it be better to put my external backup drive on a diff windows pc first and would that fix it on the dead Windows PC? Any help is greatly appreciated and tyvm in advance ^^ I found this guide [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

---

### Post by jbrown96 on 2008-09-17
usually mount fails on fat32/ntfs partitions because they were not umounted properly. there are marked as needing to be checked, and since mount doesn't do this, it fails. If this is the problem you shouldn't have any problem appending "-o force" to the end of your mount command. You might want to elaborate on "windows died" because there may be some other problem.

---

### Post by Ericthegreat on 2008-09-17
First windows went bluescreen then afterward it says windows was unable to start with all the startup options ive tryed them all it goes to the windows flag moves bout half a inch and restarts in a never ending loop by switching to my external that ubuntu is installed on i can launch ubuntu

---

### Post by jbrown96 on 2008-09-17
I assume that Windows is a NTFS file system. The problem is that  NTFS is proprietary, and so the Linux implementation (NTFS-3g) is a hack and may or may not support the entire system correctly. It works in most cases (I have never had a problem), and it is stable enough for regular use, but once strange cases (like Windows crashing) start getting thrown at it, who knows what might happen. I think that there are three possibilities for you: try to repair Windows (boot form the XP disk), force mount in ubuntu, or install Windows to another disk, then add the corrupted disk in as a non-system disk and see if windows can make it work. I would recommend making a backup (if you have the disk space, which must be >= the entire size of your Windows partition) before you do anything because any of these methods may permanently corrupt the data. 
1) boot into Ubuntu
2) sudo fdisk -l to list your partitions
3) Very, very carefully figure out where your Windows partition is and where your destination for it is. (you will look for /dev/sda1 /dev/sdb2 something like that)
4) make a bit-for-bit copy of the partition
```
,sudo dd of=/dev/sda1 if=/dev/sdb2
```
You need to replace /dev/sda1 with the partition where WINDOWS IS LOCATED and /dev/sdb2 with the partition where the BACKUP WILL BE LOCATED. 
This command will not run. The comma at the beginning is intentional. 
Check the command again to make sure that the locations are correct. Check again. Check again...
Once you are absolutely sure, remove the comma and execute. If you mess this up, it will overwrite all your data. dd is short for "data dump" but many call it "data destroyer." You have been warned. 

After that try force mounting with
```
sudo mkdir /media/windows
```
```
sudo mount -t auto /dev/sda1 /media/windows -o force
```
again replace /dev/sda1 with your windows partition

---

### Post by Ericthegreat on 2008-09-17
if it helps any i have accessed both my backup and my windows hdd before windows went crazy (i actully use ubuntu) and also since i already have a backup id really hate to destroy what i have on my backup just cause i tryed to backup a few extra files so would it be best to put my currently inaccessable backup drive on a diff windows pc? should that unblock it or will it still be blocked on my system untill i force unlock it?

---

### Post by jbrown96 on 2008-09-17
To "unblock it" you must mount it correctly once; this will clear the flag that says the partition is unclean. If you mount it in windows, it will take care of everything without even telling you. However, ubuntu wants to let you know that there was a problem last time it was removed, so it won't mount until it makes you aware of the problem and makes you expliciting (with -o force) state that you want to mount it. ubuntu then removes the flag and everything should work fine. 
I don't want you to lose your data; the last post was very paranoiad. It is most likely not necessary and will also take quiet a while too. Just try the force mount command that I posted last time.

---

### Post by jbrown96 on 2008-09-17
double post. sorry

---

### Post by Ericthegreat on 2008-09-17
Np tyvm for your help im at work now will try it once i get home ^^

---

### Post by Ericthegreat on 2008-09-17
Thank you so much it worked perfectly ^^

---

