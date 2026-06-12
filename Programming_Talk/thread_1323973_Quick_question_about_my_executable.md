---
title: "Quick question about my executable"
date: 2009-11-12
forum: Programming Talk
---

### Post by SouthOfHell on 2009-11-12
Hey i compiled my program (a C program) with g++

at the terminal i ran:

```
file myprogram
```

and the output was:

```
myprogram: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, not stripped
```

What does it mean by "not stripped"?

---

### Post by Arndt on 2009-11-12
> **SouthOfHell said:**
> Hey i compiled my program (a C program) with g++

at the terminal i ran:

```
file myprogram
```

and the output was:

```
myprogram: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, not stripped
```

What does it mean by "not stripped"?

It means that all symbols needed while linking the program (associations of names with addresses) are still present. That's necessary if you want to use a debugger on the program, but otherwise not. Stripping is an explicit operation, which the program 'strip' can do. (Maybe the linker can be told directly to strip symbols, too.)

---

### Post by SouthOfHell on 2009-11-12
Is there any reason why a binary should be stripped of its symbols once the debugging is no longer needed?

---

### Post by Arndt on 2009-11-13
> **SouthOfHell said:**
> Is there any reason why a binary should be stripped of its symbols once the debugging is no longer needed?

The original reason is that the executable becomes smaller. That should hardly be an issue nowadays. Another reason is that the code becomes harder to reverse-engineer.

---

