---
title: "NTFS filesystem?"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by Priest Apostate on 2014-03-13
I have some free disk space that I wanted to finally set up for use. 
As I will be transferring files back and forth between my Windows 8 system, is there an NTFS filesystem type that will work towards that end?

---

### Post by thenh813 on 2014-03-13
Hmmm... not quite sure what you mean. NTFS is a compatable filesystem and will work just fine. FAT32 (also called VFAT) works just as well but dosent support files larger than 4GB. I reccommend NTFS for sharing between Ubuntu and Windows. If you ever wondered wht NTFS means it stands for **New Technology File System**[.]("http://en.wikipedia.org/wiki/NTFS#cite_note-ntfs_abbr-1")

Or you can do things the other way around, instead of Using Linux to read NTFS/FAT, use Windows to read EXT2/EXT3. Download this driver, and follow the instructions. [http://www.fs-driver.org/](http://www.fs-driver.org/) Works great, Windows can read EXT2 and EXT3 as if it was designed for it, the Linux filesystems even get drive letters. I personally set my Windows My Documents folder to be my Linux home folder, so I dont have to move files between OSes. It takes a little reading to set up, but for the slightly better than average user (if you have a dual boot, you probabally are anyway) it is the best solution.

Oh, I also forgot to add, It says NT/2000/XP/2003/Vista/2008, but it also works on Windows 7. Have no idea about Windows 8, sorry, you can try it if thats what you use, just make a restore point before. Chances are it would work, but better to be sanfe than sorry. NOTICE: The filesystem Journal is not used, so EXT3's power loss safety has no effect when writing with this driver.

---

### Post by Mark Phelps on 2014-03-13
Personally, I would go for NTFS for a shared DATA partition.  The Linux community has had the ntfs-3g driver available for some time now, and it does a great job of handling NTFS partitions -- as long as they are use for sharing data.

---

### Post by Priest Apostate on 2014-03-14
Sorry - I was pressed for time at work, and didn't have a chance to clarify that a bit. 
I am trying to format some free space for mounting on my Ubuntu 12.04 system, with the intention to use it for Samba file storage. Because I will be transferring files to and from my Windows 8 system, I wanted to find out if there was an NTFS filesystem for Ubuntu that I could choose for fdisk, that would work towards that end.

---

### Post by sotiris2 on 2014-03-14
Wait if it is **NOT** a dual boot system, as in ubuntu and windows installed on the same computer and running alternatively as you wish. Or an external drive that will actually connect to the win machine with a cable. But rather the ubuntu machine sharing files on a network (via samba) as a fileserver. 

Then the filesystem where the files are stored does **not** actually matter (provided it's readable by ubuntu) as samba shares the files via a protocol that windows understand. If you have problem accessing the files you are sharing it's probably a mistaken configuration in samba.

---

### Post by Priest Apostate on 2014-03-14
Ah, is this to say that (if properly configured) I can store the file on the server (using say, EXT3 or EXT4 for example), and Samba will allow me to upload to/download from it to my Win8 system without any issues?

---

### Post by sotiris2 on 2014-03-14
Yes i share stuff with samba from Public folder inside my home ext4 partition with no problem with winxp and win7 machines.

---

