---
title: "[SOLVED] GParted - Need to resize ext3 partition into unallocated"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Senuf on 2008-11-01
Hello.

First of all, sorry for my english. It's not my native tongue.

This is my first post in here. I was a Mac user a while ago. Then I had to switch to Window$. I didn't precisely like it, but I had to do the switch. A very short while ago, as soon as I had the chance, with online instructions, I achieved a double-boot system (only because I still need certain programs that work only on Win --or Mac--, and they still don't work as well --or at all-- under WINE), so I installed Ubuntu 8.04 (Hardy Heron) still having XP. Since then, I achieved two Ubuntu converts, heheh. My sister bought a new PC. The store insisted on installing Window$ (I hate it when they do that), but my sister listened to my advice, went with Ubuntu 100% (not even doubble-boot) and she's happier than a butcher's dog. And then my wife, who now wonders how could she have been relying on window$ for so long. She now won't TOUCH a window$ machine without putting her worse "this is disgusting" face on. Even saying things. Some things that would make a hooligan blush.

Now, to the point:
Thing is... It seems that the instructions I followed were OK, but covered the needs of the person who posted said instructions, but it seems they don't cover mine. I wanted to upgrade to Intrepid Ibex (8.10), but had no room for the upgrade. I should have given more space for certain partition, as you'll see.

Yesterday night I booted from the Ubuntu 8.04 live. Since I have two hard disks, just in case, I moved some important files I had in the Ubuntu HD into the Win HD, so I could work with not so many worries. In the Win HD I have the specific Windows partition (ntfs) and another ntfs partition which I access from Ubuntu too, where I put my work files.

Then I started GParted, went to my Ubuntu Hard Disk (/dev/sdb), and (see attached screen capture) resized (shrinked) sdb7 then moved sdb6 into the resulting unallocated space, then did the same with the sdb5 (swap) and then I wanted to resize sdb1 (ext3) into the remaining unallocated space, but I can't. It will only let me SHRINK it, not make it bigger (screen capture might give you a clue, I dunno, I'm not a Ubuntu expert by any means).

I thought I had made my homework OK, before all this, I read lots of instructions online and it seemed everything was as it should have been, but somehow it wasn't.

Any hint, please?

Thanks in advance.

Senuf

PS: I hope my post was clear. Please excuse any mistake/error/horror.

---

### Post by tompickles on 2008-11-01
This is because sdb1 is not in your extended partition. It is a primary partition. All your other partitions are in the extended partition sbd2. Best way to fix. Hmm.. Not really sure. You say you have two hdd. How difficult is it to back up *all* your work, and then reinstall with the new 8.10 disk onto your Ubuntu drive and then have the new setup there of swap, / and /home? I have a feeling though this is really not what you want to do.

---

### Post by Senuf on 2008-11-01
Thanks for your time and will to help, Tompickles!

Concerning your answer... Hmmmm... I had the hope to retain all my personal settings, Firefox bookmarks, installed applications (with their settings), etc. Even Mahjongg scores (that is a MAJOR issue between my wife and me heh, go figure...).

Well, on the other hand, providing I CAN do what you say, will my boot HD still provide me with the double/boot option? I mean, will it still recognize my Ubuntu HD/partition?

Oh, and I will have to install 8.04 and then upgrade. I don't have the 8.10 CD yet.

---

### Post by kansasnoob on 2008-11-01
So you want a larger sdb1?

First click on sdb5 (swap) and tick swapoff.

Then click on sdb2 (extended) and choose "move/resize". Shrink it to the right gobbling up the "unallocated space".

Then click on sdb1 and choose "move/resize". Expand it to the right to eat up the "unallocated space" you just created by resizing the extended partition.

Then you'll have to click apply!

**DO NOT CHOOSE TO "FORMAT" ANYTHING OR YOU"LL LOSE YOUR STUFF!**

I'd expect that to take at least 20 to 30 minutes to complete!

---

### Post by Senuf on 2008-11-01
Kansasnoob,

First, thanks a lot for caring and answering.

I "swapoffed" (heh) sdb5, but I can't just expand sdb2 to the right, because (see my attached file in the first post) there's nothing to the right of it. Somehow sdb2 COMPRISES the following: Unallocated, sdb5 (linu/swap), sdb6 (ext3) and sdb7 (fat32).

