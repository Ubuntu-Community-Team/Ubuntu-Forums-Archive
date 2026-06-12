---
title: "[SOLVED] all of Hardy in one extended partition?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by egalvan on 2008-09-07
Is it POSSIBLE to install ALL of Hardy within one extended partition?

boot
root
home
swap

all of it on one?

what if I leave swap on a seperate partition?


Note, I'm running a bunch of Linux experiments and want to work on this, but not if it's not possible :)
I have too many to run, and I need to cut down on the possibilities.

Don't care if it's insane, un-wieldly, impractical...

it's an experiment. smile :lolflag:


[B][COLOR="Red"]edit and add.....

Many thanks to all who gave their ideas, please see my post #12 for more details...
:)[/COLOR][/B]

---

### Post by wolfen69 on 2008-09-07
yes you can, except for swap. it needs to be on it's own.

---

### Post by sancho panza on 2008-09-07
Yes you can, but you'll need to create the swap as another (swap) partition within your extended partition. So one (ext3) partition on the extended partition holds boot, root and home and another (swap) holds the swap.

---

### Post by egalvan on 2008-09-07
> **wolfen69 said:**
> yes you can, except for swap. it needs to be on it's own.

OK, thanks

now here's another,,,

can I put the four PARTITONS inside an extended partition?

boot
root
home
swap

separate partitions inside extended

---

### Post by dorkdork777 on 2008-09-07
Yep, AFAIK they can call go into an extended. No problems there, but you might need to have another partition that isn't in extended for it to work.

---

### Post by ByteJuggler on 2008-09-07
> **wolfen69 said:**
> yes you can, except for swap. it needs to be on it's own.

Not even that is neccesary - you can set up swap to go to a swapfile if you want.

---

### Post by egalvan on 2008-09-07
> **sancho panza said:**
> Yes you can, but you'll need to create the swap as another (swap) partition within your extended partition. So one (ext3) partition on the extended partition holds boot, root and home and another (swap) holds the swap.

I posted my previous post before yours popped up.

As for the swap FILE idea, where can I get more info?

Thanks, I now have more ammunition for my expermiment.

ErnestG

:popcorn:

---

### Post by egalvan on 2008-09-07
> **dorkdork777 said:**
> Yep, AFAIK they can call go into an extended. No problems there, but you might need to have another partition that isn't in extended for it to work.

Admittedly a few years ago, but I used to set up hard drives with only one extended partition all the time....
I used that trick to keep MS from scrambling drive letters

---

### Post by Shazaam on 2008-09-07
I think you are allowed 24 or so (correct me if I am wrong) logical partitions inside an Extended partition. What I do is make one /swap partition (primary or logical, doesn't matter) that ALL of my distros (5 across 3 drives) share. No problems so far.

---

### Post by egalvan on 2008-09-07
> **Shazaam said:**
> I think you are allowed 24 or so (correct me if I am wrong) logical partitions inside an Extended partition. What I do is make one /swap partition (primary or logical, doesn't matter) that ALL of my distros (5 across 3 drives) share. No problems so far.

I suffer from CRS, but I do rembember the limit being 64 (0 to 63).

I remember the fun a friend and i had putting 8 PRIMARY partitions on one hard drive. Yes, one can break beyond the 4-primary limit.

Lots of fun things to do when one is told that one cannot do it. :)

---

### Post by kansasnoob on 2008-09-07
You might find this helpful:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

From the GRUB page there:

> How to make a separate /boot partition.-contains the Linux kernel, initrd.img and GRUB files.

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

Regarding swap, it can quite well be located inside an extended partition as you can see here on my machine:

[ATTACH]84450[/ATTACH]

What I have there is Windows in one Primary partition and Ubuntu 8.04, Mint Elyssa, and a shared swap all in one extended partition.

This is also a great source of knowledge:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by egalvan on 2008-09-07
As i said, wow and thanks for all the ideas.

But you all seem so serious... :)

Smile, it's all an experiment, it's NOT going to be put to practical use!
(well, I think it won't,, maybe, perhaps....:-k)

What I had in mind was installing as many Linux distros as possible on a laptop.
I  take this laptop to LUG (Linux User Group) meetings.

I am so often asked about this or that distro, and I don't always have the CD or time to install it.

So I remembered the time a buddy of mine and I put about twenty different systems on one computer.
 We were so proud.... \\:D/
then we learned that the record was over 150 (and climbing!)...
 so humbled. :redface:

So I thought, "put a bunch of Gnu/Linux on one laptop". I figure ten to twenty ought to pretty well represent Gnu/Linu/BSD.

Crazy, huh?

As I said, it's an experiment, meant to make me think, and others to laugh.

So keep your ideas coming, but smile!

ErnestG 

:popcorn:

---

### Post by egalvan on 2008-09-07
> **kansasnoob said:**
> You might find this helpful:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

Yes! one of my favorite places, but I have yet to read it all!
> 
What I have there is Windows in one Primary partition and Ubuntu 8.04, Mint Elyssa, and a shared swap all in one extended partition.

OK, now I know it's possible... THANKS!!


> This is also a great source of knowledge:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Yes, another of my favorites, but also have not read it all...

many thanks!

---

### Post by ByteJuggler on 2008-09-07
> **egalvan said:**
> I posted my previous post before yours popped up.

As for the swap FILE idea, where can I get more info?

Thanks, I now have more ammunition for my expermiment.

ErnestG

:popcorn:

To create a swapfile on an existing partition (e.g. say the root partition), do the following:

1.) Create a file of the required size (in the appropriate place, here I just use /swapfile which you can modify all through the below, if needed):
```
sudo dd if=/dev/zero of=/swapfile bs=1MB count=512
```
The bs=1MB together with count=512 means you're creating a 512MB swapfile. Adjust as needed.

2.) Format it as swap space:
```
sudo mkswap /swapfile
```

3.) Tell the system to use it:
```
sudo swapon /swapfile
```

4.) See it being used:
```
free
```

5.) Edit the fstab file and add a line at the bottom, to have the swap space automatically activated at boot (if you want), by adding a line to the fstab file as follows:
```
/swapfile   none   swap   sw   0   0
```

That's it.

---

