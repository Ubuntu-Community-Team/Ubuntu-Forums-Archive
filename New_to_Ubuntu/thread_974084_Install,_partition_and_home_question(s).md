---
title: "Install, partition and home question(s)"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by jolly_grunt on 2008-11-07
I've been getting ready to install ubuntu by reading through these forums in order to get a have good idea as to what I should do before, during and after installation.

I'm planning to do a clean install over Windows XP on my laptop. I don't have anything vitally important on said laptop other than a few pics that I'll backup on a pen drive beforehand.

Now for the questions:

Currently my laptop has one HD with two partitions. Will the ubuntu install leave them alone, or will they be made into one whole partition?

Does it matter whether, or not, my current XP install is defragged before I install ubuntu?

Should I format the disk before installing ubuntu?

During install can you do a clean install and also make partitons?

I've read that it's a good idea to keep "/home" on a separate partition. How do you do that?

If so, how big of a partition should be made for "/home"?

---

### Post by beno1990 on 2008-11-07
> **jolly_grunt said:**
> 
Currently my laptop has one HD with two partitions. Will the ubuntu install leave them alone, or will they be made into one whole partition?


You can choose if you partition the disk manually in the Ubuntu setup's partitioner.

> 
Does it matter whether, or not, my current XP install is defragged before I install ubuntu?


If you're choosing to erase Windows and only have Ubuntu installed, no. It doesn't matter either way.

> 
Should I format the disk before installing ubuntu?


The Ubuntu setup will do that for you.

> 
During install can you do a clean install and also make partitons?


The partitioner is very customisable. :)

> 
I've read that it's a good idea to keep "/home" on a separate partition. How do you do that?


It's not neccessary, but it can prevent you from losing data in the event you reinstall the OS.

To do it, in the manual partitioner, make a partition and set the mount point to /home.

> 
If so, how big of a partition should be made for "/home"?

It's usually most of your drive. Typically, 1-2GB swap partition, 16-32GB / (root) partition, and 200MB /boot partition and the rest for /home will be good enough.

---

### Post by stevebond001 on 2008-11-07
I installed my Home folder on a separate partition when I installed Hardy, some months ago (see screenshot).  I have now benefited from this because I have just upgraded to Intrepid, safe in the knowledge that my Home folder and all my data is safely tucked out of the way.

I would strongly suggest that you create a separate partition and mount your Home folder there.

---

### Post by mapes12 on 2008-11-07
If you're just starting out with Ubuntu and to save us guys some serious typing have a read of this site which has everything you need to get you going: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

In my experience, as you work your way through the installation screens read everything very carefully. Particularly, the "Partitioning" section. If you have set up your partitions before hand make sure you select "Manual" then highlight each partition and set the variables so that the installer knows what you want to do e.g. where to install /(root) and where to install /home

The other posters are correct about installing /home on a separate partition. It makes live much easier when upgrading or if you loose your system for whatever reason. Everything is kept safe.

---

