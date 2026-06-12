---
title: "FAT32 timestamps"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by dondos on 2008-10-28
Hello everybody,

when I mount a FAT32 partition, some files appear to have wrong timestamps. Specifically, all files modified during the summer months, appear having their timestamps modified by +1 hour. A few weeks ago (when Daylight Savings was in effect) those files had correct timestamps!

When observing the same files under Win2000 or Win98, timestamps always appear ok.

So, my question is why Linux "translates" the timestamps, depending on whether DST is in effect or not? Is this by design or is it a bug?

Looks like a bug to me. I think that Linux should respect the timestamps of the FAT32 partition. FAT32 stores timestamps according to the local time, not UTC, so there should be no need for conversion.

Thanks in advance,
Yiannis.

---

### Post by dondos on 2009-09-18
I still believe that this is a problem that can be rectified, so I reported it as a bug in Launchpad [(Bug #612292)]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612292")

---

