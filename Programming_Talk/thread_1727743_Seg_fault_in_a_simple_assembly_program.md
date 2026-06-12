---
title: "Seg fault in a simple assembly program"
date: 2011-04-12
forum: Programming Talk
---

### Post by antman8969 on 2011-04-12
Here is the code. All I want to do is move one byte into the the memory that 'string' points to. I'm guessing it is a syntax error but I've been looking for the proper way to do this for hours. Any help would be greatly appreciated.


```


section .data:
string:		db	0,0

section .text:
global main

main:
	mov byte [string],'A'    ;seg fault. what is the proper way?
	

exit:
	mov eax,1
	mov ebx,0
	int 80h
```

I've also tried loading the char into a register and moving it from there, but that made no difference.

---

### Post by antman8969 on 2011-04-12
Ok I just got it. First off, I had to remove the colons from the section titles, so

```
section .data:
```

became 

```
section data
```

and so on. I also had to define the string in the .bss section like this

```
string times 10 resb 0
```

then I could change it!

---

