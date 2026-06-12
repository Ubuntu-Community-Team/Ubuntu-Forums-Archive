---
title: "How do I expand or shrink a partition?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Jackfrost123 on 2008-05-25
I installed ubuntu dual boot with vista on an ext3 partion on the same physical disk. I want to shrink the vista partition and expand the ext3 one. I don't mind deleting the ntfs partition altogether but I want to expand the ext3 one for sure! Partition editor doesn't seem to give me that option...Thanks!

Also I want to expand my swap partition. I get constant error that there is not enough swap to hibernate, why is that? I have 600 mb swap and a 512 memory.

Thanks fellas!

---

### Post by cdtech on 2008-05-25
The best method is to use gparted with the live CD. It worked for me.

---

### Post by Inxsible on 2008-05-25
+1 for GParted

---

### Post by overdrank on 2008-05-25
> **Jackfrost123 said:**
> I installed ubuntu dual boot with vista on an ext3 partion on the same physical disk. I want to shrink the vista partition and expand the ext3 one. I don't mind deleting the ntfs partition altogether but I want to expand the ext3 one for sure! Partition editor doesn't seem to give me that option...Thanks!

Also I want to expand my swap partition. I get constant error that there is not enough swap to hibernate, why is that? I have 600 mb swap and a 512 memory.

Thanks fellas!

Hi and I believe you will need to shrink vista partition from within vista. To expand the ext3 using the live cd this way the partition will not be mounted. As for the swap this link may help
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by SpaceCowboyMA on 2008-05-25
> **overdrank said:**
> Hi and I believe you will need to shrink vista partition from within vista. To expand the ext3 using the live cd this way the partition will not be mounted. As for the swap this link may help
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Just did this with NTFS XP partition.  I'd installed a month ago only using 50% of my disk.  Since then haven't booted to windows more than a few times and set up VBox to the raw partition so really no need now save occasional Civ 4 bouts.  I just shrunk XP down to its installed size plus 1GB.

As cdtech stated the live CD is your best option.  If not and you have ntfsprogs installed you can resize your NTFS partition while booted off your hard disk.  However, if you intend to resize your EXT3 partiton you will need the live cd as you won't be able to resize a mounted partition.

Boot from the live cd and run gparted& from a terminal.  The only gotcha I encountered was that the livecd will use a local swap partition if one exists.  If your swap is on the same partition as the EXT3 you intend to resize, you will need to swapoff first or the resize/move option won't seem to work.

---

### Post by Jackfrost123 on 2008-05-25
Hey everybody thanks a lot!

> **SpaceCowboyMA said:**
> 
Boot from the live cd and run gparted& from a terminal.  The only gotcha I encountered was that the livecd will use a local swap partition if one exists.  If your swap is on the same partition as the EXT3 you intend to resize, you will need to swapoff first or the resize/move option won't seem to work.

Let me get this right, the swap, my swap, is on the same physical disc, but on one partition on its own, as per the standard installation. Do you mean I will encounter a problem if it's on the same partition or on the same physical volume, from what you say I gather you mean the former so I guess I will be ok. Is gparted fairly straight forward in terms of commands? Since it's only command line. (btw. I don't mind destroying the vista partition, I plan to install xp afresh anyway.)

Again thanks everybody.

---

### Post by Inxsible on 2008-05-25
Gparted is not command line. On the live cd, its under System>>Administration>>Gparted. Try it out.

---

### Post by forestpixie on 2008-05-25
If you use the partition editor from the ubuntu livecd then the livecd will be using swap if it is present so you will need to turn it off if you want to do anything with it - probably unless you set it up differently you have an extended partition with the root and swap in it.

Gparted is a gui application it's not command line

---

### Post by dazzlindonna on 2008-05-25
And you turn off swap, how?

---

### Post by Inxsible on 2008-05-25
> **dazzlindonna said:**
> And you turn off swap, how?Open up a terminal and type in ```
swapoff
```

---

### Post by trothigar on 2008-05-25
sudo swapoff -a

---

### Post by Raccoon1400 on 2008-05-25
> **overdrank said:**
> Hi and I believe you will need to shrink vista partition from within vista. To expand the ext3 using the live cd this way the partition will not be mounted. As for the swap this link may help
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I think partiton manager is gparted. Make sure you unmount the partition first.

No, you do not need to do it from within vista. I have done this fine from the gparted live cd.

---

### Post by Jackfrost123 on 2008-05-26
Problem for me:

For some strange reason and whilst being in via the live cd, and having turned swap off, I can't resize my main ext3 boot linux partition to something more than what is already allocated, the 6 gbs it already is. Despite having 50 gibs of recently deleted ntfs partition, currently 50 gibs of unallocated space....All that via gparted...

Sigh...

---

### Post by forestpixie on 2008-05-26
Open the partition editor and post a screenshot here

---

### Post by Jackfrost123 on 2008-05-26
k.

---

### Post by Inxsible on 2008-05-26
Thats because you have the swap between the ext3 and the unallocated space. To merge or extend a partition, they need to be contiguous.

What you can do is delete the swap partition and then create a new swap near the start of the drive (if this is the only OS you are gonna have) If you plan to add more OS'es then you need to leave space for them accordingly. 

After you create your swap somewhere near the head of the drive, you can extend the ext3 partition

---

### Post by forestpixie on 2008-05-26
Thought so - you need to get sda3 next to the unallocated space.

Delete the swap then move sda3 to the left so unallocated space is to the right.
Then create a new swap with some of the unallocated space and then finally resize sda3 to take remainder of unallocated. I always apply each part seperately.

It could take some time to do it so don't be too worried and whatever you do don't turn it off.

Edit - of course you could put swap at the beginning of the drive :)

---

### Post by Jackfrost123 on 2008-05-26
thanks guys, one issue I am having is that in the create new partition options window it doesn't give me the option of a new swap, just extended partion (which is?) and primary partition.

I am thinking of going with the option of putting the swap ahead of everything, at the beginning of the drive. Is there any reason not to?

---

### Post by Inxsible on 2008-05-27
> **Jackfrost123 said:**
> thanks guys, one issue I am having is that in the create new partition options window it doesn't give me the option of a new swap, just extended partion (which is?) and primary partition.

Create an extended partition and then put the mount point as swap.

---

### Post by gtdaqua on 2008-05-28
when you boot back to the system, will the OS automatically recognize the newly created swap drive or do you have to do a fresh fdisk after booting?

---

### Post by trothigar on 2008-05-29
shouldn't have to muck around with fdisk.

If its newly created you might have to edit /etc/fstab

---

