---
title: "Symlinks"
date: 2017-04-25
forum: New to Ubuntu
---

### Post by Sean_Ooley on 2017-04-25
Ok, I'm stuck. I've read multiple How-tos and FAQs about symlinks, but apparently I'm unable to grasp either the concept, the syntax or both and now am asking for help. 

I dual boot Win10 and Xubuntu and have 3 disks. SDA has 4 partitions, an ext4 partition that contains the root or Xubuntu, an ext4 partition that contains /home, a FAT32 partition for EFI and an NTFS partition for Win10. SDB and SDC each have one NTFS partition that contains media, programs, documents, etc.

SDB has the following folders: Documents, Picture, Downloads, Videos among others.

What I want to do is to symlink each of those folders to my home folder but I keep failing. Right now, I have the big NTFS drive at /home/myname/Storage using FSTAB. I want to have symlinks that show as /home/myname/Videos and when I click on Videos in a file manager or list the files in the command line for the videos in the /home/myname/Storage/Videos to show.

Thank you for reading my convoluted explanation and for any help.

---

### Post by Dennis N on 2017-04-25
If you want the link in home to be named Videos, you need to remove the existing Videos folder in your home folder first. Then make the link, running the command below from the home folder.

```
ln -s /home/myname/Storage/Videos Videos
```

---

### Post by Sean_Ooley on 2017-04-25
Thanks!

---

### Post by SeijiSensei on 2017-04-25
> **Dennis N said:**
> ```
ln -s /home/myname/Storage/Videos Videos
```
Actually you don't need the trailing "Videos".  Using "ln -s /home/myname/Storage/Videos" will create a link called "Videos".

---

### Post by Dennis N on 2017-04-25
I am aware of that, but I like to advocate just one pattern to remember: ln -s <target> <link-name>

---

