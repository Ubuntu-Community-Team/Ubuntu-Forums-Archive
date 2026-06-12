---
title: "Extra partition"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by BackBack on 2008-06-07
I had Windows Vista installed on my laptop, and I decided to have ubuntu as a second OS, but problem is I accidentally installed two partitions instead of two.  Under GParted I'm trying to trash the extra one, and resize the Vista one (I believe it's the NTFS one), and the Ubuntu one (not sure which one that would be).  I want them split 50%-50%, so roughly 68 gigs each.  Can I get a bit of help please?

Here's a screenshot of all the partitions I have.  I know that the recovery and swap stay unchanged, but what about the other three?

[http://img183.imageshack.us/img183/5903/screenshotcy3.png](http://img183.imageshack.us/img183/5903/screenshotcy3.png)

---

### Post by BackBack on 2008-06-07
Can I get a bit of help please? :/

---

### Post by dhughes on 2008-06-07
Boot with the LiveCD so the disk isn't mounted and just delete sda3 it's a container for sda5 and sda6 although you may have to delete sda5 and sda6 separately though and then finally sda3. Click save or apply to perform the action.

 Resize the NTFS partition to size you want. Click apply to perform the action.

 Make the new partition for Ubuntu. Click apply to perform the action.

 Other than that, I'd make the Swap 2GB, to me 4GB seems a bit large. I would also make a two partitions (three if you include Swap), the other one would be for /Home it would be about 70% bigger than / (for root). I like having a separate partition for /Home for safety. That's just my personal preference but it's not required of course it's up to you, keep it simple if this whole thing is new to you.

---

### Post by avtolle on 2008-06-07
I'd advise using the Vista app to resize that partition as well.

---

### Post by BackBack on 2008-06-07
But that's just my problem, I **am** running Gparted through the LiveCD, but it's not letting me move/resize or delete.  I'm assuming it's because of those two locks by exnteded and linus-swap, and I can't seem to get rid of them.

It's asking me to "unmount any logical partitions having a number higher than 5." How would I do that?

---

### Post by avtolle on 2008-06-07
> **BackBack said:**
> But that's just my problem, I **am** running Gparted through the LiveCD, but it's not letting me move/resize or delete.  I'm assuming it's because of those two locks by exnteded and linus-swap, and I can't seem to get rid of them.

It's asking me to "unmount any logical partitions having a number higher than 5." How would I do that?
Something to check: did these partitions get mounted by the system? I've had this problem before, so minimize the Gparted window, and see if the partitions (volumes) are shown as mounted on the desktop. If so, right click and unmount. I'll warn you to be quick about getting back into Gparted once unmounting, as there is a nasty quickness to the speed with which the same are mounted again.

---

### Post by BackBack on 2008-06-07
I only see the install shortcut on the desktop.  Is there a different place on the LiveCD that I could find it?

---

### Post by dhughes on 2008-06-08
> **BackBack said:**
> I only see the install shortcut on the desktop.  Is there a different place on the LiveCD that I could find it?

 When using the Ubuntu Live CD if on the menu up top you click 'Places' (it's to the right of 'Applications') and then 'Computer' you'll see any mounted or unmounted drives that have been detected.

 Right click the device you don't want mounted and choose Unmount Volume since you can't alter a partition on a drive that is in use(mounted).

 Once you do that you should be able to do what was discussed above i.e. deleting the partitions you want to delete and resize.

---

### Post by Stefanie on 2008-06-08
if you want to resize or modify your swap-partition, try right-clicking the partition in gparted and select "swapoff". for some reason, my swap is always on even when i'm running the live cd.

---

