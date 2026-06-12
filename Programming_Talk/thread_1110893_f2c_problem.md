---
title: "f2c problem"
date: 2009-03-30
forum: Programming Talk
---

### Post by Kevin A on 2009-03-30
I want to translate a Fortran code to C (to only understand it, not compile it) but it has errors such this:  

Error on line 1286 of psffit.f: labeled continuation line (starts "end if")

what can I do? I don't care if it won't translate some lines.
And if you know some other programs that can translate a Fortran to C, C++, Python or Matlab, can you introduce it to me,

Thanks,

---

### Post by bapoumba on 2009-03-30
Moved to PT.

---

### Post by newagelink on 2009-06-10
I'm new to FORTRAN 77, but the following makes me think you have a line that is too long for the compiler to read (beyond 74 characters or so), or you have incorrectly appended a line of code to the line before it (to correct such a length problem): > labeled continuation line The "(starts "end if")" would then refer either to the problematic line or the one immediately before or after it.

I encountered an error that I think used such language when I was dealing with an "unbalanced parentheses" error.

Hope this helps.

---

