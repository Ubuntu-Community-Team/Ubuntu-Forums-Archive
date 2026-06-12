---
title: "cannot increase root partition sda1"
date: 2013-12-21
forum: New to Ubuntu
---

### Post by pjstock on 2013-12-21
like many beginners, I allocated too little space to my root partition sda1 (it is only 6GB or so) and I am always getting Low Disk Space warnings.
(this is a battered old laptop that I am just trying to keep functioning for browsing. No sensitive data.)
I figure an additional 4GB should suffice. 
I have read a variety of posts, threads and partitioning How Tos and thought I was on the right track.

as the attached screenshot shows, I have an unallocated 29GB adjacent to the root partition.

But when booted on a Ubuntu Live USB stick, Gparted> Resize / Move does not allow me to increase the root partition to absorb some of that unallocated space.

What am I doing wrong?

Many thanks

Peter

---

### Post by Elfy on 2013-12-21
right click swap - swapoff

possibly need to reload the devices.

Now - the unallocated space is INSIDE the extended partition, so you will need to resize that first - shrinking it. Then you'll be able to increase the space in sda1.

You might find that you'll need to move things around as well.



Please ensure that you've got backups of data you can't afford to lose.

Don't assume that because it's taking a while to complete that it's not doing anything - don't just turn it off and hope for the best ;)

---

### Post by grahammechanical on 2013-12-21
My guess is that the unallocated space is actually a partition, an extended partition into which we can create logical partitions and work around the 4 primary partition limit. If you add together the amount of unallocated space to the size of the swap partition it will equal the size of sda - the extended partition. This is because the swap partition is actually a logical partition inside the extended partition. To put it another way that unallocated space is unallocated inside the extended partition.  You need unallocated space outside that partition to the front of it.

You can try first shrinking sda2, the extended partition, to create unallocated space in front of sda2 and try resizing sda1 into that unallocated space.

Regards.

---

### Post by pjstock on 2013-12-21
thanks.
but when I try to Swapoff I get this error message:

"Could Not deactivate swap"
"swapoff: /dev/sda5 swapoff failed: cannot allocate memory"

thanks
 but I get no options to shrink or resize sda2.
with sda2 selected, my only option under Partition is Manage Flags. Everything else is greyed out. 
with unallocated selected, all options under Partition are greyed out.
sda5 (Swap) selected only Swapoff and Manage Flags are available and Swapoff fails ("cannot allocated memory")

---

### Post by 1clue on 2013-12-21
How much RAM do you have?  Type 'free' for me, and post the output please.

If there's no sensitive data, let me point out that you're only using 2 partitions:  / and swap.  There's no need for an extended partition.

Note:  If you're intimidated by manually handling disk partitioning tasks, then stop reading here.  Someone will no doubt scold me for saying what I'm about to say in the Absolute Beginner's section.  But since you said nothing sensitive and browsing only, you probably don't mind the idea of scraping off and trying something else.

If it were me, I'd make the entire hard disk LVM2 except /boot.  /boot can be 256m or so, ext2.  You're already using ext4 for /.

What this does is let you resize / and possibly even swap on-the-fly, no rebooting.  And it's an educational exercise.

Again, this is swatting a fly with a bulldozer and maybe more technical than should be in an Absolute Beginner's thread.

---

### Post by pjstock on 2013-12-21
here are the results of Free (attached)

