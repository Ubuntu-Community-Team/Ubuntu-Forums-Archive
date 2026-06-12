---
title: "[SOLVED] Kernel Update?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-10-14
Hi All,

As I am sure all have noticed, there is a new kernel version out today.  I thought I remembered reading that you should not update your kernel.  What are the benefits and risks??  Should I back up before I do so?  Also, with Intrepid on the horizon, as I understand we should not be doing upgrades, just do a clean fresh install.  I know what files I need to save, but how do I back up all my packages so that I can just load up and not spend a week making everything play nice again :)

---

### Post by handydan918 on 2008-10-14
misposted

---

### Post by weirdtalk on 2008-10-14
um, when you say kernel update do you mean the Linux kernel, or the Ubuntu distribution. 

Easy way to tell Linux kernel number will be around 2.6 (point something) and Ubuntu number will be around 7 or 8 (point something).

because my answer is different based on which it is.

---

### Post by rideburton56 on 2008-10-14
The Linux Kernel is what my first question is about

---

### Post by sumguy231 on 2008-10-14
You should install all regular security updates for your current kernel from the update manager, as those are security updates. But as for updating to new major kernel versions (like the new 2.6.27 version you mentioned), you should only do so if you:
1.) Really know what you're doing, and
2.) Have a reason to upgrade, like some of your hardware is only supported in the new version or it fixes a major bug you've been having.

Barring those two conditions, just don't worry about it.

As for upgrading from Hardy to Intrepid, I would personally recommend a clean reinstall as those usually work out better but if you back your stuff up you might as well try upgrading it anyway and seeing if you have problems.

---

### Post by rideburton56 on 2008-10-14
there was a post on this about using dpkg to print a list of all the installed packages that I have, and that i uninstalled.  Unfortunately, he deleted his post.  I felt that it was valuable I just wanted to confirm the commands and that when I am on a fresh OS (intrepid ibex) that it will pull all packages off that list from the repos.

---

### Post by detroit/zero on 2008-10-14
> **rideburton56 said:**
> there was a post on this about using dpkg to print a list of all the installed packages that I have, and that i uninstalled.  Unfortunately, he deleted his post.  I felt that it was valuable I just wanted to confirm the commands and that when I am on a fresh OS (intrepid ibex) that it will pull all packages off that list from the repos.
The commands are:
```
sudo dpkg --get-selections > ~/Desktop/packages.log
```and```
sudo dpkg --set-selections < ~/Desktop/packages.log
```Of course, you can name the file anything you want, and put it anywhere you want; that's just an example.

---

### Post by rideburton56 on 2008-10-14
So I would run the second command after doing a fresh install?

---

### Post by detroit/zero on 2008-10-15
> **rideburton56 said:**
> So I would run the second command after doing a fresh install?
Yes, exactly. Obviously, with doing a fresh install, you want to make sure you have that packages.log file somewhere it's not going to get lost or overwritten.

---

### Post by Orange_and_Green on 2008-10-15
Hello :) I am working on a program that automates the task of keeping backups of your installed packages... see the link in my signature if you are interested...

Also, when you update to a newer kernel, you also get to keep the old one, and entries are added to your GRUB menu so that you can boot from either of the two. So if you're curious, just go ahead and try, it's all easily reversible.

NOTE: If you boot from the new kernel and it says something about low graphics mode (or if the screen looks funny in any way) it means the new kernel is incompatible with your video driver. If this happens, do not click on ANY button offering to fix graphical settings, just get the hell out of there at once and boot from your older kernel from GRUB.

---

### Post by philinux on 2008-10-15
> **rideburton56 said:**
> Hi All,

As I am sure all have noticed, there is a new kernel version out today.  I thought I remembered reading that you should not update your kernel.  What are the benefits and risks??  Should I back up before I do so?  Also, with Intrepid on the horizon, as I understand we should not be doing upgrades, just do a clean fresh install.  I know what files I need to save, but how do I back up all my packages so that I can just load up and not spend a week making everything play nice again :)

Just keep updating as normal and all will be fine. Just remember to back up stuff in home. As this is where all your settings are for the installed apps. These get picked up again should you reinstall and restore your home from backup.. If you got home on it's own partition it's even easier.

---

