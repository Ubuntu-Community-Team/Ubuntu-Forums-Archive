---
title: "loose data from usb external  hard disk"
date: 2020-11-23
forum: New to Ubuntu
---

### Post by devjava on 2020-11-23
hi,
i have a usb external disk mounted as /dev/mdxi . when i type cp ubuntu.iso    /dev/mdxi, all my data in my external disk is removed and ubuntu.iso is extracted int my disk.how can i recover my data. i try to use TestDisk with photorec but it can't find my files.
thanks

---

### Post by TheFu on 2020-11-23
/dev/mdxi  is a device name, not a mount point.  it isn't mounted unless you used a directory in the mount command after the device name.  That is an unusual device name too.

If you used **cp ubuntu.iso /dev/mdxi** without sudo, then nothing should have happened. If yo used sudo or a root login, then you overwrote the file system with whatever ubuntu.iso contains.  That is probably a iso9660 file system.  That data is gone.  Use your backups to restore it.  It would have written only over the length that ubuntu.iso holds, so 700 gb? for the cdrom version and a few GB f t is the DVD verson. 

Why use a command without understanding the parameters AND the order of those inputs?

Backup copes are the solution.  Lacking that, t will be extremely painful. Start by getting another HDD that is at least the same size as the mdxi device.  photorec can find files, but not the file names.  It will create restored files using a numbering scheme that doesn't always make sense. Ending up with thousands of files that don't have good names is the best outcome.

---

### Post by devjava on 2020-11-24
> **TheFu said:**
> /dev/mdxi  is a device name, not a mount point.  it isn't mounted unless you used a directory in the mount command after the device name.  That is an unusual device name too.

If you used **cp ubuntu.iso /dev/mdxi** without sudo, then nothing should have happened. If yo used sudo or a root login, then you overwrote the file system with whatever ubuntu.iso contains.  That is probably a iso9660 file system.  That data is gone.  Use your backups to restore it.  It would have written only over the length that ubuntu.iso holds, so 700 gb? for the cdrom version and a few GB f t is the DVD verson. 

Why use a command without understanding the parameters AND the order of those inputs?

Backup copes are the solution.  Lacking that, t will be extremely painful. Start by getting another HDD that is at least the same size as the mdxi device.  photorec can find files, but not the file names.  It will create restored files using a numbering scheme that doesn't always make sense. Ending up with thousands of files that don't have good names is the best outcome.

i have two questions for you please,
how can i backup my filesystem?
how can i be like you  in linux?

---

### Post by ActionParsnip on 2020-11-24
You can backup your important files by simply making a copy to a second storage. That's all a backup is. There are software solutions like deja-dup and all that stuff but ultimately its another copy of the same data on a different disk. You can buy a 1Tb USB drive for very little and copy the stuff you want. You can even use Google Drive or One Drive or Dropbox etc to store data online for you.
Lots of options. 
What does "be like you in Linux" mean?

---

### Post by TheFu on 2020-11-24
> **devjava said:**
> i have two questions for you please,
how can i backup my filesystem?
how can i be like you  in linux?

First, answer the questions already asked, please.
And it would be interesting to know about how much data was on the device.  50MB is very different from 8TB.

There are many ways to backup a file system. But I don't think that is really what you want. I think you want to backup files, which ware stored on a file system, which is placed into a partition, which is part of a HDD organized through the partition table. It is possible to "backup" at any of those levels, but there is complexities when it comes to restoring for each.  Most people really just want to backup their files, permissions, ownership, groups, and ACLs.  For that, rsync is a reasonable beginner tool. If the files are just data, not programs or settings, any program that can copy from A ---> B can be used.  However, rsync is more efficient.

Learning Linux : [https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed)
If you want to learn Linux, it takes time and effort.  There is always more to know. Always.  Most people usually only know what we need to know, at the time we need to know it.  But in the beginning, jumping into the middle of commands without much background can be dangerous to your data. Find a mentor, someone you can watch. Use Unix daily for multiple hours.  Hopefully, it is your job, so you can be paid. Read books on scripting, architecture, design.  Join a local LUG and become active. Many of those old guys are full of knowledge, but you have to ask good questions and have a minimal background.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) that book should provide a reasonable minimal background for beginners.

I fear it is too late for your data to be backed up unless you have lots and lots of time (months - years) to manually go through all the files and rename them.  Backups need to happen BEFORE there are any issues with the data and files.

There are many advanced techniques to attempt to get much of the data you have back, but an understanding of how file systems work would be required.  Few people have that knowledge and usually they charge high prices for their service.

Ever heard the saying, "measure twice, cut once?"  That applies to Unix commands too.  Be very careful running commands unless you are certain about each parameter and the correct order is used.  Swapping the order can do bad things, as I think you realize now.

---

### Post by devjava on 2020-11-25
> **TheFu said:**
> First, answer the questions already asked, please.
And it would be interesting to know about how much data was on the device.  50MB is very different from 8TB.

