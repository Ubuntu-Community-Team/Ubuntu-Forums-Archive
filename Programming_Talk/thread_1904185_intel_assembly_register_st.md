---
title: "intel assembly register st?"
date: 2012-01-04
forum: Programming Talk
---

### Post by /bin/sh on 2012-01-04
While I was doing some intel assembly code on kate text editor I by mistake wrote "st" and I saw that st was blue (I had set kate to blue for a register), this means st is a register. What is st used for, is it 8, 16, 32 or 64 bit or a segment register?

---

### Post by nvteighen on 2012-01-04
> **/bin/sh said:**
> While I was doing some intel assembly code on kate text editor I by mistake wrote "st" and I saw that st was blue (I had set kate to blue for a register), this means st is a register. What is st used for, is it 8, 16, 32 or 64 bit or a segment register?

My ASM knowledge is very limited, but I never heard of any ST register... Take a look at: [http://en.wikipedia.org/wiki/X86#x86_registers](http://en.wikipedia.org/wiki/X86#x86_registers)

Anyway, never deduce anything from syntax highlighting. Under common-lisp-mode + SLIME, Emacs marks anything starting with "with-" as if it was a keyword... But no matter how hard you try looking for "with-my-girlfriend" on the Common Lisp HyperSpec, you won't find it... or her... :P

(No, it's not a bug, it's a feature. There's a reason for it and it's actually handy, but it'll be a bit lengthy to explain here, apart from completely off-topic)

---

### Post by /bin/sh on 2012-01-04
I found that in your link ([[http://en.wikipedia.org/wiki/X86#x86_registers](http://en.wikipedia.org/wiki/X86#x86_registers)) under 32-bit at line 9 it said:
"With the 80486 a floating-point processing unit (FPU) was added, with eight 80-bit wide registers: st(0) to st(7)."
So I guess st(0) to st(7) are registers.

---

### Post by nvteighen on 2012-01-04
> **/bin/sh said:**
> I found that in your link ([[http://en.wikipedia.org/wiki/X86#x86_registers](http://en.wikipedia.org/wiki/X86#x86_registers)) under 32-bit at line 9 it said:
"With the 80486 a floating-point processing unit (FPU) was added, with eight 80-bit wide registers: st(0) to st(7)."
So I guess st(0) to st(7) are registers.

Yay, I fail at reading! Hehe... So, yup, they are then :D

---

### Post by Bachstelze on 2012-01-04
The reason you have never heard of them is that they have been superseded by the mmx registers with the Pentium MMX, which themselves have been superseded by the xmm registers with the Pentium III. Nowadays, compilers will use the xmm registers (if the processor supports them) when compiling code that contains floating-point operations.

```
firas@av104151 ~ % cat test.c 
float foo(float x)
{
        return 2*x;
}
firas@av104151 ~ % gcc -std=c99 -pedantic -Wall -Wextra -m32 -S test.c
firas@av104151 ~ % cat test.s
	.text
.globl _foo
_foo:
	pushl	%ebp
	movl	%esp, %ebp
	subl	$24, %esp
	movss	8(%ebp), %xmm0
	addss	%xmm0, %xmm0
	movss	%xmm0, -12(%ebp)
	flds	-12(%ebp)
	leave
	ret
	.subsections_via_symbols
firas@av104151 ~ % gcc -std=c99 -pedantic -Wall -Wextra -m32 -march=i386 -S test.c
firas@av104151 ~ % cat test.s                                                     
	.text
.globl _foo
_foo:
	pushl	%ebp
	movl	%esp, %ebp
	subl	$8, %esp
	flds	8(%ebp)
	fadd	%st(0), %st
	leave
	ret
	.subsections_via_symbols

```

---

