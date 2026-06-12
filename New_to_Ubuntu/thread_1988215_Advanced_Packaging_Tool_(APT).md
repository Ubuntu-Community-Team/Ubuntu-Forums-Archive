---
title: "Advanced Packaging Tool (APT)"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by Shadius on 2012-05-27
Hey everybody :) 

I'm in search of some knowledge. I was confused about what ***apt-get*** is and what APT is in general, so I started reading about what I now know is the Advanced Packaging Tool (APT) from [here.]("https://help.ubuntu.com/community/AptGet/Howto#Package_management_with_APT") I need some clarification on two particular commands. 

The first:
```
sudo apt-get autoclean
```
> This command removes .deb files for packages that are no longer installed on your system. Depending on your installation habits, removing these files from /var/cache/apt/archives may regain a significant amount of diskspace.

This command can **only** be used for .deb files? If packages are no longer installed on my system, I'm assuming that some files are left over from the once installed packages and this removes those files, thus freeing up disk space? So why are these remnants of once installed packages left behind? Shouldn't the Update Manager be removing them when it's performing an update? 

The second:
```
sudo apt-get clean
```
> The same as above, except it removes all packages from the package cache. This may not be desirable if you have a slow internet connection, since it will cause you to redownload any packages you need to install a program.

The package cache is in /var/cache/apt/archives . The command

du -sh /var/cache/apt/archives
will tell you how much space cached packages are consuming.

Is removing all packages safe? So far, I only know of .deb and .rpm packages. What others are there? Also, isn't a package a program, so if you remove a package you remove a program? 

I am getting a bit confused here. Information overload, maybe? :lolflag: Please assist me in gaining a better understanding of APT.

---

### Post by MG&amp;TL on 2012-05-27
Okay, let's break things down a bit...

-First of all, you almost never get .deb and .rpm (APT and Yum respectively) packages on the same system-they would write over each other, and bad things would happen.

-Software source code is built on a server into a binary, then packaged into a packaging format such as .deb or .rpm. The binary contains the actual software product, the .deb contains information about the product, such as which files it provides, what to do before and after installation, what to do to remove it, what it needs to work properly, as well as the binary itself.

-"This command can **only** be used for .deb files?"-yes, APT is a frontend to dpkg, which deals with .deb files. If you run this command:

```
ls /var/cache/apt/archives/
```you should be able to see a lot of files to do with the packages you have installed.

-"I'm assuming that some files are left over from the once installed  packages and this removes those files, thus freeing up disk space? So  why are these remnants of once installed packages left behind?" What APT does is download the .deb file from one of the sources listed in /etc/apt/sources.list, then uses dpkg to install it. So if you remove a package from your system, the .deb file is left behind, wherever APT left it. All 

```
apt-get autoclean
```does is remove those .debs for which the package are not longer installed.

-"Shouldn't the Update Manager be removing them when it's performing an update? "-why would it? If, for instance, you remove package xyz, then decide you need it again, it's much faster to install it, as APT doesn't have to download it, just check it's still the newest version. 

-Some files from the package are left behind after you remove a package. These are configuration files-this is handy for things with big configuration files-particularly server packages. If, for whatever reason, you have to reinstall package abc, you still want your configuration files there to save you doing them again. If you do want to remove configuration files for a package when you remove it, use:

```
sudo apt-get remove --purge <package>
```-```
sudo apt-get clean
``` wipes out all of the pre-downloaded .deb files-it doesn't wipe out your system. ;) The packages remain. :)

-A few other ones:

```
sudo apt-get autoremove
```removes abc, def, and ghi that were required by xyz,  but are no longer needed as xyz has been removed.

Hope that helped a bit.

@everyone-correct me if I made a mistake...still learning.

---

### Post by roelforg on 2012-05-27
> **MG&TL said:**
> Okay, let's break things down a bit...

-First of all, you almost never get .deb and .rpm (APT and Yum respectively) packages on the same system-they would write over each other, and bad things would happen.

-Software source code is built on a server into a binary, then packaged into a packaging format such as .deb or .rpm. The binary contains the actual software product, the .deb contains information about the product, such as which files it provides, what to do before and after installation, what to do to remove it, what it needs to work properly, as well as the binary itself.

-"This command can **only** be used for .deb files?"-yes, APT is a frontend to dpkg, which deals with .deb files. If you run this command:

```
ls /var/cache/apt/archives/
```you should be able to see a lot of files to do with the packages you have installed.

-"I'm assuming that some files are left over from the once installed  packages and this removes those files, thus freeing up disk space? So  why are these remnants of once installed packages left behind?" What APT does is download the .deb file from one of the sources listed in /etc/apt/sources.list, then uses dpkg to install it. So if you remove a package from your system, the .deb file is left behind, wherever APT left it. All 

```
apt-get autoclean
```does is remove those .debs for which the package are not longer installed.

-"Shouldn't the Update Manager be removing them when it's performing an update? "-why would it? If, for instance, you remove package xyz, then decide you need it again, it's much faster to install it, as APT doesn't have to download it, just check it's still the newest version. 

-Some files from the package are left behind after you remove a package. These are configuration files-this is handy for things with big configuration files-particularly server packages. If, for whatever reason, you have to reinstall package abc, you still want your configuration files there to save you doing them again. If you do want to remove configuration files for a package when you remove it, use:

```
sudo apt-get remove --purge <package>
```-```
sudo apt-get clean
``` wipes out all of the pre-downloaded .deb files-it doesn't wipe out your system. ;) The packages remain. :)

-A few other ones:

```
sudo apt-get autoremove
```removes abc, def, and ghi that were required by xyz,  but are no longer needed as xyz has been removed.

Hope that helped a bit.

@everyone-correct me if I made a mistake...still learning.

Don't worry, you've got it correct.
Just remember that apt and yum aren't the only package managers that use deb and rpm respectivly.

---

### Post by vasa1 on 2012-05-27
> **MG&TL said:**
> ...
-Some files from the package are left behind after you remove a package. These are configuration files-this is handy for things with big configuration files-particularly server packages. If, for whatever reason, you have to reinstall package abc, you still want your configuration files there to save you doing them again. If you do want to remove configuration files for a package when you remove it, use:

```
sudo apt-get remove --purge <package>
```...

@everyone-correct me if I made a mistake...still learning.

Just one point: **purge** doesn't remove the config files in one's home folder. We have to remove these ourselves (if we want to).

---

### Post by MG&amp;TL on 2012-05-27
> **vasa1 said:**
> Just one point: **purge** doesn't remove the config files in one's home folder. We have to remove these ourselves (if we want to).

Oh yeah, files that programs create themselves stick around. Unfortunately. :(

---

### Post by oldos2er on 2012-05-27
**apt-get clean** and **apt-get autoclean** only operate on files in APT's cache,  /var/cache/apt/archives/
They don't touch any other files or installed software. You might be thinking of **apt-get autoremove** which "...is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now no longer needed."

---

### Post by vasa1 on 2012-05-27
> **MG&TL said:**
> Oh yeah, files that programs create themselves stick around. Unfortunately. :( and depending on the circumstances, it may be necessary to get rid of these files if one wants to make a totally fresh install. For example, one may install and uninstall Firefox several times over but if stuff is left around in ~/.mozilla, problems with a corrupt profile *may* nullify the effort of a re-install. (IIRC, at the time of uninstalling Firefox in MS Windows, users are asked if they wish to retain their profile. I'm not sure whether the same applies for Ubuntu. I've had no need to uninstall Firefox from Ubuntu and so I can't comment.)

---

### Post by Shadius on 2012-06-17
Thank you everyone for helping me understand this. :)

---

