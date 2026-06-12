---
title: "Why's ubuntu so bulky?"
date: 2011-09-07
forum: Recurring Discussions
---

### Post by Zeta-K on 2011-09-07
I've been running an identical hardware setup with Gentoo and Ubuntu and both are functionally about the same(same programs, uses Gnome, same hardware support) except Gentoo boots in under half the time (22 secs vs 50 secs) and when I allow each to finish loading Gnome and open gnome-system-monitor, Gentoo uses roughly 90 MB of RAM while Ubuntu uses almost 350 MB of RAM! Why does Ubuntu use so much more RAM?

---

### Post by BeRoot ReBoot on 2011-09-07
With gentoo, you have to adjust boot and loading times for all the time you spent waiting for your stuff to compile. Take that into account, and you'll find Ubuntu is actually much faster.

):P

---

### Post by CharlesA on 2011-09-07
Wow.. I was just about to say that if you want a super slick distro to use Gentoo...

Or Debian, or just install a core DE and add only what you want.

Is 350MB of RAM really that much?

---

### Post by Zeta-K on 2011-09-07
> **BeRoot ReBoot said:**
> With gentoo, you have to adjust boot and loading times for all the time you spent waiting for your stuff to compile. Take that into account, and you'll find Ubuntu is actually much faster.

):P

True, but I just ran genkernel so I would have maximum hardware support and let it compile while I was sleeping.

---

### Post by Paddy Landau on 2011-09-07
In Ubuntu, the reported RAM includes transient file caching. Therefore, you can't compare the two.

---

### Post by CharlesA on 2011-09-07
> **Paddy Landau said:**
> In Ubuntu, the reported RAM includes transient file caching. Therefore, you can't compare the two.

Right. :)

```
free -m
``` will tell you how much "real" memory you are using.

---

### Post by Zeta-K on 2011-09-07
> **Paddy Landau said:**
> In Ubuntu, the reported RAM includes transient file caching. Therefore, you can't compare the two.
And system monitor on other systems doesn't?

---

### Post by CharlesA on 2011-09-07
System monitor has overhead. Run the command from my previous post to find the amount of memory being used.

---

### Post by KiwiNZ on 2011-09-07
It doesn't look too bulky to me :P

---

