---
title: "compiling 32-bit code on edgy 64?"
date: 2006-10-27
forum: Programming Talk
---

### Post by The Warlock on 2006-10-27
I just upgraded to 64-bit edgy from 32-bit dapper. I need to be able to assemble regular IA32 asm for a class. What's the gcc extention to do this, and do I need to install any additional packages?

---

### Post by The Warlock on 2006-10-27
Okay, evidently I need to use the -m32 extension and install ia32-libs.

---

### Post by rplantz on 2006-10-28
> **The Warlock said:**
> Okay, evidently I need to use the -m32 extension and install ia32-libs.

I responded to your question on the X86 64-bit forum.

Did you get it to work?

I'm still having a problem with the stubs-32.h header file.

Edit: I just determined that you need to install libc6-dev-i386.

---

