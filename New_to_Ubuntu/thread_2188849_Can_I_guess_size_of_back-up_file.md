---
title: "Can I guess size of back-up file?"
date: 2013-11-19
forum: New to Ubuntu
---

### Post by arroy_0209 on 2013-11-19
I am using ubuntu12.04 and have never taken backup of my system earlier. In fact I do not have enough knowledge of any back-up program but trying to learn the steps following one illustration avilable from net. The problem is I need to use bare metal restore beckup using a program called "Redo". However this craetes a backup of entire system and the image file tends to be huge. Can I guess what will be the size of the back-up file? If I use command du -sh in my home, the result shows 48Gb. I guess this only includes the files in my home. If system files are taken in addition to these, what will be the size? I tried using the same command in root (/) but after waiting for few minutes, there was no final result so I stopped the command. I need to know these since I have only one external hard drive working whose capacity is about 90Gb (and there are some other files already in it). If the back-up size is more than that, I will have to create separate backup (in DVD) for some files in my home and proceed with rest to be saved in the ext HD. But how do I know/guess size of the final backup file to be created by Redo?

In general are sizes of backup files of pdf/audio/executable files larger than/smaller than/comparable to sizes of original files? Or does that depend on the back-up program?

---

### Post by ibjsb4 on 2013-11-20
Do you want a clone of your installed system?

I have used clonezilla for this.

[http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)

This software matches the size of the partition or HDD to the copy and not the actual size (GB) of your install.  So if you want to clone a 90GB HDD you need a 90GB or bigger HDD.

---

### Post by Bucky Ball on 2013-11-20
Right click on /home, properties.

---

### Post by sandyd on 2013-11-20
> **arroy_0209 said:**
> I am using ubuntu12.04 and have never taken backup of my system earlier. In fact I do not have enough knowledge of any back-up program but trying to learn the steps following one illustration avilable from net. The problem is I need to use bare metal restore beckup using a program called "Redo". However this craetes a backup of entire system and the image file tends to be huge. Can I guess what will be the size of the back-up file? If I use command du -sh in my home, the result shows 48Gb. I guess this only includes the files in my home. If system files are taken in addition to these, what will be the size? I tried using the same command in root (/) but after waiting for few minutes, there was no final result so I stopped the command. I need to know these since I have only one external hard drive working whose capacity is about 90Gb (and there are some other files already in it). If the back-up size is more than that, I will have to create separate backup (in DVD) for some files in my home and proceed with rest to be saved in the ext HD. But how do I know/guess size of the final backup file to be created by Redo?

In general are sizes of backup files of pdf/audio/executable files larger than/smaller than/comparable to sizes of original files? Or does that depend on the back-up program?

```

df -h
```

---

### Post by newb85 on 2013-11-20
If you're looking for a GUI way to see the size of system files, I've found baobab works well.   It does basically the same thing as treesize in Windows.

---

