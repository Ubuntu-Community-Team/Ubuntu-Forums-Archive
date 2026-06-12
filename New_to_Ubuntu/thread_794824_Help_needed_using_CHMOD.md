---
title: "Help needed using CHMOD"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by virbonus on 2008-05-15
I know this is stupid, but I have been unable to figure out how to make an entire drive writeable. I am a newbie to Linux, but not to networking. I have 8.04 Server installed along with Samba. I have a USB drive that is shared and that I can and read from my Windows network. I want to be able to map the drive to my Windows computers and read and WRITE files to the drive. I have tried every variant of CHMOD that I can think of like "sudo chmod 777 /media/External/*" but I still can't write to the drive though I can read from it. Any help would be appreciated.

---

### Post by Xiong Chiamiov on 2008-05-15
Since you have Server, I'm assuming that you don't have a GUI installed, or else you could just do it through the file manager.

I believe you'll have to use the path more as /dev/sda1 or so (I don't know what it is for you specifically, but you can find out with sudo fdisk -l).  Also, depending on the type of disk it is, you may have to change it in your fstab. (FAT, NTFS, ext3?)

---

### Post by warbread on 2008-05-15
You'll need to use the recursive option ('-R') to make an entire file structure writable.  In your case, 

```
:-$ sudo chmod -R 777 /media/External/* 
```

Otherwise, it will complain about all of the folders on the drive.

---

### Post by virbonus on 2008-05-15
Thanks - I got it.

---

