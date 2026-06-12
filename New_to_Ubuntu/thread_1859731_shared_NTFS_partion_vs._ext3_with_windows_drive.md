---
title: "shared NTFS partion vs. ext3 with windows drive"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by sssuizaaa on 2011-10-14
Hello all,

I've been using ubuntu for a year installed in Windows (using wubi) and now I decided to make a proper installation. After reading as much as I could in forums here's what I decided:

background:
ASUS laptop. intel i3, 4 GB RAM, 500 GB HD nvidia graphics
I have already eliminated the security partition that comes with the image of the system and I have reduced the windows partition. So the present situation of the hard drive is one primary partition of 80GB for windows and the rest is unallocated space.
I have already downloaded the iso of Ubuntu 11.10 64-bit

My plans:
During installation, I will go to the manual partitioning and there I would create:
1 logical partition for the swap. Size 4GB. Location end of the drive
1 logical partition for the root mounted at /. Size:20GB file system: ext4. Location end of the drive
1 primary partition for DATA. size: the rest (around 396 GB). file system: ext3. Mounted at /DATA

My reasons: 
4GB for swap. I've read a lot about this and I found no clear rules. I thought 4GB is a good compromise. Why at the end of the drive? I do not know
20GB for the root seems more than enough for what I have read and I do not have much space constrains. Why immediately after the swap, because then I will have the data partition between ubuntu and windows.
Why ext3 for the data partition? because then I would be able to share data with windows using one of the available drivers that allow to read and write ext3 partitions from windows (like ext2fsd). Why a primary partition? well, I do not know much. I have been reading a lot about partitions and I do not see much practical differences between primary and logical. I thought that if I have to change ext3 to NTFS it may be simpler from a primary partition? maybe not....
I have been reading a lot about having a partition for /home but I do not see much the benefit. My original idea is to use a data partition mounted at /DATA. That would be ext3 accessible from windows using a driver. 
The reason for that is that I plant to primarily work with Ubuntu and using only windows for some applications.

My questions:
1. Would the above make any sense?
2. Is it better to use an NTFS partition for sharing information between OS than an ext3 partition accessible from windows?. Apparently Ubuntu is dealing well with NTFS, right?
If a NTFS partition is a better choice, should i include a mounting point for it during the installation process?

Thank you very much for your help,

ssuizaa

---

### Post by aeiah on 2011-10-14
use NTFS. the linux driver is far more trustworthy than the windows driver for ext3.

if you regularly move between linux and windows on the same system, you could mount --bind your linux Documents, Music, Pictures, Videos etc home folders to your Data partition (and likewise do the same thing with windows)

---

### Post by sssuizaaa on 2011-10-14
That was fast!. Thank you aeiah.

I will then use NTFS. Do you know if I should create a mounting point for this NTFS partition during the ubuntu installation? (say /DATA for instance?).
Not sure that I follow you with the binding linux documents to the data partition. Do you mean the documents at /home? I was not expecting to save my documents there but at the /DATA partition. What you said makes me thing that it may be an easier way?

Regards,

ssuizaa

---

### Post by westie457 on 2011-10-14
Hello sssuizaaa and welcome.

Do not see anything wrong with your plans, they seem good to me.

Only a couple of suggestions to add though. Have a separate /Home partition for all of your system settings and configuration files. It only needs to be 1 or 2 GIB in size and will always be there unless you decide to wipe it.

The /Data partition should be NTFS format because it can be read easily from Linux and sometimes the Windows tools to read EXTx (2,3 or 4) can be a bit flaky.

Do not know if making a mount point for the data partition is a good idea as I only mount mine on demand.

Do not be surprised if 'oldfred' finds this thread and gives the same advice or even different. It will all be good.

Happy Ubuntuing.

---

### Post by aeiah on 2011-10-14
yea you can specify where your data partition is mounted to during installation, (/media/data would be a good choice). however, check and double-check that the ubuntu install isn't going to format it (unless its empty right now)


as for my rambling about mount binding and the like:

in windows you have a 'my documents' folder, and others (my pictures, my videos, my music). you can change the target from the default C:\ location to folders on your data partition. you can do the same thing with ubuntu, so both OSes look at the same location for your documents, photos, etc by default. you'd do this by using mount --bind (at a later point when things are set up). this isnt the same as having your home partition on your data partition - all your home config files would be in their normal place

in ubuntu, you have your home partition: /home/username/
in there, you have default directories like /home/username/Documents, /home/username/Pictures etc.

you can set it up so when you open your /home/username/Documents/ directory, its actually opening a location on your data partition. its like a shortcut, but invisible and seamless.

but anyway, as i said this is just something you could do for convenience after installation and isnt necessary in any way.

---

### Post by sssuizaaa on 2011-10-14
Thank you for the response.

The partition does not exist so I will tell ubuntu to create it during the installation. So no problems with formatting it.

regards

---

### Post by sssuizaaa on 2011-10-14
Thank you, I'll add an additional logical partition for the /home then.

regards,

ssuizaa

---

