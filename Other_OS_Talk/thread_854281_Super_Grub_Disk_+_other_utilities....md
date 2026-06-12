---
title: "Super Grub Disk + other utilities..."
date: 2008-07-09
forum: Other OS Talk
---

### Post by VCSkier on 2008-07-09
I'm trying to build a couple live cd's with some utilities that might come in handy, and I need some help.  I've been following Herman's guide, "[URL="http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html#How_To_Build_a_Super_Grub_DiskGParted"]
How To Build Your Own GParted LiveCD/Puppy Linux/Super Grub Disk CD[/URL]."  Unfortunately though, I've gotten to a point where I don't know how to continue.  I want to do things slightly different than the example Herman uses; I want one cd for general linux repairs and one for fixing up my friend's computers, who are more likely to be having Windows problems.

The linux disk, so far, would have[LIST]
[*]Super Grub Disk
[*]Parted Magic
[*]Puppy Linux
[*]SystemRescueCd
[/LIST]

While the windows one would have[LIST]
[*]Super Grub Disk
[*]Vista Recovery Disc
[*]Trinity Rescue Kit
[/LIST]

Those lists might change, and I'm certainly open to suggestions regarding them, but right now my primary concern is getting together the boot process of it all.

I've got all of the individual live cd's mounted, and then their contents merged into one directory.  Now, as the guide shows, I'm trying to use Super Grub Disk's boot/grub/menu.lst to add the others to the initial boot list, in my case Parted Magic, Puppy Linux, and SystemRescueCd.  I'm pretty sure with Puppy, I can just point it to the vmlinuz and initrd like this```
title Puppy-4.00-k2.6.21.7-seamonkey
kernel $(grub_device)/vmlinuz  root=/dev/ram0 pmedia=cd
initrd $(grub_device)/initrd.gz
```

Parted Magic and SystemRescueCd seem to be more complicated to me though.  Parted Magic seems to use vesamenu.c32 to boot, and I have no idea what SystemRescueCd uses.  Any help would be appreciated.  Thanks!

(I'm attaching my current boot/grub/menu.lst for Super Grub Disk)

---

