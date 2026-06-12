---
title: "Resizing my &quot;Home&quot; partition"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by portach king on 2008-05-23
Hi guys,
When I did a fresh install of Hardy a few weeks ago I decided to partition my 80GB harddrive, one half for Home and the other for Root. Now I'm realising my Home is running low on space (8GB left) and there is way too much free space on the root (28.8GB left).
I split the drive 40GB/40Gb (or thereabouts). I have two questions really.

1. Can I resize the partitions safely without having to reinstall of format the drive?

2. How much space should I give the Root drive just to be safe?

---

### Post by smurphy_it on 2008-05-23
yes you can resize them... But not while using them.

Basically, just boot the liveCD and use gparted to resize your partitions.

I can't see you needing more than 10-20GB for the / partition.  I guess that depends on your usage, programs etc....

---

### Post by bumanie on 2008-05-23
Partitioning hard drives containing a filesystem is never 100% safe. There is a chance ones filesystem can be mucked up, or if there is a power outage part way through the process - basically 'good-bye' filesystem. Having said that, I have successfully done what you are proposing a number of times with the gparted live cd and never lost any information at all. The process does take a number of hours however. As for how large to make / normally 10g would be large enough, but you already have 12g in / - that sounds too much. Depite this, I guess in your case, a 20g / should be enough which will allow you an extra 20g of storage. I would check / and see whether there are any errant files/downloads that should be in /home partition. Back up anything vitally important before doing the re-partitioning, just in case something goes wrong - it ususally works well, but there are no guarantees.

---

### Post by philinux on 2008-05-23
My home is on it's own partition which makes reinstalling a doddle.

My / was allocated 12 gig and its using just over 4 so anything like 8 to 12 gig should be fine.

I'd backup anything important first.

Be aware once you give the go ahead to the partitioner it can take ages to resize.

---

### Post by portach king on 2008-05-24
Hey guys,
Im currently trying to get this done. Im running off the live cd, but Im a little confused. I've cleared up an extra 20GB of "ulallocated space", but how do I merge that with my dev/hda6 (ie. Home partition)?
 Thanks again

---

### Post by philinux on 2008-05-24
You expand your home partition to use the empty space you created.

---

### Post by portach king on 2008-05-24
> **philinux said:**
> You expand your home partition to use the empty space you created.

That's what I figured I would have to do but it won't let me. The only option I'm basically being offered is creating a new partition with the empty space. When I try and resize the the Home partition it won't allow it's size to go up any further than it already is...

Thanks by the way philinux, you're being very helpful. I hope I can sort this out asap.

---

### Post by philinux on 2008-05-24
I'm doing this from memory as gparted is something I dont play with on a regular basis. :)

You can see all the partition and the free unallocated space correct.

So you would then right click on your home partition and resize it.
Or do you drag the tags at the end of the partition after you highlight it.

One or the other.

---

### Post by saldie on 2008-05-24
You may have the same problem as I do.
Check out my post here:

[http://ubuntuforums.org/showthread.php?t=797569&highlight=partition+home](http://ubuntuforums.org/showthread.php?t=797569&highlight=partition+home)

If the free space is not next to the partition you need to expand looks like you can't.

---

### Post by portach king on 2008-05-24
Your kidding. That is my problem then. How can I move my smaller partiton to the right then so the free space is beside the partition I want to expand?
I don't need to do a fresh install, do I? :(

---

### Post by xjgnsdof on 2008-05-24
In the box that says "free space before..." or something like that, you want to input the free space that you have if you're trying to move it *behind* a partition. If you're trying to move free space *after* a partition, then you would input that number in the box that says "free space after..."

GParted is easy to use once you know how to move free space around because that's the first step to resizing existing partitions.

---

### Post by saldie on 2008-05-24
I don't know how your disk partitioned, but if it is partitioned like mine and the free space cannot be placed next to your Home part., then looks like your out of luck.
I don't know how much you've used Gparted, but you can create free space in front or behind your partition, don't know if that helps at all.

---

### Post by styphon on 2008-05-24
If you only have two partitions on your drive then this shouldn't be too hard. I'm guessing that you have the free space at the front of your drive, / in the middle of the drive and /home at the end of the drive. In which case you need to expand your / into the free space and then reduce it at the other end (by dragging the tabs at either end of the drive). This should leave the space in the middle of the drive and you should then be able to expand your home drive into the free space.

---

### Post by portach king on 2008-05-24
Thanks guys. I got it working now. It's in the process of moving and copying. Hopefully that will go with no hitches! :)

---

### Post by philinux on 2008-05-24
Dont forget it can take eons to finish.

---

