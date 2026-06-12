---
title: "Newbie Question regarding fstab and drive access"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by Bean12345 on 2012-03-03
Hi all

First off I'm new to linux, migrated from windows xp, purely for speed reasons.

I'm having trouble accessing some of my drives, ideally i would like full access to read / write to my hard drives and partitions. Currently even when i run nautilus with sudo it tells me my drives are read only and i cannot modify them. I have tried editing fstab but i'm unsure if the problem lies there or not.

Here is my fstab file 

> 
UUID=B850B07F50B045C2    /media/New    ntfs    rw,auto,user,exec    0 0  
UUID=9CD4B767D4B741F6    /media/sdb1    ntfs    rw,auto,user,exec    0 0  
UUID=da1f56bc-ea3d-4c3c-950a-cac44f5fb126  /swap        swap  sw                       0  0  
UUID=4c099e60-3270-4de5-a403-d440b045e066  /            ext4  defaults                 0  1  
> 

Any help would be greatly appreciated, if more info is needed i will gladly provide it, but please note i may need to be given the terminal commands to find relevant info

---

### Post by TheFu on 2012-03-03
I don't have an answer other than to say that NTFS is not the best choice for file systems under Linux. Access uses a user-land FUSE driver and it doesn't support all the permissions that any of the UNIX file systems do.  That is not usually an issue, but if there is file system corruption, the file system may protect itself by mounting as read-only.  

sudo is a hammer and probably not the best answer for this problem in a GUI app.

First, you need to be clear about which partition(s) cannot be written to.  
$ sudo touch    /media/New/t
$ sudo touch    /media/sdb1/t
$ sudo touch  /t

Which, if any, of those commands failed?
If it is one of the NTFS partitions, there is a tool '**ntfsfix'** that may help correct the issue sorta like a chkdsk or scandisk would.  I've never used it, but you need to know the device name, not the UUID name to use it. Do not run it on non-NTFS partitions. Read on for how to find the device name.

If it is the / partition, then you should try rebooting and hopefully the OS will see the problem and automatically run fsck for you.  If you find you want to force an fsck on the partition holding / in the future - when it is writable, use:
$ sudo touch /forcefsck
You'll manually run - you need to know which device maps to the / UUID.  That can be found by looking in /dev/disk/by-uuid/ to see where the UUID links.
$ ls -al /dev/disk/by-uuid/4*
That should return something like ../../sda1.  Since you can't write to it now, you'll need to boot off some other  media, like a DVD/CD and get into a maintenance shell. If the answer is "sda1", then your command should be
# fsck -t ext4 /dev/sda1

Answer 'yes' when asked.
Assuming everything is fixed, reboot and let the HDD boot, not the DVD/CD media. Everything should be good.

If you don't know why there was corruption (did you power off the machine, not using shutdown?) ... then I'd start watching that physical disk. It may be going bad.  Definitely get your backups working perfectly and enable SMART data on the HDD.

For more info on fsck [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)
For more info on ntfsfix [http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/](http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/)

I hope this is helpful and clear enough that it can be followed.

---

### Post by Bean12345 on 2012-03-03
results are as follows

touch: cannot touch `/media/New/t': Read-only file system
touch: cannot touch `/media/sdb1/t': Read-only file system

the ntfsfix gave the response Permission denied.

then tried with sudo and got Device or resource busy

---

### Post by Sami345 on 2012-03-03
> **Bean12345 said:**
> then tried with sudo and got Device or resource busy
I guess you should unmount the partition before trying to use ntfsfix.

---

### Post by Bean12345 on 2012-03-03
ok unmounted sdb1 and re-ran nftsfix it went through

sadly upon reboot no change, still reports as read only

---

### Post by Morbius1 on 2012-03-03
I have read posts of an odd bug that somehow the ntfs writeable driver is not installed by default. Try to install it:
```
sudo apt-get install ntfs-3g
```It should tell you if it's already there and it should install it if it's not.

You may have to reboot for it to take affect but try this first:

Unmount an ntfs partition:
```
sudo umount    /media/New
```Then remount it with a:
```
sudo mount -a
```

---

### Post by Bean12345 on 2012-03-04
Thanks Morbius that did the trick

Also thanks to everyone else for their help, I've started my learning process thanks to you guys :D

---