I am not exactly a complete Ubuntu novice. I have used it on and off for years. But since I have always found it arcane and fiddly, I have never really progressed beyond the Beginners stage. (I still for instance cannot fathom the basics of partitioning. which is probably how I've wound up in this muddle. I thought one HAD to have a root partition for system stuff and some other partition for programs and personal data. and since this unit only has a 30GB HDD, I had shaved the root side too thin. )

I would be happy to just have a dead simple setup. I can start from scratch but since I always have trouble getting stuff like wireless adapters working, I am always reluctant to blow away a working install.

But I cannot update the system for instance because I am always down to about 300mb space and the packages can't install. So the system is currently about 400 days out of date.

Peter

I was trying to follow this How To example, which seems to pretty closely match my situation.

[http://www.rootusers.com/use-gparted-to-increase-disk-size-of-a-linux-native-partition/](http://www.rootusers.com/use-gparted-to-increase-disk-size-of-a-linux-native-partition/)

the difference being that in the example there are none of the Locks on the various segments.
can I not just get those locks off?

---

### Post by Elfy on 2013-12-21
You do have to have a / partition - but other than perhaps swap you don't need anything else - /boot, /home etc as seperate partitions are generally needed, though /home 'can' be useful in some situations.

free is showing that there is swap being used

close gparted

run this from a terminal and then restart gparted

```
sudo swapoff -a
```

Then you should be ok to go.

Now you say the machine is 400days out of date - I wonder if perhaps you'd be better off just doing a reinstall here - especially as you say 

> this is a battered old laptop that I am just trying to keep functioning for browsing. No sensitive data

if there is nothing of importance that's certainly what I'd be doing - a clean install is likely to be a *lot* quicker to complete than the various partition tasks you are going to need to perform here.

---

### Post by pjstock on 2013-12-21
thank you.
If I go the clean install route, could you suggest for me a workable partitioning configuration that would avoid me getting into this mess again?
I expect that when I did this install originally, I followed some suggestions for partitioning and somehow wound up with this setup.

---

### Post by philinux on 2013-12-21
I just have / 12gig, /swap 2 gig as I have 2 gig ram and a 250 gig hard drive and the rest is /data

 I use ext4 file system.

---

### Post by pjstock on 2013-12-21
Bravo! 

sudo swapoff -a did the trick.

Thank you.

Now, I have 29Gb of unallocated adjacent to /dev/sda1.
How should I resize to optimize? just slide sda1 to gobble up the entire unallocated?

---

### Post by 1clue on 2013-12-21
I would suggest a / and a swap partition.  I would also suggest you look for a little more RAM.  For something this old you can find it in a scrap pile at some office.  IT departments are notorious for never throwing anything away.  You're hitting swap and I imagine you're hitting it constantly, which will both slow you down a lot and cause early drive failure.

Find a way to max the memory on that, and it's a great first step.

You could choose "automatic partitioning" and probably not turn out too bad.

---

### Post by pjstock on 2013-12-21
may I see a Gparted screen shot of your setup ? 
I think I currently have two physical partitions (sda1 and sda2) with /swap under /sda2
should I only have 1 physical (not sure that is the correct term. Extended?) partitions?

---

### Post by 1clue on 2013-12-21
Sorry, an addendum regarding memory.

For older hardware, memory and such are generally really cheap.  I did my wife's laptop (a newer one, came with Vista) for like USD$40 and that took her up to 4g.

Getting big memory is still big money.  But older hardware, it's like they're hoping to sell it so they don't have to stock antiques, or worse yet throw away an unsold product.  And again, lots of IT departments have a drawer full of memory and other stuff that might someday be useful, you could score all you need to max your box for free that way.

---

### Post by pjstock on 2013-12-21
thank you all.you have been extraordinarily patient and helpful as usual.

so now that I am back up and running, I am just wondering if you partitioning is optimal or if there is a simple fix that could clean it up further.

Attached is what it looks like now, after the resizing exercise.

I expect that the linux-swap over there under sda2 is unnecessary, but I am not sure.
how would I tuck it back in under sda1?
Could I then delete sda2?

how would I create a /data partition if that is recommended.?

Peter

---

### Post by Impavidus on 2013-12-21
That seems perfect to me. You don't really need to put the swap partition in an extended partition, but it doesn't harm either, so keep it like that. Usually people recommend /data or /home partitions, but on small drives like yours it often best to put everything in the / partition.

---

### Post by Elfy on 2013-12-21
I'd leave well enough alone now that you've got there.

> how would I tuck it back in under sda1?
Could I then delete sda2?
swap is always going to be a seperate partition whether it's inside an extended or a primary in it's own right. I'd not bother - unless you want to get into editing fstab as well to point at the new swap's UUID.

If you want to do it as a learning exercise then go for it.

Reboot to the live medium.

swapoff - run gparted - delete the swap, then the extended then create a new swap, then edit fstab

Run

```
sudo blkid
```

Mount the existing system and edit the file

```
sudo mkdir /mnt/temp

sudo mount - t ext4 /dev/sda1 /mnt/temp

gksudo gedit /mnt/etc/fstab
```

Change the UUID for your swap line to the new UUID you've noted above. Save the edited file

```
sudo umount /mnt/temp
```

When you reboot swap will now be in a primary partition.

If you aren't using Ubuntu then change gedit for the installed gui text editor, or use nano :)

---

