---
title: "question about the Intro to Programming article I am reading"
date: 2007-03-24
forum: Programming Talk
---

### Post by billdotson on 2007-03-24
This it the Application to Variables section which is about the application of bytes to variables in programming:

Application to Variables

System memory must be allocated to store variable values; both the compiler and the author of a program must work together to determine how much memory should be allocated for each variable, and this memory is allocated in a sequence of consecutive bytes in memory.

So when a program is run the variables like say for instance the settings for the program are stored in memory and when you first run a program there are bytes at the beginning of the program that tell how to allocate those variables?

---

### Post by Wybiral on 2007-03-24
> **billdotson said:**
> This it the Application to Variables section which is about the application of bytes to variables in programming:

Application to Variables

System memory must be allocated to store variable values; both the compiler and the author of a program must work together to determine how much memory should be allocated for each variable, and this memory is allocated in a sequence of consecutive bytes in memory.

So when a program is run the variables like say for instance the settings for the program are stored in memory and when you first run a program there are bytes at the beginning of the program that tell how to allocate those variables?

What language are you talking about?

---

### Post by billdotson on 2007-03-24
I think it was generalizing about the common way that modern languages do it.

---

### Post by Wybiral on 2007-03-24
Well, in C and C++, static variables are allocated on the stack each time they come into scope and dynamically allocated variables are allocated on the heap and the stack is used to store those heap-variable addresses. In languages like Python... I believe most of the variables are allocated in the heap and the VM manages them all so that they may be allocated and destroyed dynamically without the programmer having to deal with them.

As far as memory and variables being in bytes... What other form can they be in? Computers rely on bytes...

So what was the question exactly?

---

### Post by Mr. C. on 2007-03-24
I don't believe static variables are stack-based.  Static's within a function retain their values after the exiting scope.  Statics are the same as globals, but with hidden name space (eg. they are not exported or visible outside the scope).

Auto-matic variables are allocated on the stack upon scope entry.

Global variables with initializing values are allocated in the data section of the executable (which is loaded in full pages when first referenced).

Memory dynamically allocated via malloc and friends, uses (and extends) the bss section, but this is primarly a function of *nix implementations.

MrC

---

### Post by Wybiral on 2007-03-24
> **Mr. C. said:**
> I don't believe static variables are stack-based.

I didn't mean static as in the static keyword in C and C++, I just meant non-dynamic.

---

### Post by j_g on 2007-03-24
Static variables aren't stack-based in C/C++. He means "local" variables.

---

### Post by Wybiral on 2007-03-24
Yeah, I meant the definition of the word static, not the keyword in C. It was a bad choice of words, lol.

---

### Post by Ramses de Norre on 2007-03-25
> **billdotson said:**
> ...
System memory must be allocated to store variable values; both the compiler and the author of a program must work together to determine how much memory should be allocated for each variable, and this memory is allocated in a sequence of consecutive bytes in memory.

So when a program is run the variables like say for instance the settings for the program are stored in memory and when you first run a program there are bytes at the beginning of the program that tell how to allocate those variables?

No, the text means that when you write the instruction to make a variable in your code (for instance **int a;**) the variable **a** will be stored as a series of consecutive bytes in memory. You can then give the variable a value (**a=6;**) and those bytes will represent the value 6.
You don't actually have to say "Give me 12 bytes of memory", those things are taken care of by abstractions like the different variable types (int, float, long, ...).

---

