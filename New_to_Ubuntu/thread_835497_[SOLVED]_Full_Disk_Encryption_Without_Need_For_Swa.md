---
title: "[SOLVED] Full Disk Encryption Without Need For Swap Password"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by shanepardue on 2008-06-20
Is there a way to unlock both the partition and the swap with one password? 
I installed Ubuntu with the encrypted option on the alternate disk, but 
would like to only type the encryption passkey once if at all possible. 
Thanks for any help!

---

### Post by AusIV4 on 2008-06-20
Using the alternate CD, I did the following.

Create a small (250ish MB) partition for /boot.

Allocate the rest as an encrypted device.

Set the encrypted device to be an LVM volume.

Divide the LVM into desired volumes (I did a 10 GB root, 2 GB swap, and the rest for /home).

Run the installer.

When you boot, it should prompt you for one password which will decrypt everything.

---

### Post by Golem XIV on 2008-06-20
Unless you did a manual setup, all your partitions are encrypted with the same password.

The password isn't really used to encrypt the data, rather itr is used to encrypt the key(s) that encrypt the data.  This way you can have one password for all partitions.

---

### Post by shanepardue on 2008-06-20
> **AusIV4 said:**
> Using the alternate CD, I did the following.

Create a small (250ish MB) partition for /boot.

Allocate the rest as an encrypted device.

Set the encrypted device to be an LVM volume.

Divide the LVM into desired volumes (I did a 10 GB root, 2 GB swap, and the rest for /home).

Run the installer.

When you boot, it should prompt you for one password which will decrypt everything.
Ahh, so the key is setting it up as an lvm volume? I didn't do that step. 
If that's the case, I'll have to try imaging my partition and redoing this 
or is there a better way to fix the situation?

---

### Post by shanepardue on 2008-06-20
> **Golem XIV said:**
> Unless you did a manual setup, all your partitions are encrypted with the same password.

The password isn't really used to encrypt the data, rather itr is used to encrypt the key(s) that encrypt the data.  This way you can have one password for all partitions.
I did do a manual setup. They both have the same password, but it still asks twice 
each time. I'd like to avoid reinstalling if at all possible, but I'm not seeing an 
option since it's really annoying to type this many passwords to get my computer up 
and running.

Thanks for your help!

---

### Post by bodhi.zazen on 2008-06-20
Fastest solution for you , set up a swap file.

[http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3](http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3)

[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

Then comment out or delete the entry for your swap partition.

You can resize the crypt if you like (use gparted to delete the swap partition, enlarge the crypt, make swap file => viola)

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by shanepardue on 2008-06-20
> **bodhi.zazen said:**
> Fastest solution for you , set up a swap file.

[http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3](http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3)

[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

Then comment out or delete the entry for your swap partition.

You can resize the crypt if you like (use gparted to delete the swap partition, enlarge the crypt, make swap file => viola)

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
I'm thinking a swap file may decrease performance, but maybe I'm wrong...

If I were to image and restore the partition, would I just lukeOpen the partition 
from a livecd, image it, then install Ubuntu the right way restoring the image in 
the same spot?

Sorry for the abundance of questions, I just want to make sure my plan is on the 
right track. Thanks!

---

### Post by shanepardue on 2008-06-20
I just reinstalled..thanks guys!

---

### Post by bodhi.zazen on 2008-06-20
> **shanepardue said:**
> I'm thinking a swap file may decrease performance, but maybe I'm wrong...

If I were to image and restore the partition, would I just lukeOpen the partition 
from a livecd, image it, then install Ubuntu the right way restoring the image in 
the same spot?

Sorry for the abundance of questions, I just want to make sure my plan is on the 
right track. Thanks!

In theory a swap partition is faster because you do not have the overhead of a file system.

In practice, if you are using swap you are already taking a performance hit and I *doubt* a swap partition would feel slower then a swap partition on anything close to a modern computer. How much ram do you have ? Do you even use swap ?

---

### Post by tkibugu on 2011-12-15
_[I deleted post contents]_
[]("http://agnulinuxuser.blogspot.com/2011/12/encrypting-swap-partition.html")

---

