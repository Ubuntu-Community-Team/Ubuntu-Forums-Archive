---
title: "DLL decompiler!"
date: 2007-01-16
forum: Programming Talk
---

### Post by Elisei on 2007-01-16
Hi!

Is there a way to actually take a .dll file and convert it back to a source code, something like a decompiler; i know there is a great java decompiler, but is there stuff for other languages like c++ lets say?;

thanks;

---

### Post by Wybiral on 2007-01-16
I've seen some... But they rarely produce WORKING c++ code, and the names are all mangled. You'd have better luck with C than C++ because of how they store the names in assembly.

Also, dll's aren't really a linux thing, perhaps "so" or do you mean executables in general?

Also, if you know assembly you can just open up a hex editor :)

---

### Post by phossal on 2007-01-16
> **Elisei said:**
> Is there a way to actually take a .dll file and convert it back to a source code, something like a decompiler; i know there is a great java decompiler, but is there stuff for other languages like c++ lets say?

In short, no. There isn't. You're experiencing the difference between machine code (.dll, .exe, etc) and bytecode (Java, etc). Bytecode can almost always be decompiled. Machine code, prepared from sources like C, and C++, is best attacked with a good disassembler. 

Wybiral is right, though. Even using an awesome disassembler, you're going to be facing assembly. IDA Pro, will at least map out the functions, though. If you're determined to find a decompiler, check out boomerang.

Question in reverse, have you seen a *good* Java decompiler? I haven't. I'd be interested in any recommendations.

---

### Post by winch on 2007-01-16
[Boomerang]("http://boomerang.sourceforge.net/") is a general open source retargetable decompiler of machine code programs.

These sorts of programs generally require a lot of background knowledge and experiance before you can get anything useful out of them. More of a tool in your tool kit than a solution.

---

