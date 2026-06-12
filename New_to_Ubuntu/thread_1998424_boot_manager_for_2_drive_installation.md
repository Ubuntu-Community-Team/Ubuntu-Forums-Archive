---
title: "boot manager for 2 drive installation"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by lkjjr on 2012-06-06
New to Ubuntu/Linux and really excited to have found this alternative to MS. I have a lot of experience with PCs, but have been really exasperated by the MS restrictions, costs and attitudes. Recently tried several Linux distros and settled in with Ubuntu 12.04. Have already learned a lot, and much of that from this forum. 
 
 
Currently running dual boot w/Win7Pro 64bit and 12.04 64bit on a 160gb hdd. I'm wanting to improve my set up with a 2nd hdd mounted in a removable/swap-able hard drive caddy. Because of the pain/unpleasantness of Windows validation I want to keep W7 on the primary/internal drive. I'm pretty cool with understanding how to delete Ubuntu, re-partition the drive and restore the MBR. I'll reinstall 12.04 to the 2nd hdd.
 
 
Here's where I could use advice. I've done a good bit of searching (here and elsewhere), but have had a difficult time locating the specific answer I need. I may need to swap out the caddy for a CD-ROM occasionally, and when I do I want to be able to boot W7 from the primary drive without hassle. But when I return the 2nd hdd to the bay, I want to be able to get to either OS without needing to “reprogram” a boot loader. My question is...
 
 
Would it be better in this instance to install Grub to 2nd hdd and have it manage the boot options when present, or better to have W7 manage booting by having 12.04 as a second menu choice there (using EasyBCD)?
 
 
I guess at the bottom line I'm trying to treat the 2nd hdd almost like using a flash drive, only with greater storage capacity
 
Thanks for all the help so far and thanks for taking a look at this too...

---

### Post by oldfred on 2012-06-06
You should be able to install grub2's boot loader to the external drive & set BIOS to boot that first, Internal 2nd. Then if external is not found it will boot the internal and it has the Windows boot loader.

You do have to use manual install or Something else to get the combo box on where to install grub's boot loader. All the auto installs default to sda or usually the internal drive.

Difference in installer is not huge between versions.
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by lkjjr on 2012-06-06
Thanks OldFred...
I am able to follow that logic and it sures looks like what I needed.
The "pg24" link really lays it out well too.  Waiting on the 2nd drive and caddy to arrive.  I'll get back to the thread and let everyone know how it works out.
 
p.s. great forum, feel fortunate to "be here."

---

### Post by wilee-nilee on 2012-06-06
> **lkjjr said:**
> Thanks OldFred...
I am able to follow that logic and it sures looks like what I needed.
The "pg24" link really lays it out well too.  Waiting on the 2nd drive and caddy to arrive.  I'll get back to the thread and let everyone know how it works out.
 
p.s. great forum, feel fortunate to "be here."

Hermans site is dah bomb for sure. ;)

---

### Post by lkjjr on 2012-06-15
Just wanted to check back in to validate that this strategy worked beautifully as suggested.  By installing Grub on 2nd hdd (sata drive in swappable bay caddy) and pointing to that drive before the internal hdd in bios boot priority,  I'm able to remove the 2nd hdd and boot to Win 7 normally with the W7 boot loader.  Then return the 2nd hdd to the bay and dual boot is available via Grub as before.

Thanks OldFred ...

---

