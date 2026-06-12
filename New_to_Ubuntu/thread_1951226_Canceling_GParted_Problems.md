---
title: "Canceling GParted Problems"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by schilkyl on 2012-04-02
While I am no beginner to Linux in any way, I am to this site and so I must begin my adventure here in the Absolute Beginner Talk section. 

Here is my problem:
I have a 400GB internal laptop hdd that was partitioned to have Ubuntu and Windows 7 running on it. My windows 7 needed to be redone fresh so I booted to an Ubuntu 11.10 LiveCD to erase the partition using GParted. I then decided I wanted to resize my existing Ubuntu partition. I think I was going from about 300 to the full size of my hard drive. I started the operation and waited about 10 min. I realized that the process was going to take a very very long time and so hit the cancel button to end the operation. Now my problems begin. Everything begins to freeze up and eventually I get the computer to shut down

NOTE: the GParted cancellation operation did NOT complete as it should have and my original Ubuntu partition did NOT return the its previous state. 

Rebooting sent me to grub rescue and so its back to the LiveCD. 

I dont know what to do to go about recovering my Ubuntu drive. Nothing has been changed since I restarted and while I assume there is a possibility for data loss, I dont believe it should be much. Worst case scenario I have to backup my files and do a fresh install though I dont know how I will be able to access the files. 

If you need any more info just let me know as I hope to get this fixed quickly. Thanks

---

### Post by santosh83 on 2012-04-02
> **schilkyl said:**
> While I am no beginner to Linux in any way, I am to this site and so I must begin my adventure here in the Absolute Beginner Talk section. 

Here is my problem:
I have a 400GB internal laptop hdd that was partitioned to have Ubuntu and Windows 7 running on it. My windows 7 needed to be redone fresh so I booted to an Ubuntu 11.10 LiveCD to erase the partition using GParted. I then decided I wanted to resize my existing Ubuntu partition. I think I was going from about 300 to the full size of my hard drive. I started the operation and waited about 10 min. I realized that the process was going to take a very very long time and so hit the cancel button to end the operation. Now my problems begin. Everything begins to freeze up and eventually I get the computer to shut down

NOTE: the GParted cancellation operation did NOT complete as it should have and my original Ubuntu partition did NOT return the its previous state. 

Rebooting sent me to grub rescue and so its back to the LiveCD. 

I dont know what to do to go about recovering my Ubuntu drive. Nothing has been changed since I restarted and while I assume there is a possibility for data loss, I dont believe it should be much. Worst case scenario I have to backup my files and do a fresh install though I dont know how I will be able to access the files. 

If you need any more info just let me know as I hope to get this fixed quickly. Thanks

I'm guessing it was the filesystem resize operation which took so long. GParted does a dummy run, so it'd take twice as long as the actual operation as well.

Did you try mounting your Linux partitions from your LiveCD? If the filesystem is messed up, mount should complain. Also do an fsck of the partitions from your LiveCD. Then as soon as possible, copy all your unique data to another source, since recovery is by no means sure for you at this point.

After its done, start GParted again, and check out the state of your partitions. If you can remember the old (down to a few Mb give or take), you can try resizing back to the old size.

---

### Post by Cheesemill on 2012-04-02
Cancelling Gparted and then not even waiting for the current operation to finish is a sure fire way to mess up your drive.

Your best way forward from here is to wipe the disk and then reinstall Windows and Ubuntu and then restore your data from a backup.

If you don't have a backup then your best bet is probably to use Testdisk to try and recover some of your data, be warned though, doing a full disk scan with Testdisk will take even longer than the partition resize would have taken in the first place.

---

### Post by Mark Phelps on 2012-04-02
Not to pick on GParted, but cancelling ANY partitioning operation before it is done risks serious damage to the affected filesystem.  In many cases, the damage is simply not fixable.

You'll probably have to try to recover what little data you can and reinstall from scratch.

---

### Post by schilkyl on 2012-04-02
I figure my only option is to just recover what I can. I can mount sda1  and get to my data. I assume all I need to back up really is my home  folder? Anyways, GParted doesnt recognize as a valid format so I cant do  anything with it.

---

### Post by CharlesA on 2012-04-02
> **Mark Phelps said:**
> Not to pick on GParted, but cancelling ANY partitioning operation before it is done risks serious damage to the affected filesystem.  In many cases, the damage is simply not fixable.

You'll probably have to try to recover what little data you can and reinstall from scratch.

+1. It's a good idea to backup your stuff before messing with partitions.

> **schilkyl said:**
> I figure my only option is to just recover what I can. I can mount sda1  and get to my data. I assume all I need to back up really is my home  folder? Anyways, GParted doesnt recognize as a valid format so I cant do  anything with it.

All you really need is your home folder, and any config files you might have changed (if you did at all).

---

### Post by santosh83 on 2012-04-02
> **schilkyl said:**
> I figure my only option is to just recover what I can. I can mount sda1  and get to my data. I assume all I need to back up really is my home  folder? Anyways, GParted doesnt recognize as a valid format so I cant do  anything with it.

Interesting that Gparted gets confused by the messed up filesystem, but LiveCD is able to mount it successfully! If GParted (based on libparted) doesn't work, then resize2fs (part of e2fsprogs) is probably also not going to work.

At this point you probably should just attempt to copy all the absolutely essential data and simply reformat.

---

### Post by schilkyl on 2012-04-02
In the process of right now. I think its interesting to note that right when I was using GParted to resize my partition, the cd kept whirring up and then spinning down. At some times it seemed not to be running at all which is part of why I decided to stop the resize.
I am not running a LiveUSB instead and find it to be much quicker and more responsive to anything I want to do.

---

### Post by Mark Phelps on 2012-04-02
> **schilkyl said:**
> At some times it seemed not to be running at all which is part of why I decided to stop the resize.

After it has done the partition analysis, while it is doing the first (simulation) run, if the code needed to do this is all now resident in memory, there would be no need to access the CD anymore.

So, lack of CD noise is not an indication it's done -- it's more an indication that it is doing serious hard drive work that does not involve accessing the CD.

---

### Post by schilkyl on 2012-04-04
> **Mark Phelps said:**
> After it has done the partition analysis, while it is doing the first (simulation) run, if the code needed to do this is all now resident in memory, there would be no need to access the CD anymore.

So, lack of CD noise is not an indication it's done -- it's more an indication that it is doing serious hard drive work that does not involve accessing the CD.

That does make sense. Thanks!

Computer is wiped, partitioned, and back to normal now less some preferences in applications. Thanks everyone

---

