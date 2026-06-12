---
title: "Viewing background process calls"
date: 2009-01-05
forum: Programming Talk
---

### Post by jasonvtop on 2009-01-05
Hello all,

is there a program/way which allows to view the procedures/calls while we interact with an application's user interface? say e.g. while i'm playing with the GIMP/firefox/any program, i see the commands which are being executed behind.

so cool if possible :D 
even cooler if you can re-execute the commands from the terminal :D

---

### Post by imdano on 2009-01-05
Sounds like you want something like strace, which will trace out signals and system calls for you. Open a terminal and run ```
strace <command>
```It's extremely verbose, but if you look carefully at the output you can usually find the interesting bits.

---

