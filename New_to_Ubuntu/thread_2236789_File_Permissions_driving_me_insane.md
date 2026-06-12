---
title: "File Permissions driving me insane"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by biyian on 2014-07-29
I am new to Ubuntu 14.04 and am running it as a media server on an old rig I had in a closet.  My problem is that anytime I create a new file or folder the owners permission is set to forbidden and I have to go and manually change it. This is causing a lot of problems in media center automation.  Is there any way to set default file permission for all folders and their contents that are created in a certain folder? Or is there something messed up that would fix this so that the owner of the file isn't forbidden by default?

---

### Post by yancek on 2014-07-29
Where are you creating the folders?  A normal user should have ownership permissions to anything in the /home/username directory.  Outside that, it usually requires root/admin access which means using sudo in Ubuntu.  And yes you can set user permissions but where are you doing this?  Some directories need to be owned by root, /media and /mnt partitions should not be a problem.

---

### Post by biyian on 2014-07-29
Yes everything is working fine in my home directory, it is my /mnt/media that I am having a problem with.  I just created a new folder to test again and then did ls -ld this was the output d---rwsrwx+ 2 [username] [username] 4096 Jul 28 23:43 /mnt/media_sdb1/gfdd

---

### Post by yancek on 2014-07-29
>  d---rwsrwx+ 2 [username] [username] 4096 Jul 28 23:43 /mnt/media_sdb1/gfdd 		

I don't know how you are creating these directories, but your output above shows that the user has no permissions at all which is what the three dashes after the initial d mean.  You have the setuid bit for the group indicated by the s in the permissions output.  Some info on setuid:

[http://www.cyberciti.biz/faq/unix-bsd-linux-setuid-file/](http://www.cyberciti.biz/faq/unix-bsd-linux-setuid-file/)

---

### Post by Morbius1 on 2014-07-29
The other oddity is the "+" at the end of the permissions. That usually means an ACL is in force and controlling permissions.

Take a look at the output of this command to find out what the acl values are:
```
getfacl -t /mnt/media_sdb1/gfdd
```

---

### Post by biyian on 2014-07-29
> **Morbius1 said:**
> The other oddity is the "+" at the end of the permissions. That usually means an ACL is in force and controlling permissions.  Take a look at the output of this command to find out what the acl values are: ```
getfacl -t /mnt/media_sdb1/gfdd
```  getfacl -t /mnt/media_sdb1/gfdd getfacl: Removing leading '/' from absolute path names # file: mnt/media_sdb1/gfdd USER   biyian    ---  --- user   biyian    rwx  rwx GROUP  biyian    rwx  rwx mask             rwx  rwx other            rwx  rwx

---

