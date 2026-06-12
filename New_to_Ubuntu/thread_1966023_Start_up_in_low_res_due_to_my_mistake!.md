---
title: "Start up in low res due to my mistake!"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by johnspeedster on 2012-04-26
My reluctance to learn about partitioning has caught up and bit me on the ... I had been using several versions of Ubuntu for years then screwed 11.10 after I bought a new TV and loaded Serviio - but that's a different story. Loaded 12.04 happily and copied over bookmarks, tried and failed to move e-mail from Evolution to Thunderbird - but another different story. Started to bring Shotwell photos from an old version through to 12.04, but... I used copy instead of move and delete. Overnight, computer ran out of space and now only starts in low res and I'm lost. Booting from my Live CD, I can see (a mess!) I now have four situations. A 120 GB partition with 3.7 GB free, a 12 GB with 6.2 free, a 15 GB with 11.8 free, and a 9.4 with 0 free. Can I change partition sizes from the live CD? The other problems I can work away at, but this one has stalled me. Thanks for all the great advice the team gives us.

---

### Post by NoNameWill on 2012-04-26
Yes you can with gparted. I believe it is installed on the ubuntu live disk. I have only done it once. Don't remember what distro I used.

---

### Post by papibe on 2012-04-26
Hi johnspeedster.

You have very little space to resize.

This is what I would do:
[LIST]
[*]Use the live CD/USB to boot on it.
[*]Choose 'Try Ubuntu' instead of install.
[*]One on the desktop you can mount your partitions by going to 'Computer' (just double click on them).
[*]Delete all you can.
[*]Then try to boot normally.
[/LIST]

In case you still can't boot. You would need to move files out of your disk. Connect an external USB hardrive, or install another internal drive. Then you can use the same procedure describe above to move files out of your current disk to the new one.

Just some thoughts.
Regards.

---

### Post by johnspeedster on 2012-04-26
Thanks for those quick replies. Could not move data - photos - to external drive from sda9 as I am "not the owner" because I am using live CD I guess. I deleted "pictures" from the full partition - sda9 - and emptied trash thinking that would solve the problem but it had made no difference?? 
Gparted loads fine and I shrunk one partition -sda7 - from 15 down to 3GB. My full partition is not adjacent to this unallocate space and instructions to increase size of partition are not clear. When I shrunk the partition on the left of the problem sda9 and tried to increase the size at the beginning, I got a warning about shifting the start point and I backed off. Is that a legitimate way to do it? What I need to do eventually is to bring the data in sda6 = 120 Gb (mostly pictures using move and delete) into sda9 which is the 12.04 version. I can then delete (or whatever) sda5 and sda7 as they were two failed attempts at installing other Ubuntu versions and contain no data I need to save. Current order is sda5 with 6GB free, sda9 with 0 space, unallocated 3MB, sda7, then unallocated 11GB, sda8 swap total 3GB, unallocated 8MB, sda6 total 111GB. The other way will be to re-format and load data back from my last backup but I would prefer not to have to do that.

---

### Post by johnspeedster on 2012-04-27
Another though has occurred to me which may be my best option. If I uninstall 12.04, then install it again using better partition sizes and use correct file transfer procedures would that work? To do so, should I use the Live CD or do it from 11.10 which I have now discovered how to load?

---