There are many ways to backup a file system. But I don't think that is really what you want. I think you want to backup files, which ware stored on a file system, which is placed into a partition, which is part of a HDD organized through the partition table. It is possible to "backup" at any of those levels, but there is complexities when it comes to restoring for each.  Most people really just want to backup their files, permissions, ownership, groups, and ACLs.  For that, rsync is a reasonable beginner tool. If the files are just data, not programs or settings, any program that can copy from A ---> B can be used.  However, rsync is more efficient.

Learning Linux : [https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed)
If you want to learn Linux, it takes time and effort.  There is always more to know. Always.  Most people usually only know what we need to know, at the time we need to know it.  But in the beginning, jumping into the middle of commands without much background can be dangerous to your data. Find a mentor, someone you can watch. Use Unix daily for multiple hours.  Hopefully, it is your job, so you can be paid. Read books on scripting, architecture, design.  Join a local LUG and become active. Many of those old guys are full of knowledge, but you have to ask good questions and have a minimal background.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) that book should provide a reasonable minimal background for beginners.

I fear it is too late for your data to be backed up unless you have lots and lots of time (months - years) to manually go through all the files and rename them.  Backups need to happen BEFORE there are any issues with the data and files.

There are many advanced techniques to attempt to get much of the data you have back, but an understanding of how file systems work would be required.  Few people have that knowledge and usually they charge high prices for their service.

Ever heard the saying, "measure twice, cut once?"  That applies to Unix commands too.  Be very careful running commands unless you are certain about each parameter and the correct order is used.  Swapping the order can do bad things, as I think you realize now.

thanks for your response, i m java developer but i want to learn also  linux admin and this site an books are a pretty  good i like it  , i  have for  you an other 2 questions  please :
 there is a different OS  linux that used like  live USB  that recover data it's used for  forensic computing . can i use it to recover my data do you know a good  one ?
i want to create a script that can do automatic search every  week for videos,twitt,books do you know any book that can help me to do  that?  
thanks for your goods information

---

### Post by devjava on 2020-11-25
> **ActionParsnip said:**
> You can backup your important files by simply making a copy to a second storage. That's all a backup is. There are software solutions like deja-dup and all that stuff but ultimately its another copy of the same data on a different disk. You can buy a 1Tb USB drive for very little and copy the stuff you want. You can even use Google Drive or One Drive or Dropbox etc to store data online for you.
Lots of options. 
What does "be like you in Linux" mean?

thanks for your response , i don t ask the exact question, i have an external disk that have  320 Go. i crush it with  1.2 Go and I hope  to recover the other 318 Go. with the same folders. names and tree structure.

---

### Post by ActionParsnip on 2020-11-25
What does
>  i crush it with 1.2 Go
Mean, please?

---

### Post by Impavidus on 2020-11-25
> **devjava said:**
> thanks for your response , i don t ask the exact question, i have an external disk that have  320 Go. i crush it with  1.2 Go and I hope  to recover the other 318 Go. with the same folders. names and tree structure.
So you had a 320 GB drive and overwrote the first 1200MB of it, so you hope the other 318.8GB are recoverable. Most of the data must still be there, that's true. The tree structure is a different matter. As noted above,
> **TheFu said:**
> 
There are many advanced techniques to attempt to get much of the data  you have back, but an understanding of how file systems work would be  required.  Few people have that knowledge and usually they charge high  prices for their service.
and you haven't told us yet what filesystem was on that drive. Maybe it's a filesystem that stores its table of contents on the first 2GB. In that case, all structure is gone.

So your best hope is to use a file recovery tool specifically designed for the filesystem that used to be on that drive (or pay someone to do it for you). Don't expect to get the entire structure back, although for some filesystems, you never know.

Then bring order back in the heap of recovered files. You can automatically order them by filetype and many file formats contain some metadata like title or creation date, which could also be processed automatically. But a lot of it would be handwork.

---

### Post by devjava on 2020-11-25
> **Impavidus said:**
> So you had a 320 GB drive and overwrote the first 1200MB of it, so you hope the other 318.8GB are recoverable. Most of the data must still be there, that's true. The tree structure is a different matter. As noted above,

and you haven't told us yet what filesystem was on that drive. Maybe it's a filesystem that stores its table of contents on the first 2GB. In that case, all structure is gone.

So your best hope is to use a file recovery tool specifically designed for the filesystem that used to be on that drive (or pay someone to do it for you). Don't expect to get the entire structure back, although for some filesystems, you never know.

Then bring order back in the heap of recovered files. You can automatically order them by filetype and many file formats contain some metadata like title or creation date, which could also be processed automatically. But a lot of it would be handwork.
theoretically when we remove data , the data steel in memory segment until write on this segment a new data. on my disk i don't have software installed or metadata , i had just a personnal files and some  good books amd olds java  projects that i worked on.

---

### Post by MartyBuntu on 2020-11-25
You ran PhotoRec and TestDisk on the drive and they found *nothing*?

Your data is gone. Invest in a backup solution in the future.

---

