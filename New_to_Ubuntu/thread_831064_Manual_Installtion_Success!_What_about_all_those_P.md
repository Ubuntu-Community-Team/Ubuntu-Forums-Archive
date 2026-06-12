---
title: "Manual Installtion Success! What about all those Partitions?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Andavane on 2008-06-16
Hardy Heron
===========
I was elated to install the latest Ubuntu manually with a partition for root (60 GB), one for swap (2GB) and one for home (20GB). During the process I noticed that I was offered the choice for many other folders to have their own partitions as well. I was tempted to make one for "usr" but was uncertain, not knowing what size partition to make for it. 
Would there have been an advantage in doing this? 
Or in making partitions for some of the other things as well? 
It is a fresh installation, so it would not (I hope) be a hassle to do the job again.There were many options there.
Regards
John
==========
Asus PC
AMD Chip
300 GB Hard drive
Windows Vista on 50 GB

---

### Post by steve101101 on 2008-06-16
> **Andavane said:**
> Hardy Heron
===========
I was elated to install the latest Ubuntu manually with a partition for root (60 GB), one for swap (2GB) and one for home (20GB). During the process I noticed that I was offered the choice for many other folders to have their own partitions as well. I was tempted to make one for "usr" but was uncertain, not knowing what size partition to make for it. 
Would there have been an advantage in doing this? 
Or in making partitions for some of the other things as well? 
It is a fresh installation, so it would not (I hope) be a hassle to do the job again.There were many options there.
Regards
John
==========
Asus PC
AMD Chip
300 GB Hard drive
Windows Vista on 50 GB

the default options are almost always fine and will get ubuntu running quickly. you can always change partitions later if you need to reallocate space.

---

### Post by forestpixie on 2008-06-16
Ok - I don't bother with the /usr etc but do have a /home - depends what you're doing I think. I read it's good to have /boot partition if you use lots of different distros.

But.. you're / partition is probably about 50Gb too big to my mind. So i would chnage that and make the /home bigger.

/ is where programs get installed, /home will have your data

---

### Post by steve101101 on 2008-06-16
> **forestpixie said:**
> Ok - I don't bother with the /usr etc but do have a /home - depends what you're doing I think. I read it's good to have /boot partition if you use lots of different distros.

But.. you're / partition is probably about 50Gb too big to my mind. So i would chnage that and make the /home bigger.

/ is where programs get installed, /home will have your data

good point. i ready the post too quickly. i also agree.

---

### Post by louieb on 2008-06-16
Basically if your running a production server. separate partitions for the various  parts  of the file system is a common practice.  Something to do with security and protection against  the main part of the installation getting full.

For home desktop or server use. I use 4 / (root), /home, /data, and swap. 

If you wind up redoing it  10 GB is more that enough for / (root) just use the rest to make your /home partition larger. 

Welcome and Good Luck.
lou

>  I read it's good to have /boot partition if you use lots of different distros.Been there done that. I'll never ever do it again. Reason being  when one of the distros upgrades it kernel. the GRUB update program screws up the entries for the rest.

---

### Post by forestpixie on 2008-06-16
> If you wind up redoing it 10 GB if more that enough for / (root) just use the rest to make your /home partition larger.

+1 - meant to say that

---

### Post by Andavane on 2008-06-16
Thanks for your suggestions.
Would there be a point in keeping the /home partition backed up regulary?

---

### Post by forestpixie on 2008-06-16
There's always a point in keeping things backed up if the only place data is kept is there.

But it's only your data you need to worry about.

---

### Post by Andavane on 2008-06-16
Thanks.
I have an 80 GB external hard drive, divided into three partitions.
I keep all my date there.
Main vital data is only about 700 MB.
After backing up the the drive that is further backed up to my mate's laptop, and the hard drive moves about with me.
I was just thinking about if I need to move to another machine.
It would be nice to take all my settings and programs with me.
Regards
John

---

### Post by forestpixie on 2008-06-16
Only your settings/configs are in home - the installed files will usually go into the / partition.

---

