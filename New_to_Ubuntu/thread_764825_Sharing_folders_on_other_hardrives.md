---
title: "Sharing folders on other hardrives"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by kazamx on 2008-04-24
I am currently running Hardy final. I have a number of hard drives in my current computer. I am able to share folders from with my Ubuntu partition without any problems. 

I would like to share folders from other hard drives within my computer. The problem seems to be that any other hard drives have their permission set as root, and this is stopping me from sharing the folders. 

Can anyone tell me how to give myself the permissions to be able to share these folders?

---

### Post by superprash2003 on 2008-04-24
it is possible to share folders as read only even if its owned by root.. you can type sudo nautilus in the terminal and browse to the drive and change permissions graphically there

---

### Post by herbster on 2008-04-24
Kazamx, you mean accessing other drives on the same computer, or over a network?

Paste the output of:

```
sudo fdisk -l
```

and

```
df -h
```

---

### Post by stchman on 2008-04-24
> **kazamx said:**
> I am currently running Hardy final. I have a number of hard drives in my current computer. I am able to share folders from with my Ubuntu partition without any problems. 

I would like to share folders from other hard drives within my computer. The problem seems to be that any other hard drives have their permission set as root, and this is stopping me from sharing the folders. 

Can anyone tell me how to give myself the permissions to be able to share these folders?

You need to add the partitions in your fstab.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

