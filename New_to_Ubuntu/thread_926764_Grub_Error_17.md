---
title: "Grub Error 17"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by nrcooled on 2008-09-22
Alright, here's my story.  I tried to upgrade to Hardy and the installation failed miserably.  I've tried to fix the bad install but the only option was to just remove ubuntu all together and start fresh.

So I removed Ubuntu and deleted the partition through Vista.  I wanted to install ubuntu on the other HDD in my laptop.  Now, for obvious reasons the Grub is not happy at all.  Can someone help me just get my computer to boot?

The Grub comes up and just gives an Error 17 with nothing else on the screen but the Grub version number and Error 17.  

Cliff's notes:
-Removed Ubuntu and it's partition after failed upgrade
-Grub fubar'd 
-Grub gives Error 17
-Want to get original Widows boot loader back to start fresh
-Please help

---

### Post by ianhaycox on 2008-09-22
[This may help]("http://ubuntuforums.org/showthread.php?t=897984") and for everything you ever wanted to know about fixing grub/ubuntu/windows booting problems try [this grub page]("http://users.bigpond.net.au/hermanzone/p15.htm").

---

### Post by billgoldberg on 2008-09-22
Did you already installed Ubuntu again?

If you do that, everything should be good.

--

There is a great tool for just this kind of problem.

It's called the "super grub disk".

It will allow you to boot Vista, Ubuntu, repair the mbr, repair the grub, ...

It's a live cd, so burn that puppy to a cd, reboot and you will be good.

---

### Post by kansasnoob on 2008-09-22
> Want to get original Widows boot loader back to start fresh

You'll need to restore Vista's mbr. If you have no disc you can get one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

or here:

[http://www.winvistatips.com/fix-mbr-a116.php](http://www.winvistatips.com/fix-mbr-a116.php)

You want to "fix boot" and "fix mbr"!

---

### Post by nrcooled on 2008-09-22
Thanks for the help everyone.  I have the recovery CD's from HP and I am hoping that they have the Bootrec.exe program on them.  I'll play with it tonight and try to fix it.

Edit:  Just found out that the HP recovery disks don't have bootrec.exe on them :(  I guess I'll have to find a different way to get the program.

---

### Post by kansasnoob on 2008-09-22
> Edit: Just found out that the HP recovery disks don't have bootrec.exe on them  I guess I'll have to find a different way to get the program.

They're on the disc I linked to!

---

### Post by nrcooled on 2008-09-23
> **kansasnoob said:**
> You'll need to restore Vista's mbr. If you have no disc you can get one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

or here:

[http://www.winvistatips.com/fix-mbr-a116.php](http://www.winvistatips.com/fix-mbr-a116.php)

You want to "fix boot" and "fix mbr"!

quickest fix evAr!!!  Thanks for the help.  Downloaded the torrent and burned the ISO.  Booted to the disk and ran two commands.  Done!

Now to see if I can get Hardy to install properly on my box.

---

