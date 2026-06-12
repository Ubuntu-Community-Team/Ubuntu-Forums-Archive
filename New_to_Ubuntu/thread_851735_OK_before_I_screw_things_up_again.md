---
title: "OK before I screw things up again"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Atomic Dog on 2008-07-07
I tried to install hardy today and screwed the pooch.  Luckily I made a HD image, which I restored, and want to set about to install hardy cleanly on my laptop.  My setup:
Vista partition
XP partition
Gutsy EXT3 partition
Grub for bootloader

I want to wipe out gutsy and do a clean install of hardy at least on the same partition, preferably wipe out the existing gutsy partition and create a new one adding the free 25gb I have after my gutsy partition.

If I delete the Gutsy partition, the Hardy disc does not "see" the vista and xp partitions (wants to use the whole drive only - probably because it obviously messes up grub when I delete the gutsy partition).  I don't see a way to tell Hardy to use the existing ext3 partition (if I can't wipe it out and create a new partition/install), or the right way to get it installed without hosing vista or XP.

Any suggestions are appreciated.

---

### Post by ibuclaw on 2008-07-07
Selecting "**manual**" when the partition editor crops up in the install steps sounds like a good idea from the information you've given.

You get full access to the hard-drive layout, so you can explicitly set the ext3 partition as your root.

Regards
Iain

---

