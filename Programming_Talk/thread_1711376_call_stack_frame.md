---
title: "call stack frame"
date: 2011-03-21
forum: Programming Talk
---

### Post by cybo on 2011-03-21
i'm trying to understand what is stored in the call stack frame. the book i'm reading mentions it briefly. the frame is described to store: incoming parameters, return value, temporary storage, saved state information, outgoing parameters. i think i understand everything except temporary storage and saved state information. as far as i understand temporary storage is used to store variables that were declared and used in the function. but i have no idea what saved state information is and how it is used. i would really appreciated if someone could help out.

---

### Post by slavik on 2011-03-21
saved state - all registers on the cpu are saved and restored at the end.

so if your program takes a parameter in eax and returns the value in eax, you saved ebx, ecx, edx, etc. if you are going to use them for your function and then restore them at the end.

---

### Post by cybo on 2011-03-21
thanks

---

