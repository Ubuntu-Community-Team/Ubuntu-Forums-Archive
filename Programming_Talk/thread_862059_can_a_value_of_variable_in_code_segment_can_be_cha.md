---
title: "can a value of variable in code segment can be changed"
date: 2008-07-17
forum: Programming Talk
---

### Post by me_himanshu on 2008-07-17
int main(void)
{

const int num = 5;
int *ptr = (int *) &num;
*ptr = 6;
printf("\n value at num is %d and *ptr %d",num , *ptr);
printf("\n ptr address %u : num address %u",ptr,&num);

return 0;

}


when i run the above piece of code in gcc i get the value of num=6

If  num  is const, so it should go in the code segment, and the value of a variable in the code segment cannot be changed...then why the value of num is being changed????

---

### Post by Zugzwang on 2008-07-17
> **me_himanshu said:**
> 
when i run the above piece of code in gcc i get the value of num=6

If  num  is const, so it should go in the code segment, and the value of a variable in the code segment cannot be changed...then why the value of num is being changed????

Because it isn't in the code segment. Depending on the implementation of the compiler it can either be on the stack (if "const" doesn't affect variable placement) of to the data/.text/.bss/whatever segment (as this happens normally with static variables).

EDIT: Why don't you just run the debugger and have a look at where it is placed?

---

### Post by Tony Flury on 2008-07-17
The key word const in your decalaration just says to the compiler that the variable num should not be used as the target for an assignment (so you can't do num = 6). The actual data in memory (whether it is on the heap/stack etc) does not get tagged as const (it is entirely a compiler instruction). (i.e. a const variable and a non-const variable will look exactly the same in memory during program run time if they store the same value).

When it comes to pointers, The compiler does not track where a pointer points to during the program run time (and in a large program in could change over the life time of the execution, and some of those maybe not be const), and therefore you as a programmer cannot assume that const data wont change if you access it via pointers as you have done.

---

### Post by Zugzwang on 2008-07-18
Hey Tony, the OP's question was in fact why there is no segmentation fault thrown when executing the code since the regions in memory in which the code is stored is meant to be immutable. So it's just a technical question.

Actually, I tried finding out where it is stored. The C example provided compiled to the following source (using gcc):

```

        .file   "test.c"
        .section        .rodata
        .align 4
.LC0:
        .string "\n value at num is %d and *ptr %d"
        .align 4
.LC1:
        .string "\n ptr address %u : num address %u"
        .text
.globl main
        .type   main, @function
main:
        leal    4(%esp), %ecx
        andl    $-16, %esp
        pushl   -4(%ecx)
        pushl   %ebp
        movl    %esp, %ebp
        pushl   %ecx
        subl    $36, %esp
        movl    $5, -12(%ebp)
        leal    -12(%ebp), %eax
        movl    %eax, -8(%ebp)
        movl    -8(%ebp), %eax
        movl    $6, (%eax)
        movl    -8(%ebp), %eax
        movl    (%eax), %eax
        movl    -12(%ebp), %edx
        movl    %eax, 8(%esp)
        movl    %edx, 4(%esp)
        movl    $.LC0, (%esp)
        call    printf
        leal    -12(%ebp), %eax
        movl    %eax, 8(%esp)
        movl    -8(%ebp), %eax
        movl    %eax, 4(%esp)
        movl    $.LC1, (%esp)
        call    printf
        movl    $0, %eax
        addl    $36, %esp
        popl    %ecx
        popl    %ebp
        leal    -4(%ecx), %esp
        ret
        .size   main, .-main
        .ident  "GCC: (GNU) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)"
        .section        .note.GNU-stack,"",@progbits

```

So you can see (provided that you've got enough knowledge of X86 assember)  that the "num" variable is pushed onto the stack and is therefore mutable. The instruction "movl    $5, -12(%ebp)" is the one that initialises the variable and it uses the "ebp" register which is used for stack access.

---

