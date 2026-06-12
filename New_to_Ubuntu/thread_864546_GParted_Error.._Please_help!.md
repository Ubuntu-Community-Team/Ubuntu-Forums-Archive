---
title: "GParted Error.. Please help!"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Guest101 on 2008-07-19
Hi,

I am having problems installing Ubuntu 8.04 Desktop Edition. I am fine all the way up to "Step 4". At this point (as you most likely know) you are given three options on how to partition.([http://www.techotopia.com/images/5/52/Ubuntu_disk_partitioning_screen.jpg](http://www.techotopia.com/images/5/52/Ubuntu_disk_partitioning_screen.jpg))

Number 1: You drag along how much you want windows and Ubuntu to have.

Number 2: You give Ubuntu ALL the space.

Number 3: Manual.

I choose number 1. Gave Ubuntu 12GBs of space (I had 140gb free). I then pressed forward. So then the % thing came up. It stayed on 0% for about 30seconds, then a error message came up saying something about it not being able to write the changes to disk, and the re-size operation had been aborted.

So, I try again later, same thing. Then I make a new disc at 4x speed, and verify it with Ubuntu. It passes (no errors) but the same thing happens. 

So... I guess I now need a guide on how to use the manual bit.. or I need someone to figure out why the error message came up..

Anyone?

Thanks in advance.

BTW: I did defrag.

---

### Post by spiderbatdad on 2008-07-19
Could you post some specs regarding what type of machine you are trying to install on...hardware configuration, numbers of disk?

It does look like an error on the image cd, but that is just a guess.

---

### Post by Guest101 on 2008-07-19
> **spiderbatdad said:**
> Could you post some specs regarding what type of machine you are trying to install on...hardware configuration, numbers of disk?

It does look like an error on the image cd, but that is just a guess.

Intel Core Duo 2 T7500 2.2GhZ
2GB RAM
200GB HDD (1)
Intel X3100 Intergrated Graphics

I have burnt two CDs, both didnt worked. And I checked them both for errors with the Ubuntu.. and no errors.

---

### Post by louieb on 2008-07-19
1st run windows chkdsk on the partition.  2nd defrag your windows partition. ( I see you did that). 3rd make sure you shutdown windows gracefully. 
The parted family will not  touch an NTFS partition if it thinks its not in good shape. 

Might get a better reason if you open System>Administration>Partition Editor. and try creating your partitions there. Then use the manual option of the install to let the installer know where you want Ubuntu installed. 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")
good but boring videos here  [Linux.com Gparted videos]("http://www.linux.com/articles/114157")

---

### Post by spiderbatdad on 2008-07-19
agree with louieb, something seems amiss with the ntfs partition. You might try defragging again, even if the system tells you the volume doesn't need it. Then try to install. I do have a similar story regarding two iso's that both verified with md5sums. I couldn't get them to write to the disk. Months later, by chance I burned another image from a new download site and voila, Ubuntu installed...this is not to say you need to burn another disk, but if all else fails, you might consider a different mirror and burn the disk at 2x.

---

### Post by Guest101 on 2008-07-20
> **louieb said:**
> 1st run windows chkdsk on the partition.  2nd defrag your windows partition. ( I see you did that). 3rd make sure you shutdown windows gracefully. 
The parted family will not  touch an NTFS partition if it thinks its not in good shape. 

Might get a better reason if you open System>Administration>Partition Editor. and try creating your partitions there. Then use the manual option of the install to let the installer know where you want Ubuntu installed. 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")
good but boring videos here  [Linux.com Gparted videos]("http://www.linux.com/articles/114157")

Thanks for your help.. Ill have ago and report back ;)

---

### Post by kansasnoob on 2008-07-20
I think Louieb was the first to catch this! You're dual booting! Cool! That's a great way to go at first!

But you don't mention whether you have XP or Vista. If you have Vista use this guide:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

It's always better to resize a Vista OS partition with Vista's own "tools".

---

