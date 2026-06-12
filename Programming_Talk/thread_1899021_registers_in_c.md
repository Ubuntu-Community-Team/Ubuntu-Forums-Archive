---
title: "registers in c"
date: 2011-12-22
forum: Programming Talk
---

### Post by /bin/sh on 2011-12-22
How do I know which is which in r1 r2 r3 ... ?
I am making both c and assembly files in my project and I need to know if r1 is asm("ah"); and r2 is asm("al"); or something else.
And do I need to use the register type before each register:
```

register r1;

```

---

### Post by ofnuts on 2011-12-22
> **/bin/sh said:**
> How do I know which is which in r1 r2 r3 ... ?
I am making both c and assembly files in my project and I need to know if r1 is asm("ah"); and r2 is asm("al"); or something else.
And do I need to use the register type before each register:
```

register r1;

```"register" in C is just a hint that the variable should remain in a register. But modern compiler plain ignore it, they usually know better. "register" isn't a type, it's a type modifier., the real  syntax would be "register int x;".

Some calling conventions use some registers to pass variables (but none supported by GCC it seems).

Your ASM code should retrieve parameters from the stack, see [http://en.wikipedia.org/wiki/X86_calling_conventions](http://en.wikipedia.org/wiki/X86_calling_conventions)

---

### Post by Bachstelze on 2011-12-23
More precisely, the C standard says this about [font=monospace]register[/font]:

> 6.7.1 Storage-class specifiers

Constraints

4	A declaration of an identifier for an object with storage-class specifier [font=monospace]register[/font] suggests that access to the object be as fast as possible. The extent to which such suggestions are effective is implementation-defined.

---

### Post by Arndt on 2011-12-23
> **/bin/sh said:**
> How do I know which is which in r1 r2 r3 ... ?
I am making both c and assembly files in my project and I need to know if r1 is asm("ah"); and r2 is asm("al"); or something else.
And do I need to use the register type before each register:
```

register r1;

```

Could this be of interest? [http://ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html#s5](http://ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html#s5)

---

