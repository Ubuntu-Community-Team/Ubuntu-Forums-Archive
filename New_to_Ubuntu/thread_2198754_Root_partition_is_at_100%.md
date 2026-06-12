---
title: "Root partition is at 100%"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by mbrothwell on 2014-01-10
I've had trouble running applications, namely Plex media server. It worked once but has ceased functioning. I see that my root filesystem is 100% in use:

[IMG]http://tryimg.com/4/ubcb.jpg[/IMG]

I assume that's bad...could this possibly create problems?

[IMG]http://tryimg.com/4/uncn.jpg[/IMG]

The disk has 21.5 GB, but sda1 and sda2 are only using 10 GB? 

[IMG]http://tryimg.com/4/ueme.jpg[/IMG]

I'm a total noob but my guess is a need to create a new partition on /dev/sda and add it to the root filesystem? Perhaps one of you kind folks could point me in the right direction? Thanks

---

### Post by philinux on 2014-01-10
Have a look here.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

And for a quick fix check this out for removing old kernels. The can take up quite a bit of space.
Make sure you use the Dry Run in step 6. Just use copy and paste into a terminal.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by Impavidus on 2014-01-10
The old kernels are in /boot on sda1, so that is no problem. The root partition is on sda5, which is only 10GB. However, it looks like you encrypted the root partition, which complicates matters. I don't really know about resizing encrypted partitions.

---

### Post by mbrothwell on 2014-01-10
> **philinux said:**
> Have a look here.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

And for a quick fix check this out for removing old kernels. The can take up quite a bit of space.
Make sure you use the Dry Run in step 6. Just use copy and paste into a terminal.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

The 2nd link freed up about 300 MB, not bad. The first link was very useful! Freed up 3GB just from log files! Thanks. 

But it raised another question. Kern.log was almost 2GB, why isn't it being rotated out on reboots? Even manually running the rotate command produced a kern.log.1 file that was 500kb and left the kern.log file at it's original size. I want the machine to run pretty much 24/7, as it's my media server at night and my distraction from my job during the day ;) (right now). Will I have to periodically cleanse these files to keep from running out of space?

---

### Post by mbrothwell on 2014-01-10
> **Impavidus said:**
> The old kernels are in /boot on sda1, so that is no problem. The root partition is on sda5, which is only 10GB. However, it looks like you encrypted the root partition, which complicates matters. I don't really know about resizing encrypted partitions.

Aw shucks, I could've sworn that I selected not encrypted when I installed Ubuntu, hopefully the 8GB will be enough to work with going forward.

---

### Post by Impavidus on 2014-01-10
> **mbrothwell said:**
> Aw shucks, I could've sworn that I selected not encrypted when I installed Ubuntu, hopefully the 8GB will be enough to work with going forward.

I don't know for sure, maybe you just choose an uncommon way of partitioning. Separate boot partition and lvm partition usually indicates encryption. If you don't have to enter a password during boot (before the login screen/prompt) it's not encrypted. But anyway, it's the lvm partition that changes matters as most people don't use them, so they can't tell you about it. They are actually meant to make changing partitions easier...

Several GB of logs shouldn't happen. Can you find any repeating messages in those logs? It may indicate something's wrong.

---

### Post by mbrothwell on 2014-01-10
I erased the content of the two logs that were over 1GB, but if they fill up again I will look into it, thanks.

---

### Post by rrnbtter on 2014-01-10
Greetings,
It makes some sense to use a separate USR dir. The structure that I use looks like this on a 500 Gig Drive
Partition 1 Boot 800meg
Partition 2 Swap 4 Gig
Partition 3 / (Root)  8Gig
Logical Partition 4 USR 15Gig
Logical Partition 5 Home (Remainder of Drive, but I add a Windows partition at the end.
Logical Partition 6 Windows 'Fat 32 5Gig

I have never lost a Home Dir using this formula and it also makes a duel boot a breeze since a reinstall of Ubuntu won't tamper with the windows Boot loader. 
Also don't forget to look in /USR/SRC for Kernel Poop it will add up to a considerable chunk.

---

### Post by plurga on 2014-01-10
i was checking if there are some restirctions that say something abt the space size that plex software use , but they dont mention anything abt it.
[http://www.engadget.com/2013/02/14/setting-up-a-plex-environment/](http://www.engadget.com/2013/02/14/setting-up-a-plex-environment/)
in this link 
[http://askubuntu.com/questions/266825/what-do-i-do-when-my-root-filesystem-is-full](http://askubuntu.com/questions/266825/what-do-i-do-when-my-root-filesystem-is-full)
there are some likely reasons for an overflowing root partitions , may be it can help u.

---

