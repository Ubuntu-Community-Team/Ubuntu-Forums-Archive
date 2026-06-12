---
title: "Ubuntu installed via Wubi, lost regarding upgrading windows"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by zyphial on 2012-12-06
I'm far from a power user, so I have very little understanding of setting up dual boot systems. My objective is to get a dual booting Windows 8/Ubuntu 12.04 system up and running without losing my current setup in Ubuntu (the windows data can and probably should get nuked from orbit).

Here's my current setup: 2 Hard Drives, C:\ and D:\, with C:\ containing a standard Windows XP install and D:\ containing a Wubi install of Ubuntu 12.04.

 I plan to upgrade my XP install to Windows 8 (an unfortunate necessity) and to upgrade my C:\ drive from 160 GB to a full TB, but I'm not sure what the proper upgrade path is.  Right now, I plan to 1) Replace C:\ with a new, much larger hard drive by using liveCD to copy the windows partition. In part, this is insurance: I don't trust windows upgrade and if it fails, I want to keep my untouched XP install safe. 2) I will create a second, bare partition on the new drive and migrate the Wubi install from the C:\ clone onto the new partition. I want to keep all the data I have in Ubuntu, so I'm trying to just migrate wubi. 3) Upgrade windows XP to Windows 8.

My concerns are twofold. A little bit of googling seems to make the first problem a non-issue - migrating the Wubi install onto its own partition SEEMS easy enough, but I'm hesitant to just dive right in. The second concern, though, is trying to convert my system into a dual boot Windows 8/Ubuntu 12.04 system without having to wipe everything and start from scratch.

I did research and found that windows 8 does not play nice with dual booting, and not only likes to wipe all partitions but also tampers with the MBR (a term I only vaguely understand). Rather than dive in and wind up losing everything, I thought I would talk to someone more experienced first. I really appreciate any help on the matter.

So, in short, **Can anyone give me advice on how best to wind up with a cloned C:\ set up as a dual boot Windows 8/Ubuntu 12.04 system, with windows 8 and ubuntu on seperate partitions, given my set up currently?**  Thank you all. This forum is very informative.

---

### Post by monkeybrain2012 on 2012-12-06
Wubi is not dual boot, it is a sort of a test drive version running out of the Windows file system so of course it will be gone if Windows is no more. In a dual boot both OS have equal status and each has its own partition. Ubuntu through WUBI doesn't have equal status as Windows.

---

### Post by zyphial on 2012-12-06
Yes, thank you for trying to help, but that much I already understood. I currently have a wub install and want to migrate that to a full equal-to-windows install. I'm also upgrading XP to 8 at the same time, which complicates matters. I'm asking advance on the beast means to go from Wubi on XP to an Ubuntu/Windows 8 dual boot, preferably without losing the data on my Wubi drive (several gigs of game files, work related materials, multimedia).

It's a lot of things at once, I realize, but unfortunately they're linked and must happen together. As you said, I can't boot Wubi if Windows 8 wipes the XP install (as it will, 32bit to 64 bit MUST), so I can't migrate at some later date.

---

### Post by monkeybrain2012 on 2012-12-06
For the reason I stated I never use Wubi, now is it possible to move your files out to Windows XP? I think there should be some ways to share files with Wubi, no? If you can do that you can then move these data somewhere, like to an external drive.

I never use Windows 8 so this is probably wrong, but with Xp you first install XP, then shrink the XP partition (some people say you should use a Windows tool to do it in Windows after Windows7, though i just used gparted when I was dual booting with XP a few years ago) then boot from a Ubuntu live CD or usb and choose "something else" to install into the free space, (formatted as Ext 4 and the flag is /) and don't forget to save a few G for swap. 

There is also an option called "install along side", presumably if you use this option you don't need to manually partition your drive beforehand, but I have never used it so I don't know how exactly does it do the partition. It seems you have more control to do it manually.

---

### Post by zyphial on 2012-12-06
The direct Windows XP -> Windows 8 install path is different from the Windows 7 -> Windows 8 path, and it's quite explicit in that Windows 8 must wipe the slate clean when installing from XP - there is no side along installation option. I'm also not really interested in having 2 windows versions installed (tbh, 1 is too many, but I don't have a choice).

Ultimately, I'm looking to dual boot Ubuntu with windows 8. It sounds like you're saying I wont be able to transfer the Wubi installation into a full blown linux install (though, I thought this was possible? Perhaps I misunderstood what I read - clarification by anyone who's certain would be much appreciated).

The problem with simply duplicating the data on the wubi install is that what I'm seeking to keep is too large for any alternative storage I have (~50 gigs). That's actually why I'm upgrading my hard drive and why I wanted to migrate Wubi rather than fresh install Ubuntu. That may be the easiest option, but I'm trying to avoid it if it's unnecessary.

---

### Post by monkeybrain2012 on 2012-12-06
I wasn't talking about installing 2 windows, I was talking about installing Ubuntu alongside WIndows, all I wrote above is about how to install Ubuntu in a separate partition when Windows is already installed.

Basically manually partition the hard drive, then boot into a Ubuntu live CD and install with the "something else" option. If you install with the "install along side" option then you don't need to partition your drive manually but I don't know how it would actually do the partition, like I said, I have never used it.

What I said above applies to Windows XP, if you have windows 7 or 8 there may be some changes, I don't know, haven't used Windows for a few years now.

As far as I know there is no way to change WUBI to a real install, and if there is a way, it is probably too complicated to be bothered. I was asking whether you have a way to just save your data outside Wubi, in XP where you installed WUBI (I suppose there is a way to share files between WUBI and the ambient WIndows system, no?) From XP you can transfer them to an external hard drive for back up and then once you have installed Ubuntu you can move them back.

---

### Post by arpanaut on 2012-12-06
Here's the "Semi-Official" method for migration:  [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Give it a shot, backup of your data is still suggested. 
Things Can and Will go wrong.

---

### Post by Mark Phelps on 2012-12-07
> **monkeybrain2012 said:**
> As far as I know there is no way to change WUBI to a real install ...

Then you should take a couple of minutes and check out the Wiki for Wubi.  The Wubi Guide contains the instructions for doing just this kind of migration.

---

### Post by zyphial on 2012-12-07
Thank you, but I should mention I've read the relevant portion (migration) of the Wubi Wiki and it doesn't directly address this issue. If I migrate before upgrading windows, Windows 8 as I understand will not cooperate and hide the ubuntu partition (or even overwrite it) and installing windows 8 first will erase the .MBR that linked the Ubuntu virtual partition to the Windows boot.ini, making it unreachable.

If anyone can explain how I can safely migrate, then install windows 8 without destroying the Ubuntu partition, and lastly fix the damage Microsoft inflicts in trying to block the Linux side-along, I'd appreciate it. I can't find a guide for someone in my position.

I've read a lot of horror stories involving Windows 8 and Microsoft's efforts to jam Linux installs and I want to avoid the pitfalls. Thank you for the help.

---

