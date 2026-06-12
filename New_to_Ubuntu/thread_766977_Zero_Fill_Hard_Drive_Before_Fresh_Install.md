---
title: "Zero Fill Hard Drive Before Fresh Install"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Michl on 2008-04-25
My project today was to do a Zero Fill on my hard drive
and then do a fresh install of Hardy from a live CD, but
before I get going I think I need to double-check.  Measure
twice and cut once, so to speak.  Have I ignored something?

By the way, I dual boot and the drive I want zero fill is
the master.

Thank you!!
Michael

---

### Post by skroops on 2008-04-25
I don't understand the question.

You want to zero-fill and then install hardy on a dual-boot machine.  Isn't that essentially the same process as wiping and installing hardy, with a few extra steps for the zero fill?  Seems like you should just do it.

---

### Post by Michl on 2008-04-29
I don't think so.  Linux seems pretty lazy when it finds a ext3
partition.  It certainly does not wipe the disk.

In any case, I did a zero fill and then a fresh
install.  You can zero fill with linux.  Run a 
live CD and in the terminal enter:

```
dd if=/dev/zero of=/dev/hda bs=1M
```

It took about 1.5 hours for 120 GB.

---

