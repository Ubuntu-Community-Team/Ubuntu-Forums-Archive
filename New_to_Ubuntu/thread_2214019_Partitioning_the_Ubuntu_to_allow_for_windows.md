---
title: "Partitioning the Ubuntu to allow for windows"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by cahmadi26 on 2014-03-30
Hey everybody,

So I have Ubuntu running as a primary OS on my hard drive which has about 230gb of total space. I want to partition the drive so i can install windows; however, when i visit gparted to unmount the drive and resize it, it says:
 
The partition could not be unmounted from the following mount points:

/


Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

I unmounted all the other drives successfully and still receive this notification. Any ideas? Also, my computer does not recognize my USB as a bootable drive even though i used the WinUSB program to make it bootable. Can anyone help me out?

Thanks,
Cyrus

---

### Post by carl4926 on 2014-03-30
To manage your partitions I suggest using a Gparted Live CD

It sounds like you are saying you are trying to manage partitions that you are currently using.

---

### Post by cahmadi26 on 2014-03-30
where do i get that? and yes i am trying to manage the main partition which im on right now, how else would i partition it?

---

### Post by carl4926 on 2014-03-30
> **cahmadi26 said:**
> where do i get that? and yes i am trying to manage the main partition which im on right now, how else would i partition it?

[http://gparted.org/download.php](http://gparted.org/download.php)

---

### Post by carl4926 on 2014-03-30
> **carl4926 said:**
> [http://gparted.org/download.php](http://gparted.org/download.php)

FYI 
The ubuntu live DVD/USB has gparted on it, but you may need to swap off if it involved moving swap in any way

---

