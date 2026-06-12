---
title: "Can someone explain this MIPS code to me"
date: 2008-07-01
forum: Programming Talk
---

### Post by JohnThompson on 2008-07-01
I understand that the mips code below modifies itself but I don't understand what is does. Can someone explain to me what it does? Thanks.

111100 is assume to be the opcode of jal.


jal  next
.
.
.
next: li  $at, 0XF0000000
      sw  $at, 0($ra)
      jr  $ra

---

