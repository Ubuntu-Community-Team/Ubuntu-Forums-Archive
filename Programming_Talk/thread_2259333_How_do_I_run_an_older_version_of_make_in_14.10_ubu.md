---
title: "How do I run an older version of make in 14.10 ubuntu?"
date: 2015-01-03
forum: Programming Talk
---

### Post by shahin on 2015-01-03
What is the best way for me to run make 3.81 or 3.82 please? I am trying to build an Android image and they don't like make 4.0:-(

---

### Post by schragge on 2015-01-03
Are you sure that make 4.0 is to be blamed? The incompatibilities between 3.82 and 4.0 are minimal, mostly related to whitespace treatment in non-recipe lines if special target .POSIX is specified and variable names ending in ! character. Both are pretty obscure features rarely used in makefiles. Even though Android website recommends GNU make 3.81-3.82 (because they test-build it on precise which ships with make 3.81), I find it hard to believe it fails to build with make 4.0.

---

### Post by ofnuts on 2015-01-04
What kind of errors do you get?

---

### Post by sudheer_vaddi on 2015-10-25
build/core/main.mk:45: ********************************************************************************
build/core/main.mk:46: *  You are using version 4.0 of make.
build/core/main.mk:47: *  Android can only be built by versions 3.81 and 3.82.
build/core/main.mk:48: *  see [https://source.android.com/source/download.html](https://source.android.com/source/download.html)
build/core/main.mk:49: ********************************************************************************
build/core/main.mk:50: *** stopping.  Stop.

---

### Post by Bucky Ball on 2015-10-25
Just a tip: You probably shouldn't bother running anything in 14.10 as it is no longer supported and the repos are closed. Not good to have it online as it receives no updates/upgrades, including security updates. Advise upgrading to a supported release, 14.04 LTS, supported until 2019, or 15.10 (15.04 dies in January 2016 so hardly worth the effort, IMHO). But then, you may have very good reason for running an unsupported release. 

Good luck. :)

---

