---
title: "[SOLVED] How do I mount my windows hard-drive?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by ferral-cat on 2008-09-10
Hi There I recently installed Xubuntu 8.04

I have Xubuntu installed on my second sata hdd

I Windows XP on my first Sata hdd.


Please help.  Last time I installed linux (on a different computer) it did all this for me automatically but now when I go to /mnt/ directory there is nothing there.

---

### Post by wolfen69 on 2008-09-10
does it show up in /media ?

---

### Post by bobnutfield on 2008-09-10
As Wolfen69 has suggested, it should automatically show up in media, but you can verify that it is being recognized by running:

> sudo fdisk -l

If all is well, it will be listed probably as /dev/sda with the first partition as /dev/sda1.  If it is, you can mount it manually, to test it, then if you want it to be mounted automatically at boot time, you can add it to your /etc/fstab file.  To mount it manually, try:

> sudo mount -t ntfs /dev/sda1 /mnt #assuming that /dev/sda1 is your correct Windows partition.

---

### Post by acidsolution on 2008-09-10
if your windows partition is ntfs than you have to shutdown windows properly before mounting drive in ubuntu .
Hibernating windows won't allow the mounting of ntfs partition in Ubuntu.

---

### Post by ferral-cat on 2008-09-10
> **wolfen69 said:**
> does it show up in /media ?

no there is nothing there except cdrom

---

### Post by ferral-cat on 2008-09-10
> **acidsolution said:**
> if your windows partition is ntfs than you have to shutdown windows properly before mounting drive in ubuntu .
Hibernating windows won't allow the mounting of ntfs partition in Ubuntu.

Thank you for this tip.  Fortuantely in my case I had properly shutdown the Windows last time.

---

### Post by tangibleorange on 2008-09-10
could you please post the output of:

```
ls /dev/sd*
```

(if it's still not working)

---

### Post by ferral-cat on 2008-09-10
> **bobnutfield said:**
> As Wolfen69 has suggested, it should automatically show up in media, but you can verify that it is being recognized by running:



If all is well, it will be listed probably as /dev/sda with the first partition as /dev/sda1.  If it is, you can mount it manually, to test it, then if you want it to be mounted automatically at boot time, you can add it to your /etc/fstab file.  To mount it manually, try:

 #assuming that /dev/sda1 is your correct Windows partition.

Thanks bobnutfield,

That solved my problem.  Im glad u advised me to run the command ```

```sudo fdisk -l ```

``` 

Glad u told me to run that first because it is actually sda2 that is my Windows partition.

---

### Post by ferral-cat on 2008-09-10
Wow you guys are really smart.  How the heck do u memorize the syntax of all these commands at the bash prompt?  

The only one I know by heart is 

```
df -h
```

---

### Post by tangibleorange on 2008-09-10
hehe. you just pick them up as your browse the forums really, use them on your own machine, and then they tend to stick (at least for me...)

---

### Post by bobnutfield on 2008-09-10
It does take quite a while to get to the point the most used commands are second nature, but I used a reference book for about two years before I felt comfortable to count on my memory.  A good one is one by O'Reilly called the "Linux Phrasebook."

---

### Post by pilarchen on 2008-10-27
Hi,
I'm also looking for help. My harddisk is also divided (windows/xubuntu) and the windows part is under media listed but I can't find my old files..... I don't know were they are now :confused: 
A Friend of mine instaled Xubuntu yesterday and i was working perfect, but today I lost the both Panels (top und button), and now, when I got back them, I'm missing all my old files :(:(:(
what should i do??????

---

