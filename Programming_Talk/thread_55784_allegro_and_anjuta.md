---
title: "allegro and anjuta"
date: 2005-08-10
forum: Programming Talk
---

### Post by benqbasic on 2005-08-10
Hey,

Ive been trying to get anjuta and the allegro lib working. 

Does any one know how to configure a anjuta project to compile the allegro library?

Thanks,

---

### Post by Hanj on 2005-08-12
First do "sudo apt-get install liballegro4.1" if you haven't done so.

Then start a regular console project in Anjuta and add `allegro-config --libs` (with the backticks) to
Settings->Compiler and linker options->Options->Linker flags

Compile and enjoy Allegro in all its glory.

---

