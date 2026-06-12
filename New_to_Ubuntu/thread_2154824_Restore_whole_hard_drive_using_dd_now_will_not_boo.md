---
title: "Restore whole hard drive using dd now will not boot"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by tododo on 2013-06-16
Hi
Running ubuntu server 12.04 

Tried recovering hard drive using dd in the live environment from a whole disc image - seemed to go well
But on boot I had a grub rescue prompt - seemed to repair that with boot repair but still not entirely booting

Im assuming its an MBR thing 

[http://paste.ubuntu.com/5768657/](http://paste.ubuntu.com/5768657/)

Any advice anybody - completely stuck

Thanks for any info

---

### Post by sudodus on 2013-06-16
Do you have a script or some note of how you created the disk image?

Maybe you restored an image of the whole drive to a partition (or vice versa). You need to run exactly the inverse procedure compared to the backup (when you created the disk image).

Please post the dd command you were running!

-o-

*Warning*: Double-check and triple-check the command line, when you run dd. It is nick-named 'disk destroyer' because a minor typing error can overwrite valuable data.

---

### Post by oldfred on 2013-06-16
You are missing swap on sdc. And it shows an extended partition with no entry.

Normally you can boot with missing swap, but perhaps the MBR table error is preventing booting. Grub needs to scan partition table and wants that to be correct or it does not work.
I might create new swap and update UUID in fstab.

---

### Post by sudodus on 2013-06-16
If you had a backup of the whole drive, dd would have restored also the swap partition, but not if it was a backup of only a partition.

If you had a backup made by Clonezilla, the swap partition would not be saved.

---

