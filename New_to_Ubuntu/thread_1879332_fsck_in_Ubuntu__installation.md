---
title: "fsck in Ubuntu  installation"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by jrev on 2011-11-11
when starting the Ubuntu installation I came across an irrecoverable error.
Then I found I could use the fsck command without quitting the installation.
But what is the exact command in order to check the whole disk ?
I have typed 
> # fsck -y /dev/sda1and the answer was
> /dev/sda1 clean, xxxxxfiles, xxxxxxxblocks

thanks for your help

---

### Post by oldfred on 2011-11-11
You cannot check entire drive, but each partition. And each partition needs to be unmounted to avoid major problems. Plus you may have different file systems (formats) in each partitions. So if it is NTFS you have to use chkdsk from a Windows repair CD.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by jrev on 2011-11-12
thanks a lot for this complete response :D

---

