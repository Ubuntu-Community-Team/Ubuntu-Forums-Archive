---
title: "Qucs help"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by balagosa on 2008-06-23
I have a problem on syncing Qucs with freehdl. I already got freehdl installed from the repos. Afterwards, I installed Qucs and hoping that simulating an Analog Simulation would go smoothly.

I had one error. the file **freehdl.pc** was not located in PKG_CONFIG_PATH. I copied freehdl.pc to **/usr/shar/freehdl** and **/usr/lib/freehdl**. That one solved it and the problem was gone. I gave simulating a second go, and this error popped out: **freehdl-libtool: link: specify a tag with `--tag'**
```
Starting new simulation on Mon 23. Jun 2008 at 19:48:48

creating netlist... done.
running C++ conversion... done.
compiling functions... done.
compiling main... done.
linking...freehdl-libtool: link: unable to infer tagged configuration

Errors occurred during simulation on Mon 23. Jun 2008 at 19:48:51
Aborted.

```

This is about it, i hope someone can help me. If all else fails, i will give ktechlab a shot.

---

### Post by balagosa on 2008-06-23
*bump*

---

### Post by balagosa on 2008-06-24
I expected someone would have a know-how of this :(

---

### Post by balagosa on 2008-06-24
*last bump*

---

