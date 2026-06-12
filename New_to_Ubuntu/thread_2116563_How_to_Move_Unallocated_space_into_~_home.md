---
title: "How to Move Unallocated space into ~ /home"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-02-16
/sda5 is ~/home. In GParted, to /sda5's left is 65 gig of unallocated space on the hard drive.

I tried expanding (in GParted terminology "resizing") the /sda5 to include the unallocated space, but the slider has nowhere to go.

Is it possible to make the unallocated space a part of /sda5? If 'yes' how do I go about doing that?

---

### Post by Yellow Pasque on 2013-02-16
You can't resize a partition when it's in use. Boot a LiveUSB and then you can resize. Note that the partition is inside the extended partion (the teal box), so you'll have to make the extended partition bigger first.

---

### Post by mcduck on 2013-02-16
sda5 is a logical partition, located inside the sda4 extended partition. So, to use the unpartitioned space, you'll first have to grow the sda4 to use that space. After that, growing sda5 should be possible.

Make sure you have proper backups, of course, as with any partition editing task... :)

---

### Post by Impavidus on 2013-02-16
Before you can grow sda4 you'll have to disable swap. Right click on sda6 and select swapoff (if I'm correct).

---

### Post by Mark_in_Hollywood on 2013-02-16
> **Temüjin said:**
> You can't resize a partition when it's in use. Boot a LiveUSB and then you can resize. Note that the partition is inside the extended partion (the teal box), so you'll have to make the extended partition bigger first.

I'm the OP. That top post was in LiveUSB. The screenshot should convey that. Sorry for the confusion.

I tried to do what is in these responses, before posting this. I turned 'swap' off, tried to resize - found nothing I could do, hence the OP.

I forgot to say that /home is backed up.

---

### Post by Mark_in_Hollywood on 2013-02-16
Is there an advantage to running Deja-Dup from LiveUSB session? Deja made a backup of /home in the last 3 days, and anything newer than that isn't critically important.?

I have my deja-duped backup on an external usb (320gig) drive. Current backup of /home take 50%.

If I use Deja-Dup in LiveUSB session, will there be a permission problem on restoring /home to /sda5?

I have mounted the external USB drive into /mnt. The filesystem calls it /sde1 (per GParted).

---

### Post by oldfred on 2013-02-16
Now you have moved swap in the way so you cannot do it. Your first post had swap after the /home, now it is between the unallocated and /home.

You will have to delete swap. When you recreate it, it will have a new UUID so you will have to edit fstab. Moving partition should not change UUID, but be sure to have working liveCd and be prepared to reinstall grub if necessary.

As posted above. You have to use liveCD, you have to right click and swap off.  You have to expand extended partition left into unallocated, move /home left into unallocated and then expand /home right. You can only expand partitions right, not left, but you can with extended.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Mark_in_Hollywood on 2013-02-16
EVERYTHING A-OK

I did have to run GRUB Recover - fsck (repair file system) I forgot the line entry on the GRUB Recovery screen, but after updating /sda3 the boot partition, all seems normal.


Thank you Old Fred and everyone else supporting me through this demanding process.

---

