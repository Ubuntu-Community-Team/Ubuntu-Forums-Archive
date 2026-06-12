---
title: "getting back to windows 7 from ubuntu"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by swisss on 2013-02-07
I had windows xp on my pc and got a bunch of viruses on it.  Figured it was about time to reformat it.  Reformatted everything not knowing that there was a smaller partition that was for restarting everything.  So once i reformatted it, it pretty much became a paper weight.  I figured i had nothing to lose by putting on a free operating system to see if i could use it.  After using ubuntu for a while it keeps crashing and it's difficult to navigate around.  Long story short i want to get back to windows and have gotten my hands on a windows 7 boot disc.  Everything i find on the net says to just let windows install and it will overwrite anything it needs to to work.  It came up with a blue screen after a bit of loading and installing.  It said it stopped things from working because it could have caused issues to my pc.  Read around and tried "Memtest86".  It is currently running and has so far racked up 780 failing addresses.  This seems pretty bad but i don't know where to go once it finishes.  Are these errors from the install that failed or is there something physically wrong like fried components?

---

### Post by aspergerian on 2013-02-07
I wonder if your XP pc has insufficient capacity for running Ubuntu 12.04 well. Before you install w7, you might try Xubuntu.

---

### Post by swisss on 2013-02-07
i'm trying to get away from ubuntu.  Is there a way of getting everything off and trying the windows 7 install from scratch?

---

### Post by Cheesemill on 2013-02-07
If you are getting that many errors from memtest then it's probably a hardware issue.

Failing RAM would also have caused the crashing in Ubuntu.

---

### Post by sudodus on 2013-02-07
> **swisss said:**
> i'm trying to get away from ubuntu.  Is there a way of getting everything off and trying the windows 7 install from scratch?
I think that Windows can overwrite an old operating system, if it is Windows or another one does not matter. If you wish, it is possible to overwrite the partition table and the file systems (the first few megabytes is probably enough, but you can overwrite the whole disk). But I think it is not necessary. Instead wipe the partitions, and let Windows create partitions on a clean disk. This means that the bits of the data files are still there, but the partition table and the file system tables are wiped.

If this is what you want, use the Ubuntu boot disk, and boot the computer into a live session. When it is running, you can start ***gparted. ***It is a GUI program, where you select which drive to view and edit. Then you can delete all the partitionsfrom the internal drive.

---

### Post by sudodus on 2013-02-07
> **Cheesemill said:**
> If you are getting that many errors from memtest then it's probably a hardware issue.

Failing RAM would also have caused the crashing in Ubuntu.

+1
You need to solve the problem found by memtest, before installing any new operating system.

---

### Post by swisss on 2013-02-07
it's been going now for 2.5 hours and found 1167.  It keeps getting to 100% then resetting back to 0.

---

### Post by Cheesemill on 2013-02-07
> **swisss said:**
> It keeps getting to 100% then resetting back to 0.
That's what memtest does, it will keep running the tests forever unless you tell it to stop.
It does this because you sometimes get intermittent errors that don't show up if you only do one pass.

---

### Post by sudodus on 2013-02-07
> **swisss said:**
> it's been going now for 2.5 hours and found 1167.  It keeps getting to 100% then resetting back to 0.

If you get more than 0 errors after a whole night running memtest, it is too much.

So if you have more than one memory card, remove them systematically, and test with memtest again, until you can identify which card is bad (it is probably only one bad card). Often there is a lifetime guarantee on RAM cards, so you can try to get it replaced, if you have some document showing where you bought it (or if you bought it with the computer).

---

