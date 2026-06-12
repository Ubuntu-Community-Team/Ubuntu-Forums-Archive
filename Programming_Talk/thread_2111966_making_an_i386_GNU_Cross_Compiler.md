---
title: "making an i386 GNU Cross Compiler?"
date: 2013-02-03
forum: Programming Talk
---

### Post by Jamie_Edwards on 2013-02-03
Hi guys,

I've been trying to Google how to make an i386 cross compiler in Ubuntu and have managed to find one [_**here**_]("http://wiki.osdev.org/GCC_Cross-Compiler_on_Debian_Linux"), only problem is that the header says

> For some reason the repositories are currently broken. I'm trying to figure out why. JackScott 05:42, 20 July 2010 (UTC)

That means the instructions provided on it hasn't worked for the last three years. So I've come here to ask if anyone has any way of making a GNU Cross Compiler for i386 ( but on a x86_64 system )?

Thanks.

Jamie.

---

### Post by Bachstelze on 2013-02-03
Use the -m32 flag of gcc to compile i386 programs on an amd64 system. If that's not what you want to do, please elaborate.

---

### Post by Jamie_Edwards on 2013-02-03
> **Bachstelze said:**
> Use the -m32 flag of gcc to compile i386 programs on an amd64 system. If that's not what you want to do, please elaborate.

I'm already using -m32, I want to try and port gcc over to my o.s and they're saying in the wiki that I need to have a cross compiler to achieve that.

---

### Post by Bachstelze on 2013-02-03
> **Jamie_Edwards said:**
> I'm already using -m32, I want to try and port gcc over to my o.s and they're saying in the wiki that I need to have a cross compiler to achieve that.

Then the link you posted will not help you. You need to have a C compiler for "your OS", whatever that is.

---

