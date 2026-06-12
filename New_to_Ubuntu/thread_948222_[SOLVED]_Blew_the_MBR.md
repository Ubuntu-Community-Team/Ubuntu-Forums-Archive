---
title: "[SOLVED] Blew the MBR?????"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Kellemora on 2008-10-15
Hi Gang

OK, I'm in over my head now!

WHERE is the MBR or does it not have one?

I'll start by saying I DO NOT HAVE WinDOZE on this machine and it WAS working perfectly all month.

Step Son did something, tried to play a game from CD designed for a WinDOZE machine.  He said it played entirely from the CD, so I let him boot it up.  The game didn't work of course!

I have THREE Grub Menu.lst's all identical (this is not new, have been that way since I installed to 3 partitions and copied each to each as backups months ago).

hda1, hda2 and hda3 hold the Distro's, hda4E/hda5 is the Swap.

hda1 is Ubuntu, hda2 is Debian, hda3 was Ubuntu Server, now it's Edubuntu.

Up until he installed the game CD, when I booted up, Grub came up and let me select which Distro or it would automatically boot into Ubuntu if I waited 3 seconds.  The GRUB that controlled boot up was on hda1 (hd0,0)  Making changes to the two other copies did not affect boot up, so I left them for awhile and then later copied the right one over them.  Figured I could boot into them if there ever was a problem.  But I see now, it don't work that way.

Using GParted I checked to see everything is intact.  Used Ubuntu Live CD to see that the /boot/grub/menu.lst is intact and complete.  It's there just as it should be on all three partitions, unchanged.

With the Ubuntu LIVE CD I can boot into Ubuntu and access the menu.lst, but nothing is wrong with it.  Checked fstab and the UUID's are correct, or should I say, unchanged also from how they used to read.

What appears to be happening is that the MBR (if that exists on a non-WinDOZE machine), is looking for either Windows or the game CD.  
I do get a boot Screen similar to grub, but the only selection listed on it is some letters and a serial number, nothing like I'm used to seeing.  So, there must be a NEW GRUB written somewhere where I can't find it.  I assume this is on the MBR.

But where is the MBR and how do I overwrite it with a working one?

Thanks
Gary

---

### Post by Tatty on 2008-10-15
This will show you how to re-install your Grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Kellemora on 2008-10-15
Hi Tatty

I don't have WinDOZE, but it worked like a charm!

I must have tried a dozen searches and this page never came up!

But it worked great!

Now I'll go change my underwear, as I have a busy schedule tomorrow!
Just LOVE these 7AM to 2AM days, hi hi..........

TTUL
Gary

---

