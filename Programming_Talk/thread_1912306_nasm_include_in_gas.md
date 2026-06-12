---
title: "nasm include in gas"
date: 2012-01-20
forum: Programming Talk
---

### Post by /bin/sh on 2012-01-20
Here is my problem:

file1.c:
```

main ()
{
  asm (
    ".intel_syntax\n"
    "%include "file2.asm"\n"
    ".att_syntax\n"
    "call _start"
  );
}

```

file2.asm:
```

section .data

string:    db 'Hey!!!', 10
string_len:    equ $-string

section .text

global _start

_start:
  mov eax, 4
  mov ebx, 1
  mov ecx, string
  mov edx, string_len
  int 80h

  mov eax, 1
  mov ebx, 0
  int 80h

```

Then I compile it:
```

gcc file1.c -o file1

```

output:
```

Assembler messages:
Error: junk at end of line, first unrecognized character is `%'

```

HUH!!!

---

### Post by Zugzwang on 2012-01-20
The keyword ".intel_syntax" only means that the x86/x64 commands to follow are assumed to be in Intel syntax. For assembler control commands such as "include", you still have to use the Gnu Assembler's syntax. 

The equivalent to "%include" in gas is ".include": [http://tigcc.ticalc.org/doc/gnuasm.html#SEC97](http://tigcc.ticalc.org/doc/gnuasm.html#SEC97)

However, you should better not assume that the gnu assembler is able to use NASM's control command syntax in your .asm file.

---

### Post by /bin/sh on 2012-01-20
Is there a way to include a file as intel syntax type?

---

### Post by Zugzwang on 2012-01-20
Erm, you just did?

"Intel Syntax" refers to the syntax of the x86/x64 processor commands, and those should be in in intel syntax in the way you do it.

You can't use many assembler directives in inline assembly anyway. For example, your "section" commands cannot be used in inline assembly as it makes no sense here.

The proper way is to use NASM for your assembly files and then linking against the objects created using NASM.

---

