---
title: "Cross compiling"
date: 2010-09-21
forum: Programming Talk
---

### Post by madmax_mfc on 2010-09-21
Hi,
I need to cross compile some **Fortran** code for vxWorks (PPC604).
The code is "stored" and compiled on an Intel (Ubuntu) PC, and the target is a PPC604 vxWorks on a board (in  a crate!).

My PC: 
CPU:     Intel Pentium IV 3.2 GHz 
OS:       Ubuntu 10.04 LTS lucid
GCC:    4.4.3
F77:      1.5
MAKE:   3.81


Thank in advance

Max

---

### Post by dargaud on 2010-09-21
Well, that's not the best forum to ask ! The quick answer is to get the VxWorks cross compiler from them ($$$). I could tell you in 3 lines how to compile for a PPC604 linux architecture, but I'm pretty sure (although not *absolutely* sure) it's not going to run on VxWorks.

---

### Post by madmax_mfc on 2010-09-21
> **dargaud said:**
> Well, that's not the best forum to ask ! The quick answer is to get the VxWorks cross compiler from them ($$$). I could tell you in 3 lines how to compile for a PPC604 linux architecture, but I'm pretty sure (although not *absolutely* sure) it's not going to run on VxWorks.


Yes, you are right, but I've not found where to post my thread. :(

I've not found a fortran compiler on windriver site and I was looking for a free compiler.

I'm not a linux guru and I'm not able (I think) to "compile compiler and cross compilers" if this is too difficult.

I can try, but I'm not sure! :(

---

### Post by madmax_mfc on 2010-09-22
No idea? :rolleyes:
It's very important.

Thanks

Max

---

### Post by lisati on 2010-09-22
Moved to "Programming talk"

---

### Post by madmax_mfc on 2010-09-26
No one with a similar problem?

---

### Post by phrostbyte on 2010-09-26
> **madmax_mfc said:**
> No one with a similar problem?

Unless some NASA engineers frequent this board, probably not. :)

GCC can compile Fortran, but compile it for VxWorks is a different story. I'm thinking you probably need a compiler from VxWorks.

Here is more info on the current state of VxWorks support:
[http://gcc.gnu.org/install/specific.html#x-x-vxworks](http://gcc.gnu.org/install/specific.html#x-x-vxworks)

---

