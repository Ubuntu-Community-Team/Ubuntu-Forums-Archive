---
title: "Partitioning"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by vagelism on 2012-02-01
Hello to all.
I have my laptop partitioned like the image from gparted.
in dev/sda1 is windows partition.
in dev/sda6 is the linux 
I want to eliminate the windows partition since I do not use it anymore and give some of its space to the dev/sda5 and to linux partition.
Is it a safe way to do it and be able to boot my system after?

Please keep easy.
Thank you!

---

### Post by sanderd17 on 2012-02-01
It's totally safe to remove the Windows partition with Gparted (As Grub is doing all the work of booting the OS). But the problem is that sda5 is on the complete other side of the HDD.

So you will have to move a lot, and it could take very long (count an hour or more). 

To delete the partition and extend/move the other ones, you will have to do it via a Live CD. In any case, never interrupt Gparted when it's started.

---

### Post by vagelism on 2012-02-01
> **sanderd17 said:**
> It's totally safe to remove the Windows partition with Gparted (As Grub is doing all the work of booting the OS). But the problem is that sda5 is on the complete other side of the HDD.

So you will have to move a lot, and it could take very long (count an hour or more). 

To delete the partition and extend/move the other ones, you will have to do it via a Live CD. In any case, never interrupt Gparted when it's started.

So if I understood correct I only have to delete via gparted the windows partition , even if there is going one the boot process.
Is it so safe??? 
I am afraid to do so ;)
Thank you!

---

### Post by sanderd17 on 2012-02-01
deleting that one partition is quite safe. moving the other ones isn't so safe (a long operation is more vunerable to corruption).

---

### Post by vagelism on 2012-02-01
can I do the procedure without the moving?

---

### Post by Mark Phelps on 2012-02-01
> **vagelism said:**
> can I do the procedure without the moving?

Your original question was to combine the new free space resulting from removing Windows with the existing sda5 partition.

The answer is NO -- you can NOT do this without moving as there are partitions between the existing Windows partition and sda5.  

To combine spaces or partitions, they have to be adjacent to one another.

---

### Post by vagelism on 2012-02-01
So the steps are :
delete
and then move the free space

Correct?

---

### Post by Resplendent Raven on 2012-02-01
Think this should answer all your questions - [http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

And to answer your question directly you can only move space that is already free or that is freed by shrinking or deleting a partition. So yes you are correct.

---

### Post by Miljet on 2012-02-01
You can not "move" free space. You can move file systems into it, or you can empty it to make free space, but the space is where it is and will stay there.

What you are trying to do is very likely to cause problems unless you understand exactly what you are doing.

I would recommend waiting until you are ready to upgrade to a later version and then installing the new version in the space now occupied by Windows. Ubuntu 12.04 will be released in a couple more months.  After that, it would be much easier to adjust your remaining partitions.

---

### Post by Bartender on 2012-02-02
IMO you should absolutely NOT take this on without backing up all your personal data to an external HDD.

Once you've done that, I'd be inclined to ask if it wouldn't make more sense to just wipe the drive and start over?  Set it up the way you want it, then copy your personal data back into the new data folder, or /home folder?

I'm not absolutely sure about this, but if you wipe out Windows, GRUB is gonna go sideways, isn't it?  GRUB is your bootloader.  Unless newer versions of GRUB are much more adaptable than in the past, you'll get nothing but an error message when you restart the PC after wiping out Windows.  It's not impossible to repair GRUB from a non-responsive PC, but it's not a task to be taken lightly either.

I'm pretty sure GRUB *can* be fixed from an Ubuntu LiveCD.  I'm not familiar with the steps.

---

### Post by vagelism on 2012-02-02
Thank you for your advice.

---

