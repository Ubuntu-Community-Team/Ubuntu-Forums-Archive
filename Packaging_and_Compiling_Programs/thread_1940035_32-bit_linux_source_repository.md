---
title: "32-bit linux source repository"
date: 2012-03-12
forum: Packaging and Compiling Programs
---

### Post by phgphd on 2012-03-12
What repository do I need to retrieve 32 bit linux includes and libs? I want to compile my software code for 32 bit x86 architecture although I have 64-bit Ubuntu laptop.

---

### Post by Bachstelze on 2012-03-13
First, cross-compiling is not trivial, and you sould only do it if you can't do otherwise. In your case, you can very well make a 32-bit VirtualBox, and it will work very well.

If you really want to cross-compile, the first thing you will need is [font=monospace]gcc-multilib[/font], which contains 32-bit versions of all the compiling toolchain. Then there are libraries. There's a lot of them in tha package [font=monospace]ia32-libs[/font], and a few libraries have separate 32-bit package (look for packages beginning with [font=monospace]lib32[/font]). In general, though, if your program uses a lot of third-party libraries, you will have to install some of them manually. It's not complicated, basically you download the 32-bit package for a library from [http://packages.ubuntu.com](http://packages.ubuntu.com), you extract it with [font=monospace]dpkg -x[/font], and you copy the library files into [font=monospace]/usr/lib32[/font]. It's still a lot of hassle, though, so really, just make a 32-bit VBox. :)

---

### Post by SevenMachines on 2012-03-14
Ubuntu comes with multiarch enabled by default these days (since oneiric?) on amd64.
You should have something like 
```
$ cat /etc/dpkg/dpkg.cfg.d/multiarch 
foreign-architecture i386
```This means that i386 libs are available in synaptic or by appending :i386 on the command line. ie
```
$ sudo apt-get install libmath++-dev:i386
```Having said that I'd go with [Bachstelze]("http://ubuntuforums.org/member.php?u=51114") and use virtualisation instead. For one, multiarch libs won't always be installable, some will conflict and not install. You could have a chroot or a 32 bit toolchain but its just more work than is needed I'd say. 
Simplest method, install virtualbox or virt-manager, virtualbox is probably the best desktop choice. Then install a i386 ubuntu and build in there. You get an easily maintained 32 bit system with one click :)

---

### Post by phgphd on 2012-03-25
Thank you. I will take your advice and the virtualbox route.

---

