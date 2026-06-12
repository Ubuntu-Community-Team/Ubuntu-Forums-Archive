---
title: "LiveCD Casper script"
date: 2007-10-17
forum: Programming Talk
---

### Post by picopir8 on 2007-10-17
I am making a custom liveCD and I am editing the casper script (/usr/share/initramfs-tools/scripts/casper). 

I am trying to add additional mount options to the persistent mount but I am not sure how to go about doing it.

Existing line looks like:
mount ${cowdevice} -t ${cow_fstype} -o rw /cow || panic "Can not mount $cowdevice on /cow"

I wanted to add the sync option so I tried:
mount ${cowdevice} -t ${cow_fstype} -o rw,sync /cow || panic "Can not mount $cowdevice on /cow"

and...
mount ${cowdevice} -t ${cow_fstype} -o rw -o sync /cow || panic "Can not mount $cowdevice on /cow"

but neither worked.

Any suggestions?

---

