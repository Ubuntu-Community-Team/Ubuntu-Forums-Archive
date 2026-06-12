---
title: "[SOLVED] Removing Windows/NTFS Partition(s)"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by bumbleb33 on 2008-11-17
Alright, so I'm completely sold on Ubuntu. I've had it installed as a dual boot with Windows XP for awhile now, and I hardly go back to the Windows installation these days.

I've had a look around the forums, and I've found some answers, but not quite sure if/how they apply to my situation.

Basically, when I just had Windows installed, I had 2 partitions, one 20GB for C: and the rest a second partition. Naturally, I installed Ubuntu (repartitioned the 2nd partition) on the second partition.

When I open up GParted here's what it looks like:

/dev/sda1 -- ntfs -- boot
/dev/sda2 -- extended -- lba
----/dev/sda5/ -- ntfs
----/dev/sda6/ -- ext3 <--- ubuntu installed here
----/dev/sda7/ -- linux-swap

So, how would I go about reclaiming the space taken from the 2 ntfs partitions without having to reinstall Ubuntu?

Thanks in advance.

---

### Post by rampageoberon on 2008-11-17
You can use gparted for this. Use the Ubuntu LiveCD or Gparted LiveCD to bootup and then delete the windows partition and grow your linux partition. ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))

Hope that helps.

---

### Post by Dedoimedo on 2008-11-17
Hello,

Simply format the partitions you don't want as, let's say ext3.
And then mount them in Ubuntu by editing the /etc/fstab file <--- ask how if you don't know.

You can then mount the extra space as /data-1 or data-2 or something and keep data there.

If you want to resize or move ubuntu, including home, this could be a little trickier, but it's doable.

Report progress, ask for more help if needed.

Dedoimedo

---

### Post by bumbleb33 on 2008-11-17
> **Dedoimedo said:**
> mount them in Ubuntu by editing the /etc/fstab file

Yes, help doing that would be VERY much appreciated.

> **Dedoimedo said:**
> 
If you want to resize or move ubuntu, including home, this could be a little trickier, but it's doable.

Ultimately, this is what I would like to do.

Again, thanks for the help!

---

### Post by tarps87 on 2008-11-17
> **rampageoberon said:**
> You can use gparted for this. Use the Ubuntu LiveCD or Gparted LiveCD to bootup and then delete the windows partition and grow your linux partition. ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))

Hope that helps.

I think this way will do what you're looking for but instead of downloading the gparted cd you can us the Ubuntu one if you still have it.
It must be done from a live cd as you can unmount the drive you are running from.
Once in gparted (System -> Administration -> partitioner) select the NTFS partition and delete it, now select the Ubuntu partition and change the size. I believe gparted now allows drag sizing, so you should be able to drag the edge of the Ubuntu partition over the unallocated/unformatted space.

Edit: To get resize and delete right click on the partition you want to edit

---

### Post by bumbleb33 on 2008-11-17
Okay, I'm not sure what I've changed, but I've managed to reclaim the space from one partition using the live CD, how would I go about getting the space back from the first one? Even if I delete it, I'm still unable to 'drag' the extended partition over the unallocate space...

---

### Post by Dedoimedo on 2008-11-17
> **bumbleb33 said:**
> Yes, help doing that would be VERY much appreciated.



Ultimately, this is what I would like to do.

Again, thanks for the help!

Hello,

Let's begin with simple steps. Formatting them is easy. Select the relevant partition, format as ext3, keep them primary and logical as they were.

In other words, just format sda1 to ext3 (or other filesystem), keep it primary, format sda5 to ext3, keep it logical.

Create two directories for mounting these partitions.

```
sudo mkdir -p /mnt/windows-main
sudo mkdir -p /mnt/windows-second
```

Use the names as you want, data, data12, backup, anything.

Then, backup /etc/fstab

```
sudo cp /etc/fstab /etc/fstab-backup
```

Next, add these two lines to the file:

```

/dev/sda1 /mnt/windows-main ext3 auto 0 0
/dev/sda5 /mnt/windows-second ext3 auto 0 0

```

Save.

Remount everything.

```
sudo mount -a
```

And then navigate to these mount points. Your new partitions should be there for you to use.

