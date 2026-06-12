---
title: "Compiler/Assembler related questions."
date: 2008-05-24
forum: Programming Talk
---

### Post by Senesence on 2008-05-24
From what I understand, the C compiler (in general) takes a piece of C source code and converts it into machine code that can actually execute. The assembler does the same, doesn't it? I mean in relation to the asm code provided, like the C compiler, it also produces machine code.

My questions:
[LIST=1]
[*]Are the above assumptions correct?
[*]If so, why is assembly usually presented as "faster running"? I mean if we get machine code in both cases, wouldn't it run at the same speed as C code?
[/LIST]

TIA.

---

### Post by CptPicard on 2008-05-24
> **Senesence said:**
> 
[*]Are the above assumptions correct?


Yes.

> 
[*]If so, why is assembly usually presented as "faster running"? I mean if we get machine code in both cases, wouldn't it run at the same speed as C code?


*Sometimes* you are able to write faster code by hand-crafting your assembly if you know there is some specific trick to it the compiler is not aware of. Most of the time these days the compiler is so good that it actually is able to produce more consistently optimized code than a human would.

The "rrrawwrr I handcode all my assembler as it's faster!!1" is a speed kiddy cult thing.

---

### Post by pmasiar on 2008-05-24
1) yes

2) every compiler created executable code. Difference is in details - how much optimization efforts were sunked to it, what were the goals, etc. But solving a problem in ASM does not automagically guarantee better performance: clueless ASM coder can create solution which performs worse than good Python code.

---

### Post by LaRoza on 2008-05-24
> **Senesence said:**
> From what I understand, the C compiler (in general) takes a piece of C source code and converts it into machine code that can actually execute. The assembler does the same, doesn't it? I mean in relation to the asm code provided, like the C compiler, it also produces machine code.



gcc actually converts the C into assembly and assembles and links that, but otherwise, you are correct.

---

### Post by maximinus_uk on 2008-05-24
Yes, you are correct.

When you write C code, the compiler turns that into machine code. However, with assembly, there is a direct mapping between your code and the machine code produced, for example to turn the asm

```
mov bx, ax

```

into machine code is trivial, whereas to turn C code into machine code is *not* a trivial task.

It used to be that years ago a programmer could write better machine code than the compiler but nowadays is this is almost always not true. Firstly, all the clever tricks that we may have used as a coder in the past are now known by the compiler, and the complexity of the CPU's has increased.

When I last did mixed C/assembler programming (a 3d game back in the early 90's) the general rule of thumb was that if you were clever about it, you might get a 10% speed improvement over C by hard coding a particular inline function in asm. But by far the better way to get a speed increase is to use a better algorithm. This is even more true nowadays, which is why I stick to Python for the small stuff and LISP for the serious work, since they allow you to express an algorithm much more elegantly.

---

### Post by Bichromat on 2008-05-25
You can see the assembly code gcc produces :
```

$ gcc -S my_code.c

```
creates a my_code.s.

---

### Post by LaRoza on 2008-05-25
> **Bichromat said:**
> You can see the assembly code gcc produces :
```

$ gcc -S my_code.c

```
creates a my_code.s.

Remember, that assembly is written for the machine to read, not humans.

---

