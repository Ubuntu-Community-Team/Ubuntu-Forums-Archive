---
title: "how to update to latest software in Lubuntu 12.04?"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by hansq on 2013-09-16
Hi Ubuntu Forums,

I've recently installed [Lubuntu]("http://www.lubuntu.net/") 12.04 on my [IBM Thinkpad X40]("http://www.cnet.com/laptops/lenovo-thinkpad-x40-2386/4505-3121_7-30733357.html") . I like Lubuntu, but the problem is I can't upgrade to a newer version of this distro because my laptop's processor does not support PAE (The newer distros require this). Alot of the software that came preinstalled on it is buggy and outdated (for example The Gimp, Abiword, etc ... are a few versions behind).

Some solutions that I thought of:
- install new apps from source (but in my experience this process is very time consuming and at times frustrating because I need to download dependencies and build tools)
- find a .deb package (i like this, but there isn't always one available)

The program that I'm currently interested in installing is Gimp 2.8. I have version 2.6 installed and is the only version in my software centre.

What is the easiest way to keep my applications up to date?

Thanks,

---

### Post by Werne on 2013-09-16
Well, keeping the software up-to-date on old distros is tricky, you'd need to install software either from source (a pain in the rear, though I have compiled a ton of it), or get the .deb package and all required dependencies from the newer distro (like 12.10 or 13.04).

First may or may not work, it's a long tiresome process if you compile large software, and you may need some dependencies you'll have to hunt for all aroud the web.

And the second option is risky, though I find that when it comes to Debian, a mixed system can remain stable. You can either find debs online or you can add a repository from a newer Ubuntu then apt-pin the release to Precise and packages you want to upgrade (along with their dependencies) to Quantal/Raring.

A third option would be using fake pae, but I'm not sure how that would work (or will it work). Look it up on {insert_web_search_engine}.

There's also a fourth option which is long and time consuming (especially on that old thing). You can run on Linux 3.2 from Precise after update to Quantal (don't remove the old non-pae kernel, Quantal should be able to boot from it, not sure about Raring) then download and compile Linux 3.5 yourself, without pae. You can do the same for Raring (Linux 3.8) after booting into non-pae Linux 3.5, if you want Raring.



But honestly, the simplest way would be to opt for another lightweight distro that works on a non-pae kernel and has newer software.

If you want LXDE, you can get Debian Wheezy LXDE which has both a i486 (non-pae) and i686-pae kernels on a 32-bit image (don't know if software is newer, I know GIMP is version 2.8.2 and Abiword is 2.9.2 on stable). Ubuntu was forked from Debian so they are similar, and there will likely be a non-pae kernel in Jessie as well (there's a linux-image-3.10.2-486 package in testing repo). Software gets old after a while though, I just pin the testing repo with packages I want and Debian Mozilla Team repo for Iceweasel. Using testing is also an option.

Debian is the only one I used on machines that old but I'm sure there's plenty more distributions that support non-pae CPUs. *buntu is not one of them any more though, i486 support was dropped in 12.10 and beyond, not sure why though.

---

### Post by sudodus on 2013-09-16
You can try the easy way with [Lubuntu-fake-PAE]("https://help.ubuntu.com/community/Lubuntu-fake-PAE") or the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971")

Lubuntu-fake-PAE 'grub-n-iso' is a general method, that boots the standard Lubuntu iso file from grub, and it is the method to use, if you want dual boot (for example with Windows). Otherwise, for single boot, the OBI offers an easy and fast method for several systems suitable for ageing computers (including Pentium M and Celeron M CPUs).

---

### Post by holycow131415 on 2013-09-17
You could install ppas too

[http://www.webupd8.org/2013/06/install-gimp-286-in-ubuntu-ppa.html](http://www.webupd8.org/2013/06/install-gimp-286-in-ubuntu-ppa.html)

---

