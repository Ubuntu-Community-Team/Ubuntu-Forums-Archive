---
title: "[SOLVED] gfortran 4.2.1-5ubuntu4 generates bad code"
date: 2007-11-26
forum: Programming Talk
---

### Post by bmetz on 2007-11-26
It is many years since I last tried to use FORTRAN.  I am now trying
to use gfortran to work through some examples from a book.
Unfortunately I am being hampered by a bug in gfortran

[FONT="Courier New"]
$ gfortran --version
GNU Fortran (GCC) 4.2.1 (Ubuntu 4.2.1-5ubuntu4)
Copyright (C) 2007 Free Software Foundation, Inc.
[/FONT]

Is the following a known bug in gfortran ?

If I compile the following, all appears to be o.k.:

[FONT="Courier New"]
      Subroutine fn(f, b, y, m)
      dimension f(m,m)
      y = b / f(1,1)
      return
      end
[/FONT]

However, change it to this:

[FONT="Courier New"]
      Subroutine fn(f, b, y, m)
      dimension f(m,m), b(m), y(m)
      y(l) = b(1) / f(1,1)
      return
      end
[/FONT]

and the generated code is wrong.

The key point is the treatment of the index of y(1).  It appears that
it is intended to be copied to the local stack frame and used later.
In the (second) version above, the copying to the local stack frame is
skipped in the generated code.

The following assembler code is generated from the second version by
    $ gfortran -S subs2.f
The instruction which references an uninitialised part of the stack is
indicated by "*******".  It appears that the code would be correct if
$1 (i.e. the index of y(1)) had been previously stored in -4(%ebp).

[FONT="Courier New"]
        .file   "subs2.f"
        .text
.globl fn_
        .type   fn_, @function
fn_:
        pushl   %ebp
        movl    %esp, %ebp
        subl    $24, %esp
        movl    20(%ebp), %eax
        movl    (%eax), %eax
        testl   %eax, %eax
        js      .L2
        jmp     .L4
.L2:
.L4:
        movl    20(%ebp), %eax
        movl    (%eax), %eax
        testl   %eax, %eax
        js      .L5
        jmp     .L7
.L5:
.L7:
        movl    20(%ebp), %eax
        movl    (%eax), %eax
        movl    %eax, -20(%ebp)
        cmpl    $0, -20(%ebp)
        js      .L8
        movl    -20(%ebp), %eax
        movl    %eax, -24(%ebp)
        jmp     .L10
.L8:
        movl    $0, -24(%ebp)
.L10:
        movl    -24(%ebp), %eax
        movl    %eax, -20(%ebp)
        movl    20(%ebp), %eax
        movl    (%eax), %eax
        imull   -20(%ebp), %eax
        testl   %eax, %eax
        js      .L11
        jmp     .L13
.L11:
.L13:
        movl    -20(%ebp), %edx
        notl    %edx
        movl    -4(%ebp), %ecx     *******
        subl    $1, %ecx
        movl    12(%ebp), %eax
        flds    (%eax)
        movl    -20(%ebp), %eax
        addl    $1, %eax
        leal    (%eax,%edx), %edx
        movl    8(%ebp), %eax
        flds    (%eax,%edx,4)
        fdivrp  %st, %st(1)
        movl    16(%ebp), %eax
        fstps   (%eax,%ecx,4)
        leave
        ret
        .size   fn_, .-fn_
        .ident  "GCC: (GNU) 4.2.1 (Ubuntu 4.2.1-5ubuntu4)"
        .section        .note.GNU-stack,"",@progbits
[/FONT]

---

### Post by bmetz on 2007-11-26
PLease ignore the message.  It was resolved by the gfortran bugzilla.  There is actually a typo in the code, which has y(l) instead of the correct y(1).

---

### Post by LaRoza on 2007-11-26
> **bmetz said:**
> PLease ignore the message.  It was resolved by the gfortran bugzilla.  There is actually a typo in the code, which has y(l) instead of the correct y(1).

You should mark it as solved. Glad it is fixed.

---

### Post by bmetz on 2007-11-27
Thanks for the tip.  I wasn't aware that I could mark the thread as solved.

---

### Post by LaRoza on 2007-11-27
> **bmetz said:**
> Thanks for the tip.  I wasn't aware that I could mark the thread as solved.

It is a somewhat hidden feature, but really helps those browsing the forum. I use gfortran, and was somewhat alarmed at the title.

---

