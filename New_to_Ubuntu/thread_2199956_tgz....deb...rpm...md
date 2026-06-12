---
title: "tgz....deb...rpm.."
date: 2014-01-16
forum: New to Ubuntu
---

### Post by skater-nin on 2014-01-16
im a window user to linux user. i download these types of files but idk what to do with it. i am double clicking it and nothing happening. just show contents.

---

### Post by buzzingrobot on 2014-01-16
They are archives, essentially.  I.e., organized collections of compiled code, source code, scripts, text files, etc. Each archive is created and unarchived with a particular set of tools. Different kinds of archive were created at different times over the history of Unix/Linux to solve different problems.

Ubuntu software is distributed in archives with the ".deb" suffix.  Typically, a stock Ubuntu installation will offer to install a ".deb" archive with the Software Center. You can right click on a ".deb" file in Files (the file manager) and it should display that it will "Open With" the Software Center.  If that does not happen, right click on a ".deb" file, move down and select "Properties", then 'Open With", and select Software Center whichh should install it.  

".deb" files are used by many distributions (they're named after the Debian distribution where the format originated).  Files intended for installation on one distribution may or may work in other distributions, including Ubuntu, and should be avoided.  That is, software needs to be specifically packaged for a particular Linux distribution, and often a particular release of that distribution, before it can be successfully installed.

In fact, avoid downloading files from random sources and trying to install them. It's safest to install from the official Ubuntu repositories.

---

### Post by llamabr on 2014-01-16
As buzzingrobot suggests -- free yourself from this mindset where, to get a new program, you must go to the web and find it, and download it, and double click on it, etc.  One of the most attractive things about ubuntu is the package manager system.  Integrated fully into ubuntu is a very easy, comprehensive system of searching for and installing software.  You can begin here:

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

and if you have any trouble, come back and ask us.  Welcome to the forum.  It's a friendly place.

---

### Post by skater-nin on 2014-01-16
> **buzzingrobot said:**
> They are archives, essentially.  I.e., organized collections of compiled code, source code, scripts, text files, etc. Each archive is created and unarchived with a particular set of tools. Different kinds of archive were created at different times over the history of Unix/Linux to solve different problems.

Ubuntu software is distributed in archives with the ".deb" suffix.  Typically, a stock Ubuntu installation will offer to install a ".deb" archive with the Software Center. You can right click on a ".deb" file in Files (the file manager) and it should display that it will "Open With" the Software Center.  If that does not happen, right click on a ".deb" file, move down and select "Properties", then 'Open With", and select Software Center whichh should install it.  

".deb" files are used by many distributions (they're named after the Debian distribution where the format originated).  Files intended for installation on one distribution may or may work in other distributions, including Ubuntu, and should be avoided.  That is, software needs to be specifically packaged for a particular Linux distribution, and often a particular release of that distribution, before it can be successfully installed.

In fact, avoid downloading files from random sources and trying to install them. It's safest to install from the official Ubuntu repositories.

dang that was easy peasy to install. thanks

---

### Post by silvervulpus on 2014-01-16
there are command lines for unpacking .tar.gz's .deb files, they arent hard to learn or remember, you just type them into terminal followed by the package name  exampleFILE.TAR.GZ or whatever
[http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file)
this page should have everything you need
also go to the ubuntu software center or use synaptic package manager, both are much easier than hand installing

---

### Post by Impavidus on 2014-01-16
Ubuntu has been designed to use .deb achives. They contain software that can be installed on Ubuntu. .rpm is used by some other Linux distros and can't be installed on Ubuntu (well, there are some hacks, but you risk breaking your system if you try them). .tgz (short for .tar.gz and commonly knows as a tarball; the abreviation tgz was designed to be compatible with systems that don't accept long filenames with double extensions, like dos) is a general archive format. It can contain anything and there are no rules for installation from tarballs.

Of course, only install software from these archives if you trust the source. They could contain malware.

---

### Post by mastablasta on 2014-01-17
> **Impavidus said:**
>  It can contain anything and there are no rules for installation from tarballs.


usually they contain source code (not always) and there is usually a readme file inside. it will give isntructions on how to install it. sometimes they need to be compiled first.

use .deb, PPA (personal package archive), or official repositories (Software centre). last one is safest and easiest to use.

---

