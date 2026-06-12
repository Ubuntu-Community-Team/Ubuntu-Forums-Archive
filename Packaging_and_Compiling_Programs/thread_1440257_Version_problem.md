---
title: "Version problem"
date: 2010-03-27
forum: Packaging and Compiling Programs
---

### Post by blscreen on 2010-03-27
Hello,

I tried to package the latest imagemagick release. It compiles fine, but when I install the packages, I get an error (same for the other imagemagick packages):

```
dpkg: dependency problems prevent configuration of libmagickcore2-extra:
 libmagickcore2-extra depends on libmagickcore2 (>= 7:6.6.0.9); however:
  Version of libmagickcore2 on system is 7:6.6.0.9-0~ppa1.
```

This is strange because 7:6.6.0.9-0~ppa1 is a higher version compared to 7:6.6.0.9, or is it not?

What am I doing wrong here?

Best Regards.

---

### Post by SevenMachines on 2010-03-28
hi there,  7:6.6.0.9-0~ppa1 is considered a lesser version than 7:6.6.0.9. for versioning rules see[ ubuntu policy guide - versions.]("http://people.canonical.com/%7Ecjwatson/ubuntu-policy/policy.html/ch-controlfields.html#s-f-Version")
i may be confused :) but i think in this case it goes something like this...
* 7:6.6.0.9 is considered as 7:6.6.0.9-0 by the packaging system (it adds debian revision 0)
* ~ is sorted as less, so 7:6.6.0.9-0~ppa1 is earlier than 7:6.6.0.9-0

---

