---
title: "what exactly is a distribution?"
date: 2008-04-28
forum: Programming Talk
---

### Post by pbpersson on 2008-04-28
I am a little confused as to what a distribution really is.

Previously I thought the "certified" kernel was released by Linus Torvalds

Then the KDE, Gnome, and other package creators would develop a new version of their programs to work with that kernel

Each distribution would then get the source code and create packages for their distribution with perhaps a slightly different layout or different colors

I thought a "distribution" was the choice of packages and artwork that were all brought together - sort of like your cable company decides which 100 channels they want to provide to you out of the hundreds out there in the satellite world.

However, I just read that Ubuntu has kernel developers and there are different kernel versions for Ubuntu so now I am confused.

Can someone explain to me what makes Ubuntu different from SUSE and Mandriva?  I thought if the kernel version and the KDE version was the same between distributions that they were almost the same version of Linux!  

When the Ubuntu developers are going to create a new distribution, they get a kernel from Linus.....and then how much do they change?

---

### Post by LaRoza on 2008-04-28
A distribution is just a usable collection of software. It is mostly used with Linux distros, but not all distributions use Linux (some use Hurd, FreeBSD, etc)

Anyone can compile a custom kernel. There are too many single options to really enumerate.

The biggest differences I suppose are the package management methods.

---

### Post by CptPicard on 2008-04-28
You're correct. A distribution is just a packaging of software. Nothing stops distribution authors from making their own customizations to, say, the kernel or KDE or GNOME if they feel like they need them... it's perfectly acceptable and sometimes necessary to make the whole thing work nicely together. What Linus provides for example is just the plain vanilla kernel... you really need to hack it up a little sometimes when creating your own system.

---

### Post by pmasiar on 2008-04-28
@OP: You are correct. Only it is little more complicated than just select packages and artwork. :-)

Developers also develop custom utilities, select drivers, select defaults suitable for usage patterns (and recompile kernel accordingly), merge bugfixes to packages and kernel not accepted by upstream yet, and many more things only 'Masters of Universe' know about.

---

### Post by LaRoza on 2008-04-28
> **pmasiar said:**
> @OP: You are correct. Only it is little more complicated than just select packages and artwork. :-)

Developers also develop custom utilities, select drivers, select defaults suitable for usage patterns (and recompile kernel accordingly), merge bugfixes to packages and kernel not accepted by upstream yet, and many more things only 'Masters of Universe' know about.

Master of the Universe they are called (only mentioned because they go by "MOTU")

---

