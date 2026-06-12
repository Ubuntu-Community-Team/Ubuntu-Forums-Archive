---
title: "How much disk space?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by andyrue304 on 2008-04-23
Hello all,

I'm new to Ubuntu. Been meaning to get into Linux for ages and thought why not with Hardy. I'm (hopefully) receiving a laptop with Ubuntu pre-installed next Friday, but before that happens, I'd like to install it on my desktop.

I have Windows Vista installed and have a Hard Drive partition of 250Gb/250Gb.

Obviously my Ubuntu is going to go onto the second partition (not the one with Vista!), but the problem is that so far I've been using this partition for large files like my Music collection (over 80Gb) and my videos (around 150Gb) so I only have about 25Gb left on this drive.

I know this will be enough for an Ubuntu install, but would you recommend more space? Shall I move some files over to the other partition, as that has like 100Gb free still?

Also, will Ubuntu install nicely on a drive that already has files on it?

Thanks in advance for your advice.

---

### Post by philinux on 2008-04-23
Thats enough space.

---

### Post by Ub1476 on 2008-04-23
25GB is more than enough. Here's a guide for installing when you have to different HDDS:

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=(installing](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=(installing))

Even though I would recommend you to mount the ISO in Vista, then let Ubuntu install within Vista (later you can remove it in add/remove in Vista). Since you're going to just try it out it's probably the easiest.

---

### Post by woaiwojia on 2008-04-23
Thats enough space.

10G   /

1G    SWAP

14G   /home

---

### Post by Joeb454 on 2008-04-23
Woah!

_*Don't install Ubuntu on a drive that's already got files on it*_. You'll need to give it it's own partition!

You could always make a 25Gb partition on the drive though :)

---

### Post by hyper_ch on 2008-04-23
In Vista you have a partitioning programm that can shrink your existing second 250 GB drive. First, defrag that drive 2-3 times and then use the vista partitionier for shrinking. That way your files will not get lost.

DO NOT DELETE that 250 GB partition but DO SHRINK it.

Once you've shrinked that 250GB down and have 25GB unused space, leave it like that. Do not format it!

During Ubuntu installation you then select "USE LARGEST CONTINOUS FREE SPACE".

---

### Post by andyrue304 on 2008-04-23
> **Joeb454 said:**
> Woah!

_*Don't install Ubuntu on a drive that's already got files on it*_. You'll need to give it it's own partition!

You could always make a 25Gb partition on the drive though :)

Thanks, I thought that was a bad idea!

If I make a new partition, should I make it in Windows first or does the installer do that for me? Is there a chance I'll loose any files?

---

### Post by andyrue304 on 2008-04-23
> **hyper_ch said:**
> In Vista you have a partitioning programm that can shrink your existing second 250 GB drive. First, defrag that drive 2-3 times and then use the vista partitionier for shrinking. That way your files will not get lost.

DO NOT DELETE that 250 GB partition but DO SHRINK it.

Once you've shrinked that 250GB down and have 25GB unused space, leave it like that. Do not format it!

During Ubuntu installation you then select "USE LARGEST CONTINOUS FREE SPACE".


Great stuff,

I'll try it!

---

### Post by Joeb454 on 2008-04-23
Glad you read the posts by **hyper_ch** and myself before you started. I was speaking from experience (I forgot to move some stuff off a drive once :()

---

### Post by andyrue304 on 2008-04-23
> **Joeb454 said:**
> Glad you read the posts by **hyper_ch** and myself before you started. I was speaking from experience (I forgot to move some stuff off a drive once :()

Youch!

I'm not gonna be starting this install until the torrent has downloaded anyway. (I'm starting to download tomorrow)

If I choose "use most continuous space" in the installer, won't that then choose my current C: drive as that has more space on it?

---

### Post by Joeb454 on 2008-04-23
If you have an empty partition (i.e. totally emtpy and unformatted) then it will use that. Your drive C:\ will be seen as used space (because it is formatted).

And may I wish you luck in downloading the iso file tomorrow. It's going to be very chaotic ;)

---

### Post by MONODA on 2008-04-23
you should first shrink your vista partition then select the "use most continuous space" in the installer. This will just use the unformatted space on your harddrive, not the C: drive.

---

