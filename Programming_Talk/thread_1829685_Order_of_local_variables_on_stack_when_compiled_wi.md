---
title: "Order of local variables on stack when compiled with -fno-stack-protector"
date: 2011-08-20
forum: Programming Talk
---

### Post by gnometorule on 2011-08-20
When compiling a function that generically looks as follows...

```

tokenfct(char* s){

       char string[16];
       int i;

       (.....)
}

```...then, on the stack, I find the vars in this order (variable on top at lower memory address) -

Without disabling smash protection using the above flag (== expected order):

int
char*

When using the above flag:

char*
int


(1) Ideas? This seems downright odd. 

(2) If you know how to compile w/o smash protection, but still putting the local vars onto the stack in the expected FILO order, kindly advise too.

Both gdb and gcc I'm using are per about a year ago (can pull up v.  numbers if that matters).

---

### Post by gnometorule on 2011-08-21
It's not a result of optimization. To be sure, I recompiled using option -O0 (capital O, zero) which, to my knowledge, disables all optimizations. I haven't built a C compiler yet. I thought that a stack frame should respect FILO order in program functions. Maybe this is not how it's spelled out in more recent versions of the C standard?

As another test, I inverted the order of local variable declarations in the function. This alternative code results in the same C disassembly and, hence, stack frame.

---

### Post by Bachstelze on 2011-08-21
> **gnometorule said:**
> Maybe this is not how it's spelled out in more recent versions of the C standard?


This certainly never was spelled out in any version of the C standard. For all the standard cares, you may just as well not have a stack at all. The stack is an implementation detail. (As a matter of fact, the word "stack" never appears in the standard.)

---

### Post by gnometorule on 2011-08-22
Thanks. I was under the impression that old distros implemented FILO as it appears in the source code. If it's not in the standard, and as the 'I have an answer to any and all questions" person here it seems, you'd know - so thanks for clarifying, BS.

---

