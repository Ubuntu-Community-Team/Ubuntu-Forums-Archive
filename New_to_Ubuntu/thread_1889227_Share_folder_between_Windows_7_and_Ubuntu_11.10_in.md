---
title: "Share folder between Windows 7 and Ubuntu 11.10 in dual boot"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by yangli on 2011-11-30
My laptop has dual boot with Windows 7 Pro and Ubuntu 11.10. Both are 64 bits. I want to share files between the two system, so I can access files in Ubuntu when I use Windows and vice versa. I wonder if it's possible to share a folder between them so I can access it in both systems. I can see the Windows stuff in Ubuntu but not in the opposite way. 

Please help. Thanks.

---

### Post by 001neeraj on 2011-12-01
windows can't access linux files and folders...because windows7 uses ntfs filesystem and ubuntu 10.10 uses ext4 filesystem...

---

### Post by mlentink on 2011-12-01
> **001neeraj said:**
> windows can't access linux files and folders...because windows7 uses ntfs filesystem and ubuntu 10.10 uses ext4 filesystem...
Not entirely true
You may want to look at [http://www.fs-driver.org/](http://www.fs-driver.org/).
Granted, I do not know if this works with EXT4 formatted partitions, which the OP most likely has. 
Another possibility is what I use: create a NTFS formatted "Data" partition, which is accessible by both.


Edit: Found this one too, but have not tried it: [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by 3rdalbum on 2011-12-01
Ubuntu can read and write NTFS partitions, which is what your Windows will be using. Just put your Ubuntu files onto the NTFS partition and you can read them in Windows.

---

### Post by mastablasta on 2011-12-01
> **mlentink said:**
> Not entirely true
You may want to look at [http://www.fs-driver.org/](http://www.fs-driver.org/).
Granted, I do not know if this works with EXT4 formatted partitions, which the OP most likely has. 
Another possibility is what I use: create a NTFS formatted "Data" partition, which is accessible by both.
 
 
Edit: Found this one too, but have not tried it: [http://www.ext2fsd.com/](http://www.ext2fsd.com/)
 
 
total commander has an extension that can read linux files.
 
also as mentioned just ut the linux files in a folder on disk with NTFS partition.

---

### Post by Jacobonbuntu on 2011-12-01
...I think I would prefer the way Mlentink suggests, that is how I did it in the time I had dual boot. experimenting with reading ext4 from windows (if it is possible at all) might not be as reliable as the other way around....
Linux handles ntfs very well nowadays

---

### Post by yangli on 2011-12-01
Thank you guys for the information.

---

### Post by shuttleworthwannabe on 2011-12-01
> **yangli said:**
> My laptop has dual boot with Windows 7 Pro and Ubuntu 11.10. Both are 64 bits. I want to share files between the two system, so I can access files in Ubuntu when I use Windows and vice versa. I wonder if it's possible to share a folder between them so I can access it in both systems. I can see the Windows stuff in Ubuntu but not in the opposite way. 

Please help. Thanks.

Is partitioning the drive still an option? You could partition the drive like so:

Disk 1: Windows OS (NTFS)
Disk 2: Data Drive (NTFS)
Disk 3: Ubuntu OS (ext4)
Disk 4: linuxswap 

In this way you can have access to your data drive both ways. That is what I do if/when I am dual booting.

---

### Post by farrinux on 2011-12-01
> **3rdalbum said:**
> Ubuntu can read and write NTFS partitions, which is what your Windows will be using. Just put your Ubuntu files onto the NTFS partition and you can read them in Windows.

Ditto with 3rdalbum, I dual boot and if I share files they are always on a folder in the win drive.  So long as the file from linux is a format I can use in windows I have no problems. Most of what I share between are pics and documents.

---

### Post by Flash858 on 2012-01-01
I use a utility called ext2explore on my Windows side. It does not natively mount the partition, but allows copying a file from my Linux partitions for use in Windows. Don't let the name throw you, it works perfectly with ext4.

---

### Post by Mark Phelps on 2012-01-01
> **yangli said:**
> I want to share files between the two system, so I can access files in Ubuntu when I use Windows and vice versa. 

Just make sure that, if you Hibernate the laptop in Windows, and then use Ubuntu, and then access the Windows partition, you only READ from it. 

Do NOT write to it.  IF you do, any of several bad things can happen, including the file additions/updates disappearing when you then boot back into Windows, to the Windows partition becoming corrupted and not able to boot again.

---

