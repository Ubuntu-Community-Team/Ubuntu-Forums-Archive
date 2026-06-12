---
title: "GDB doesn't stop on conditional breakpoint"
date: 2011-12-21
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2011-12-21
I'm debugging a program which has hundreds of printf calls.
At some point it prints "APP GameDLLInit". I want to set breakpoint there.

I tried
```

(gdb) break printf
Breakpoint 1, __printf (format=0x837ffec "PID: %i\n") at printf.c:29
29	printf.c: No such file or directory.
	in printf.c
.....
.....
<breakpoint triggered here>
(gdb) cond 1 ( strncmp(format,"APP GameDLLInit",15) == 0 )
(gdb) continue

```

But gdb just keeps going. The string is printed out as if there was no breakpoint. Why doesn't gdb stop?
All I want is a stack trace from where this string is printed.

Thank you

---

### Post by Arndt on 2011-12-22
> **crazyfuturamanoob said:**
> I'm debugging a program which has hundreds of printf calls.
At some point it prints "APP GameDLLInit". I want to set breakpoint there.

I tried
```

(gdb) break printf
Breakpoint 1, __printf (format=0x837ffec "PID: %i\n") at printf.c:29
29	printf.c: No such file or directory.
	in printf.c
.....
.....
<breakpoint triggered here>
(gdb) cond 1 ( strncmp(format,"APP GameDLLInit",15) == 0 )
(gdb) continue

```

But gdb just keeps going. The string is printed out as if there was no breakpoint. Why doesn't gdb stop?
All I want is a stack trace from where this string is printed.

Thank you

I don't know much about it, but with a test program, I noticed that not all printf calls in the source code go through the __printf function:

```
#include <stdlib.h>
#include <stdio.h>

int main()
{
  printf("hopp");
  printf(" hej\n");

  printf("hopp");
  printf(" hej\n");

  return 0;
}

```

The "hopp" strings go through __printf, but the others, note that they end with a newline, go through _IO_puts (I found that out by single-stepping into the call). So try putting a breakpoint on that function as well.

---

### Post by Bachstelze on 2011-12-22
Not 100% sure but I don't think you can use function calls in conditionals in gdb.

---

### Post by Arndt on 2011-12-22
> **Bachstelze said:**
> Not 100% sure but I don't think you can use function calls in conditionals in gdb.

What happens if you try it out?

---

### Post by Bachstelze on 2011-12-22
> **Arndt said:**
> What happens if you try it out?

I'm too lazy to do it right now, but from past experience, when you enter an invalid condition, gdb just does nothing and ignores the breakpoint.

---

