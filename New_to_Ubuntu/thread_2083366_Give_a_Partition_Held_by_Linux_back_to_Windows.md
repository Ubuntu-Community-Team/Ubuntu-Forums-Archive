---
title: "Give a Partition Held by Linux back to Windows"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by PumaMania on 2012-11-12
Hey all, when I was installing Ubuntu 12.04 LTS on my computer, I gave it a lot of space. I'd now like to give some back to Windows, which I use most for my work and is therefore my primary OS. 

I am using my bootable USB thumb drive to access GParted, and I have shrunk Ubuntu down to 50GB. I now have about 58GB left that I formatted to NTFS so that it works with Windows. It is still under dev/sda 4 which also includes my Ubuntu partition and swap. 

How can I move it up to dev/sd3 somehow, so that Windows will recognise the extra 58GB? Help will be greatly appreciated :)

(Screenshot below)

---

### Post by howefield on 2012-11-12
Have you booted into Windows since formatting the ntfs partion ?

Windows should see it where it is.

---

### Post by Mr_JMM on 2012-11-12
At the moment it is a seperate partition so you'd have to assign it in Wiondows with a drive letter.
However, it seems what you're asking is to add the space to sda3 to enlarge this partition. To do this you'll have to remove it (sda7) then move the extended partition sda4 so that the unused space is before it. You'd then enlarge sda3 to fill this unused space.
As the partitions are now you can't just allocate without moving them around afaik.

Unless you know you're going to use all that space for windows files I would personally resize and move the linux partitions (reformat sda7 to ext3/4) and have 2 root partitions and a seprate home or allocate sda7 as a seperate linux home partiton, shrinking sda5 to around 10-15GB.

I like to play around with linux so I'd be tempted to have to linux partitions for different distros.

Otherwise, again, see first paragraph.

---

### Post by PumaMania on 2012-11-12
> **Mr_JMM said:**
> At the moment it is a seperate partition so you'd have to assign it in Wiondows with a drive letter.
However, it seems what you're asking is to add the space to sda3 to enlarge this partition. To do this you'll have to remove it (sda7) then move the extended partition sda4 so that the unused space is before it. You'd then enlarge sda3 to fill this unused space.
As the partitions are now you can't just allocate without moving them around afaik.

Unless you know you're going to use all that space for windows files I would personally resize and move the linux partitions (reformat sda7 to ext3/4) and have 2 root partitions and a seprate home or allocate sda7 as a seperate linux home partiton, shrinking sda5 to around 10-15GB.

I like to play around with linux so I'd be tempted to have to linux partitions for different distros.

Otherwise, again, see first paragraph.

I'm going to opt for the first paragraph of what you said. I have tried several distros and I keep running back to Ubuntu :) Two problems arise:

One: sd4 is locked, because of the sd6 swap. I can turn swapoff and then move sd5 around. Will this mess with the Grub 2 bootloader? And what would I do after I complete this (if I were to do it). It seems that I would just mode sd5 to the end, and give sd7 space to take its place, but it would still be stuck in sd4. 

Again thank you.

---

### Post by Mr_JMM on 2012-11-12
You like the difficult options like me then! :)

Yes, as you stated you'll need to turn swapoff.
Delete sda7 partition.
Delete the swap partition (sda6).*
Shrink sda4 so it's just big enough for sda5 and sda6.
Recreate the swap partition.*
If possible, and I recommend doing this from a live DVD using Gparted, move sda4 so that there is space before it and none after it. There should be a slider that allows you to do this.
Save changes so far.
Now enlarge sda3 to fill the gap. Again, the slider should make this simple to do.
* Added after as I forgot first time.

Or,

Backup contents of /home (should do this anyway in case it goes wrong),
Delete sda4.
Enlarge sda3.
Add a new partition (recreating sda4).
Install Ubuntu as a fresh install.

If you go for the former, please let me know how you get on. Be warned, as with all partition editing, assume the worse and backup accordingly.

---

### Post by PumaMania on 2012-11-12
> **Mr_JMM said:**
> You like the difficult options like me then! :)

Yes, as you stated you'll need to turn swapoff.
Delete sda7 partition.
Shrink sda4 so it's just big enough for sda5 and sda6.
If possible, and I recommend doing this from a live DVD using Gparted, move sda4 so that there is space before it and none after it. There should be a slider that allows you to do this.
Save changes so far.
Now enlarge sda3 to fill the gap. Again, the slider should make this simple to do.

Or,

Backup contents of /home (should do this anyway in case it goes wrong),
Delete sda4.
Enlarge sda3.
Add a new partition (recreating sda4).
Install Ubuntu as a fresh install.

If you go for the former, please let me know how you get on. Be warned, as with all partition editing, assume the worse and backup accordingly.

I keep getting this when I try to resize sd4 (see attachment). I can enter a number but the option to resize doesn't show up.

---

### Post by Mr_JMM on 2012-11-12
Sorry, I missed a step:

You'll probably need to delete the swap partition and then recreate it. Because you have something at both ends of the partition it's preventing you from shrinking it.

---

### Post by arpanaut on 2012-11-12
You know that you can use the ntfs partition from windows without taking it out of the extended partition.  You have almost 250 Gigs of space still available in your windows part.  So why risk all the re-partitioning of the extended, when you could still use the space as it is, away from your win system partition just in case that gets corrupted or has issues in the future.
I know that it is not as tidy, but still functional from a windows point of view.
Just a suggestion...

---

### Post by PumaMania on 2012-11-12
> **Mr_JMM said:**
> Sorry, I missed a step:

You'll probably need to delete the swap partition and then recreate it. Because you have something at both ends of the partition it's preventing you from shrinking it.

When I did this, I was finally able to get in business. The 60GB of unallocated space that was previously sda7 was freed, but I could only make a maximum of 4 partitions :(

I've decided to settle and recreate sda7 as an NTFS drive. Windows will recognise it as a separate drive and I will just use that. Thank you so much for your dedicated help to me :)

---

### Post by Mr_JMM on 2012-11-12
No worries.
Strange that you had issues, I literally recreated your drive using a spare I had and am in the middle of the step to add space before the partition with no problems so far (I like to double check the advice I'm giving works). If you change your mind, let me know.

For future reference, you're not adding any extra partitions for it to complain about, the recreated swap would have gone in the extended and you can create many more logical partitions within it.

Glad you got it resolved one way or another.

---

