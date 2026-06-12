---
title: "cout source code?"
date: 2010-02-12
forum: Programming Talk
---

### Post by munky99999 on 2010-02-12
I'm just wondering. Where might one see the cout or similar source code?

As to see how it goes about outputting to the current terminal. When an app puts all the output of commands to it's gui window. Is it rewriting the cout code? or just using it and building their own terminal?

Also would I be correct in thinking that it would be completely different code depending on totally different factors? Such as arch or distro or osbrand.? If so, would this be the limitation of porting over apps?

---

### Post by night_fox on 2010-02-14
Its in libstdc++, and declared here: [http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/a00920_source.html](http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/a00920_source.html) but it refers to something else. You'll have to trek through loads of abstractions to find out what it actually does.

---

### Post by Lux Perpetua on 2010-02-14
> **munky99999 said:**
> When an app puts all the output of commands to it's gui window. Is it rewriting the cout code? or just using it and building their own terminal?No, GUI displays are not made using cout or iostreams. Graphical displays on Linux are made by interfacing with the X-Windows system, which hides the graphics hardware.

---

### Post by Zugzwang on 2010-02-15
Processes in linux communicate over pipes (@everyone: please correct me if I am wrong). The program itself just writes its output to one of its pipes (stdout), which is opened by default when starting the process. The process of displaying the output is then left to the parent process (or any other process the parent process forwards the pipe to), which can do anything it wants with it. So a gnome terminal for example could paint the output onto its windows whereas some other process can simply ignore it.

To sum it up: Actually displaying the terminal output is *not* the concern of a process. For details, look here: [http://en.wikipedia.org/wiki/Pipeline_(Unix](http://en.wikipedia.org/wiki/Pipeline_(Unix))

---

