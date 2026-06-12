---
title: "GNU-Autotools: Building an executable?"
date: 2012-05-18
forum: Programming Talk
---

### Post by fallenshadow on 2012-05-18
Hi guys/gals,

I recently went to update my GNU autotools for my project. I did so and thought it was working perfectly until it created a class library (shared library) instead of a working executable. :?

Can anyone explain why this is happening? or offer a solution?

---

### Post by fallenshadow on 2012-05-18
Here is an image to show you what result I get and what the result should be:

On the left the expected result, on the right - what happens after using make.

[IMG]http://ubuntuone.com/1PQmKTALMbHAsTH51VGXnK[/IMG]

I think maybe this GNU autotools implementation is too complex for me, when I only need something pretty simple.

---

### Post by athina on 2012-05-18
you can always use eclipse (or another ide). nice editor, debug tools and many options (gui) for building apps

---

### Post by pbrane on 2012-05-18
> **fallenshadow said:**
> Hi guys/gals,

I recently went to update my GNU autotools for my project. I did so and thought it was working perfectly until it created a class library (shared library) instead of a working executable. :?

Can anyone explain why this is happening? or offer a solution?

The file created is actually an executable ELF file. You can run it from the command line to verify. I don't know why the file manager sees it as a shared library. I'm trying to find a solution, I'll post back if I do.

EDIT: simply remove the compiler flag **-fPIE -pie**

---

### Post by fallenshadow on 2012-05-21
I tried that but every time I run ./configure the output in the terminal is this:

> Preprocessor Flags ...:  -O2 -D_FORTIFY_SOURCE=2 -fPIE -pie -Wall
 Compiler Flags .......:  -O2 -D_FORTIFY_SOURCE=2 -fPIE -pie -Wall -pthread ETC.

That means its putting it in there for some reason. How can I stop it inserting it every time?

---

### Post by pbrane on 2012-05-21
run **./autogen.sh** to rebuild the configure script. If you don't have autogen.sh use **autoreconf**.

Make sure you are editing **configure.ac** or **configure.in** as the case may be.

---

### Post by fallenshadow on 2012-05-22
Thanks, got it sorted this morning! :)

---

