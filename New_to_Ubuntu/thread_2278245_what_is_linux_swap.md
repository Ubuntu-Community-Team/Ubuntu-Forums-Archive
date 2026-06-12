---
title: "what is linux swap?"
date: 2015-05-14
forum: New to Ubuntu
---

### Post by houmingc on 2015-05-14
Can someone tell me what is linux swap for?
it has to be run on NTFS or FAT32?

---

### Post by sammiev on 2015-05-14
Hi houmingc,

Here is a good start on [swap]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F") for you.

---

### Post by jimmy-frydkaer on 2015-05-15
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=2274067](http://ubuntuforums.org/showthread.php?t=2274067)

---

### Post by lisati on 2015-05-15
[This web page]("https://www.linux.com/news/software/applications/8208-all-about-linux-swap-space") deals with what "swap" is and what its for.

---

### Post by RobGoss on 2015-05-15
Great info thanks for posting this.

---

### Post by buzzingrobot on 2015-05-15
> **houmingc said:**
> Can someone tell me what is linux swap for?
it has to be run on NTFS or FAT32?

Swap in Unix/Linux is a partition (not a file).  Its purpose is to substitute physical space on a drive for RAM space when RAM runs short.  When a program or a process asks the Linux kernel for an allocation of available RAM, if that amount of RAM is not available, the kernel will move enough of the contents of RAM to the swap partition to allow that allocation to be made. Later, when a program or process requests access to the memory swapped out on the swap partition, the kernel reads it back into RAM, first swapping out some RAM if it needs to make space available.

Swap dates from the earliest days of Unix, when drives were small, large, and very expensive, and when RAM was also expensive. Unix systems could not be used productively on such systems without relying on the use of swap. Desktop Linux users today with more than minimal RAM (say, 4-8 gigs) most likely will never see their systems use swap unless they are doing something like processing a large number of large video files. On the other hand, unless you are extremely short of drive space, I think it's reasonable to have a swap partition to allow the system to perform correctly in extreme circumstance.

Use of swap when RAM use is maximized makes a system very sluggish since accessing a drive is orders of magnitude slower than accessing RAM. This slowness is the reason we see users with inadequate amounts of RAM complain about swap slowing down their machine.  The alternative, though, is that their machine would be even slower without swap, and eventually lock up.

The swap partition is not formatted and does not use a file system, e.g., NTFS, EXT4, etc.

---

### Post by kurt18947 on 2015-05-15
> **buzzingrobot said:**
> Swap in Unix/Linux is a partition (not a file).

It can be a file :smile:. 

[https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)

One limitation of swap file vs. swap partition is that a swap file cannot be used to hibernate; hibernation requires a separate swap partition AFAIK. I've read where hibernation on Ubuntu can be unreliable and I find suspend or simply shutting down works fine for my purposes. Desktop Ubuntu boots quite quickly. A swap file is pretty easy to add post install. I'm pretty sure a swap partition can be added post install as well but I don't know that it's as straightforward. I might have a machine with 3 or 4 GB. RAM. That's plenty IME for most linux desktops. If I want to install something like VirtualBox or VMplayer and have several OS s loaded at the same time, 3 or 4 GB. is probably not enough.

---

