---
title: "Fixing partitions"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by dgbearcat on 2008-11-09
Hey guys,

On some advice to deal with nvidia issues on 8.10, I did a fresh install, which seems to be holding up. I didn't have my home in a separate partition, though, so I'm just starting totally from scratch.

One thing, though, is that I think it did something funky with my partitions. I think it overwrote just part of my original ubuntu partition, and left the swap from before, and made a new one. Could someone take a look at this screen shot and tell me which things I can delete and add to my main install? The partitions at the front and back are windows boot tools of some kind. I'm just not sure what the ~500 meg thing is, and how to figure out which of the swaps I can delete. 

Ubuntu mounts something with ~500 megs, and all it has on it is "lost and found". Any idea where that's from or what it is?

[[IMG]http://img87.imageshack.us/img87/7392/88620582qu4.th.png[/IMG]](http://img87.imageshack.us/my.php?image=88620582qu4.png)[[IMG]http://img87.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by Pelham123 on 2008-11-09
Take a look here for lost & found:

[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

Also, ?screen shot

---

### Post by dgbearcat on 2008-11-09
> **Pelham123 said:**
> Take a look here for lost & found:

[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

Also, ?screen shot

I attached a screen shot...it's there for me.

---

### Post by Pelham123 on 2008-11-10
> **dgbearcat said:**
> I attached a screen shot...it's there for me.

Yeah, dunno what happened. Looked at it from a work PC...wasnt there. But can see it now ;)

I would run the following command in a terminal

```
free -m
```

This will tell you the size of your swap partition and therefore the one you are using.

The ~500MB partition is a boot partition (as marked under the flags column).

---

### Post by indytim on 2008-11-10
Assuming that you ran GParted while booted in Ubuntu:

1.  If you look at the graphic, you will see lock keys to the left of the partition.  That means that those partitions are locked out from you for any changes while you are booted to Ubuntu (present state).  

2.You will see that sda8 swap is locked.  That means that is the one you are currently using.  You can delete sda6.

3. You will also see that sda7 is locked.  That is your current Ubuntu active partition.  I'm assuming your old Ubuntu was sda5.  You can delete this one if it is not being auto-mounted for you at bootup.  If it is auto-mounted, the easiest thing to do is to comment it out of your /etc/fstab file on your active Ubuntu installation.  You can search "fstab" in the forums if you need additional assistance with this.

4.  Leave sda1, sda2, sda3 and sda4 alone as they are either your extended partition or most likely Window recovery partitions (you are probably using a big box store pc as they like to put this stuffola in there).

5.  After things have stabilized, you should think about downsizing your Ubuntu partition and split your /home off into it's own partition.  Among other things this will make life easier for you if/when you have to rebuild from scratch or upgrade.

6.  Consider using the manual partition setup on future installs.  It will put you in charge of what is actually happening on your partitions at build time (ie. like using the same /swap across all of your Linux ops).

7.  Get a copy of GpartedLive and burn the iso to a bootable cd.  Boot from that for future partition work.

Hope this is of some help.

Good Luck,

IndyTim

---

### Post by mapes12 on 2008-11-10
> Get a copy of GpartedLive and burn the iso to a bootable cd.

From here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

> 
split your /home off into it's own partition.

Like this: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Alternatively, delete all your partitions and start again. Your current configuration is messy and if you do have Extended Partitions with Logical Volumes within them

```
sudo lshw
```  will give you more detail, they are not a good place to install Linux because Extended Partitions are a throw back to DOS to over come the 4 Primary Partition Limitation in DOS.

In planning your partitions have a look here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by indytim on 2008-11-10
> Alternatively, delete all your partitions and start again.

Be prepared to completely re-install Windows on this advice..

> they are not a good place to install Linux because Extended Partitions are a throw back to DOS to over come the 4 Primary Partition Limitation in DOS.

What is the basis of this recommendation?  I am currently running 4 different variations of Linux with /swap and dedicated /home within an extended partition...

IndyTim

---

