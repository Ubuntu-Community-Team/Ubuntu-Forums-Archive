---
title: "Not sure"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by vanden12 on 2008-10-30
I very new to using Raid in linux...My new Hp computer came shipped with 2 raid drives(2x 320gb) and have heard many thing about setting up raids and such on ubuntu...But I think that I got a software raid called NVIDIA MediaShield&#8482; Storage...

Now I want to know how to do one of 2 things...

First how well does 8.10 install on raid system....Is it something where I can just use the guide installer and it will work?

2ed how do I remove the array/raid... I want to make them a master and slave drive how do I do it?

and  I have read the [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid) and still do not understand..

---

### Post by Zzl1xndd on 2008-10-30
I guess the starting place here should be what kind of raid do you want to set up. 

Are you looking for raid0 (2 dives acting as 1)

or raid1 a Mirror?

---

### Post by vanden12 on 2008-10-30
raid0

---

### Post by Zzl1xndd on 2008-10-31
From the looks of things the NVIDIA MediaShield is hardware raid so you should be able to do into your Bios and set up the drive as a striped set (raid0) and you should have no trouble installing ubuntu as it will be your motherboard handling the work. 

This being said I have never used the NVIDIA MediaShield and have only installed Ubuntu server on a system using hardware raid.

---

### Post by vanden12 on 2008-10-31
So does the striped set make 2 diffrent 320 HDD? 

Does Grub pick this out?

and yes NVIDIA MediaShield has it's own bois...and I thought haveing hardware raid was rare...

Here somthing I post a while back if it helps

> Hey guys I just got my new computer...and Sabayon and ubuntu runs like a dream on it Video,Sound,Wifi all work out of the box on the live cd.....But I got a new HP Pavilion Elite m9300z with a 640GB RAID 0 (2 x 320GB SATA HDDs).and I heaving a hard time installing both Sabayon and ubuntu.... I chould really use some help...

Here something I post on the sabayon forums but got no reply 

[QUOTE][quote]Are you installing using auto partition ?No manual but I have tried AUTO  it just format the whole drive and grub still doesnt load...

> If so have you added to grub.conf 
dolvm2 doscsi dodmraid
or is it dordraid , too long ago to remember.Would I do it from a live cd...If you can find the code I need that be very helpfulk

> Do you have say a 128mb ext2 partition for /boot separate from the raid ? to help get it started .I tried that once it dident make much difference 

> Is the raid controller configured ie: hardware or software / lvm partition.
SOmthing called NVIDIA® MediaShield&#8482; Storage


> Also check grub version and kernel it was build on as you might have to build a custom grub + kernel for booting the raid .It the stock 3.5 kernel and grub... and if ubuntu can do it why cant Sabayon?(Yes I know there diffrent seeing as one use Gentoo and other use Deb) 


Is there a easy way to remove the Raid? I wont mind haveing 1 320 if it saves me alot of trouble..

If you have anything else that might help feel free to post it.[/QUOTE]
Still looking to get any help on this..

I going to wait till the 8.10 becomes gold before installing ubuntu..... and I going to install ubuntu 64 bit...[/QUOTE]

---

### Post by Zzl1xndd on 2008-10-31
a striped set set is 2 hard drives working as 1. thus giving you 640 gigs of hard drive space and faster read/write access. The down side being that if 1 drive fails everything is gone. Grub should be fine (once again based on my experience with Server equipment). And you are correct hardware raid on consumer level hardware is rare.

---

### Post by vanden12 on 2008-10-31
So just makeing sure...

I dont have to to anything in the cmd line before install ubuntu... It just install after I format my raid into a striped..

I backing up my data now...

---

### Post by Zzl1xndd on 2008-10-31
To the best of my Knowlege on the subject. But I was using high end server hardware lets see if we can get some confomation from someone that has used consumer grade equipment.

---

### Post by vanden12 on 2008-10-31
If it fails whould Wubi be somthing do use?

---

### Post by vanden12 on 2008-10-31
Can I get someone to confomation?By anyone else..

---

