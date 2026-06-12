---
title: "Can I use Puppy Linux to build a Linux From Scratch install?"
date: 2009-01-13
forum: Other OS Talk
---

### Post by nerd0795 on 2009-01-13
I'm going to make my own Linux From Scratch install and the thing is you need a host linux distro.  I'm only doing this on my old computer incase I screw something up.  It's a machine that MIGHT be able to run windows XP.  I have a slow internet connection so I decided that I'm going to use Puppy Linux for the small size.  Since it will only be a temporary install.

The thing is.  Is Puppy Linux capable of being able to create the linux from scratch install?  I will HAVE TO BE ABLE to install linux packages to another partition using terminal (which I think all linux distros will support)  I'm just making sure.

---

### Post by nerd0795 on 2009-01-13
> **nerd0795 said:**
> I'm going to make my own Linux From Scratch install and the thing is you need a host linux distro.  I'm only doing this on my old computer incase I screw something up.  It's a machine that MIGHT be able to run windows XP.  I have a slow internet connection so I decided that I'm going to use Puppy Linux for the small size.  Since it will only be a temporary install.

The thing is.  Is Puppy Linux capable of being able to create the linux from scratch install?  I will HAVE TO BE ABLE to install linux packages to another partition using terminal (which I think all linux distros will support)  I'm just making sure.

OOPS :/  Never knew about their live cd, but I wanna take my time with this build, so I'm still gonna install Puppy if it works.

---

### Post by wolfen69 on 2009-01-13
the thing is, it's easy to make your own puppy. 

but the regular puppy works so well i don't worry about it. hell, how many versions of puppy are there?

---

### Post by Sorivenul on 2009-01-14
> **wolfen69 said:**
> how many versions of puppy are there?
I believe I counted 61 [listed here]("http://www.puppylinux.org/downloads/puplets") on the Puppy site, though I could have miscounted - it's late and I'm tired. Of course, that is not all of them, especially as more and more users make their own.

@OP:
I think you could use Puppy to build LFS, but make sure to install all the build tools you need (bison, flex, and so on as they should be listed in the LFS handbook). I've done LFS from Slackware and Debian-based systems, as well as the LiveCD in a virtual machine, so there are plenty of ways. Good luck!

---

### Post by smartboyathome on 2009-01-14
You need to install the devtools in puppy in order to use it. It means modifying the ISO image to include the dev image for puppy.

---

### Post by mohitchawla on 2009-01-15
You'd be really better off using the LFS live CD itself as the host environment because:

1. It includes the exact versions of the tools required. Inconsistencies can arise frequently if you have different version of GCC or binutils and such in your host system. And since you have a slow system, you wouldn't really be thinking of compiling/obtaining different versions of these tools.

2. You need to install the devx package for the version of Puppy you are4 using for the development tools (for example, for Puppy 4 you have to get the devx_400.sfs package) , which again might not have the exact versions of the tools required and compiling different versions will waste time.

3. The LFS live CD provides a lightweight environment itself, so using Puppy won't prove to be really advantageous in terms of speed.

---

### Post by smartboyathome on 2009-01-15
The LFS livecd is out of date and the SVN build is broken. :-\

---

