---
title: "C FILE (_IO_FILE struct) Question"
date: 2008-07-28
forum: Programming Talk
---

### Post by era86 on 2008-07-28
I am curious as to how I can get the current offset of a FILE * after a certain amount of reads.  I am basically trying to create an index file for a rather large data file.  My function reads in from the data file and, after a couple of reads, marks the data and the offset of where it is located.

I was wondering if it is possible to write the data to the index and the current position of the FILE * within the file as the offset.

Any help is appreciated.  Thanks in advanced.

---

### Post by KingTermite on 2008-07-28
Sounds like you "may" want to switch to binary file functions like fread, fwrite, fpos, ftell, etc.....

You may be able to get just the position with ftell() though.

---

### Post by era86 on 2008-07-28
> **KingTermite said:**
> Sounds like you "may" want to switch to binary file functions like fread, fwrite, fpos, ftell, etc.....

You may be able to get just the position with ftell() though.

Hey thanks!  I'll take a look at those and keep ya posted. :guitar:

---

