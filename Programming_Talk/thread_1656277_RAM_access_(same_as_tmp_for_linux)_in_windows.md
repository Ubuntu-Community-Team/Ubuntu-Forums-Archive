---
title: "RAM access (same as /tmp/ for linux) in windows?"
date: 2010-12-30
forum: Programming Talk
---

### Post by giuspen on 2010-12-30
Hi,
does anybody know if there's a location in windows operative systems where the RAM is mounted so that I can write data and be sure that at next pc reboot that data will not be there anymore?
Thanks in advance.

---

### Post by NathanB on 2010-12-31
Yeah, it is called a "RAM disk" and use to be popular back in the DOS days.  Microsoft has a "sample" driver as a free download here:  [http://support.microsoft.com/kb/257405](http://support.microsoft.com/kb/257405)

But you can do a little Googling around for "RAM disk" or "RAM drive" if that one doesn't fit your needs.  If you're running 32-bit Windows XP, you could even use the old DOS-based ones if you happen to bump into one (which is likely).

---

### Post by endotherm on 2010-12-31
not much that you can use with filesystem-like semantics. a ram disk may do just what you need as Nathan has suggested, but there isn't a file system location that is already built into windows systems.

---

### Post by giuspen on 2010-12-31
> **endotherm said:**
> there isn't a file system location that is already built into windows systems

a file system location already built in is what I was looking for, being that not possible I will use a temporary folder and then delete it. thanks.

---

