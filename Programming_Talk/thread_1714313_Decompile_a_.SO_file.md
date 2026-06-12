---
title: "Decompile a .SO file?"
date: 2011-03-25
forum: Programming Talk
---

### Post by hopkinskong on 2011-03-25
Hello,
 
How to decompile a .so file? That .so was located in /lib, and the arch. is ARM, so i can't find a decompiler to decompile that!
 
Any solutions?
 
Thanks.

---

### Post by slavik on 2011-03-25
> **hopkinskong said:**
> Hello,
 
How to decompile a .so file? That .so was located in /lib, and the arch. is ARM, so i can't find a decompiler to decompile that!
 
Any solutions?
 
Thanks.
no, there are no solutions.

what library is this that you need the actual code to it and it isn't available?

---

### Post by MadCow108 on 2011-03-25
```
objdump -D sofile
```
according to manpage it can also handle arm
if you have the source you might prefer -S

---

### Post by nvteighen on 2011-03-25
And be aware that decompiling will just give you ASM code; don't expect it to magically give you the original C, C++ source!

---

### Post by hopkinskong on 2011-03-26
> **MadCow108 said:**
> ```
objdump -D sofile
```
according to manpage it can also handle arm
if you have the source you might prefer -S
 command not found! what hapened?

---

### Post by hopkinskong on 2011-03-26
> **slavik said:**
> no, there are no solutions.
 
what library is this that you need the actual code to it and it isn't available?
 hmm the library is available, but the source are not available!
 
like some so file from another device, adobr flash,etc

---

### Post by pbrane on 2011-03-26
You should have the ARM cross complier version of objdump to disassemble the .so file. It would be found in binutils. I don't think there is an ARM cross compiler in the repos.

---

### Post by nvteighen on 2011-03-26
> **hopkinskong said:**
> hmm the library is available, but the source are not available!
 
like some so file from another device, adobr flash,etc

First, all you'd get from decompiling is Assembly, which is quite difficult to understand; again, don't expect getting the source like it was originally written by the developers!

But, second, be careful. Reverse engineering propietary software like Adobe Flash is illegal. Ok, *maybe*, private reverse engineering of propietary software may be legal... it's quite certain nobody will care if you do and don't tell anyone. But you can't take advantage of reverse engineered code.

Now, if it's a Free Software library, then, you better look for the source either using apt-get or at the project's website.

---

