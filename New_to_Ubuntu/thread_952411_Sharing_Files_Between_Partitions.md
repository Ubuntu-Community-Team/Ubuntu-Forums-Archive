---
title: "Sharing Files Between Partitions"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by xItachi on 2008-10-19
I have 2 partitions, Ubuntu & Windows.  I want to be able to share my music & playlist library between the two partitions and since Windows cannot access the Linux partition easily, I was thinking of having my Music folder on my Windows partition and the playlist file inside the folder.  iTunes (Windows) would read from that folder and Amarok (Ubuntu) would also read from that folder for music.  Would playing the songs from Ubuntu be any slower than playing it normally as if it was on my Ubuntu partition?  Thanks

---

### Post by shredder12 on 2008-10-19
No, I don't think..It's hardly going to affect the player..As you might know when we copy or move something between the partitions then the speed is mostly above 10 Mbps and with that speed your player will never get slow..
Hope this clarifies your doubt ...

---

### Post by sethvath on 2008-10-19
If you dual boot, having a DATA partition to share files between ubuntu and windows is a good idea. To ensure compatability, make sure it is formatted as FAT32, NTFS might not work as well.

---

### Post by Elfy on 2008-10-19
I used to do exactly the same thing when I had windows. I never had a problem myslef with ntfs.

You will need to make sure that the windows files are mounted before you open amarok or it will lose your library

---

### Post by hyper_ch on 2008-10-19
you can use

ext2/3 drivers to access the linux partitions in windows [http://www.fs-driver.org/](http://www.fs-driver.org/)

or install ntfs3g to gain read/write access to your windows partition

or setup a seperate partition with fat32 onto which both windows and linux can read/write by default, however it is an ancient filesystem

---

### Post by stephanvaningen on 2008-10-19
I also used a ext2/3 reader/writer in windows like the previous post mentions. To be honest I would also prefer to keep the data on the Linux side and let Windows read on the Linux share via the program referred to in previous thread. I used it like that (until I used only Ubuntu:-D) for a few months and I never experiences problems with that program.

The ntfs3g is standard available in Ubuntu since afew versions I believe, and windoze partitions are readilly available in your Ubuntu by default.

---

### Post by Paqman on 2008-10-19
> **sethvath said:**
> To ensure compatability, make sure it is formatted as FAT32, NTFS might not work as well.

FAT32 is pretty obsolete. It suffers from terrible fragmentation, and doesn't handle large files well.

NTFS support on Linux is excellent these days, and installed by default. Leaving the files on the Windows partition is a nice easy option, really.

---

### Post by spocksbeard on 2008-10-19
> **sethvath said:**
> If you dual boot, having a DATA partition to share files between ubuntu and windows is a good idea. To ensure compatability, make sure it is formatted as FAT32, NTFS might not work as well.

This is what I was trying to do when I installed Ubuntu last night, however something didn't work properly (I think I may have set a mount point wrong for the shared drive) as I can access my windows partition but not the one I intended to share.

Would you be able to offer any advice as to how to get it working?

---

### Post by bodhi.zazen on 2008-10-19
> **spocksbeard said:**
> This is what I was trying to do when I installed Ubuntu last night, however something didn't work properly (I think I may have set a mount point wrong for the shared drive) as I can access my windows partition but not the one I intended to share.

Would you be able to offer any advice as to how to get it working?

We need a little more information to help you ...

such as the partition (/dev/sd??), file system (FAT?) , and mount point.

See also :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Also if you share a partition with windows, be sure to scan it for viruses from windows if you download things to it form Ubuntu.

---

### Post by a0u on 2008-10-19
Personally, I have a data partition formatted as NTFS, and I've never encountered any significant problems with Ubuntu's NTFS read/write support.

> **hyper_ch said:**
> you can use

ext2/3 drivers to access the linux partitions in windows [http://www.fs-driver.org/](http://www.fs-driver.org/)
That may be convenient, but IMHO it might also be a big security risk, since you are exposing your GNU/Linux filesystem to all sorts of Windows malware.

---

### Post by hyper_ch on 2008-10-19
and how woul diwndows malware affect the ext2/3 partitions?

---

### Post by bodhi.zazen on 2008-10-19
> **a0u said:**
> Personally, I have a data partition formatted as NTFS, and I've never encountered any significant problems with Ubuntu's NTFS read/write support.


That may be convenient, but IMHO it might also be a big security risk, since you are exposing your GNU/Linux file system to all sorts of Windows malware.

I am not sure the security risks of a shared data partition are any less with NTFS vs ext2/3.

Either way, windows malware will not run on Linux, the data partition is still mounted (presumably with rw access) in windows, and you can still circumvent window security by downloading a file in Ubuntu (to the data partition) and mount it in windows without scanning it for viruses.

---

### Post by Paqman on 2008-10-19
> **hyper_ch said:**
> and how woul diwndows malware affect the ext2/3 partitions?

It probably wouldn't. But malware, by definition, behaves in unpredictable ways. It not unreasonable to think that it could corrupt files on the Linux partition, especially since it would have write permissions to all files.

---

### Post by hyper_ch on 2008-10-19
it would be far simpler for malware to just wipe all partitions... but you can concern yourself about mounted linux partitions in windows - if you want to.

---

### Post by Paqman on 2008-10-19
> **hyper_ch said:**
> it would be far simpler for malware to just wipe all partitions... but you can concern yourself about mounted linux partitions in windows - if you want to.

Can't say that I lie awake at night worrying about it :)

---

### Post by xItachi on 2008-10-20
What if my Linux partition is reiserfs?

---

### Post by jerome1232 on 2008-10-20
I personally use ntfs as the common grounds for my os's for one reason, it's the only journaled file system that works with read/write across Linux/Mac/Windows. When Windows writes to ext3, it's mounted as ext2 and thus no journaling.

---

### Post by xItachi on 2008-10-20
I also want to try and share my bookmarks between the two partitions for Firefox.  The bookmarks for Windows are on 'C:/Program Files/Mozilla Firefox/defaults/profile', and the ones for Ubuntu are in '/etc/firefox/profile' or something like that I think.  So what I did was leave the bookmarks on the Windows partition and make a symbolic link "ln -s" of the profile folder onto the Linux partition.  So far it seems like the bookmarks are still there on my Ubuntu firefox but when I'm on my Windows firefox, they're not there.  Any ideas?  Thanks

---

### Post by rolnics on 2008-10-20
> **xItachi said:**
> I also want to try and share my bookmarks between the two partitions for Firefox.

Why not use something like Foxmarks or similar online bookmark syncing add-on? I used for home & work, although it screws my fastdial links!

---

