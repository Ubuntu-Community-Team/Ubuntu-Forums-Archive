---
title: "Inline assembly in C program - GCC"
date: 2016-01-13
forum: Programming Talk
---

### Post by bla9 on 2016-01-13
Hi everyone,
I'm kinda new to the inline ASM inside a c code in GCC (used to do it with MSVC).
I have a code that I'm trying to convert to GCC syntax, which checks if the program is running under vm/vpc or not.
This is a part of the code I have right now:
```

int IsInsideVMWare()
{
    int rc = 0;
    int tmp = 1;
    try
    {
        __asm__(
            "push   %%edx\n\t"
            "push   %%ecx\n\t" // Flag
            "push   %%ebx\n\t"
            "mov    867788104, %%eax\n\t"
            "movl   $0, %%ebx\n\t"
            "movl   $10, %%ecx\n\t"
            "movl    8688, %%edx\n\t"
            "in     %%dx, %%eax\n\t"
            "cmp    %%ebx, 867788104\n\t"
            "mov    %1, %0"
            : "=r" (rc)
            : "r" (tmp));
    }
    catch (...)
    {
        rc = 0;
    }


    return rc;
}


```

I'm trying to insert the ASCII value of 'VMXh' into eax register, then the ASCII value of 'VX' to edx and then  compare the value of ebx to the ASCII value of 'VMXh'. if it's equal, then the variable rc is increasing by 1. Else, it stays 0. At the end, if rc  = 1, it means the program is under VMWare (there is another check for VPC), and if not (rc = 0) the program is running under real OS (or h/w you want to call it when it's not under VMWare).

If I build and run this code, the code::blocks compiles it without any errors, but the program crashes at the beginning and outputs the error > Process returned -1073741819 (0xC0000005).

What am I doing wrong?

Thanks.

---

