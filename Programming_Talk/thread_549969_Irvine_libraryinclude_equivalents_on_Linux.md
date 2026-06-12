---
title: "Irvine library/include equivalents on Linux?"
date: 2007-09-13
forum: Programming Talk
---

### Post by xat_ on 2007-09-13
I'm taking a course on assembly, but it's rather Windows-centric. The material/examples/libraries/includes come from [this book]("http://kipirvine.com/asm/"). Are there Linux equivalents for this, or will I have to run things under Wine/dosbox?

---

### Post by geraldm on 2007-09-13
The assembly language compiler is MASM, and running under
wine/DOS looks to me like the closest equivalent.  A lot depends
on the details in the instructions, but the macro features do not
transfer well to other assembler compilers.  Preparing the programs
for a different assembler would add a significant burdon to the 
course materials.  The instructor should know if there is an equivalent
project.

Gerald

---

