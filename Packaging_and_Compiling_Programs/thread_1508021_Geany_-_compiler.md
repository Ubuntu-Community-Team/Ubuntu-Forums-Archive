---
title: "Geany - compiler"
date: 2010-06-12
forum: Packaging and Compiling Programs
---

### Post by spamalot on 2010-06-12
Hello,

How can I set up Geany to use the gcc compiler? There are no compiler detected as Codeblocks. That's a limitation.

---

### Post by WitchCraft on 2010-06-12
Good question. Tell me once you know how.

---

### Post by GregBrannon on 2010-06-12
Geany either checks for installed compilers when it is installed or assumes which are installed, not sure.  However it works, Geany then decides which compilers to use based on the source code filenames.  If you're working on a source file with a .c extension, you should be able to check which compiler will be used when you tell Geany to compile by selecting, "Build," then "Set Includes and Arguments."

If gcc is not shown as the default C compiler in the resulting lists, then add it and see what happens.  This assumes, of course, that you have the Gnu Compiler Collection installed.  If not, install it.

---

