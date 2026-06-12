---
title: "Crux for Pentium 4"
date: 2008-03-05
forum: Other OS Talk
---

### Post by chimerical_brio on 2008-03-05
So from what I've been able to figure out, Crux and Arch are both pretty much i686 distros. Anyone know of any distros similar to Crux in the philosophy of barebones, but which will run on i386 (Pentium 4)? How well would FreeBSD line up with that notion?

---

### Post by fwojciec on 2008-03-05
Pentium 4 is i686 (basically everything above pentium 2 is).

---

### Post by K.Mandla on 2008-03-06
Ah, Pentium Pro and up is i686. 

[http://en.wikipedia.org/wiki/I686](http://en.wikipedia.org/wiki/I686)

If you can boot the Crux CD, you can compile the kernel to run on whatever architecture and build all your packages from there. That's what I do.

---

### Post by chimerical_brio on 2008-03-06
Correct me if I'm wrong (I really don't know anything about this sort of thing), but I'm pretty sure Pentium 4 is i386. But I'll try Crux and see if it works on my P4 anyway.

---

### Post by chimerical_brio on 2008-03-06
Correct me if I'm wrong (I really don't know anything about this sort of thing), but I'm pretty sure Pentium 4 is i386. But I'll try Crux and see if it works on my P4 anyway.

---

### Post by djbsteart1 on 2008-03-06
> **chimerical_brio said:**
> Correct me if I'm wrong (I really don't know anything about this sort of thing), but I'm pretty sure Pentium 4 is i386. But I'll try Crux and see if it works on my P4 anyway.

The p4 is i686, I have Arch on a p3 fine so your p4 shouldn't be a problem.

---

### Post by fwojciec on 2008-03-06
> **chimerical_brio said:**
> Correct me if I'm wrong (I really don't know anything about this sort of thing), but I'm pretty sure Pentium 4 is i386. But I'll try Crux and see if it works on my P4 anyway.

I have Arch (i686 optimized as well) installed on a P4 machine.

---

### Post by mozetti on 2008-03-06
Technically P4 is i386, but that's because i386 applies to x86 starting at i386 and going forward. A P4 is i686, with i686 being a subset within i386.

---

### Post by kpkeerthi on 2008-03-07
I have Arch running on Pentium 4 desktop.

---

### Post by SunnyRabbiera on 2008-03-07
Another P4 optimized distro question?
seems redundant as I have used ubuntu on my P4 for ages and have no issues with it except for a few that have no relation to the processor.

---

### Post by mozetti on 2008-03-07
> **SunnyRabbiera said:**
> Another P4 optimized distro question?
seems redundant as I have used ubuntu on my P4 for ages and have no issues with it except for a few that have no relation to the processor.

Agree. But if it is really that much of an issue for you, just install Ubuntu and re-compile your kernel to be optimized for i686.

---

### Post by SunnyRabbiera on 2008-03-07
> **mozetti said:**
> Agree. But if it is really that much of an issue for you, just install Ubuntu and re-compile your kernel to be optimized for i686.

actually my issues have no relation to the processor, just the buggy structure of gutsy that gets my goat here.
I am sort of anticipating hardy and hope its as stable as they say it will be.

---

