---
title: "My struggle to use Clonezilla..."
date: 2014-07-04
forum: New to Ubuntu
---

### Post by amzolt on 2014-07-04
I'm using 14.04...

I installed Clonezilla from the Software Center and chose "disk to disk" and "beginners mode"...

All I got was a menu that listed my "Source Disk"---sdb...

I have two internal hard disks on my computer and can see them as sda & sdb...

I want to select sda as Source and sdb as Target but can figure out no way to do this...

Help?

---

### Post by sudodus on 2014-07-04
The best way to use Clonezilla for normal users (who are not server gurus) is to download a Clonezilla iso file and make a boot CD/DVD/USB drive. Run Clonezilla as a live system booted from that drive :-)

Then the other drives (your sda and sdb) will be available as source drives for cloning/making compressed images.

---

### Post by cwmoser on 2014-07-04
Yes, make a bootable Clonezilla CDROM.  Then boot your PC on that CDROM.
Then with Clonzilla running from the CDROM all your hard drives will be available
for cloning.

Carl

---

### Post by amzolt on 2014-07-04
Thank you Sudodus and Carl---I'll give it a try...

---

