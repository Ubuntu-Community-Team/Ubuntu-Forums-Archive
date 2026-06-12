---
title: "using as command to assemble a PIC object"
date: 2013-06-08
forum: Programming Talk
---

### Post by allynm on 2013-06-08
Hello everyone,

I decided to learn more about shared objects, the dynamic linker, etc. My question pertains to Postition Independent Code creation using the as (GAS) command.  There is no command line option to create PIC from an assembly language file.  One can use gcc -fPIC -o out.obj out.s and this will create PIC which can subsequently be linked using -shared option to produce an libout.so  How would one create PIC from the as command, followed by the ld command?  There must be some way to do it by including the appropriate libraries but I can't zero in on what they are.

Thanks,
Mark Allyn

---

### Post by xb12x on 2013-06-08
> **allynm said:**
> Hello everyone,

I decided to learn more about shared objects, the dynamic linker, etc. My question pertains to Postition Independent Code creation using the as (GAS) command.  There is no command line option to create PIC from an assembly language file.  One can use gcc -fPIC -o out.obj out.s and this will create PIC which can subsequently be linked using -shared option to produce an libout.so  How would one create PIC from the as command, followed by the ld command?  There must be some way to do it by including the appropriate libraries but I can't zero in on what they are.

Thanks,
Mark Allyn


It's not just about finding a command-line option.

To write Position Independent Code in assembly you'll to need to know almost as much as the GCC tools know about PIC. Which means you'll need to learn a bunch about how the assembler works,  how the O.S. works including memory management and global offsets, etc, etc, etc.

It will definitely be a learning experience.

---

