---
title: "Is there a high-resolution cross-platform timer in C++'s standard library?"
date: 2011-09-22
forum: Programming Talk
---

### Post by s3a on 2011-09-22
Is there a high-resolution cross-platform timer in C++'s standard library? I ask because I want to do some benchmarks for an Engineering "English" class (but please don't assume I am too smart since it's my first semester in University and I am not even taking any computer science courses this semester - but I have taken Java courses in the past so I am not clueless). When I Google, I find so many different answers and I'd like to avoid external libraries if possible. I would additionally like to get accuracy down to the nanosecond.

Any help in doing so would be greatly appreciated!
Thanks in advance!

---

### Post by Vaphell on 2011-09-22
if you couldn't find it then it doesn't exist ;-)

what do you want to measure exactly? nanosecond precision doesn't make much sense either way, measurements will be all over the place, depending on what the machine does at the moment. Usually you get reliable results by repeating measured operation N times (where N is a really big number) and dividing total time by N.

---

### Post by karlson on 2011-09-22
> **s3a said:**
> Is there a high-resolution cross-platform timer in C++'s standard library? I ask because I want to do some benchmarks for an Engineering "English" class (but please don't assume I am too smart since it's my first semester in University and I am not even taking any computer science courses this semester - but I have taken Java courses in the past so I am not clueless). When I Google, I find so many different answers and I'd like to avoid external libraries if possible. I would additionally like to get accuracy down to the nanosecond.

Any help in doing so would be greatly appreciated!
Thanks in advance!

I think you are looking for something like POSIX high-resolution timers.  Like timer_create function etc.  So I would get something POSIX compliant on "other" platforms you are working on like CYGWIN for Windows.

---

