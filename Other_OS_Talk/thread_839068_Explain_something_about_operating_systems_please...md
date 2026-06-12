---
title: "Explain something about operating systems please.."
date: 2008-06-24
forum: Other OS Talk
---

### Post by Fzang on 2008-06-24
Wikipedia either makes it hard to understand or not information enough..

I have a couple of questions..

1) What is the difference between an Unix-system and an "Unix-like-system"?

2) What classifies an OS as "linux"? There's 100s of distros, all boiled down to being "linux" instead of 100 different systems, and they all use linux software

3) What's the difference between OS X and other Unix-systems? OS X has it's own category and software, but I believe Solaris is unix as well, yet it's a linux?

---

### Post by cammin on 2008-06-24
I don't know how to put any of it in a better way than Wikipedia has, but this might help.

Unix is a trademarked name of an operating system.
The people who own the trademark will let other people use the UNIX name if they pay to have their OS certified for the Single UNIX specification. Basically it has to comply with a set of standards so that it can be used interchangeably with other operating systems that use the UNIX name.

Unix-like is an operating system that is either based on Unix, used to be based on unix (BSD got rid of any UNIX code) or as in the case of Linux, written from scratch, but designed to function like Unix.

Linux distros are all based on the Linux kernel. Usually they are just different combinations of default programs, but sometimes people make modifications to the kernel itself, as well as write their own programs specifically for their distro.

OSX was based on BSD, But Apple made so many changes to it, that it's not compatable with it. Apple had OSX, Single UNIX standards certified, so they can use the UNIX name.

Solaris used to be proprietary version of Unix. It gets to use the UNIX trademark since it's standards compliant.
They released an open source version called OpenSolaris. The founder of Debian Linux is involved with that.

---

### Post by saulgoode on 2008-06-24
> **Fzang said:**
> 1) What is the difference between an Unix-system and an "Unix-like-system"?
Unix is a brand, similar to "Frisbee" or "Kleenex"; though there are a lot of "flying disks" or "facial tissues", only the official ones certified by the owner of the brand get to call themselves by the official name.

> **Fzang said:**
> 2) What classifies an OS as "linux"? There's 100s of distros, all boiled down to being "linux" instead of 100 different systems, and they all use linux software

Technically, the OS is not "Linux"; Linux is only part of the operating system (specifically, the "kernel"). Linux handles most of the interfacing between programs and your computer's hardware. Rather than an application having to handle every device available, it only has to be able to interface with Linux.

> **Fzang said:**
> 3) What's the difference between OS X and other Unix-systems? OS X has it's own category and software, but I believe Solaris is unix as well, yet it's a linux?

Neither Solaris and OS X are Linux. They are derived from the original Unix and both have been certified as being [Official Unix](http://www.opengroup.org/openbrand/register/). It should be noted that sometimes the difference between being "Unix" and not being Unix is more a matter of paying the registration fee -- for example, BSD (upon which OS X is based) could probably qualify for official Unix status if they paid the cost of certification.

---

### Post by timcredible on 2008-06-24
> **Fzang said:**
> Wikipedia either makes it hard to understand or not information enough..

I have a couple of questions..

1) What is the difference between an Unix-system and an "Unix-like-system"?
not much

> 2) What classifies an OS as "linux"? There's 100s of distros, all boiled down to being "linux" instead of 100 different systems, and they all use linux software
all the distributions you're probably looking at are linux because they use the same linux kernel, they just put together different applications onto a CD.

> 3) What's the difference between OS X and other Unix-systems?
Apple went out of their way to make sure it's difficult to run unix/linux applications on OS X.  But if you see OS X, you'll notice it's basically bsd (or linux) with the gnome window manager and cairo-dock (or AWN).  

>  OS X has it's own category and software, but I believe Solaris is unix as well, yet it's a linux?
Solaris is Sun's version of unix.  HP/UX is HP's version of unix. They're not linux because they don't use the linux kernel. They're more incompatible than different linux distros though, because each one has  different kernels.  but if you worked on them, you'd use the same commands, same file structure, etc.

---

### Post by dca on 2008-06-24
POSIX-compliant OS' = Unix, Linux, BSD
 
non-POSIX = Windows
 
 
...maybe this helps...
 
[http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

---

