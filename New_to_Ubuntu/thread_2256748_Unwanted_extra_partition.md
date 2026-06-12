---
title: "Unwanted extra partition"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by Evil Wayz on 2014-12-14
Something weird was going on when I put 14.04 on my system.  I have two hard drives, one from my linux mint system that I use for storage since it's 2 tb, and another 40 gig hd that my os is on.  Anyways it wouldn't recognize the forty gig drive, kept wanting to either install of the 2tb or wipe it off entirely.  So I ended up partitioning it manually and I screwed that up with a huge swap space.  So I used gparted live and shrunk the swap space down to a reasonable size which left me with 5 gigs of free space.  I  tried to expand the first partition into that space but it wouldn't let me.  So I created an ext4 partition there figuring i could use that.  Only it's ownership is root.  So what I need is either instructions on how to properly expand my primary partion so i don't hae this weird little orphan, or how to change permissions on that second partition so I can a tleast use it.

---

### Post by nerdtron on 2014-12-14
Please post a screenshot of Gparted to show your partitions.

Also, If you are installing Ubuntu on a computer with two hard drives, it's better to disconnect the 2TB hard drive first. This way, Ubuntu will be forced to install on the 40Gb hard drive.

---

### Post by Evil Wayz on 2014-12-14
[IMG]http://i57.tinypic.com/2d9pitt.png[/IMG]

---

### Post by The Cog on 2014-12-14
sda5 and sda6 are both inside the extended partition sda2. The easiest way out is probably to rearrange things from a live CD. 
Choose to try out rather than to install. Then launch gparted and do the following steps:
Stop using the swap partition: right click it and choose swapoff.
Delete sda5 and sda6.
Now you can delete the container sda2.
Enlarge sda1, leaving enough space for your swap partition
Create a swap partition in the remaining space.

---

### Post by Evil Wayz on 2014-12-14
I knew there was a reason why I couldn't extend sda1 but I couldn't figure out how to move that blue line, I forgot that was the original parameters of the swap.  I'll try that.

---

### Post by oldfred on 2014-12-15
If you delete & recreate swap, be sure to update fstab with new UUID for swap.
It should boot without update, but will give an error on partition not found.

       sudo blkid -c /dev/null -o list

 sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts:
sudo mount -a

---

