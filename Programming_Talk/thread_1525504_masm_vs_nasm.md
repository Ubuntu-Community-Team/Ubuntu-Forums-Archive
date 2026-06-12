---
title: "masm vs nasm"
date: 2010-07-06
forum: Programming Talk
---

### Post by yousafsajjad on 2010-07-06
i am trying to convert some code from masm to nasm .. but i cant seem to figure out one thing .. can anyone please help me with the following:
```

DESCRIPTOR    MACRO    name, limit, base, flags 
name    label    dword 
    dw    limit and 0FFFFh 
    dw    base and 0FFFFh 
    db    (base and 0FF0000h) shr 16 
    db    flags and 0FFh 
    db    ((flags and 0F00h) shr 4) or ((limit and 00F0000h) shr 16) 
    db    (base and 0FF000000h) shr 24 
    ENDM 
 
;The GDT for protected mode operation. 
    align    4 
GDTstart label    qword 
DESCRIPTOR    nulldesc,       0, 0,    0h    ; null descriptor 
DESCRIPTOR    datadesc,    0FFFFFh, 0,  092h    ; data segment 
DESCRIPTOR    stackdesc,    0FFFFh, 0,  092h    ; stack segment 
DESCRIPTOR    fatdatadesc, 0FFFFFh, 0, 0892h    ; BIG data segment 
DESCRIPTOR    fatcodedesc, 0FFFFFh, 0, 0C9Eh    ; BIG code segment 
DESCRIPTOR    codedesc,     0FFFFh, 0,  09Eh    ; code segment 
DESCRIPTOR    realdatadesc, 0FFFFh, 0,  093h    ; real mode data segment 
GDTend    label    qword

```

I dont understand "DESCRIPTOR    nulldesc,       0, 0,    0h" and other lines like that ..

---

### Post by xb12x on 2010-07-06
If I understand your question, it has nothing to do with nasm vs masn.

'DESCRIPTOR    nulldesc,    0,    0,    0h    ; null descriptor'

The first slot in the GDT is always set this way. It's a dummy descriptor and not used; a place-hoder.

I don't know exactly what the history is but it probably has something to do with being backwards compatible all the way back to the first Intel protected mode processors and Microsoft O.S.'s 
 Perhaps it was a way to easily identify the start of the descriptors table.

---

### Post by yousafsajjad on 2010-07-07
I read about it yesterday and i can see how stupid my question sounds .. It is just a macro with parameters and doing some operation on them

---

