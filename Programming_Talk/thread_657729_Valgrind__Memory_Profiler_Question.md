---
title: "Valgrind / Memory Profiler Question"
date: 2008-01-03
forum: Programming Talk
---

### Post by JupiterV2 on 2008-01-03
I decided it would be a good idea to check for memory leaks in my program and chose Valgrind for no better reason that Wine devs use it..It appears to run as expected andt reported no issues/leaks of the code I have written (Yay me!). Hhowever, there were a host of issues reported aboug gtkmm or related gtk+/pango/etc libraries. 

Is there a way to suppress these errors and have it only report on my code?

On an aside, do projects like gtkmm not use a memory profiler to check for leaks so they may be fixed or are the errors unavoidable/ and/or false positives?

---

### Post by rufius on 2008-01-04
If you read through the valgrind documentation there's a way to suppress certain errors based on some user provided pattern. At least I  seem to recall that.

Hope that helps :)

---

### Post by JupiterV2 on 2008-01-04
Lesson learned: I should have done my homework better.

---

### Post by rufius on 2008-01-05
Sometimes such things get the better of us ;).

---

