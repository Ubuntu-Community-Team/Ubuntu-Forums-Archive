---
title: "How to resolve function naming conflict in static library"
date: 2005-09-13
forum: Programming Talk
---

### Post by yccheok on 2005-09-13
Hi, I had two object file which each of them have a function called "void sayhello"

The problem is:
I try to create a static library from them

ar rcs libmy_library.a dummy.o smartie.o

When my client try to static link his code with my

g++ test.c -L. -lmy_library

The user had no idea which sayhello will be called. Either from dummy.o or smartie. 

How I can resolve this function naming conflict problem? Is there any way to check this conflict during ar rcs time? I.e. they will give you warning or error some sort of that.

Thank you.

---

### Post by LordHunter317 on 2005-09-13
Assuming it's C code, you can't do that, it's illegal, and if you used ld instead of ar, it should have given you a link time error.

---

### Post by yccheok on 2005-09-14
Can you please show me how I can do that in ld? If ld can give me error on the naming conflict, does it mean I should choose to use ld instead of ar?

---

### Post by LordHunter317 on 2005-09-14
My mistake, I can't find a way to do it.

---

