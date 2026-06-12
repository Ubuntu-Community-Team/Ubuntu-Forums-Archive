---
title: "Partition resize trouble"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by daisygirl on 2008-07-12
I searched but couldn't manage to find any existing threads describing the problem I'm having.

512MB ram, and I think 2.1GHz processor.

I'm trying to resize my Windows partition (currently the entire drive) using the live CD.  When I selected the new size I wanted the partition to be (about 50GB smaller) and started the process, it looked okay at first--CD drive making sounds and a dialog box showing 0% progress.  

But it stayed at 0% for quite some time.  I left it alone for about an hour, and when I came back the monitor had powered itself off.  I wasn't sure if it had finished and hibernated or what, so I clicked with the mouse, which powered the monitor back up, but the screen is entirely blank.  Clicking also made the CD drive start whirring again.  

Right now the power lights on on the computer and monitor are on, but screen still blank and nothing seems to be happening.   I did hold down the power button for a few seconds trying to reboot in case it was done, but nothing happened at all.  I'm leery of hitting the big power switch in the back in case it's actually still doing something.

So my questions are:

1) How long should resizing a partition take, and is it normal for the monitor to blank out like that?  I know it warned me at the beginning that it could take "quite some time" but I'd expected I'd be able to see the progress dialog while it was working.

2) Is something really awful likely to happen if I force the machine to reboot and it turns out it was still resizing the partition?

Thanks!

---

### Post by TSS on 2008-07-12
If you have Windows Vista I suggest you use the built in tool to shrink the partion. 
See: [http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

I've also never heard of a partition operation that takes longer then an hour, but that's just me!

---

### Post by daisygirl on 2008-07-12
Sorry, forgot to put that in my post.  It's WinXp (home edition, which doesn't have any kind of especially useful tools included, right?)

---

### Post by TSS on 2008-07-12
The built in partitioning tool for Windows XP does not shrink volumes (I don't think).  

You might try a GParted LiveCD: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Read this: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

The above tutorial uses Windows Vista but it should apply to XP as well.  Also, make sure you back up your data and have your Windows XP install disk available!  You'll need to repair the installation to be able to boot into XP.

EDIT: I forgot to mention that it is possible that shrinking the partition might take a bit, depending on your computer.  I don't want to give you bad advice, but GParted has always worked for my partitioning needs.

---

### Post by daisygirl on 2008-07-12
Thanks!

I went ahead and used the main power switch to reboot.  Fortunately it really had finished and I have two partitions now--I was really concerned that I'd be messing it up.  Huge relief there.

I also have a CD with GParted and some other tools on it, which I'd forgotten I even had.  Think I might just finish up making the various partitions I still need with that before switching back to the Ubuntu CD to install.

---

### Post by Gannon8 on 2008-07-12
Check both filesystems, just in case. There maybe an error.

---

