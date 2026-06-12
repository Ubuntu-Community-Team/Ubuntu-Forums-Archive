---
title: "Valgrind suppression file for a specific library?"
date: 2010-01-14
forum: Programming Talk
---

### Post by Senesence on 2010-01-14
Let's say I have "libsomething.so", and valgrind generates a whole lot of errors which relate to that library.

I know that I could run valgrind with the --gen-suppressions=yes option, and copy paste all the generated suppression blocks to a suppression file, which I could then set with --suppressions=/path/to/my/suppressions/file.supp.

However, I was wondering if maybe there is a simpler way to just ignore everything that "libsomething.so" does, completely, without having to copy paste, or scroll through 100 (or so) errors.

Is there an option like that?

If not, what would be the easiest way to ignore a library?

---

### Post by Senesence on 2010-01-15
Anyone?

---

### Post by MadCow108 on 2010-01-15
obj:object.so
in the suppression file is probably what you are looking for
also note text (* ?) and frame (...) wildcards help suppressing tons of similar problems

---

