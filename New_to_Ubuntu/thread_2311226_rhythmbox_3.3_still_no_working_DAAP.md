---
title: "rhythmbox 3.3 still no working DAAP?"
date: 2016-01-25
forum: New to Ubuntu
---

### Post by wyrm111 on 2016-01-25
DAAP has been busted on rhythmbox for months now. I thought I'd give it another shot and compiled 3.3 from source. All relevant (and not so relevant) packages installed, proper flags utilized... Core Dump Great... I'm going to assume this was an abandoned feature for the rhythmbox team. Anyone get anything other then a coredump on their machines? Or does anyone remember the last working version? I'll happily revert to and older version to get the feature working

---

### Post by davidmohammed on 2016-01-25
if you are core dumping then this is a sign of a bug - get a good gdb trace and file it as a bug report on gnome bugzilla so that the rhythmbox devs can actually see what the issue is.

The devs may not know about the broken daap - you can help out by letting them know!

More info about how to get more info via gdb here - [https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

Create a bug report with the backtrace here - [https://bugzilla.gnome.org/enter_bug.cgi?product=rhythmbox](https://bugzilla.gnome.org/enter_bug.cgi?product=rhythmbox)

---

