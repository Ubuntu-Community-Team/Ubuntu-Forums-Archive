---
title: "[SOLVED] how to permanetly mount another partition"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by default00 on 2008-05-31
how do i setup ubuntu so that my windows partition automatically mounts. I have many of my files stored on my windows partition including my background. My desktop background used to automatically appear when i logged in on ubuntu 7.10 and the windows partition would appear automatically on the desktop. Now when i log in on 8.04 i have to click Places -> then my other partition to make my background appear. Is there anyway to have this automatically mount?

---

### Post by TeoBigusGeekus on 2008-05-31
Please post us the output of
```
sudo fdisk -l
```
as well as
```
mount
```

Also post us the content of your fstab file
```
gksudo gedit /etc/fstab
```

---

### Post by Bakon Jarser on 2008-05-31
install the ntfs configuration tool.  when your drive is unmounted run it, it will be installed in system tools.  It will give you the option to mount your ntfs partitions on startup.  you will need to choose a mount point.  I suggest /media/Windows or you can replace Windows with whatever you want the drive to be called.

```
sudo apt-get install ntfs-config
```

---

### Post by Joeb454 on 2008-05-31
See the link at the bottom of my sig :) It should work just fine for you

---

### Post by Victormd on 2008-05-31
> **default00 said:**
> how do i setup ubuntu so that my windows partition automatically mounts. I have many of my files stored on my windows partition including my background. My desktop background used to automatically appear when i logged in on ubuntu 7.10 and the windows partition would appear automatically on the desktop. Now when i log in on 8.04 i have to click Places -> then my other partition to make my background appear. Is there anyway to have this automatically mount?

Check out this how to:
[http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)

---

### Post by Mentem on 2008-05-31
> **Joeb454 said:**
> See the link at the bottom of my sig :) It should work just fine for you

Why does this sound familiar? :D :lolflag:

---

### Post by Joeb454 on 2008-05-31
What're you trying to say ;)

---

