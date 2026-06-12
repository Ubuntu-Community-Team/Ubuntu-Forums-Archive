---
title: "Accessing BIOS through programmin"
date: 2011-02-01
forum: Programming Talk
---

### Post by mecrazycoder on 2011-02-01
Hi,
  Is it possible to access BIOS through programming? For example I want to change the boot priority like higher priority to external device etc through programming.

---

### Post by Martin Witte on 2011-02-01
This is impossible as far as I know.

---

### Post by worksofcraft on 2011-02-01
> **mecrazycoder said:**
> Hi,
  Is it possible to access BIOS through programming? For example I want to change the boot priority like higher priority to external device etc through programming.

I think the boot priority is one of the settings in what is called the PC CMOS setup. CMOS refers to a semiconductor technologogy that uses so little electricity that it can run off a tiny battery for years. Thus it is a way to retain configuration settings while power was switched off although these days there are many better ways like flash memory for doing that.

You would have to Google about the standard CMOS settings and it may not be very standard across different brands of computers. To gain access to memory at specific hardware address you will also have to program at kernel level, so it won't be an easy thing to do and it is not something I have ever tried.

---

### Post by mecrazycoder on 2011-02-01
thank you all for ur kind reply

---

