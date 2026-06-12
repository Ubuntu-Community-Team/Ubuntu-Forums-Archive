---
title: "Australian daylight saving has changed, need update"
date: 2006-02-01
forum: Repositories &amp; Backports
---

### Post by nick4mony on 2006-02-01
The daylight end-date in some parts of Australia has changed from Sun Mar 26, to Sun Apr 2, for this year only (2006).  We need some new timezone files that reflect this change.

The daylight saving has changed to suit the Commonwealth games in Melbourne, Australia (someone needs to check Sydney, Hobart, Canberra, Broken_Hill, Adelaide, Lord_Howe, and various aliases, because the various government departments involved may decide to all do the same thing).

According to [http://www.information.vic.gov.au/resources/daylight.htm](http://www.information.vic.gov.au/resources/daylight.htm) the daylight saving is to end on 2 April.  However, when I use zdump, it tells me March 26
```

nick@pc0218:~$ zdump -v -c 2006,2007 Australia/Melbourne
Australia/Melbourne  Fri Dec 13 20:45:52 1901 UTC = Sat Dec 14 06:45:52 1901 EST isdst=0 gmtoff=36000
Australia/Melbourne  Sat Dec 14 20:45:52 1901 UTC = Sun Dec 15 06:45:52 1901 EST isdst=0 gmtoff=36000
Australia/Melbourne  Sat Mar 25 15:59:59 2006 UTC = Sun Mar 26 02:59:59 2006 EST isdst=1 gmtoff=39600
Australia/Melbourne  Sat Mar 25 16:00:00 2006 UTC = Sun Mar 26 02:00:00 2006 EST isdst=0 gmtoff=36000
Australia/Melbourne  Sat Oct 28 15:59:59 2006 UTC = Sun Oct 29 01:59:59 2006 EST isdst=0 gmtoff=36000
Australia/Melbourne  Sat Oct 28 16:00:00 2006 UTC = Sun Oct 29 03:00:00 2006 EST isdst=1 gmtoff=39600
Australia/Melbourne  Mon Jan 18 03:14:07 2038 UTC = Mon Jan 18 14:14:07 2038 EST isdst=1 gmtoff=39600
Australia/Melbourne  Tue Jan 19 03:14:07 2038 UTC = Tue Jan 19 14:14:07 2038 EST isdst=1 gmtoff=39600

```

When can we expect an update?

**Update**Note I am on a machine running **Breezy**, not my usual Warthog machine.

---

### Post by bikeboy on 2006-02-08
Same problem Nick. Apparently a lot of distros have updated info but it isn't that way for me. 

[http://forums.whirlpool.net.au/forum-replies.cfm?t=471404#r2](http://forums.whirlpool.net.au/forum-replies.cfm?t=471404#r2)

Hopefully we can bump it to somebody important's attention. Wouldn't know where else to go to tell devs.

---

### Post by nocturn on 2006-02-08
If there isn't one already, file a bugreport on this to get the attention of a dev.

---

### Post by bikeboy on 2006-02-08
It seems there is a bug filed already. In the report this link was given which shows how to manually update the zoneinfo.

[http://www.linuxsa.org.au/pipermail/linuxsa/2006-February/082329.html](http://www.linuxsa.org.au/pipermail/linuxsa/2006-February/082329.html)

---

### Post by ewe2 on 2006-02-28
Even Microsoft was quicker with a patch. This is inexusable.

---

### Post by ewe2 on 2006-02-28
If you want to compile the fix yourself, go to [ftp://elsie.nci.nih.gov/pub/](ftp://elsie.nci.nih.gov/pub/) and grab tzdata2006b.tar.gz, which holds the timezone source. Don't forget to back up!

---

