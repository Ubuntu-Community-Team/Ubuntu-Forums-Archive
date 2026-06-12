---
title: "does ubuntu have a disk partioner utility?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by dvigue on 2008-08-22
I think that i did not make my partion large enough. i am dual booting with XP.  does ubuntu have a utility like "partition magic" that will let me play with all the partions without having to reload windows and Linux?

Love this ubuntu. i even turned my wife onto it.

Thanks in advance
derek

---

### Post by jerome1232 on 2008-08-22
gparted is one.

```
sudo apt-get install gparted
```

---

### Post by Joeb454 on 2008-08-22
> **dvigue said:**
> does ubuntu have a utility like "partition magic" that will let me **play with all the partions**

Never play with partitions ;) Always make sure you have a backup.

I learnt the hard way

---

### Post by jamesrfla on 2008-08-22
You can run gparted on the Ubuntu live cd or do what jerome132 suggested.

---

### Post by billgoldberg on 2008-08-22
> **Joeb454 said:**
> Never play with partitions ;) Always make sure you have a backup.

I learnt the hard way

Certainly don't try resizing them and moving them at the same time.

I also found that out the hard way.

---

### Post by dvigue on 2008-08-22
i ran that program.  It will not let me extend my XP partition and decrease my linux partition.  

any idea what steps i have to do it in?

---

### Post by dvigue on 2008-08-23
can anyone tell me the proper steps so i can resize my xp and Linux partition? it will not let me, it is grayed out...

Thanks

---

### Post by Dutch70 on 2008-08-23
You have to do it from the live cd, you cant change the partitions while you have them mounted.

 Insert your live cd, restart your computer to boot to the live cd. Then install gparted. and you will be able to change the partitions. Don't forget your back ups, and your windowsXP cd.

you can burn the live cd here...
[http://www.ubuntu.com/](http://www.ubuntu.com/)

also check this link for help on partitioning...
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by sandysandy on 2008-08-23
for creating new partitions or for resizing existing partitions u can use gparted (burn as iso image on CD)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

the gparted tutorial is here

[www.howtoforge.com/partitioning_with_gparted](www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by jerome1232 on 2008-08-23
I would second the gparted live cd, Ubuntu live cd likes to mount the partitions while being formatted on random occasions for me, causing errors.

---

### Post by dvigue on 2008-08-23
hey guys, well i "tried" to do all that, i was successful at making a home drive, but i cannot add to my xp partition. it will not let me, and it will not let me do it in xp also. i was using partition magic.  

here is my MESS. what i want is an xp partition, a linux partition, a home partition for linux, a "pictures" partition that i can access in both ,linux and xp (im into photography so i have alot of pics)

can u look at this and tell me what i should do, it looks like a messsss


Thanks

---

### Post by dvigue on 2008-08-24
can anyone help me with this? i really want to make sure my file system is ok, and i can now view my xp partition in linux. i forgot to mount it.

also, how hard is it to rename my drives? i forget which one is what.

---

### Post by Sef on 2008-08-24
> can u look at this and tell me what i should do, it looks like a messsss

I see a couple of things:

1) Root should be about 8 - 10 GBs.  The rest could be used as a home partition.

2) Swap should not be more than 1 GB.  The old rule of 1 1/2 - 2 times applies to ram 512 mb or less.

---

### Post by dvigue on 2008-08-24
now remember im new to linux. by root you mean the partion where all my linux files are stored correct??

Thanks for the post

also..i cannot extend the NTFS "xp" partition.  can you tell me how i can do that???

---

### Post by Dutch70 on 2008-08-25
By root, sef means the "system", or the partition with the "/" sign in front of it. Which in your case is /dev/sda5.

 You really don't need a partition especially for pics, you can access your windowsXP files from Ubuntu by installing ntfs-3g from the repositories. And you can access your Linux files from windows by installing fs-driver, here...[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html).

 Good luck, wish I could be more help, but I am not exactly sure what it is you are trying to do with the partitions you have. 

Dutch

---

### Post by dvigue on 2008-08-25
thx...great info.  

i want a seprate partition for pictures to make sure i dont mess them up. so if i have ot ever install the os again, they are safe.

---

### Post by dvigue on 2008-08-25
thx...great info.  

i want a seprate partition for pictures to make sure i dont mess them up. so if i have ot ever install the os again, they are safe.

---

### Post by Dutch70 on 2008-08-26
Well, looking at your partitions, I don't really know exactly what to tell you. So, I'll try this.

**Someone please Correct me if I'm wrong....**
If you have a separate /home partition, you should be able to reinstall Ubuntu to "/" or "root" without losing any of your pics. That is the whole purpose of creating a /home partition. A new version of ubuntu comes out every 6 months. In October, version 8.10 Intrepid Ibex will be out. [https://wiki.ubuntu.com/IntrepidIbex](https://wiki.ubuntu.com/IntrepidIbex)
A lot of people reinstall every six months, not that you have to. 

Dutch

---

