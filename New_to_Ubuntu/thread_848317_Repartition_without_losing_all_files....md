---
title: "Repartition without losing all files..."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by khr on 2008-07-03
When I installed Ubuntu, I didn't manage to find out how to divide it into 2 partitions. Edit was gray so I just went with 1 partition. Now, I've got games to work on Ubuntu, but they still lag a lot, even on the lowest possible settings. I want to get Vista back. So is it possible to divide my Ubuntu partition into 2 partitions without reformatting my hard drive?

---

### Post by Elfy on 2008-07-03
If you are saying that you currently have ubuntu and wish to install vista as a dual boot then there is no reason why not. You need to resize the partition on which buntu is installed and create a partition for vista to be installed on without reformatting the whole drive.

If you want to just have vista - then no, you can't.

---

### Post by chrisccoulson on 2008-07-03
If you've got files that you really don't want to lose, then there is no substitute for a backup when you're playing around with partitioning tools....

---

### Post by khr on 2008-07-03
Hmmm, I think you guys misunderstand.
I have 1 partition.
I want to divide that partition, so I'll get two partitions.
Is it possible to divide my 1 partition into 2 partitions without losing my files and settings in Ubuntu?

I'm sorry for any misunderstanding.

---

### Post by chrisccoulson on 2008-07-03
I didn't misunderstand. Yes, you can split one partition in to 2 by shrinking the current one and adding another in the unallocated space. While your files will probably still be intact, if there are files which you really don't want to lose then there is no substitute for a good backup when you do this type of thing.

---

### Post by khr on 2008-07-03
> **chrisccoulson said:**
> I didn't misunderstand. Yes, you can split one partition in to 2 by shrinking the current one and adding another in the unallocated space. While your files will probably still be intact, if there are files which you really don't want to lose then there is no substitute for a good backup when you do this type of thing.

Ok, thanks!
But how do I do it?

---

### Post by aashay on 2008-07-03
Yes.Use Gparted. Though you will not lose any files 99.99% of the time, there is a slim chance of it happening. I myself have never seen it screw up though. As a matter of fact, i am having one partition resized as I write this (going to try fedora)
Install it:
```
sudo apt-get install gparted
``` 
Run it:
```
sudo gparted
```
The GUI will guide you through the rest of the process
Edit: Just make sure you resize the partition so that the old (ubuntu)one is on the left and the new one on the right

---

### Post by Elfy on 2008-07-03
Yea - didn't misunderstand just making sure :)

As chrisc has said make sure you have backup - working with partitions could possibly lead to data loss.

Boot with your livecd - once it's loaded there is a partition editor in the system >admin menu - partition editor.

Before you open that thouhg the livecd will have used your swap - you need to turn that of first, open aterminal

```
sudo swapoff -a
```

Now open the partition editor - there should be 1 ext3 partition this is the installation, right click it and choose resize - then choose how big you want it to be  and apply, it will resize the partition and there will now be unallocated spce once it has finished.

If it is an extended partition you will nedd to resize that after it has finished.

Then you should have unallocated space - right click that and create new partition filetype ntfs and install to it.

It might take a while to do - I mean hours - so do not turn it off.

If vista can't find it when you try to install to the new partition, you might need to move it to the front of the disc.

---

### Post by khr on 2008-07-03
> **aashay said:**
> Yes.Use Gparted. Though you will not lose any files 99.99% of the time, there is a slim chance of it happening. I myself have never seen it screw up though. As a matter of fact, i am having one partition resized as I write this (going to try fedora)
Install it:
```
sudo apt-get install gparted
``` 
Run it:
```
sudo gparted
```
The GUI will guide you through the rest of the process
Edit: Just make sure you resize the partition so that the old (ubuntu)one is on the left and the new one on the right

Thanks!
I'll do it know, but I'll backup just in case...

---

### Post by Elfy on 2008-07-03
> I myself have never seen it screw up though.Unfortunately I have and I lost a drive full of music - had backups that time.

There is always the possibility of outside influence - lightning, building collapsing, workmen driving digger bucket through mains cable - all will cause gparted to stop in the middle of the most important part of the process Just when it was moving the one file you could not under any circumstances lose. :)

---

### Post by Elfy on 2008-07-03
You shouldn't need to install gparted, it's on hardy - not sure about gutsy or feisty, but you can't do it from within the running ubuntu - you must do it through the livecd.

---

### Post by aashay on 2008-07-04
> **forestpixie said:**
> Unfortunately I have and I lost a drive full of music - had backups that time.

There is always the possibility of outside influence - lightning, building collapsing, workmen driving digger bucket through mains cable - all will cause gparted to stop in the middle of the most important part of the process Just when it was moving the one file you could not under any circumstances lose. :)
Working on a laptop obviates most of them. :)

---

### Post by Elfy on 2008-07-04
Must say that I've never had a dodgy battery on a desktop though :)

Whether people do backups or not is their business, as long as I've pointed it out and the possibility of gparted crashing then I've done my bit.

---

### Post by BudE on 2009-03-12
> **chrisccoulson said:**
> If you've got files that you really don't want to lose, then there is no substitute for a backup when you're playing around with partitioning tools....

Good afternoon. Newbie to Ubuntu and interested in this topic too as I am about to repartition mine as well. However, I finally got Ubuntu to make my wireless network connection to work and would not want to lose whatever it took to set it up correctly. Is there anyway to back that up so I won't lose access to my wireless network? 
thanks
Bud:D

---

