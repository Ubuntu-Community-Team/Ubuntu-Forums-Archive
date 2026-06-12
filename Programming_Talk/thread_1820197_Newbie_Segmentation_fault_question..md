---
title: "Newbie Segmentation fault question."
date: 2011-08-07
forum: Programming Talk
---

### Post by manjaba on 2011-08-07
Not sure why I'm getting the Segmentation fault statement on this program which runs ok:

#HelloWorld.s my second assembly program

.data

HelloWorldString:		#label
	.ascii"Hello World\n"

.text

.globl _start

_start:
	#load all the arguments for write()

	movl $4, %eax
	movl $1, %ebx
	movl $HelloWorldString, %ecx
	movl $12, %edx
	int $0x80

Thanks

---

### Post by Zugzwang on 2011-08-07
Hmmm, there should be some code to terminate the program after you print out "Hello World".

---

### Post by johnl on 2011-08-07
You are not terminating your program correctly.

You need something like the following at the end.
```

movl $1, %eax ;; syscall 1 is exit()
movl $0, %ebx ;; argument to exit
int  $0x80    ;; do it

```

---

