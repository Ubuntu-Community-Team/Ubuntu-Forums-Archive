---
title: "Ownership of files on a USB formatted device."
date: 2015-11-08
forum: New to Ubuntu
---

### Post by richard141 on 2015-11-08
richard@fasterbox:~$ fstab
fstab: command not found
richard@fasterbox:~$ sudo fstab
[sudo] password for richard: 
sudo: fstab: command not found
richard@fasterbox:~$ 

I am trying to change ownership of a FAT32 USB stick and have tried many things ('sudo kate', installed nautilus and 'sudo nautilus', 'sudo su' etc). I keep getting 'Could not modify the ownership of file '---'. You have insufficient access to the file to perform the change'.

How do I use fstab, please?

---

### Post by bab1 on 2015-11-08
> **richard141 said:**
> richard@fasterbox:~$ fstab
fstab: command not found
richard@fasterbox:~$ sudo fstab
[sudo] password for richard: 
sudo: fstab: command not found
richard@fasterbox:~$ 

I am trying to change ownership of a FAT32 USB stick and have tried many things ('sudo kate', installed nautilus and 'sudo nautilus', 'sudo su' etc). I keep getting 'Could not modify the ownership of file '---'. You have insufficient access to the file to perform the change'.

How do I use fstab, please?
Don't hijack someone else's thread.  Start your own thread.

---

### Post by richard141 on 2015-11-08
Sorry - it just seemed to be the same question...

---

### Post by coffeecat on 2015-11-08
Moved to own thread and given a sensible thread title.

@richard141, if you are having difficulty accessing files on a FAT32 formatted USB stick, you may be going about investigating the problem in the wrong way. First of all, you can't change permissions/ownership of files on a mounted partition formatted with a Microsoft filesystem. Second - fstab is a system file, /etc/fstab to be precise.

What is the real problem you are encountering? Why are you trying to change ownership of files? If you do have a problem apart from your inability to change ownership, post the output of these two terminal commands, after plugging the USB stick in, so that forum members can help you:

```
sudo fdisk -lu
mount
```

---

