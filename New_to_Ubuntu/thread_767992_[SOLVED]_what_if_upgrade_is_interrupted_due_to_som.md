---
title: "[SOLVED] what if upgrade is interrupted due to some reason?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by bhadotia on 2008-04-26
Hi everybody!

I am upgrading my ubuntu at present .


When the upgrade started upgrade manager told me that some 1400 packages were needed to be downloaded which meant some 1.5gb. Now while the manager was downloading files I recieved the message:
100% disk space in use.
I had got only 3.77gb space left in my root partion when I started the upgrade. I thought that this would be enough for the upgrade. 
The upgrade manager window is still there , but I don't  think that  it is downloading the files.

Need help: what should I do?

---

### Post by warbread on 2008-04-26
```
 :-$ sudo apt-get clean 
```

That should free up some disk space.  I suggest cancelling the download and starting over once you've run 'clean'.  Don't worry, it'll be fine.  The worst problem you'll run into is some broken packages.  Those are easily dealt with.

---

### Post by bhadotia on 2008-04-26
After running the command I see that there is still only 695mb of space left and I think that some 1300 packages still need to be downloaded.

So can anything be done? Or will this much space be  enough?

Is there no  way in which  we can  resize  the  root  partition my root partition is 9.4gb (with 8.7 gb used)? my home partion is 30 gb.

---

### Post by warbread on 2008-04-26
I would resize your partitions, yes.  I always have at least 12 gigs for my root partition.  

Funny, I seem to remember autoclean freeing a lot more disk space than that...

---

### Post by amohanty on 2008-04-26
From the man page:
 autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

So if the upgrade needs local packages it will be kept around :)

---

### Post by bhadotia on 2008-04-26
So how can we resize the root partition?

---

### Post by amohanty on 2008-04-26
boot up with live CD.
fire up the partition editor
make sure root partition on hdd is not mounted. if it is:
in a terminal find mount points:
mount -l
sudo umount <mount point>

then resize.
HTH
AM

---

### Post by warbread on 2008-04-26
Ahem... **Be very careful when resizing partitions with data you want to keep.** This process comes with no warrenty or guarantee.  I'm not saying it's likely, but you **might** end up losing data if you resize a partition.  Always, always, always back up anything you don't want lost.  That said,


Live boot, then.

```
:-$ sudo apt-get install gparted 
```

Then, gParted can be found in Administration > gParted.  This will display all of your drives and partitions.  Click on your /home partition and click "resize".  Change the size to what you want, and then repeat the process for the root partition.  Hit 'apply'.

Let us know if you have more specific questions.

---

### Post by bhadotia on 2008-04-26
Live boot means booting with the live cd , is it ? If that is so I am doing that. I will again login through the live cd . Plz stay with me.

---

### Post by amohanty on 2008-04-26
> **warbread said:**
> Ahem... **Be very careful when resizing partitions with data you want to keep.** This process comes with no warrenty or guarantee.  I'm not saying it's likely, but you **might** end up losing data if you resize a partition.  Always, always, always back up anything you don't want lost.  That said,


Live boot, then.

```
:-$ sudo apt-get install gparted 
```

Then, gParted can be found in Administration > gParted.  This will display all of your drives and partitions.  Click on your /home partition and click "resize".  Change the size to what you want, and then repeat the process for the root partition.  Hit 'apply'.

Let us know if you have more specific questions.

whoops forgot that you mentioned live  boot... sorry

---

### Post by bhadotia on 2008-04-26
Thanks I've resized the root partition  to 20gigs  and  am performing  the  upgrade now.

---

