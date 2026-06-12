---
title: "8086 (Assembly) double lookup table question."
date: 2010-09-05
forum: Programming Talk
---

### Post by descendency on 2010-09-05
OK, what I want to do may not be possible but I think it is. 

I want to create a lookup table with the memory addresses of other lookup tables as the values in the table

Here is what the first lookup table looks like:

```
currenttable dw 73 dup ('*')
			dw itable, '**', ltable
			dw 12 dup('*')
			dw vtable, '*', xtable
			dw 167 dup ('*')
```
Then the lookup tables I want:
```
itable db 256 dup(1)
vtable db 73 dup(5)
		db 4
		db 182 dup(5)
xtable db 73 dup(10)
		db 9
		db 182 dup(10)
ltable db 88 dup(50)
		db 40
		db 167 dup(50)
```

and finally the code I wrote to translate from one table to another (which is probably hideously wrong):
```
mov current, al
mov bl, al
mov bh, 0
mov bx, [currenttable + bx]
add bx, word ptr previous
mov ax, bx
add cl, al
mov al, current
mov previous, al
```

This is 8086 code being compiled by MASM in a DOSbox environment. 

Any suggestion would be helpful.

---

