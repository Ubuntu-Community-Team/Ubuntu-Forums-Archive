---
title: "[SOLVED] I'm wondering if......"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Wheeeze on 2008-11-24
Hi folks.  I have used 8.04 since not long after it was issued and I have been fairly happy with operating it.  That is to say, I have used it but never had to write any code at all (several reasons for this).  I put it on a brand new computer but had a nightmare getting the USB wireless stick to work, mostly due to my inexperience with wireless networks.

Anyway, long story shortened, I spotted that 8.10 was out yesterday and I want to try it on this computer because it seems that a lot of my woes have been overcome, I think.  I want to end up with dual boot so that I don't wreck what I have now.

The questions are, when I start the computer with the disk in the drive, will it try to overwrite (or update) what I already have, or will there be an option to get my preferred dual boot situation?  Would the 8.10 installation read my settings from the 8.04 and not otherwise affect them?

Many thanks in advance,

Wheeeze

---

### Post by cmnorton on 2008-11-24
If it's a live CD, you should be able to boot with it and try things out. If it's not a live CD, it is easy enough to download one.

While you're test driving the new release, if you want local storage, make sure you mount your drives. Ubuntu has a nice way of putting your local drives in a place that's easily identifiable. From there, you can mount the local drives, and unmount them when you're done the test drive.

The people working on Ubuntu releases do an excellent job. However, no upgrade is perfect. That's why I stay with LTS releases. My Kubuntu T61 is my workstation, and I need it as stable as possible. Another way to do things is to get a nice, cheap system, and upgrade that, but don't make it your "pet" system. I had one of those systems, a nice cheap Acer laptop, pre-hyper threaded, but it got commandered for production work. So, expect problems when you upgrade.

---

### Post by Wheeeze on 2008-11-24
cmn.  Thanks very much for your advice, I will give it a try tomorrow as it is late evening now.  Very grateful and I'll let you know how it goes.

Wheeeze

---

### Post by jnorthr on 2008-11-24
may be less problematic if you try an upgrade first using System>Admin>Update Manager to bring your system more or less up to date. you can always try a Live CD from a unix mag just to tst drive it, If you do not 'install', it will not corrupt your system  just run slowly while you decide to install/or not.

You DO have backups of your most precious data, don't you ? ;)

---

### Post by Wheeeze on 2008-11-25
jnorthr.  Thank you for your advice too.  I can confirm that the system is always updated whenever I get the prompt.  The most precious information to me is the settings for the wireless router!  I had a nightmare setting it up and getting it going but this was probably down to my inexperience with wireless networks more than anything else.  Personal data is always backed up.

I have burnt a disk containing 8.10 but what I really want to know is if I can have dual boot with 2 Ubuntu systems. I know that you can if you have Windows at the start and introduce Ubuntu.  I also really would like to know that if dual boot is supported, will the second installation just read data from the first without changing anything, or will I need to go through the wireless network setup pain that I had before?

Thanks again, still willing to receive wisdom from anyone.

Wheeeze

---

### Post by DieB on 2008-11-25
if you want to keep settings you should do a system-upgrade via > update-manager -d but you will "loose" you system.

If you want to have two ubuntus, simply make some space on your harddrive, for the new root partition (and choose manual partitioning in the install process), you even could use the same /home-partition if you use different usernames for both systems (otherwise you might get corrupted settings of programs).

---

### Post by jimreynold2nd on 2008-11-25
If you are going to dual boot, my advice is to make a separate partition just for GrUB (500MB would be enough for GrUB plus a couple of recovery/backup tools). That way your dualboot/multiboot configuration is not messed up after kernel updates.
Downside is you have to manually edit your grub menu config after each kernel update (it's not that tedious, don't worry, just match up the auto-updated one and your real one).

---

