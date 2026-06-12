---
title: "OpenSolaris?  This isn't a Linux OS correct??"
date: 2007-03-05
forum: Other OS Talk
---

### Post by billdotson on 2007-03-05
From what I understand OpenSolaris is an operating system from Sun Microsystems and does not run on the Linux kernel.  It runs on it's own OpenSolaris kernel.  

So what exactly is OpenSolaris and what is it good at doing?  Is it free? Would it be worth putting on a partition of my harddrive?

Thanks.

---

### Post by mips on 2007-03-05
It's Unix. It's good for servers and the like. Desktop is a bit harder but many Java developers like it as everything they need is there and it works. It's hardware support needs some work.

It's free and you can try it out if you want.

I'm still waiting for my free solaris 10 DVD set, must go check the mail....
[http://ubuntuforums.org/showthread.php?t=338674](http://ubuntuforums.org/showthread.php?t=338674)

---

### Post by floke on 2007-03-05
Been waiting for mine for ages. Not anticipating anything though. And DesktopBSD didn't work with my wireless, so don't envision any joys with Solaris either.

---

### Post by mzilhao on 2007-03-05
haven't seen this mentioned yet...

[http://get.opensolaris.org/](http://get.opensolaris.org/)
> 
Get the OpenSolaris Starter Kit!

It's free! Inside you'll find tutorials, documentation, and two DVDs filled with useful software. Get started using OpenSolaris technology — right on your laptop or home PC.

This kit will help you learn about the OpenSolaris source code and the community. On the DVDs, you'll find:

    * Solaris Express — Preview future features of Sun's Solaris Operating System. Also inside: ZFS, DTrace, Containers, and hundreds of other unique features.
    * Live CDs — These bootable images allow you to check out community-built distributions of OpenSolaris, each with unique features:

      - Nexenta OS
      - BeleniX
      - SchilliX
    * Sun Studio compilers — Get advanced features for developing applications on Sun Solaris platforms.
    * OpenSolaris source code.
    * System Requirments — x86/x64 based system.


apparently, it's just like ShipIt, completely free of charge!
i've never tried OpenSolaris, so i've ordered mine! :)

---

### Post by ammunition on 2007-03-05
I ordered for months ago, haven't arrived yet. =(

---

### Post by igknighted on 2007-03-05
Actually I think this is different than Sun's Solaris 10 "ship-it clone" that everyone did a few months back.  This ships you live CDs of opensolaris distro's (I've tried Belenix before, its OK.  I think Nexenta is Debian based but modified for the opensolaris kernel... I've always meant to try that) instead of Sun's Solaris 10.  I'll have to check this out.

---

### Post by floke on 2007-03-05
Yeah, it's great.
They take your order, process it, put all the discs on a ship, sail off, chuck them overboard and then come back.

At least that would explain why mine haven't arrived anyway.

---

### Post by billdotson on 2007-03-05
so pretty much Solaris isn't that great..

---

### Post by szf on 2007-03-05
OpenSolaris is the open source core of Sun Microsystems Solaris, a UNIX operating system. For a measure of tinker-time and some hard disk space, you can [try it out]("http://get.opensolaris.org/") on bootable DVD for free [as in beer].

Solaris has some features that you won't find in Linux - examples include the ZFS filesystem and dtrace,  the Solaris Dynamic Tracing Framework.

---

### Post by MattSMiddleton on 2007-03-05
I just received Solaris 10 from Sun and was considering giving it a try, but I first wanted to know if anyone here has had any experience with Solaris and what that experience was like.

---

### Post by igknighted on 2007-03-05
> **MattSMiddleton said:**
> I just received Solaris 10 from Sun and was considering giving it a try, but I first wanted to know if anyone here has had any experience with Solaris and what that experience was like.

It's pleasant.  There are no ATI proprietary drivers at all, though there are Nvidia drivers.  It uses KDE as default, although you might be able to install gnome, not sure.  I like it overall, just not anywhere near as common as linux (imagine the problems linux has cause its not popular, just multiplied).  I would say give it a shot and see how you like it as long as you have the HD space to spare.  If you do any work with java you will love it because all the java tools are installed by default.

---

### Post by 3rdalbum on 2007-03-06
> **igknighted said:**
> It's pleasant.  There are no ATI proprietary drivers at all

Sounds like a super-stable operating system then!

> If you do any work with java you will love it because all the java tools are installed by default.

It has Java installed by default? Okay, I take back the above comment :-(

---

### Post by hans-jakob on 2007-03-06
If you want to try the OpenSolaris kernel, why not download [Nexenta]("http://www.gnusolaris.org/gswiki").

This is a Debian/Ubuntu Desktop OS based on OpenSolaris. It is still in Alpha, but it allready has over 12.000 packages in its repository.

---

### Post by billdotson on 2007-03-06
so technically the OpenSolaris kernel is a pretty technically sound kernel to base an OS on?
What would the OpenSolaris kernel do better than the Linux kernel if say Ubuntu were run on top of it?

Btw in your opinion, or if you know for a fact technically speaking what is the best kernel out there?  I have heard of the Haiku OS microkernel, and then there is the NT kernel that XP and Vista sort of run on, and the darwin kernel for OS X, and the Linux kernel for Linux OSes.

Also, I don't entirely understand how the OpenSolaris kernel is Unix.. wouldn't the OpenSolaris kernel be deemed OpenSolaris or is Unix just a standard for how operating systems are run  :? ?

The ZFS filesystem looks pretty sweet.  So there isn't anyway to get a ZFS partition to put my Ubuntu files on or something?

---

### Post by igknighted on 2007-03-06
> **billdotson said:**
> so technically the OpenSolaris kernel is a pretty technically sound kernel to base an OS on?
What would the OpenSolaris kernel do better than the Linux kernel if say Ubuntu were run on top of it?

Btw in your opinion, or if you know for a fact technically speaking what is the best kernel out there?  I have heard of the Haiku OS microkernel, and then there is the NT kernel that XP and Vista sort of run on, and the darwin kernel for OS X, and the Linux kernel for Linux OSes.

Also, I don't entirely understand how the OpenSolaris kernel is Unix.. wouldn't the OpenSolaris kernel be deemed OpenSolaris or is Unix just a standard for how operating systems are run  :? ?

The ZFS filesystem looks pretty sweet.  So there isn't anyway to get a ZFS partition to put my Ubuntu files on or something?

Solaris is considered by some to be technically superior to the linux kernel.  However, as a desktop OS it lacks the support necessary to challenge linux as the primary "windows alternative".  I have heard that it deals with hardware/system resources more efficiently than than linux does, but this is heresay, I don't have any proof to back that up.

As for the best kernel, well, like the best OS it is impossible to say.  Solaris some say is more efficient than linux, both of which we can agree are more efficient than Windows kernels.  However, solaris and linux lack some of the desktop capabilities, and adding them to the kernel to get to the same level of hardware support of windows (drivers, modules, etc.) might introduce more problems.  Therefor, the best kernel is the one that suits your needs best (IMHO), whatever they may be.

Unix is a general class of operating systems.  It mostly stems from the hierarchical file structure employed, and the general design of the kernel (all are somewhat similar). For instance, BSD, Linux, Solaris and MacOSX (along with many others) are all "unix" and thereby related.

There might be a kernel hack to add support for ZFS, I would just stick to the linux file structures.

> It has Java installed by default? Okay, I take back the above comment 

What do you have against java?  Java is a great programming language and multi-platform too.  Now that it has gone open-source I would imagine many more OSS projects in java, which could lead to cross-platform compatibility.  Imagine windows users being able to make the switch with losing any of their favorite apps... makes linux far more enticing.

---

### Post by SlCKB0Y on 2007-03-11
> **3rdalbum said:**
> Sounds like a super-stable operating system then!



It has Java installed by default? Okay, I take back the above comment :-(

How is java unstable?

---

### Post by Ateo on 2007-05-15
> **Steve.K said:**
> Been waiting for mine for ages. Not anticipating anything though. And DesktopBSD didn't work with my wireless, so don't envision any joys with Solaris either.

I got mine in under a week. Must be because I had it sent to my business.

---

### Post by dca on 2007-05-16
Mine took about two weeks.  Three DVDs.  One, the Solaris 10 OS for x86 & x64, one for Developer Tools, and one DVD for Solaris 10 OS Sparc...

---

### Post by dca on 2007-05-16
...I've been afraid to install it to test on my laptop because of the lack of drivers.  If you go to Sun's website using their 'HCL' for any particular laptop it links you to where to get driver(s) for say Broadcom NICs but the website is defunct...
 
Now this is not endorsed but I believe Bank Of America uses it as their primary platform.  All their webservers run on Solaris and if you go to their branch offices, some of the clients have a 'Sun' logo when they're connecting to something.  I don't know, caught it out the side of my eye while signing for my second mortgage and was afraid to lean over and say 'Hey, is that Solaris?'

---

### Post by 3rdalbum on 2007-05-16
> **igknighted said:**
> 
What do you have against java?  Java is a great programming language and multi-platform too. 

Ouch... having written in Python for anumber of years, I had a great deal of trouble learning Java - it's so long-winded to write anything in.

My comment was actually about stability. On my old computer, the Java runtime environment ran very slowly and often made the machine crash during or after running a Java application. I also noticed that Java programs often had problems when running on even slightly different machines, like different versions of Windows or point releases of the JRE.

Things might have changed now, but I got such a bad impression from Java that, to this day, I absolutely refuse to install Sun Java on my Ubuntu machine, and I'm not even too happy with the GNU Java being on my computer (dependency of OOo).

---

