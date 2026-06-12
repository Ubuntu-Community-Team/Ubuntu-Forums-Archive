---
title: "Stuck In hd0 limbo"
date: 2015-12-04
forum: New to Ubuntu
---

### Post by russell14 on 2015-12-04
I am trying to get my inherited server to boot.  I am installing Ubuntu 14.0.4.3 (desktop version, it's what was on it before).  
I had to replace all four hard drives in the server.
It is in a RAID-1 config with a LSI MegaRAID SAS 9260-4i card.  (again, this is what was installed before)

So, installer worked as advertised.  I reboot, and get **error:attempt to read or write outside of disk 'hd0'**
Tried some fixes I found online monkeying around with grub repair and still halts at error.
I went ahead and booted off of the live installer CD and installed boot-repair.  Let it did it's thing, along with updating my GRUB to 2.02
Still no joy.  Here's my pastebin from boot-repair: [http://paste.ubuntu.com/13681424/](http://paste.ubuntu.com/13681424/) 
I'm not quite sure where to go to next.  My knowledge is fairly limited, but if someone could point me in the direction of getting this server back up I'd be eternally grateful.  

Thanks.

---

### Post by gordintoronto on 2015-12-05
RAID 1 is for two drives, with one being an exact image of the other. With four drives, RAID 5 would be appropriate.

---

### Post by sandyd on 2015-12-05
If possible, do not use RAID5.
If you have a single failed drive, depending on the rated URE (unrecoverable read error) of the drives, if one of the remaining drives suffers a URE, your raid is dead, and will no longer be recoverable.

If you have a large drive (1T or higher), you will be much more likely to get a URE, as the average URE rating is between 10^14 and 10^16. That means that you will have a 1 in 10^14 chance of having a sector on the drive getting a URE. The larger the disk, the larger the amount of sectors (A URE affects a sector), and the higher chance you will not be getting your RAID back.

Use RAID10 or RAID6.

RAID6 will be slower (2x read speed) but offer more protection, RAID10 will be faster (4x read, 2x write) but tolerate a single drive failure.

---

### Post by gordintoronto on 2015-12-06
Sorry, Sandy, but the point of RAID 5 is that no data is lost if a single drive fails. RAID 6 can survive the loss of two drives.

Ref: [https://en.wikipedia.org/wiki/Standard_RAID_levels](https://en.wikipedia.org/wiki/Standard_RAID_levels)

---

### Post by sandyd on 2015-12-06
> **gordintoronto said:**
> Sorry, Sandy, but the point of RAID 5 is that no data is lost if a single drive fails. RAID 6 can survive the loss of two drives.

Ref: [https://en.wikipedia.org/wiki/Standard_RAID_levels](https://en.wikipedia.org/wiki/Standard_RAID_levels)

Read the part about UREs and drive sizes in my earlier post, it is not about how many drive failures the array can have, but the chance of your RAID failing when you reassemble the array due to remaining drives encountering a URE.

More information on UREs and why RAID5 should not be used anymore here: [http://www.zdnet.com/article/why-raid-5-stops-working-in-2009/](http://www.zdnet.com/article/why-raid-5-stops-working-in-2009/)

---

### Post by russell14 on 2015-12-07
Woah...didn't mean to touch off a RAID discussion.  I'll try it in a RAID 6(?) and see where that gets me.

---

### Post by russell14 on 2015-12-08
Well, that did it.  Thanks!

---

