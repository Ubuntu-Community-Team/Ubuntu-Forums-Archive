---
title: "install ubuntu on d: drive"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by hikujk123 on 2008-06-03
I am trying to dual boot xp and hardy heron.  I know who to do it if you let the ubuntu installer take over and say guided.  As you probably know, windows **usually** installs the OS on a C: drive and then has a D: drive for data.  I have no data on my D: drive.  I want to install ubuntu on it so I don't have to risk losing data on my C: drive.  When I start the ubuntu installer, the default option just wants to resize windows on my C: drive.  Another option wants it to take over my whole 40 G disk, making one big partition.  So, seeing the manual option, I thought I should partition the D: drive.  It was FAT 32, but I made it a 8 G ext 2 and a 2 G swap (I have 512 MB ram).  THe problem is that I am new to linux, so I don't know what to do after I click manual.

---

### Post by rraj.be on 2008-06-03
The best way is to get into windows and open your computer disk manager.

Delete the logic drive of D:

This will help you if you are confused which is your D: in ubuntu partitionar.

then boot into live cd and during insatlation, in partitionar chosse

```
MANUAL
```

Now you will be seeing a partition known as ```
FREE SPACE
```

Right click on it and select NEW PARTITION

The important thing is

```

Select type as ext3fs and mount point as /
```

Then click apply.

Now your partitionar will be started.

---

### Post by logos34 on 2008-06-03
> **hikujk123 said:**
>  and a 2 G swap (I have 512 MB ram).  THe problem is that I am new to linux, 

tha's overkill for typical computer usage.  1 GB should be more than adequate

---

### Post by hikujk123 on 2008-06-04
If I do what rraj.be says, will I risk harming my windows partition?  I didn't think it would because it won't be resized like it normally has to be.

---

### Post by hikujk123 on 2008-06-04
Also, should I delete the swap?  Will the **manual** ubuntu installer make one by itself?

---

### Post by Duck2006 on 2008-06-04
> **hikujk123 said:**
> If I do what rraj.be says, will I risk harming my windows partition?  I didn't think it would because it won't be resized like it normally has to be.

No, just back up any data on the drive and if it has win data on it defrage it and then partition it and install ubuntu on the space you have made for it there. Linux swap should be 1Gb at max.

---

### Post by Duck2006 on 2008-06-04
> **hikujk123 said:**
> Also, should I delete the swap?  Will the **manual** ubuntu installer make one by itself?

When you come to partitioning, use manual, and mark the partitions that you have made for your install. ie / root, and swap, and then go on with the install.

---

### Post by hikujk123 on 2008-06-04
How many partitions do I need?  Just two right?  Swap and ext3fs?  What is wrong with 2 G swap will something bad happen to my computer?

---

### Post by rraj.be on 2008-06-04
Yup you just need two .

swap and ext3fs.

because all other drives can be seen both in windows and ubuntu if its NTFS.

and its recommended as you use a dual boot.

Else your windows cant see your other drives if its  ext3fs.


Two GiB swap is unnecessary and there is nothing harmfull in it,```
 but waste of memory space.
```

Just see here for more info.

[www.faqs.org/faqs/radio/swap-guide/]("www.faqs.org/faqs/radio/swap-guide/")

---

### Post by rraj.be on 2008-06-04
```
[COLOR="Red"]Sorry the above link is a wrong one.
[/COLOR]
```


the correct one is

```
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")
```

---

### Post by Duck2006 on 2008-06-04
> **hikujk123 said:**
> How many partitions do I need?  Just two right?  Swap and ext3fs?  What is wrong with 2 G swap will something bad happen to my computer?

Yes you will need partitions at the nim, if you want your home partition on it's own partition then three partition will be needed, but you will get away with two. If you use any more than twice your ram up to 1Gb of ram, then the space will be a wast. You will find you may not even use the swap partition with that much ram.

---

