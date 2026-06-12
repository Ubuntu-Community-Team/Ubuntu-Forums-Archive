---
title: "dates in java"
date: 2011-09-14
forum: Programming Talk
---

### Post by vineeth v s on 2011-09-14
hi,

i want to take date form swing GUI of java from user as input to the program,
for doing some date calcs. so  it shouldn't be in string... ](*,)](*,)
can anybody help me pls...?

---

### Post by karlson on 2011-09-14
> **vineeth v s said:**
> hi,

i want to take date form swing GUI of java from user as input to the program,
for doing some date calcs. so  it shouldn't be in string... ](*,)](*,)
can anybody help me pls...?

strptime anyone?

---

### Post by ofnuts on 2011-09-14
> **vineeth v s said:**
> hi,

i want to take date form swing GUI of java from user as input to the program,
for doing some date calcs. so  it shouldn't be in string... ](*,)](*,)
can anybody help me pls...?
1) use a DateFormat to parse the string, if using a textfield. But I'm sure you'll find Date Selection/Calendard widgets around.
2) Use the Calendar class for your computations

---

