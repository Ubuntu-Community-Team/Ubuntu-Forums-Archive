---
title: "Assembler hello world - why does it work?"
date: 2017-03-16
forum: Programming Talk
---

### Post by w.w.milner on 2017-03-16
```
.text                          
    .global _start              
_start:
	  movl    $len, %edx           
	  movl    $msg, %ecx           
	  movl    $1,%ebx              
	  movl    $4,%eax          # system call number (sys_write)
	  int     $0x80            # call kernel
	  
	  movl    $0,%ebx             # first argument: exit code
	  movl    $1,%eax             # system call number (sys_exit)
	  int     $0x80               # call kernel
.data    
	.ascii "pack space "                   
msg:
	.ascii    "Hello from assembler\n"   
	len = . - msg 
```
The movl1 $msg, %ecx instruction turns into
b9 00 00 00 00       	mov    $0x0,%ecx
but ecx should be msg = teh start of teh string.
But it works. How?

---

### Post by w.w.milner on 2017-03-16
I've got it.
If you use objdump with the -r reloc option, like
objdump -S -s -d -r hello.o
You get 
 5:	b9 00 00 00 00       	mov    $0x0,%ecx
			6: R_X86_64_32	.data+0xb
IOW that instruction as altered when it is loaded

---

