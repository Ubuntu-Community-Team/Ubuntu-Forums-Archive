---
title: "Win7 and Ubuntu Shared Partition"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by umsamark on 2013-04-23
Hi I just installed Ubuntu today and I want to do a dual boot of Win7 and Ubuntu.


My overall goal is to have my hard disk split up like this.
150GB for Win7 OS
150GB for Ubuntu OS
700GB(FAT32) shared partition between Ubuntu and Win7 to contain all my data files

This is the current partition I have (see attached GPARTED image). As you can see it has 4 primary partitions already, so I can't make a new extended partition to put sda1,sda2 and sda3 in.


Thanks for your help,
Kasun

---

### Post by oldfred on 2013-04-23
You already have an extended partition with sda5 & sda6. You can only have one extended but it can have an unlimited number of logical partitions. 
So you can expand your extended partition left to include the unallocated. After you make that change then you can create new partition(s) in the extended. They do not have to be in order on the drive.

I would not use FAT32 unless you have to have compatibility with xBox or some other system. NTFS has a journal and supports files over 4GB where FAT32 does not. Chkdsk without a journal on a very large partition without a journal may take forever (or seem that way).
For small partitions or those on a flash drive FAT32 is ok.

 FAT 4GB file max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

### Post by umsamark on 2013-04-23
Hi Oldfred,

Thanks for the advice. I realized that I couldnt  manipulate the extended partition while being on ubuntu, so I booted the  live disk and did what you told me.

(see attached picture)
1. Booted with Live Disk
2. Allocated free space in my extended partition to a NTFS partition named /shared
3. Now I can access files in both ubuntu and Win7 using \shared partition


Thanks for your help OldFred

---

### Post by Sef on 2013-04-23
> [COLOR=#000000] I realized that I couldnt manipulate the extended partition while being on ubuntu, so I booted the live disk and did what you told me.[/COLOR]

The disk being formatted must be unmounted, i.e., not being used. Glad you figured it out.

---

