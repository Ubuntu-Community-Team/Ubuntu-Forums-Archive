---
title: "Ubuntu Vs Windows... Help!"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by hka on 2008-05-12
Hi friends,
I am absolutely new to Ubuntu and need serious help. I have been using WindowsXP so far and decided to shift to Linux recently (two days ago to be precise). I have fromatted my PC, retaining a partition where I had my documents/ pictures etc. But now I have copied everything to the desktop in Ubuntu and need to format that partition. Can anybody please help me for:

(1) Formatting a partition from Ubuntu and use that as free space?
(2) While starting up, the boot loader still gives me the option to load Windows XP, which doesn't even exist in my system. How do I remove that reference?

Since I am a first time user of Ubuntu or Linix of any kind for that matter, I need some expert help please.

Thank you so very much.

---

### Post by zenwalker on 2008-05-12
I assume that u have installed Ubuntu on a seperate partition. Any ways now to u r problem:

1) TO partition u r HDD, use Gparted tool if present, or else use Synaptic package manager (find it on the menus) and download off Ubuntu repos. 

2) Go to /boot/grub/menu.lst file and remove the winnie entry at the bootom of the file, where no # is prefixed to the lines. Make sure u dont delete ubuntu entries.

---

### Post by jamyskis on 2008-05-12
> **zenwalker said:**
> I assume that u have installed Ubuntu on a seperate partition. Any ways now to u r problem:

1) TO partition u r HDD, use Gparted tool if present, or else use Synaptic package manager (find it on the menus) and download off Ubuntu repos. 

2) Go to /boot/grub/menu.lst file and remove the winnie entry at the bootom of the file, where no # is prefixed to the lines. Make sure u dont delete ubuntu entries.

You're going to have a slight problem with doing this. Namely, GParted doesn't allow you to repartition the current root partition for safety reasons (the partition you're running Ubuntu from)

What you'll want to do is boot your LiveCD and use the Partition Editor (System/Administration) there.

You should really backup all your data before doing any partitioning, but since you were using a hard drive partition for this, I'm guessing you don't have the means.

---

### Post by nick_h on 2008-05-12
You should consider keeping the partition you used to store documents/ pictures as a separate /home partition.

You can format a partition using the mke2fs command.  For details type:
```
man mke2fs
```

---

### Post by hka on 2008-05-13
Thanks friends.

I removed the winnie entry by using the ideas provided by u all. Thanks again.

But on the formatting part, I still couldn't do it. Maybe I will continue using that as a document storgae.

---

