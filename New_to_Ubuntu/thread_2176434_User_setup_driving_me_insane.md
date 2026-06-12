---
title: "User setup driving me insane"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by bomski on 2013-09-24
**Background - **I have an Ubuntu 12.04 box with a single login (admin); on this box I have a mountable RAID array. I'd like to share existing files from this array using samba to another Ubuntu box, without giving out my admin username and password. New user here we come.

I thought this would be a trivial matter but it seems it has bested me for the moment...

I've tried numerous approaches, looked into samba configurations, even tried webmin to help with the configuration.... all i seem to be able to do is connect to the share using my admin credentials.  

Does anyone have any advice into what I might be doing wrong; or can point me in the direction of a step-by-step guide into setting up a user to have samba access to a mount point?

**EDIT: **after some experimentation of settings it seems using the following command allows my test user connect to the the share: 

sudo chmod -R 777 '/media/testarray' 

contents of /etc/fstab:
/dev/md0        /media/testarray        ext4    users,nosuid,uhelper=udisks,nodev       0       0

---

### Post by peertje on 2013-09-25
Please add [SOLVED] to the beginning of the title of this thread

---

### Post by Bucky Ball on 2013-09-25
> **peertje said:**
> Please add [SOLVED] to the beginning of the title of this thread

Actually, you do it by using Thread Tools at the top right of the page and 'Mark this thread as solved ...' ;)

Even though it looks solved, my only question is: Why are you using Samba with two Ubuntu boxes? Samba is primarily a Win thing. SSH, FTP, NFS ... there are other, probably more suitable options. But hey, if it's working for you, good luck! ;)

---

### Post by bomski on 2013-09-26
Wondered that myself too ;) 

I've actually got a couple of Macs, a Windows box and a few other devices on my network; Samba seems to be the only reliable connection for me...!

---

### Post by peertje on 2013-09-30
If you run into trouble, you can always try AFS (apple file sharing). Only the windows boxes need to have OpenAFS installed then. See [http://www.openafs.org/windows.html](http://www.openafs.org/windows.html) for more details.

---

