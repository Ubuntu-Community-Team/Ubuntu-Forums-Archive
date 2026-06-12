---
title: "How to install binutils 2.24"
date: 2014-07-10
forum: Packaging and Compiling Programs
---

### Post by afog on 2014-07-10
I have installed gcc 4.9.1 in order to compile for the new AVX512 instruction set. However, I also need to update the assembler to version 2.24 in order to assemble the compiled code. I tried to install binutils 2.24 with the usual commands: ./configure / make / sudo make install
It says  *** No rule to make target `install'.  Stop.
My binutils is version 2.22 which does not support the new instuction set.
(Linux version 3.2.0-49-generic)

---

### Post by oldos2er on 2014-07-10
Moved to Packaging & Compiling Programs.

Which version of Ubuntu are you using? 14.04 Trusty has binutils 2.24 in its repositories:  [http://packages.ubuntu.com/trusty/binutils](http://packages.ubuntu.com/trusty/binutils)

---

