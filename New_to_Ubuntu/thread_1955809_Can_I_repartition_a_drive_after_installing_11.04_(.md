---
title: "Can I repartition a drive after installing 11.04 (and not lose data/files)?"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-10
That's the basic question. I'd like to run Backtrack 5 on another partition--something I didn't plan for when I installed 11.04 a week or so ago. I've downloaded the Live CD iso file, in case it's safe to start a repartition from it. Thanks for your help.

---

### Post by leecheroflife on 2012-04-10
It should be fine, but before doing it, if you can, back up any and all data you would miss if it went walkabouts, it's low risk, but still a risk!

---

### Post by Cheesemill on 2012-04-10
Yes you can, just boot the Live CD and use gparted to resize your partitions, it may take a long time depending on the type of operation you perform though.

As always it is recommended to have a backup before any sort of partitioning operation, I have had power cuts while using gparted that have completely nuked my drives.

---

### Post by kazztan0325 on 2012-04-10
Hi jps2012,

There is **"GParted Manual"** here:
[http://gparted.sourceforge.net/display-doc.php?name=help-manual]("http://gparted.sourceforge.net/display-doc.php?name=help-manual")

I would like to recommend you to glance through the manual before using "Gnome Partition Editor (GParted)", and you should back up your data beforehand as other members said in previous posts.

---

### Post by forrestcupp on 2012-04-10
A word to the wise, based on experience. When you start the partitioning process DO NOT press Cancel, even if you've just begun. You'll be screwed if you do. They shouldn't even have the Cancel button on there. My experience with doing this is a great testimony that you should back up your data before you begin. I hadn't done a backup in about a month, and I lost a lot of sensitive data.

But if you do things right, you can do what you need to do without any problems. I've done it successfully many times. It's just that one time ...

---

### Post by FatFrog on 2012-04-10
> **forrestcupp said:**
> A word to the wise, based on experience. When you start the partitioning process DO NOT press Cancel, even if you've just begun. You'll be screwed if you do. They shouldn't even have the Cancel button on there. My experience with doing this is a great testimony that you should back up your data before you begin. I hadn't done a backup in about a month, and I lost a lot of sensitive data.

But if you do things right, you can do what you need to do without any problems. I've done it successfully many times. It's just that one time ...

Agreed. For the love of god, back up your data. I cannot tell you how many times just having a simple data backup has saved my hide.
Resizing your partition can take a while, so make like McCartney and "Let it be"

---

### Post by jps2012 on 2012-04-10
I will back up my data! Thanks, everyone, for drilling the importance of B-Ups into me (I hadn't even thought about the possibility of a power failure during the process). I probably would have have just gambled, otherwise. I'm going to do the partition today.

---

### Post by FatFrog on 2012-04-10
Excellent! Good luck.

---

### Post by jps2012 on 2012-04-10
Thanks, also, Kazztan, for the link to the GParted manual. Any recommendations on which program to use for the backups? I installed Back In TIme yesterday, but don't know how effective it is. I'm wondering if it's as good as Time Machine on a Mac.

---

### Post by Cheesemill on 2012-04-10
If you want to make a full backup of your hard drive then go for Clonezilla.

This will preserver everything including your partition table and your MBR. Vital if gparted gets cancelled.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by kazztan0325 on 2012-04-10
> **jps2012 said:**
> Thanks, also, Kazztan, for the link to the GParted manual. Any recommendations on which program to use for the backups? I installed Back In TIme yesterday, but don't know how effective it is. I'm wondering if it's as good as Time Machine on a Mac.

You are welcome, jps2012!

As for back up tool, I recommend **'Déjà Dup'** to you if you have only to back up your Home folder.

**"Details for Déjà Dup"**
[https://apps.ubuntu.com/cat/applications/natty/deja-dup/]("https://apps.ubuntu.com/cat/applications/natty/deja-dup/")

It is simple and easy to use.
And it is default back up tool for 11.10 and 12.04.

---

### Post by authentic on 2012-04-10
Thanks, that solved my problem too!

---

### Post by jps2012 on 2012-04-10
The link for the Gparted users' manual has changed. This is the new link: 

[http://gparted.sourceforge.net/display-doc.php?name=help-manual](http://gparted.sourceforge.net/display-doc.php?name=help-manual)

---

