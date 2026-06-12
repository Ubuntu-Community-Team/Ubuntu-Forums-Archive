---
title: "balancing out disk partition"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by hfp on 2008-06-07
Hey, everybody.  After I installed ubuntu I noticed that windows vista now has a total size of 22.7 GB on HP ( C: ).  Recovery ( D: ) has 8.84 GB and always seems to have just 1.00 GB free even though I have deleted files from there, but that's another story.

My question is, why does ubuntu make such an unbalanced disk partition.  I have a 500 GB harddrive and there are only 22.7 GB available in vista now.  Is there anyway I can change this?  It would be nice to have maybe 250 GB in ubuntu and 250 GB in vista, otherwise vista is going to be filled up in no time.

---

### Post by bumanie on 2008-06-07
Use the vista partitioner to alter vista's partition size. To alter or move the ubuntu partition, use gparted live cd. If the two partitions are next to each other, it would be best to move ubuntu first (ie to the right) and then use the vista partitioner to extend into the space created.

---

### Post by hfp on 2008-06-07
> **bumanie said:**
> Use the vista partitioner to alter vista's partition size. To alter or move the ubuntu partition, use gparted live cd. If the two partitions are next to each other, it would be best to move ubuntu first (ie to the right) and then use the vista partitioner to extend into the space created.

Thanks a lot, bumanie.  Where can I get gparted live cd?  Can I download it?

---

### Post by bumanie on 2008-06-07
Yes. Go [here]("http://gparted.sourceforge.net/livecd.php")

---

### Post by hfp on 2008-06-15
I went there and downloaded gparted live and put the iso on a cd, but gparted is scary.  I booted the computer with the cd in the drive and tried to follow the instructions.  This program just looks like a fantastic way to destroy the computer.  Is there not an easier way to balance out or change the disk partitions?  It is suspicious that ubuntu finds it necessary to put over 450 gb on its harddrive and only allow 22gb on windows vista.  This is starting to make me doubt how great ubuntu is.  In vista there is a disk partitioner but I can't extend it because ubuntu's hogging all the space.  Why is there no partitioner in ubuntu?

---

### Post by ChameleonDave on 2008-06-15
> **hfp said:**
> This program just looks like a fantastic way to destroy the computer.  Is there not an easier way to balance out or change the disk partitions? 

It's dangerous because it makes fundamental changes to your system.  You are now asking for a way to make fundamental changes to your system without using a risky tool that can make fundamental changes to your system.  Do you see that what you're asking is impossible?

Either resize the partitions or don't.

> **hfp said:**
>  It is suspicious that ubuntu finds it necessary to put over 450 gb on its harddrive and only allow 22gb on windows vista.

If it put less, you'd be complaining that it didn't put enough, that you were installing Ubuntu so obviously you wanted it to have most of the space, blah, blah...

You could have chosen the manual option, but you decided to let the installer guess an appropriate size, and now you complain that it's not to your liking.

You think it's suspicious that it prioritises itself?  You do realise that if you installed Ubuntu first and then Windows, Windows would actually make your Ubuntu system unbootable?

> **hfp said:**
> This is starting to make me doubt how great ubuntu is.  In vista there is a disk partitioner but I can't extend it because ubuntu's hogging all the space.
Just make Ubuntu's partition smaller then.  If Vista's partitioner can't handle Linux partitions, then that's a Vista deficiency.

> **hfp said:**
>   Why is there no partitioner in ubuntu?
Ubuntu has GParted.  To make sure you have it installed, type the following into a terminal:

```
sudo apt-get install gparted
```

However, it is best to run such programs from a CD, because you can't do too much to a partition which is currently in use, and the partition is necessarily in use if you're logged into Ubuntu, running GParted.

---

### Post by hfp on 2008-06-15
ChameleonDave, in Vista the partitioner does not appear nearly as difficult to use at gparted; not as risky I mean.  You say if it put less I'd be complaining?  It put 450 gb of a 500 gb harddrive onto ubuntu and put 22 gb onto vista.  How does that make any sense?  I'm not saying it's all ubuntu's fault; I'm saying that it is quite odd that the default installation puts a whopping 450 gb onto the ubuntu harddrive, and that to change this you have to use a scary looking program that could very well damage the computer. I think that is worth mentioning.  Then again, I just installed gparted tonight and I am not very familiar with it.  I'll keep reading the instructions.

---

### Post by ChameleonDave on 2008-06-16
> **hfp said:**
> ChameleonDave, in Vista the partitioner does not appear nearly as difficult to use at gparted;

I've never seen the Vista partitioner.  XP didn't have one, and I had to install a pirate copy of PartitionMagic.

I've never used the GParted live CD, but I've used GParted on various Linux distros, and it seems very user-friendly to me.  It is no more or less risky than any other partitioner.  It simply does the job.  It's honestly hard to understand what you're complaining about.

> **hfp said:**
> It put 450 gb of a 500 gb harddrive onto ubuntu and put 22 gb onto vista.  How does that make any sense?  

It makes sense to someone who is switching to Ubuntu, and just wants the Windows partition to be just big enough to run for the occasional legacy app.  That's what I use it for.

I have no experience of the automatic partitioning.  I have always chosen to do it manually.  It has always seemed to me that I understand what I want better than the computer does.

> **hfp said:**
> 
I'm saying that it is quite odd that the default installation puts a whopping 450 gb onto the ubuntu harddrive, and that to change this you have to use a scary looking program that could very well damage the computer. I think that is worth mentioning. 

It's probably not worth mentioning here.  We're offering support here.  If you don't like the default, then re-do it manually.  There's not much else to be said.  Everyone else manages fine.

If you disagree with the default, then I suppose you could file a bug report on Launchpad in which you explain your suggestions for a better default.  But they'll probably just say that a default that reduces the evil Windows partition to a minimum and gives the rest to Ubuntu is the best default, and that anyone who doesn't like it is free to decide, to the kilobyte, the exact size he wants for each partition.

---

### Post by hfp on 2008-06-16
Perhaps changing the disk partitions is not as difficult as I had imagined.  I'll work with it and see what I can do.  I'll let you know what happens.  By the way, your comment "Everyone else manages fine." is a bit of a stretch.  Search for "disk partitions" and you will see pages of questions and problems.

---

