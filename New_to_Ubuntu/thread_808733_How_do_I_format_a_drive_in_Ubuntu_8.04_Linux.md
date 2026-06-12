---
title: "How do I format a drive in Ubuntu 8.04 Linux"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Norman Thom on 2008-05-26
Simply stated:

How do I format a secondary drive in Ubuntu 8.04 Linux

Please Help

---

### Post by Victormd on 2008-05-26
you can install gparted which is a disk manager that allows you to format, create partitions, delete, what ever you want to do with your HDs... simply go to the terminal and type

```
sudo apt-get install gparted
```
and then type
```
gparted
```
to run the application

---

### Post by Mhurst1 on 2008-05-26
> **Victormd said:**
> 


```
gparted
```
to run the application

Of just click it in the mebu after you install it.

---

### Post by Norman Thom on 2008-05-26
Many Thanks Victormd

---

### Post by rajaram_s on 2008-05-26
Thats fine.... But can I get a way in which I can format removable devices like Pen drive etc? Also, how do I rename drives? In gparted, u need to unmount all volumes that are after the particular drive to make changes to any drive. Is there a simpler way to do it?

---

### Post by Norman Thom on 2008-05-26
Thanks Rajaram_S for your pointer re unmounting the drive to be formatted.
It was exactly what I needed to do the job.
You've all been a great help
Norm

---

