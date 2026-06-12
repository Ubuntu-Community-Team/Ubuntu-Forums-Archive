---
title: "Assembly  Beginner Help"
date: 2010-06-13
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-06-13
where are my errors ( line 7,20,11,16,19) with masm ?
```
.model small
.stack 100h
.data
main proc
    mov ax,@data
    mov ds,ax
    top:
        push ax
        and ax,0000000000011000b
        cmp ax,0000000000011000b
        je  true
        pop ax
        push ax
        and ax,0000000001100000b
        cmp ax,0000000001100000b
        je true
        pop ax
        inc ax
        jmp top
    true:
        pop ax
main endp
end main
```

---

### Post by Zugzwang on 2010-06-13
If you want others to help you, consider also adding the errors you are getting (copy&paste) to your post. Also add line numbers to your source code. Finally, state *how* you are assembling your source code (which platform?, which options?), because that actually makes a difference.

---

### Post by cap10Ibraim on 2010-06-13
screenshot

---

### Post by NathanB on 2010-06-13
Insert a line ".code" between the ".data" and "main proc" lines and your errors will go away.

Nathan.

---

### Post by cap10Ibraim on 2010-06-13
> **NathanB said:**
> Insert a line ".code" between the ".data" and "main proc" lines and your errors will go away.

Nathan.
:guitar::lolflag: thanks what a silly mistake

---

