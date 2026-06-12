---
title: "Which is more Secure/Stable? BSD kernel or Linux kernel?"
date: 2008-06-25
forum: Other OS Talk
---

### Post by acelin on 2008-06-25
Ignore user error, DE's, pretty much everything except for the core level, If everything was the same, yet you had one of these 2 kernels, which would be more stable/secure?

---

### Post by cardinals_fan on 2008-06-25
Well, that's a tough question.  Stability will depend on your hardware and the kernel versions compared.

---

### Post by jrusso2 on 2008-06-25
Overall probably BSD is more stable since the pace of developement is much slower.  However the Linux Kernel is very stable.

---

### Post by MONODA on 2008-06-26
probably the BSD kernel since many time people use proprietary drivers which are inserted into the kernel and can bring down the whole system -> i would say BSD kernel is usually more stable. Also since it is developed slower than the Linux one. 
by the way, check out this: [http://www.minix3.org/](http://www.minix3.org/)

---

### Post by acelin on 2008-06-26
Yeah I have heard of Minix... 
I think that it wont make much of a difference when it comes down to it. It depends on everything else you are using...

---

### Post by cardinals_fan on 2008-06-26
> **acelin said:**
> 
I think that it wont make much of a difference when it comes down to it. It depends on everything else you are using...
Yes.  You need more than the kernel, and stability will depend on the level of support your hardware receives, as well as the versions of programs installed.  Most BSD distros try for very stable releases, so that shouldn't be a problem.

---

### Post by rliegh on 2008-06-27
Each of the BSD kernels is different, and I'm going to say that the most secure is **probably** the OpenBSD kernel. Simply put, they've audited their **entire** source tree for vulnerabilities (the other BSDs haven't done so -at least not quite so rigorously) and as someone else mentioned, binary-only drivers are a huge security concern and OpenBSD doesn't allow for those (in the source/binaries that they themselves ship); NetBSD and FreeBSD have both made concessions on that point.

The downside is, of course, that OpenBSD is lacking in several key areas (no WINE, no XEN, and definately no binary Nvidia drivers).

As far as I'm aware of, the Solaris kernel is a nice compromise; it has the functionality of Linux (ie it has the kind of threading capability that WINE requires -OpenBSD doesn't, Nvidia makes drivers for it, xen is shipped in recent releases) but it still has a lvel of security that can rival OpenBSD.

---

### Post by MisfitI38 on 2008-06-27
> **rliegh said:**
> Each of the BSD kernels is different, and I'm going to say that the most secure is **probably** the OpenBSD kernel. Simply put, they've audited their **entire** source tree for vulnerabilities (the other BSDs haven't done so -at least not quite so rigorously) and as someone else mentioned, binary-only drivers are a huge security concern and OpenBSD doesn't allow for those (in the source/binaries that they themselves ship); NetBSD and FreeBSD have both made concessions on that point.

The downside is, of course, that OpenBSD is lacking in several key areas (no WINE, no XEN, and definately no binary Nvidia drivers).

As far as I'm aware of, the Solaris kernel is a nice compromise; it has the functionality of Linux (ie it has the kind of threading capability that WINE requires -OpenBSD doesn't, Nvidia makes drivers for it, xen is shipped in recent releases) but it still has a lvel of security that can rival OpenBSD.

Agreed.
FreeBSD has had its ups and downs, yet OpenBSD has consistently proven its acumen. The OpenBSD kernel and userspace are developed together, in a single source repository. Everything in the operating system is provided as a whole, while remaining inherently  modular. 
GNU/Linux distributions, on the other hand, are each an amalgam; a mish-mosh of kernel, earlyspace, and userspace programs developed all over the place, packaged up, and distributed together. This invariably raises security and stability issues.
The OpenBSD design approach is more fiercely focused on stability, code-correctness and security. 
I wouldn't use OpenBSD for a desktop, but for security and stability, it is most certainly without peers.

---

### Post by Sef on 2008-06-29
> I wouldn't use OpenBSD for a desktop, but for security and stability, it is most certainly without peers.

I read about openbsd being used as a desktop os.  As for security and stability, I agree with you 100%.

---

### Post by MisfitI38 on 2008-07-01
> **Sef said:**
> I read about openbsd being used as a desktop os.  As for security and stability, I agree with you 100%.

Yes, OpenBSD can be used for a desktop system if it plays nice with your hardware. 
The linux kernel, being more rapidly developed, offers better hardware support obviously. Along with rapid development, though, comes reduced stability in comparison to the hardened, more slowly developed OpenBSD kernel. :)

---

