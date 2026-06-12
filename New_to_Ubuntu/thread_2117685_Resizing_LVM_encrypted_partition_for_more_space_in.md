---
title: "Resizing LVM encrypted partition for more space in /boot"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by androssofer on 2013-02-19
So I ran update manager (on 12.10),

and it needs my boot partition to be a bit bigger (5 or 6 mb)... However my main partition is an LVM encrypted volume..

Does anyone have any ideas how to resize the LVM volume and increase the boot partition? 

I found a few posts on it, but most are either super complex, from a few years ago, or both..

Regards

Andy

---

### Post by tidmarsh on 2013-02-19
I have the exact same problem. I found [this post]("http://ubuntuforums.org/showthread.php?t=1938039") from about a year ago that says "If you used LVM, it was very easy," but doesn't tell how to do so.

I'm also stumped.

---

### Post by androssofer on 2013-03-20
Bump...

from what i found so far, this looks horrendously annoying to achieve.. you have to create a new boot partition, move boot files, delete the old, then start grub in recover mode, reinstall it.. 

but as far as I can see GParted doesn't support encrypted disks, so its not safe to resize the partition, as it doesn't know what its moving.. So i got no room for a new boot... 

Any easier methods?

---

### Post by androssofer on 2013-03-21
Found a solution to the update problem: (resize issue is still there, but not a concern now updates are working)

follow this guide to remove old kernels:

[http://www.liberiangeek.net/2012/10/remove-old-kernels-from-ubuntu-12-10-with-ubuntu-tweak/](http://www.liberiangeek.net/2012/10/remove-old-kernels-from-ubuntu-12-10-with-ubuntu-tweak/)

(is other ways using synaptic package manager if you don't like ubuntu tweak, just google "remove old kernels ubuntu")

once that is done it clears space on /boot

then run your update and the latest kernel should install :-)

---

