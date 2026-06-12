---
title: "Get access to partition Ubuntu is installed on"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by eternalko on 2012-05-17
Hello. 

I've installed Ubunt alongside Windows. My HD has 2 partitions:
C and D. I've installed Ubuntu on D.

How can I access files on partition D?

I see C in devices panel. But no D. What can I do?

---

### Post by billyseth on 2012-05-17
what type of file system did you use for your linux partition? Most likely ext3, or ext4? There are a few third-party programs that will let you access different types of file systems from windows.

---

### Post by westie457 on 2012-05-17
Welcome to the Fora.

Windows cannot see what is inside a partition that is not formatted as NTFS or any variation of the FAT (FAT, vFAT or FAT32). Linux operating systems are capable of reading almost any file-system you care to throw at it.

If you really want to use Windows to look at your Linux partition then you will need to install Ext2Fsd available from here.
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by billyseth on 2012-05-17
thanks for the back-up post Westie, I couldn't recall the name of the program I used to use, I am pretty sure that was it.

---

### Post by eternalko on 2012-05-17
Sorry. My post was not clear enough.

I want to see my partitions (D partition) from **ubuntu**, not windows. I have my files on D. And Ubuntu on D. [COLOR="DimGray"]I used this install option in Wubi.[/COLOR]  

When I work in ubuntu, I would like to see files from D. I see a mounted device C. But no D :(

---

### Post by billyseth on 2012-05-17
I'm sorry, I'm not all that familiar with the Wubi installer, it creates another partition?

---

### Post by rgreener25 on 2012-05-17
Are you saying that you used wubi and would like to view the ubuntu files from that?

---

### Post by westie457 on 2012-05-17
> **billyseth said:**
> I'm sorry, I'm not all that familiar with the Wubi installer, it creates another partition?

Wubi does not create another partition. What Wubi does is create a large file that Windows cannot see or look into. The large file is a virtual filesystem that contains everything a Linux operating system needs to run, very much like a virtual machine using VMWare or VirtualBox.

@ eternalko

When you open the File Browser (Nautilus) what do you see under DEVICES in the top left-corner? If you cannot find what you are looking for there then suggest you press Ctrl+H to show hidden files, click on 'File System' then click on Search - top right and type in host, hit enter and wait for the search to finish. All being well you should be able to find the files on the partition.

My memory might be a bit out on this as I have not used a Wubi install for about 3 years.

---

### Post by eternalko on 2012-05-17
This is the way I installed it:
[Image with installation, wubi etc. (link)]("http://dl.dropbox.com/u/1174604/CloudShot/2013/shot_18-may-12_003141.png")

Ubuntu OS files and files on D I want ot Access:
[Image 2 with files. (link)]("http://dl.dropbox.com/u/1174604/CloudShot/2013/shot_18-may-12_004414.png").

---

### Post by eternalko on 2012-05-17
> **westie457 said:**
> 
When you open the File Browser (Nautilus) what do you see under DEVICES in the top left-corner? If you cannot find what you are looking for there then suggest you press Ctrl+H to show hidden files, click on 'File System' then click on Search - top right and type in host, hit enter and wait for the search to finish.

I've done it. It took some time, roughly 40 mins of searching (while windows does it in less than 2 mins) but it has found that drive. It is in the /host folder.

So many thanks for help, Westie :)

---

### Post by westie457 on 2012-05-19
> **eternalko said:**
> I've done it. It took some time, roughly 40 mins of searching (while windows does it in less than 2 mins) but it has found that drive. It is in the /host folder.

So many thanks for help, Westie :)

Knew it was something simple but could not remember exactly, hence the long explanation. Thank you for reminding me that it is the /host folder\file.

When you get chance could you mark this **solved** using [COLOR="Red"]Thread Tools[/COLOR]

Thank you

---

