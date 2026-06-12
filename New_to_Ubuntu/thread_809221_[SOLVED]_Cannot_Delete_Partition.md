---
title: "[SOLVED] Cannot Delete Partition"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by melrom on 2008-05-27
hi-

my computer was partitioned to have 71.31 gigs to windows and the rest to linux [out of a 100 gig HDD] on an extended. I guess Gutsy was on sda5 with sda6 as swap, and Hardy installed as sda7 with sda8 as swap. The problem is that I can't delete sda5 and sda6. It keeps telling me that I have to unmount any logical partitions having a number higher than 5. But they aren't mounted as I'm using a live CD to do this. what's going on/can i fix it?

-melrom

---

### Post by forestpixie on 2008-05-27
Without seeing and knowing if it's a gparted or buntu livecd - if it is the buntu livecd - it will be using swap unless you have turned it off.

---

### Post by melrom on 2008-05-27
for now, i just shrunk the gutsy partition to be like 1 gig and then used the added the unallocated space onto the hardy install, since i don't use the gutsy partition.

i didn't really understand your response. I should delete the swap first, you're saying?

---

### Post by forestpixie on 2008-05-27
Sorry - if you are using the buntu livecd it will be using any swap it finds to help run the live os.

If that is the case you can turn it off and it shouldn't stop you moving partitions - you have 2 swaps - 1 installed with gutsy and 1 with hardy, you certainly won't need both. To be able to work on the swap partition

```
sudo swapoff
```

If you are using the ubuntu livecd post a scrnshot of gparted if youlike.

---

### Post by alienexplorers on 2008-05-27
Boot Hardy 8.04 off your hard drive.  Enter in terminal:
> mount
check to see if sda5 and sda6 are listed if so run:
> sudo umount /dev/sda5
sudo umount /dev/sda6
If /dev/sda6 does not unmount then run:
> sudo swapoff
Try unmounting /dev/sda6 again.
Rerun the > mount command.
make sure sda5 and sda6 are not listed.
Run > sudo gparted and try deleting sda5 and sda6.

---

### Post by melrom on 2008-05-27
thanks guys. :)

---

### Post by melrom on 2008-05-27
actually this did not help and i still cannot delete the partitions.

-melrom

[edit:] yes it did. i'm a fool.

---

### Post by forestpixie on 2008-05-27
No you're not - especially if you can mark the thread solved :)

oops you did

---