Anyway, I intended to go on and expand sdb1 (ext3), but to no avail.

Just in case (which I suspect shows you how little I know), I'm just doing a "swap on" on sdb5 again.

---

### Post by kansasnoob on 2008-11-01
> **Senuf said:**
> Kansasnoob,

First, thanks a lot for caring and answering.

I "swapoffed" (heh) sdb5, but I can't just expand sdb2 to the right, because (see my attached file in the first post) there's nothing to the right of it. Somehow sdb2 COMPRISES the following: Unallocated, sdb5 (linu/swap), sdb6 (ext3) and sdb7 (fat32).

Anyway, I intended to go on and expand sdb1 (ext3), but to no avail.

Just in case (which I suspect shows you how little I know), I'm just doing a "swap on" on sdb5 again.

You're skipping what I said here:

> Then click on sdb2 (extended) and choose "move/resize". Shrink it to the right gobbling up the "unallocated space".

Right now the "unallocated space is inside the extended partition (sdb2). Once you "shrink sdb2 to the right, the unallocated space will then be between sdb1 and sdb2 (outside the "extended" partition.

Then you should be able to "expand" sdb1 to the right.

---

### Post by kansasnoob on 2008-11-01
Silly thought.

You are doing this from the Ubuntu live CD aren't you?

You must use the live CD. You can't do it just by installing gparted to Ubuntu because all must be unmounted.

I must run some errands for a friend but I'll check back in an hour or so when I'm done.

I think you must be using the live CD but just wanted to check.

---

### Post by vanadium on 2008-11-01
I think kansasnoob intented to say that you could move the left side of sda2 to the right into the unallocated space. I do not think this is possible, though. You can only move/ resize an extended partition when it is empty.

The only way you can, in my opinion, enlarge sda1 and get rid of the unallocated space is to delete all partitions that reside in sda2, then delete sda2, resize sda1 and recreate an extended partition sda2 and all logical partitions inside them.

If these changes are too drastic for you, your only option to make use of the unallocated space is to turn it into an extra logical partition.

---

### Post by Senuf on 2008-11-01
> **kansasnoob said:**
> Silly thought.

You are doing this from the Ubuntu live CD aren't you?

You must use the live CD. You can't do it just by installing gparted to Ubuntu because all must be unmounted.

I must run some errands for a friend but I'll check back in an hour or so when I'm done.

I think you must be using the live CD but just wanted to check.

Yes, Kansasnoob, I'm using (booted from) the live CD, and using gparted from within it.

Thanks again.

---

### Post by Senuf on 2008-11-01
> **kansasnoob said:**
> You're skipping what I said here:



Right now the "unallocated space is inside the extended partition (sdb2). Once you "shrink sdb2 to the right, the unallocated space will then be between sdb1 and sdb2 (outside the "extended" partition.

Then you should be able to "expand" sdb1 to the right.

Hi again.
Well, I don't have the option to move/resize sdb2, only the partitions (or whatever they are) INSIDE sdb2. I don't even have the option to unmount sdb2 (heaven knows why in blazes I looked for that, but since I did, I mention it). The Unallocated space appeared when I shrinked sdb7. Then I moved sdb6 to the right, and the unallocated space then appeared between sdb5 (swap) and sdb6. Than I moved sdb5 (swap) to the right and the allocated space appeared (as I suspected it was going to happen) to the left of sdb5, where it is now. Then, following that train of thought, I guessed I would be able to just resize sdb1, and couldn't.
Sdb2, as a whole (comprising unallocated, sdb5, sdb6, and sdb7) refuses to allow me to resize it. As a matter of fact, right now the only way I have to shrink the unallocated space is to widen the swap "thing" (sdb5), but then I still am in the same position: I can't resize (expand) sdb1. Am I doing something wrong or is it just that what I try to do can't be achieved?

---

### Post by Senuf on 2008-11-01
> **vanadium said:**
> I think kansasnoob intented to say that you could move the left side of sda2 to the right into the unallocated space. I do not think this is possible, though. You can only move/ resize an extended partition when it is empty.

Yes. Since I couldn't do exactly that I created a new partition IN the unallocated space and then shrank (sp?) it moving the left side to the right in the hope of liberating space for sdb1, but what I achieved was, again, an unallocated space onto which I wasn't able to expand sdb1. So I just deleted the newly made partition because it served no purpose, and now I have the same unallocated space that I had according my attached screenshot. All is now as it was, with no solution yet. Perhaps there is no way to solve this... :(   


> **vanadium said:**
> The only way you can, in my opinion, enlarge sda1 and get rid of the unallocated space is to delete all partitions that reside in sda2, then delete sda2, resize sda1 and recreate an extended partition sda2 and all logical partitions inside them.

If these changes are too drastic for you, your only option to make use of the unallocated space is to turn it into an extra logical partition.

It's too drastic, yes, and turning the unallocated space into an extra logical partition won't give me the space I need for sdb1 (where, as far as I could see, Ubuntu is installed and is where I want to upgrade to 8.10 and whatever's to come).

Thanks a lot for your patience.

Senuf

---

### Post by kansasnoob on 2008-11-01
Hey, it's all good! I may learn something here myself!

Just FYI I'm using a small 30GB drive I use for testing. Currently I have 8.04 on sda1 and then I have an sda2 extended containing a shared swap and 8.10 on sda5.

So anyway (since I'm planning to reinstall 8.10 to do some fresh install testing) I decided to try what you're trying. I had no free (unallocated) space so I shrunk sda5.

I now have a similar situation to you! I want to make sda1 bigger but I must first shrink sda2. You'll see in this screenshot that I've right-clicked on sda2 and brought up the menu:

[ATTACH]90619[/ATTACH]

Now I'm choosing "resize/move":

[ATTACH]90621[/ATTACH]

Now, bear with me, I'll continue this in the next post. I've noticed that the forums only allow so many screenshots in one post so I'll continue and we'll find out if I'm right or wrong:confused:

---

### Post by kansasnoob on 2008-11-01
Now I've "pushed" the slider on the left of the extended partition to the right:

[ATTACH]90622[/ATTACH]

Now hold on! I'm going to complete that resize and reboot so I can show you what I have after that!

---

### Post by kansasnoob on 2008-11-01
OK, what I have now:

[ATTACH]90627[/ATTACH]

Now, it left a bit of unallocated space inside the extended partition which is nothing to worry about. That has to do with drive structure, cylinder rounding, etc. and I don't have three days to write a tutorial on drive structuring. Suffice it to say this is an old drive and I rushed through this.

Now I right-clicked sda1 and chose resize/move:

[ATTACH]90631[/ATTACH]

Hopefully they'll let me do one more screenshot in the next post.

Yes, one more post:guitar:

---

### Post by Senuf on 2008-11-01
> **kansasnoob said:**
> Hey, it's all good! I may learn something here myself!

Just FYI I'm using a small 30GB drive I use for testing. Currently I have 8.04 on sda1 and then I have an sda2 extended containing a shared swap and 8.10 on sda5.

So anyway (since I'm planning to reinstall 8.10 to do some fresh install testing) I decided to try what you're trying. I had no free (unallocated) space so I shrunk sda5.

I now have a similar situation to you! I want to make sda1 bigger but I must first shrink sda2. You'll see in this screenshot that I've right-clicked on sda2 and brought up the menu:

[ATTACH]90619[/ATTACH]

Now I'm choosing "resize/move":

[ATTACH]90621[/ATTACH]

Now, bear with me, I'll continue this in the next post. I've noticed that the forums only allow so many screenshots in one post so I'll continue and we'll find out if I'm right or wrong:confused:

Hello.
I understand what you did, and I can see now that I understood it before, but, thing is... See my attached image. I don't even have the chance to resize sdb2. I guess it might have something to do with those keys icon that appears there, visible in the image. As a newbie, but not quite as fool as my third grade teacher thought that was, I can guess it has something to do with permissions or lock status or something like that (or was my teacher right?).

Thanks again and again and again.

---

### Post by kansasnoob on 2008-11-01
Now, see what I have:

[ATTACH]90634[/ATTACH]

I can't imagine what's stopping you:confused:

Working from a live CD (and with swapoff) you should have no key-chain thingamajigs to the left of the partition you want to work with! If there's a key-chain thingy then you need to unmount something.

To the nay-sayers, yeah - I do this stuff a lot! I do know how to resize and move partitions!

Still one more post to follow regarding your having already moved/resized swap!

---

### Post by kansasnoob on 2008-11-01
> **Senuf said:**
> Hello.
I understand what you did, and I can see now that I understood it before, but, thing is... See my attached image. I don't even have the chance to resize sdb2. I guess it might have something to do with those keys icon that appears there, visible in the image. As a newbie, but not quite as fool as my third grade teacher thought that was, I can guess it has something to do with permissions or lock status or something like that (or was my teacher right?).

Thanks again and again and again.

Yes! Your partitions are "locked"! That's indicated by the keys to the left side of the partitions!

If you're using the live CD you need to select swapoff for swap and in your first post/screenshot it didn't appear that the FAT32 data partition was locked.

All partitions inside the extended partition must be unlocked to do the resize/move!

**Now, just a reminder, NEVER choose to FORMAT!**

I'd have to boot a live CD to find out, but I think you'll have an "unmount" option for the FAT32 data partition.

Again! All partitions need to be unmounted (in the case of swap - swapoff) to get-r-done!

---

### Post by Senuf on 2008-11-01
> **kansasnoob said:**
> Now, see what I have:

[ATTACH]90634[/ATTACH]

I can't imagine what's stopping you:confused:

Stop the press, stop the press!!!
Something in your post gave me the clue and now I am following your instructions, more to come soon in next post...

---

### Post by sneeks on 2008-11-01
you could always use the gparted live cd,as then all will be unmounted,there is also a how to video on miro and youtube.

---

### Post by Senuf on 2008-11-01
Kansasnoob.

Here my wife can't believe how many times I said "I'm happy, I'm happy, I'm happy". And "Can you believe, this person in Kansas (I think he's in Kansas) helping me, a complete stranger, to such an extent?".

Your posts not only helped me to achieve EXACTLY what I wanted, they were instructive and easy to follow, even for a lad who does not rely on english on a daily basis.

You saved me hours, if not days.

You rock :guitar:

Whenever you come to Buenos Aires, you've just earned a great homemade dinner, and some local guide.

I reckon I don't know how to thank you.


Senuf.

---

### Post by kansasnoob on 2008-11-01
> **Senuf said:**
> Stop the press, stop the press!!!
Something in your post gave me the clue and now I am following your instructions, more to come soon in next post...

Sorry if I sounded angry! I'm not angry with you. People always pop in and say, "you can't do that, you'll have to copy everything to a different drive and start over"!

Anyway, here's what I promised about dealing with the UUID problem from "moving/resizing" swap:

Read all of coffeecat's posts here:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

If you have questions feel free to ask!

I must go take care of my fainting goats but I'll be back.

---

### Post by Senuf on 2008-11-01
Kansasnoob, not only I did NOT feel you sounded angry, but I also went, and thanked you quite a few times. You saved my day (actually, days), and were not only as helping as someone can be, but even more so, even recreating in a hard drive of yours the same conditions I had in here, all for the sheer sake of helping someone who you don't even know. In a previous post of mine you can read that (thanks to you) I solved my problem EXACTLY THE WAY I NEEDED.
If I were a believer I would include you in my prayers, heh, that's how much I thank you!

regards,

Senuf

---

### Post by Timokl on 2011-10-09
> **kansasnoob said:**
> So you want a larger sdb1?

First click on sdb5 (swap) and tick swapoff.

Then click on sdb2 (extended) and choose "move/resize". Shrink it to the right gobbling up the "unallocated space".

Then click on sdb1 and choose "move/resize". Expand it to the right to eat up the "unallocated space" you just created by resizing the extended partition.

Then you'll have to click apply!

**DO NOT CHOOSE TO "FORMAT" ANYTHING OR YOU"LL LOSE YOUR STUFF!**

I'd expect that to take at least 20 to 30 minutes to complete!

Thanks a lot ... I had a similar situation - and this helped me to figure out how to proceed.

Timo

---

