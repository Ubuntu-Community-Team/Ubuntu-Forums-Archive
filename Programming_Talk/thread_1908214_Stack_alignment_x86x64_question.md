---
title: "Stack alignment x86/x64 question"
date: 2012-01-13
forum: Programming Talk
---

### Post by nolag on 2012-01-13
I understand that x86 requires a 16 byte stack alignment for fast use with SSE instructions, but I don't get how GCC does it for a function.  The following is an example (x86-32)

```
int test(){
    int x = 10;
    return x;
}
```

when compiled with -m32 -S produces

```
.cfi_startproc
    pushl    %ebp
    .cfi_def_cfa_offset 8
    .cfi_offset 5, -8
    movl    %esp, %ebp
    .cfi_def_cfa_register 5
    subl    $16, %esp
    movb    $10, -1(%ebp)
    movzbl    -1(%ebp), %eax
    leave
    .cfi_restore 5
    .cfi_def_cfa 4, 4
    ret
    .cfi_endproc
```

I get the subl    $16, %esp what I don't get is that there is a pushl %ebp is a long only 4 bytes, so won't that make the alignment off by 4 bytes?  Also the arguments in other functions don't seem to be taken into account (similar pushl).

I am curious because I am making a compiler, and I want to be able to use SSE instructions in the future.

Thanks in advance to any help you can provide.

---

### Post by Bachstelze on 2012-01-13
As I understand it, 16-bit alignment of esp is only required at function calls. Since your function does not call anything, 16-bit alignment is not required. Compare with:

```
firas@itsuki ~ % cat test.c 
void bar(void);

int test(void)
{
        int x = 10;
        bar();
        return x;
}

firas@itsuki ~ % gcc -std=c99 -pedantic -Wall -Wextra -m32 -S test.c
firas@itsuki ~ % cat test.s                                         
        .file   "test.c"
        .text
        .globl  test
        .type   test, @function
test:
.LFB0:
        .cfi_startproc
        pushl   %ebp
        .cfi_def_cfa_offset 8
        .cfi_offset 5, -8
        movl    %esp, %ebp
        .cfi_def_cfa_register 5
        subl    $24, %esp
        movl    $10, -12(%ebp)
        call    bar
        movl    -12(%ebp), %eax
        leave
        .cfi_restore 5
        .cfi_def_cfa 4, 4
        ret
        .cfi_endproc
.LFE0:
        .size   test, .-test
        .ident  "GCC: (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1"
        .section        .note.GNU-stack,"",@progbits

```

24 bytes plus saved ebp and return address is 32.

---

### Post by nolag on 2012-01-13
Thanks for the quick reply :D.  If I want to use an SSE instruction in my function then do I need to make sure (for speed) that it is aligned before I execute the instruction?  Also do you know if the stack needs to be aligned, or is it just the variables that are a part of the instruction?

---

