---
title: "Hard disk partition unmount."
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Pagh on 2008-10-28
Hello everyone.

I have a problem regarding the partitions on my hard drive. I currently have a 50 Gib big partition (ext3 - Ubuntu) and a 25 Gib (ext2 - for backup)
I want to delete the Ubuntu partition so that i can use the 50 gib (+ the 75 Gib that is currently just free) to do a re installation on Ubuntu 8.4.

But the problem is that when I use Gparted (live-session) to delete the partition it's says that it is unable to do so and that i must first 
"unmount any logical partitions having a number higher than 6"

I have, all in all, 5 partitions first the backup thing (called /dev/sda1),
a partition called extended (/dev/sda2) under witch the ubuntu partition (/dev/sda6) a two swap partitions (/dev/sda7 and /dev/sda5) is placed.

As far as i can see from the error massage i have to unmount one of the swap partitions.

Here comes my quistion - will it damage the rest of my partitions if I, say, unmount /dev/sda7/? and if I do so will I then be able to delete the rest of the partitions (excluded the backup partition).

All the best.
I hope some one can help me so I don't have to stay in this live session forever.

Ps. Sorry for my bad English - i hope you was able to understand me.

---

### Post by dracayr on 2008-10-28
well you can delete the partitions if you're running from a live cd. It is safe to unmount a swap partition, just swapoff before doing that (right click&#8594;swapoff)

dracayr

---

### Post by Pagh on 2008-10-28
Thanks i'll try that

---

