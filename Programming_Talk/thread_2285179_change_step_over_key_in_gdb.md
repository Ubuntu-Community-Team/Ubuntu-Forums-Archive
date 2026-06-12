---
title: "change step over key in gdb"
date: 2015-07-03
forum: Programming Talk
---

### Post by IAMTubby on 2015-07-03
Hello,
 Is it possible to change the step over key in gdb from [B]'n' to 'a' 
[/B]I will find it easier to toggle between step into (s) and step over if I can change it to 'a' instead of n

---

### Post by dwhitney67 on 2015-07-04
Sure!  Download the source package for gdb, then make the software change that you desire.  Afterwards, configure the product, and then build it.  You can install the built product in, say, /usr/local/bin.

Btw, the 'n' command in gdb implies "next", not step-over.

You might find it easier to debug programs using the Data Display Debugger (ddd), which is a GUI front-end to gdb.

---