The options I gave you to add the the fstab file can be changed. You can use other options than auto. You can use read-only, user and so forth. You can also force checks on the partitions if you want or enable quotas (that's the zeros at the end). But this is advanced stuff. The basic configuration I've written should work for you.

Again, if you need more help, ask.

Next step would be to move home to a separate partition, but there are tutorials on the forums for that already written, so search a little.

After that, we'll see.

Dedoimedo

---

### Post by tarps87 on 2008-11-17
> **bumbleb33 said:**
> Okay, I'm not sure what I've changed, but I've managed to reclaim the space from one partition using the live CD, how would I go about getting the space back from the first one? Even if I delete it, I'm still unable to 'drag' the extended partition over the unallocate space...

So you have deleted the NTFS partition? Is the resize option available when you right click the Ubuntu drive?

---

### Post by bumbleb33 on 2008-11-17
Okay, so after letting it run overnight, I've managed to 'merge' /dev/sda5 and /dev/sda6 into one larger /dev/sda5. A quick search of 'grub error 17

I'm sure I've missed something, but now when I try to boot I get a grub 'error 17'.  After a quick search around, I couldn't find any answers that really helped me figure out what to do, so I'm back here again.

What next guys?

Thanks for your help.

---

### Post by bumbleb33 on 2008-11-18
Okay, tried the good ol' Google again and solved my GRUB problem.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351), if anyone was interested.

Back to trying to get the last NTFS back.

---

### Post by bumanie on 2008-11-18
With gparted, you should be able to right click on the ntfs partition, click and choose delete and it will become unallocated space. Then you can format it to ext3 - to use it in ubuntu you may have to edit /etc/fstab - not sure, I haven't tried what you are doing, but once it is ext3 it will be able to be mounted and used without too much hassle. Make sure the partition is not mounted when using gparted - gparted doesn't work on mounted partitions.

---

### Post by tarps87 on 2008-11-18
Can you post layout of what the patitions look like now?
The output of fdisk should do
```
sudo fdisk -l
```

---

### Post by bumbleb33 on 2008-11-18
> **tarps87 said:**
> Can you post layout of what the patitions look like now?
The output of fdisk should do
```
sudo fdisk -l
```

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2            2612       19457   135315495    f  W95 Ext'd (LBA)
/dev/sda5            2612       18994   131596416   83  Linux
/dev/sda6           18995       19457     3719016   82  Linux swap / Solaris

```

This is after following Dedoimedo's instructions. Any idea how to merge it all into sda1?

---

### Post by tarps87 on 2008-11-18
The only way I can think off is using a live cd and resizing it using gparted, but I'm not sure why that isn't working. Have you tried using gedit now you have formated it?

> **bumbleb33 said:**
> 
As an aside, how do I remove the Windows GRUB entry?

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bck
```
if you are using Ubuntu
```
sudo gedit /boot/grub/menu.lst
```
if you are using Kubuntu
```
sudo kate /boot/grub/menu.lst
```
Now look for the block which as the title of what shows up in the grub menu and remove that block
e.g.
If grub shows: Microsoft Windows XP Professional
remove

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

Now save this file an test it
If it goes wrong
```
sudo cp /boot/grub/menu.lst.bck /boot/grub/menu.lst
```

---

### Post by Dedoimedo on 2008-11-18
Hi,

The resizing part should have waited a little ... like I wrote in my original post, because it's not as trivial as it seems. I'm glad you got things working.

Now, how to move data to sda1 ...

You cannot delete sda1 and leave sda2, sda5 and higher. So your best bet is to shrink sda1 to minimal size available and similarly sda5 ... and then expand the others ...

What do you think, do you want to do this?

Dedoimedo

---

### Post by tarps87 on 2008-11-18
> **Dedoimedo said:**
> Hi,
The resizing part should have waited a little ... like I wrote in my original post, because it's not as trivial as it seems. I'm glad you got things working.


Apologises I have looked at the partitioning and realised that is not at the start of the disk, I now see what you are doing

---

### Post by bumbleb33 on 2008-11-18
> **Dedoimedo said:**
> 
What do you think, do you want to do this?

Dedoimedo

Ultimately I would still like to make it all into one large partition, but I've got sda1 mounted as /mnt/stuff for now.

Thanks for all your help though.

---

### Post by Dedoimedo on 2008-11-18
Hello,

You can also do this, but I'm not sure if you want to:

Use dd to copy the partition, something like:

dd if=/dev/sda6 of=/dev/sda1

After that, you'll have to fix grub once again.

And there's a chance that something might get wrong, so be careful and back your data.

You may also want to use GUI programs for imaging, like CloneZilla. I have a tutorial on my site, check it out if you want.

Image your partition first - the one with Ubuntu on it, then image it back to sda1. Should work ...

Dedoimedo

---

### Post by MeURi on 2008-11-18
Dumb question for the "pros": can't bumbleb33 dd the linux main partition (sda5) to sda1, provided that there's enough free space, edit the menu.lst accordingly, reboot, wipe the other partitions and expand sda1?

Just a thought...

EDIT: beaten on time by Dedoimedo :-P

---

### Post by bumbleb33 on 2008-11-18
> **Dedoimedo said:**
> Hello,

You can also do this, but I'm not sure if you want to:

Use dd to copy the partition, something like:

dd if=/dev/sda6 of=/dev/sda1

After that, you'll have to fix grub once again.

And there's a chance that something might get wrong, so be careful and back your data.

You may also want to use GUI programs for imaging, like CloneZilla. I have a tutorial on my site, check it out if you want.

Image your partition first - the one with Ubuntu on it, then image it back to sda1. Should work ...

Dedoimedo

Great idea, I can't believe I didn't think of that. Quite comfortable with cloning drives, something I did regularly with Windows.

---

### Post by caljohnsmith on 2008-11-18
> **Dedoimedo said:**
> 

dd if=/dev/[COLOR="Blue"]sda6[/COLOR] of=/dev/sda1


You unfortunately can't simply dd a logical partition into a primary partition because they have a slightly different structure. Also, using dd doesn't update the partition table in the MBR with any new changes, so bumbleb33's partition table would be corrupt if you use dd in that way. It would be great if it were as simple as you suggest, but I would definitely not recommend doing that approach. :)

Bumbleb33, how about just deleting sda1, resizing your extended partition sda2 to use that space, and then you can resize sda5 to use all that space that sda1 used. There's nothing wrong with simply having one large extended partition on your entire drive with your two linux partitions in it. Would this scenario maybe work for you?

---

### Post by bumbleb33 on 2008-11-18
> **caljohnsmith said:**
> You unfortunately can't simply dd a logical partition into a primary partition because they have a slightly different structure. Also, using dd doesn't update the partition table in the MBR with any new changes, so bumbleb33's partition table would be corrupt if you use dd in that way. It would be great if it were as simple as you suggest, but I would definitely not recommend doing that approach. :)

Bumbleb33, how about just deleting sda1, resizing your extended partition sda2 to use that space, and then you can resize sda5 to use all that space that sda1 used. There's nothing wrong with simply having one large extended partition on your entire drive with your two linux partitions in it. Would this scenario maybe work for you?

Thanks for the heads up, I'll try resizing sda2, and get back to this thread on it.

Thanks for all the suggestions to all those who did, much better response than I expected :guitar:

---

### Post by bumbleb33 on 2008-11-18
> **caljohnsmith said:**
> You unfortunately can't simply dd a logical partition into a primary partition because they have a slightly different structure. Also, using dd doesn't update the partition table in the MBR with any new changes, so bumbleb33's partition table would be corrupt if you use dd in that way. It would be great if it were as simple as you suggest, but I would definitely not recommend doing that approach. :)

Bumbleb33, how about just deleting sda1, resizing your extended partition sda2 to use that space, and then you can resize sda5 to use all that space that sda1 used. There's nothing wrong with simply having one large extended partition on your entire drive with your two linux partitions in it. Would this scenario maybe work for you?

Okay, in GParted now (live cd) and unable to re-size sda2.

Might try the dd function later.

[edit]

Seems turning off the 'swap' (sda6) allows me to re-size sda2. Will try that :)

---

### Post by bumbleb33 on 2008-11-18
Alright, thanks all. Problem officiall solved.

just ran 'fdisk -l' and this is the output:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       19457   156288321    f  W95 Ext'd (LBA)
/dev/sda5               1       18994   152569242   83  Linux
/dev/sda6           18995       19457     3719016   82  Linux swap / Solaris
```

Exactly what I wanted. :)

---

