---
title: "Switching from Windows XP to Ubuntu 8.04"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Bonzzai on 2008-07-23
For some reason my computer is saying I haven't registered Windows, so I **need** to switch over to Linux again. The only problem is I want to keep my files, and I don't have an external harddrive or anything to store my files on to carry them over. Is there a way to install Linux and transfer the files over in the installation? Thanks for anyone who helps :3

---

### Post by iaculallad on 2008-07-23
> **Bonzzai said:**
> For some reason my computer is saying I haven't registered Windows, so I **need** to switch over to Linux again. The only problem is I want to keep my files, and I don't have an external harddrive or anything to store my files on to carry them over. Is there a way to install Linux and transfer the files over in the installation? Thanks for anyone who helps :3

Did you create partitions when you installed your windoze xp OS?

---

### Post by Bonzzai on 2008-07-23
> **iaculallad said:**
> Did you create partitions when you installed your windoze xp OS?

Eh, I think Windows is just using up the entire computer as one partition. ;(

---

### Post by kajillin on 2008-07-23
u can access your windows partition in ubuntu no problem. in the ubuntu installation gui it give u option on partitioning, choose to resize current partition. ubuntu needs like 5gb of hd space.

---

### Post by Sef on 2008-07-23
For right now, I would [dual boot]("http://www.psychocats.net/ubuntu/installing").  Once you get your files off of your Windows partition, then you could delete your Windows partition.

For the [partitioning]("http://www.psychocats.net/ubuntu/partitioning") (picture on the site): 

> This last dual-boot scenario is my favorite now that I know about FS-Drive, which is a small program that allows Windows to read from and write to Ext3 partitions. So FAT32 can go out the window—one less partition to worry about and none of the limitations of FAT32 (no file permissions, lots of fragmentation, and a file size limit of 4 GB).

Both are from Psychocat's Ubuntu.

---

### Post by Milyardo on 2008-07-23
You could use Gparted to create a FAT partition to copy all the files you want to backup while you install Ubuntu. After installing You could choose to keep that FAT partition or remove with GParted. GParted is installed on the Ubuntu live-CD.

---

### Post by Sef on 2008-07-23
> You could use Gparted to create a FAT partition to copy all the files you want to backup while you install Ubuntu. After installing You could choose to keep that FAT partition or remove with GParted. GParted is installed on the Ubuntu live-CD.

Since the OP wants to get rid of Windows, ext3 would be much better than FAT32 which has among other problems a size limitation of 4 gb and fragments easily.

---

### Post by kansasnoob on 2008-07-23
I would think that while installing Ubuntu if you'd simply choose the option: Guided resize and use freed space, and giving Ubuntu the default amount of space, would be a good choice.

After installation is complete, including updates, etc. go to synaptic Package Manager and install ntfsprogs. Their documentation is good and you should be able to copy any file to any external source, ie: CD, DVD, external drive, etc.

I HAVE NOT tried saving ntfs files to an ext3 partition .............. I usually use FAT32 still because I still share some files with an old Win 98 system. Don't ask why!

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

EDIT: If after installing you'd decide you want a separate NTFS or FAT32 partition that's fairly easy to do using Gparted from the Live CD. Or you could do it ahead of time.

You know though, I do have word docs that I've copied from Win XP and saved to my Ubuntu Home and even used Abiword to edit same!

---

