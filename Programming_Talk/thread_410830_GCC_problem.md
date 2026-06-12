---
title: "GCC problem"
date: 2007-04-16
forum: Programming Talk
---

### Post by hollowhead on 2007-04-16
I'm getting a segmentation fault on running my program at teh command prompt after perfect compilation using gcc4.  I used gdb to isolate the bug and have changed the code recompiled but still get the same error.  Why?  any ideas?

---

### Post by dsl on 2007-04-16
> **hollowhead said:**
> I'm getting a segmentation fault on running my program at teh command prompt after perfect compilation using gcc4.  I used gdb to isolate the bug and have changed the code recompiled but still get the same error.  Why?  any ideas?

The question is too vague. You should tell more and maybe somebody could make a suggestion.

---

### Post by Wybiral on 2007-04-16
Yeah... I think most of us are going to need to see the source to answer this one.

---

### Post by hollowhead on 2007-04-17
Sorry I will post the code.  Although on the face of it its not a code problem.  I'm sure I've had this problem before but I cannot remember the solution......

---

### Post by amo-ej1 on 2007-04-17
a segmentation fault is a simple bug you encounter ... the easiest way to pinpoint the location is loading the code through gdb and led it crash. There is no 'one magical solution' for segmentation faults ...

---

### Post by Compyx on 2007-04-17
The tool 'valgrind' is excellent in tracking memory-errors, such as writing to read-only data, dereferencing null-pointers, etc.

To install, run:
```
sudo apt-get install valgrind
```

To use:
```
valgrind --tool=memcheck --leak-check=yes ./<your_program>
```
You can ommit '--tool=memcheck' since memcheck is the default tool.

Since you're getting a segmentation fault, you'll probably see messages like 'invalid read/write ...'.

But as others have already stated, we can't really help you without seeing the code in question. So post your code (copy and paste, don't retype) if you want more help.

---

