---
title: "Hardy / Intrepid dual boot"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by BC7333 on 2008-11-11
I'll be setting up a new laptop the next couple days or so.

Want to install both hardy and intrepid as dual boot (both in grub to select)

Will use a separate home partition 

Should I first install Hardy, then Intrepid? or vice versa?

Any other things to watch out for?

Thanks!

---

### Post by Aearenda on 2008-11-11
I have done this. I use a 10Gb partition for Hardy, 10Gb for Intrepid, then a swap partition and finally a home partition. I would install Hardy first, then Intrepid, but really it doesn't matter (unlike Windows). However, I keep my home folders separate on the system I don't use every day (which is now Hardy), so that settings for Hardy and Intrepid are separated. I soft-link the sub-folders of my main home into the other one.

The gotcha is this: UUID naming of partitions.
When you set up the second system, by default it will reformat the swap partition, and it's UUID (essentially a long hex number) will change. The first system will then not find it.

How I would do it, assuming I had enough RAM to run without swap during the installation and setup:
1. Set up Hardy, with manual partitioning. Create all 4 partitions, tell it not to use the one that Intrepid will be in. Continue the installation. Get it working nicely.

2. Set up Intrepid, but proceed without swap or home partitions - so /home will be in the Intrepid root partition.
2.1 Mount the Hardy root partition manually somewhere e.g. sudo mkdir /alt && sudo mount /dev/sd?? /alt (fix the ?? with yours)
2.1 Copy the line in /alt/etc/fstab for the swap partition from Hardy to Intrepid's /etc/fstab.
2.2 Copy the line in /alt/etc/fstab for the home partition from Hardy to Intrepid, but make it mount somewhere other than /home (I use /ohome - don't forget to mkdir it).
2.3 Copy the line in /etc/fstab for the / partition in Hardy to Intrepid, but make it mount somewhere else (I use /alt)
2.4 Mount the /ohome and /alt partitions.
2.5 Link major folders from the real home into the new /home.
2.6 Get Intrepid working nicely.

You might want to simplify things by just using a combined /home - but this might cause problems with differing versions of software. I have never tried to do this other than going from older to newer.

Good luck!

Postscript: Installing Intrepid second makes its /boot/grub/menu.lst get a snapshot of Hardy's, and any new kernels in Hardy will then be ignored. I change the 'other version' entry to, for example: ```
title		Ubuntu Hardy
configfile	(hd0,0)/boot/grub/menu.lst
savedefault
```so that changes are picked up automatically.

---

### Post by BC7333 on 2008-11-11
> **Aearenda said:**
> 
2.5 Link major folders from the real home into the new /home.


Aearenda,

Many thanks! Can follow along with most but a bit confused with 2.5 and linking..

I would prefer, if possible to use the same /home directory for both, this way could keep browser / icq history, settings etc the same.  I do understand your point though with other software that might not be compatible between intrepid/hardy.

Can you describe how to 'link major folders'?

With 2gb ram shouldn't be a problem to do without swap but what about hibernate? -doesn't that use swap to save the memory image?

---

### Post by Aearenda on 2008-11-11
Sure! What I would do (have done in the last few weeks, in reality) is this:
 1. In Hardy, everything is as it has been since I installed that back in April (March, really!).
 2. In Intrepid, I have a new home folder, with the Hardy home mounted at /ohome.
 3. For each of my folders, I do ```
ln -s /ohome/me/<foldername> ~/
```

This creates a soft link in Intrepid that points to the existing folder in Hardy. Since Firefox and Thunderbird are the same versions in both, for example, I do ```
ln -s /ohome/me/.mozilla ~/
ln -s /ohome/me/.mozilla-thunderbird ~/
```Then I can use FF and TB in both, just as you want. However, I suspect Evolution has a new version, so I wouldn't try this with Evolution (I find Evo much faster than TB, but less stable).

Similarly, I would link Documents, Pictures, and so on; I also do it for .tomboy and .wine.

When you look at the folders in Nautilus, they have pointers, just like Windows shortcuts, but they work as if they were real folders, unlike in Windows.

The swap is picked up on next reboot after adding to /etc/fstab. Or you can use 'swapon'.

I hope this helps!

---

### Post by BC7333 on 2008-11-11
Aearenda,

That clears things up quite a bit!.. will let you know in a few days (probably coming weekend) how things are going.

Again thanks for chipping in!

---

### Post by indytim on 2008-11-11
> The gotcha is this: UUID naming of partitions.
When you set up the second system, by default it will reformat the swap partition, and it's UUID (essentially a long hex number) will change. The first system will then not find it.

If you select the **manual partition option** and identify the existing /swap, this should not apply as long as you do not click to re-fortmat. -OR- Is this some new "enhancement" introduced with 8.10?  I've got a common /swap running across 4 different variations of Linux and never ran into this (always use the manual partition option on the builds).

IndyTim

---

### Post by Tony Flury on 2008-11-11
I installed Intrepid onto a new partition with Hardy already installed, and existing home and swap.

I have no problem with either of them botting and using the swap areas.

All i did was made sure that i did not reformat /home and /swap when i installed Intrepid.

---

### Post by Aearenda on 2008-11-11
I don't think you get the choice not to reformat swap. I found one day that my older system was not using swap, and this was the reason why. 

You certainly do get the choice for /home. The issue for /home is hidden folders for differing versions of software, where you are likely to be booting the older version after the newer version (repeatedly reverting and then going forward again, as the dual boot option is used). It also avoids confusion when new panel applets are delivered, for example, so that the panel settings for Hardy (where I use USP) don't try to load on Intrepid (where I didn't install USP until I was sure Intrepid was usable for me every day).

If your /etc/fstab is modified to use /dev/sdxy naming, there is no problem either. It is only when UUID naming is used (the default in Ubuntu) that the swap problem occurs.

One problem with the way I do it is that the home folder on the newer installation ends up in that installation's root filesystem. It would be cleaner to have a different home folder name (set in /etc/passwd) and share the home partition properly, and I'll probably do it that way in future.

Other spots to check for UUID naming: /boot/grub/menu.lst, check the resume partition if present.  /etc/uswsusp.conf, if you have uswsusp installed.

---

### Post by indytim on 2008-11-11
> It would be cleaner to have a different home folder name (set in /etc/passwd) and share the home partition properly, and I'll probably do it that way in future.

I tried the common /home between version a while ago and ran into some significant problems.  Things may have changed since then and a common /home may be the practical approach.  Would be good to hear from someone who is actually successfully using this and their experiences.

IndyTim

---

