---
title: "Are updates for Ubuntu hardware dependent"
date: 2006-05-08
forum: Repositories &amp; Backports
---

### Post by wpshooter on 2006-05-08
After you have done the initial installation of dapper drake beta 2 version and you get the notice that there are approx. 300 updates available, are these updates that are shown in the listing **ALL** (including the ones related to updating of the kernel) supposed to be applied to the installation **OR** is what you download and subsequently install, dependent upon what type of hardware components you have in your system ?

For instance, are some of the **kernel** updates only for systems with Intel processors and others for systems with AMD processors ?  If this is true, does this same thing apply to updates **OTHER THAN** the kernel updates ?

And also, if this is true, how does one know which updates need to be applied to various systems with different hardware components (is the short descriptions that are shown under each update supposed to relate this to you ?

Thanks.

---

### Post by Dr. Nick on 2006-05-09
The updates are all newer versions of the programs installed currently, some may fix hardware problesm for hardware that you do not have. Especially kernel ones. The only thing you can do is read teh changelogs to see what has been done. If it is working and your happy you can jsut stick with the current version, unless its a security update.

Basically If thier is a new version of anything it will always appear in the updates, even if it has nothing to do with your hardware

---

### Post by az on 2006-05-09
[QUOTE=wpshooter]After you have done the initial installation of dapper drake beta 2 version and you get the notice that there are approx. 300 updates available, are these updates that are shown in the listing **ALL** (including the ones related to updating of the kernel) supposed to be applied to the installation **OR** is what you download and subsequently install, dependent upon what type of hardware components you have in your system ?[/QUOTE]

All.  If there is a change in the way they handle translations, for example, every single package will get revised and you will have to download them all.  This does not happen after release to the degree it is happening now, since this is the final stretch before release and there are  alot of busy developers fixing stuff.

[QUOTE=wpshooter]For instance, are some of the **kernel** updates only for systems with Intel processors and others for systems with AMD processors ?  If this is true, does this same thing apply to updates **OTHER THAN** the kernel updates ?[/QUOTE]

No other packages are hardware specific in that way.  All of the packages on your system are either x86, ppc or amd64.  Within that, you can install a 686, smp or k7 kernel for a pentium or amd processor, if you want.  But the system will work fine without you doing that.

[QUOTE=wpshooter]And also, if this is true, how does one know which updates need to be applied to various systems with different hardware components (is the short descriptions that are shown under each update supposed to relate this to you ?

Thanks.[/QUOTE]
Short of installing a differnet kernel, you don't have to.  It's all the same.

---

