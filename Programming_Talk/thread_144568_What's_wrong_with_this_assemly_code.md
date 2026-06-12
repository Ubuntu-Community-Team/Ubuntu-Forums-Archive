---
title: "What's wrong with this assemly code?"
date: 2006-03-14
forum: Programming Talk
---

### Post by Eric_T on 2006-03-14
I'm new to assembly language, so pardon my ignorance...
I'm trying to compare two values, let's call them x and y, and if y>x, set x=y.
Here's what I'm doing
```

asm("movl %eax, y\n\t"
    "movl %ebx, x\n\t"
    "cmpl %eax, %ebx\n\t"
    "cmovg %ebx, %eax\n\t"
    "movl %ebx,x");

```
When I try to compile it I get " undefined reference to 'a' ".

---

### Post by 1000i1 on 2006-03-14
I supose you're writing this inside a c file, the problem is that when in a line you put a variable then register name need two "%" so %eax would be %%eax, but that's not the onlye problem I think, you can't put variables this way you should do it like:
```

int x, y;
asm("movl $1, %%eax\n\t"
    "movl $2, %%ebx\n\t"
    "cmpl %eax, %ebx\n\t"
    "cmovg %ebx, %eax\n\t"
    "movl %%ebx, %0
    :"=g" (y) //Out variable
    :"g" x , y //in variable
    : "memory");

```
So that your out variables go from $0...$n and your in variables from $n+1...$k. You've got in x as $1, in y as $2, and out y as $0. I don't know if that code does what you want to, or if it works exactly this way, I'm telling you what I can remember. Hope this helps.

---

### Post by Eric_T on 2006-03-14
Sorry, forgot to tell that it's inline assembly, yes...
Ok, I think I understand your main point, but the code still doesn't compile. After rooting out some minor bugs in your code this is what I got:
```

asm("movl %1, %%eax\n\t"
    "movl %2, %%ebx\n\t"
    "cmpl %eax, %ebx\n\t"
    "cmovg %ebx, %eax\n\t"
    "movl %%ebx, %0"
    :"=r" (x)
    :"r"(x),"r"(y)
    : "memory");

```

Now I get:  " invalid 'asm': operand number missing after %-letter ".

---

### Post by 1000i1 on 2006-03-14
That's because you have %1, where you should have $1, and so on. Variables go preceeded by $ not %.

---

### Post by Eric_T on 2006-03-15
Still get the same error message... this one is really starting to annoy me!

---

### Post by supirman on 2006-03-15
The operand numbers should be prefixed with %, not $.  $ implies an immediate operand.   ALL REGISTER operands need %%, to help gcc distinguish between a numbered operand and a register operand.

Try this
```

asm("movl %1, %%eax\n\t"
    "movl %2, %%ebx\n\t"
    "cmpl %%eax, %%ebx\n\t"
    "cmovg %%ebx, %%eax\n\t"
    "movl %%eax, %0"
    :"=g"(x) //Out variable
    :"g"(x) , "g"(y) //in variable
    : "memory");

```
 or you can shorten by specifying that x,y should be registers eax,ebx like

```

asm("cmpl %%eax, %%ebx\n\t"
    "cmovg %%ebx, %%eax\n\t"
    "movl %%eax, %0"
    :"=g"(x) //Out variable
    :"a"(x) , "b"(y) //in variable
    : "memory");

```


If you're using gcc (which I assume you are), then the syntax is AT&T style, so it's "op src,dest".

---

### Post by Eric_T on 2006-03-18
That worked, supirman, thanks!

---

### Post by Eric_T on 2006-03-18
Ok, as I said earlier, please pardon my ignorance...now the code works for ints and floats, but not for doubles?

---

### Post by supirman on 2006-03-19
[http://www.math.grin.edu/~walker/courses/211.fa01/pentium-3-manual-instructions.pdf](http://www.math.grin.edu/~walker/courses/211.fa01/pentium-3-manual-instructions.pdf)

CMPSD intruction, page 97.  Doubles are special.

---

