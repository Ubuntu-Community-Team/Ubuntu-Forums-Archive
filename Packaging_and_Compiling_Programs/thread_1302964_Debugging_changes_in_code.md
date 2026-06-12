---
title: "Debugging changes in code"
date: 2009-10-27
forum: Packaging and Compiling Programs
---

### Post by NoBugs! on 2009-10-27
Is there a way to debug a section of code in an Ubuntu program?

I know you can run "sudo apt-get source programname" to get the program source, you can make modifications and ./configure, make, sudo make install to make changes, but is there any way to debug what a section of code is doing? Such as stepping through the code, using breakpoints, watches, etc?

---

### Post by NoBugs! on 2009-10-28
Can it be debugged with gdb? I installed a gui for gdb-debugging but I couldn't figure out how to start the debugging.

---

### Post by dinxter on 2009-10-29
you can certainly do set breakpoints, watches, step over, break at line number and a whole host of things with gdb. Try the tutorial [http://www.delorie.com/gnu/docs/gdb/gdb_toc.html](http://www.delorie.com/gnu/docs/gdb/gdb_toc.html)
Using one of the many IDE's with these things built tends to be the way i do it these days though

---

