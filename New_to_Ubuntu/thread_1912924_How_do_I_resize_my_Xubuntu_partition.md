---
title: "How do I resize my Xubuntu partition?"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by BareRuinedChoirs on 2012-01-21
As the picture attached to this message illustrates, there is a big area of unallocated space on my HDD immediately before my linux partition. 

I'd like to use GParted to expand my Xubuntu partition (sda3) so that it fills this space. 

So my two questions are:

1. What is the best way to do this? [i.e. do I move and then resize sda3, or is it possible to just expand it directly into the preceding empty space?]

2. Do I need to update Grub2 or anything like that? 

I realise that there is still the potential for me to add a fourth partition to my drive, but I'd rather not do this right now, since I might want to create a shared partition with Windows in future.

Apologies if this question has been answered before -- I've looked through the forums, but am a complete newbie and so would appreciate a definite answer.

---

### Post by Cheesemill on 2012-01-21
Make sure you have a backup before messing with your partitions.

Boot from a Live CD and then run gparted.

Right-click on /dev/sda6 and select swapoff to unlock your extended partition.

Resize /dev/sda3 to use all available space.

Resize /dev/sda5 to fill the extended partition.

You shouldn't need to touch Grub.

---

### Post by BareRuinedChoirs on 2012-01-22
Thanks for the advice -- I've successfully resized the partition using the method you suggested, and Grub didn't need to be changed.

---

