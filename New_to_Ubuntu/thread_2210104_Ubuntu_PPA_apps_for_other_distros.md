---
title: "Ubuntu PPA apps for other distros?"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by clementchiew on 2014-03-09
Is it possible to use Ubuntu-only PPAs in other distros and are there any methods to get them? I wanted the OS Uninstaller by YannUbuntu and Boot-Repair but I dont really want to boot a Ubuntu Live CD. Arch will be pretty nice.

---

### Post by monkeybrain20122 on 2014-03-09
No unless that 'other distro' is Mint. If you have a .deb you may be able to convert it to a rpm with alien, if you are lucky it may install.  But arch does everything from source, so even a .deb won't work let alone ppa.

---

### Post by Rob Sayer on 2014-03-09
Even with Mint I'd be very cautious.  It may be ubuntu based but they use older kernel versions.  I had mint installed about a year ago for a little while on this netbook (12.04 lts doesn't work so well so I've distro and dektop hopped waiting for 14.04 lts).

I switched back to ubuntu ... the same version mint was based upon ... because I had hardware support issues with the kernel version mint used.  Mint tech support is useless enough for run of the mill problems, let alone something like that.

---

### Post by oldos2er on 2014-03-09
> **clementchiew said:**
> Is it possible to use Ubuntu-only PPAs in other distros and are there any methods to get them? I wanted the OS Uninstaller by YannUbuntu and Boot-Repair but I dont really want to boot a Ubuntu Live CD. Arch will be pretty nice.

Boot repair offers its own live boot repair disk, see [http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by buzzingrobot on 2014-03-09
Better and safer to search for a package built for a distribution rather than install a package built for another.

PPA's, for example, can result in the installation of dependencies that overwrite core components.  Even if that seems to work, there's a real risk future updates will go wrong. The risk on a "foreign" distro would increase.

---

### Post by monkeybrain20122 on 2014-03-09
> **buzzingrobot said:**
> 
PPA's, for example, can result in the installation of dependencies that overwrite core components.  Even if that seems to work, there's a real risk future updates will go wrong. The risk on a "foreign" distro would increase.

Good point. Example is that you can add Debian's mutlimedia repo to Ubuntu's sources list but it is likely to break your system if you try to install or upgrade from it even though some lucky souls have reported success around the Ubuntu 10.10 days. :)

---

