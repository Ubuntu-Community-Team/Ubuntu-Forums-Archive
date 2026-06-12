---
title: "Edit /Boot/Grub/Menu.lst using Live CD"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by jjascarm on 2008-05-06
I Installed Ubuntu 8.04 to my second hard disk, and the problem seems to be in the menu.lst configuration. How do I sudo gedit this file when I am using the Live CD to boot into Ubuntu. I tried sudo gedit menu.list but I got an error.

Thanks for your help

---

### Post by jjascarm on 2008-05-06
Ah - I forgot to mention that it will not boot any of the listed operating systems...

---

### Post by glennric on 2008-05-06
Are you trying to edit the file on your harddisk while running the live cd?

---

### Post by tjwoosta on 2008-05-06
if your on the livecd and you do gedit menu.lst it will give you a blank file because it is reading the menu.lst from the livecd filesystem rather than the harddrive


you will need to mount the ubuntu partition and open the menu.lst thats on the hdd

sry im not sure what the correct path to your harddrive would be but you can go to the menu go to Places then click your ubuntu drive (should be underneath computer) 

then click boot then grub then menu.lst

---

### Post by jjascarm on 2008-05-06
> **tjwoosta said:**
> if your on the livecd and you do gedit menu.lst it will give you a blank file because it is reading the menu.lst from the livecd filesystem rather than the harddrive

you will need to mount the ubuntu partition and open the menu.lst thats on the hdd

sry im not sure what the correct path to your harddrive would be but you can go to the menu go to Places then click your ubuntu drive (should be underneath computer) 

then click boot then grub then menu.lst

If I do this I believe I can't save the file. I think I need to open it using sudo.

**Gelnnric** - Yes I am trying to edit the one from my hard drive Whilst using the Live CD

---

### Post by zvacet on 2008-05-07
Install grub from live CD.You have guide 

[here.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by Xiong Chiamiov on 2008-05-07
A very useful tool to have in these situations is [SuperGRUBDisk]("http://supergrubdisk.org").

---

### Post by jjascarm on 2008-05-07
Actually worked out how to do it (it was oobvious when I think about it)

ran the code following in a terminal and then broused to /boot/grub/menu.lst

```
sudo gedit
```

---

