---
title: "Assembly Question."
date: 2009-06-17
forum: Programming Talk
---

### Post by 2words4uready on 2009-06-17
Can anyone explain why this code returns 116 as an exit code?
```
.section .data
data_items:
.long 9,0
.section .text
.globl _start
_start:
movl $9, %edi
movl data_items(,%edi,4), %eax
movl %eax, %ebx
movl $1, %eax
int $0x80
```

---

### Post by Lux Perpetua on 2009-06-17
You're walking off the pier, aren't you? You're trying to get data_items[9], which doesn't exist. You have data_items[0] (9) and data_items[1] (0) and nothing else. data_items[9] could be anything, perhaps something in the text section.

---

### Post by Ariel David Moya Sequeira on 2009-06-18
My guess is: it's going to return the same value because of the assembled code, so it's not going to be quite random. However, Lux Perpetua is right: you're trying to access a value out of the bounds of the .long array, so it's not going to return any value you would expect.

---

