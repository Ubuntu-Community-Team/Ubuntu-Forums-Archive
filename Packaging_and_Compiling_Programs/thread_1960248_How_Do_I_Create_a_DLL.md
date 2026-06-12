---
title: "How Do I Create a DLL?"
date: 2012-04-17
forum: Packaging and Compiling Programs
---

### Post by Ubuntist on 2012-04-17
I know how to compile source files and link the resulting objects with libraries to produce an executable.  In order to use compiled code in certain environments (e.g., within the statistical package R), however, I need to create a DLL.  Could anyone give me a pointer on how to do that?

---

### Post by Ubuntist on 2013-02-18
I finally found out how to do this.  I'll post it, on the off chance somebody else is looking for the same information.

It's simple:  with the GNU compilers, just use the [FONT=System]-shared[/FONT] option.  For example, to create a DLL named [FONT=System]func.dll[/FONT] from the C source file [FONT=System]func.c[/FONT], do

```
gcc func.c -shared -o func.dll
```That's all there is to it!

---

### Post by Tony Flury on 2013-02-18
> **Ubuntist said:**
> I finally found out how to do this.  I'll post it, on the off chance somebody else is looking for the same information.

It's simple:  with the GNU compilers, just use the [FONT=System]-shared[/FONT] option.  For example, to create a DLL named [FONT=System]func.dll[/FONT] from the C source file [FONT=System]func.c[/FONT], do

```
gcc func.c -shared -o func.dll
```That's all there is to it!

Bear in mind this is not a Windows DLL (Dynamic Link Library), and any "dll" you create like this cannot be used on a windows machine.

What you have actually created is a "shared" object library which are normally labelled as a ".so" file - but as you have seen, under linux you can call them anything you want.

Although the naming convention is simply that (a convention) I would recommend that to avoid confusion you don't create ".dll" files for linux.

---

