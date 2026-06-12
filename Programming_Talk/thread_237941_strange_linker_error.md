---
title: "strange linker error"
date: 2006-08-16
forum: Programming Talk
---

### Post by darth_vector on 2006-08-16
i am getting a strange linker error:

! Error: Unresolved external '_eh' referenced from /src/objdir/nwadump.o

the source file contains a call to a function "eh" that is defined in a header file called gpib.h - used for instrumentation programming.

the reason the error is strange is that there is no reference to "_eh" in nwadump.o whatsoever!

i have checked, double checked and tripple checked all of the source files and can find no problem. any help would be appreciated.

---

### Post by simonn on 2006-08-17
Check that you are linking to the library that gpib.h is the header of.

---

### Post by darth_vector on 2006-08-17
thanks, but thats not it. i am linking the relevant libraries.

---

### Post by LordHunter317 on 2006-08-17
The name is being mangled, and probably correctly.  That means: you're missing a library.

---

