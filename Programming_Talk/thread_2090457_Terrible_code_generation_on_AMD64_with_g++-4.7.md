---
title: "Terrible code generation on AMD64 with g++-4.7?"
date: 2012-12-02
forum: Programming Talk
---

### Post by DonkeySalami on 2012-12-02
Dear everyone,

today I looked at the code generated for the function
```
#include <array>
void test(std::array<int, 3> &a)
{
        for(int &i: a)
                i += 123;
}
```
by g++4.6 on Intel IA32 and g++4.7 on AMD64, using the official Ubuntu packages. The results were quite surprising to me. On IA32 I get the very sensible looking:
```
_Z4testRSt5arrayIiLj3EE:
.LFB256:
        .cfi_startproc
        movl    4(%esp), %eax
        leal    12(%eax), %edx
        .p2align 4,,7
        .p2align 3
.L2:
        addl    $123, (%eax)
        addl    $4, %eax
        cmpl    %eax, %edx
        jne     .L2
        rep
        ret

```
I just wonder why it doesn't unroll the loop, but apart from that it looks fine. In contrast on AMD64 I get this - the only way I can call it - monster:
```
_Z4testRSt5arrayIiLm3EE:
.LFB886:
        .cfi_startproc
        leaq    12(%rdi), %r8
        leaq    4(%rdi), %rdx
        movq    %rdi, %rcx
        andl    $15, %ecx
        movq    %rdi, %rax
        movq    %r8, %rsi
        shrq    $2, %rcx
        subq    %rdx, %rsi
        negq    %rcx
        shrq    $2, %rsi
        andl    $3, %ecx
        addq    $1, %rsi
        cmpq    %rsi, %rcx
        cmova   %rsi, %rcx
        cmpq    $4, %rsi
        cmovbe  %rsi, %rcx
        testq   %rcx, %rcx
        je      .L4
        xorl    %edx, %edx
        .p2align 4,,10
        .p2align 3
.L5:
        addq    $1, %rdx
        addl    $123, (%rax)
        addq    $4, %rax
        cmpq    %rdx, %rcx
        ja      .L5
        cmpq    %rcx, %rsi
        je      .L1
.L4:
        movq    %rsi, %r11
        subq    %rcx, %r11
        movq    %r11, %r9
        shrq    $2, %r9
        leaq    0(,%r9,4), %r10
        testq   %r10, %r10
        je      .L10
        movdqa  .LC0(%rip), %xmm1
        leaq    (%rdi,%rcx,4), %rsi
        xorl    %edx, %edx
        xorl    %ecx, %ecx
        .p2align 4,,10
        .p2align 3
.L8:
        movdqa  (%rsi,%rdx), %xmm0
        addq    $1, %rcx
        paddd   %xmm1, %xmm0
        movdqa  %xmm0, (%rsi,%rdx)
        addq    $16, %rdx
        cmpq    %r9, %rcx
        jb      .L8
        cmpq    %r10, %r11
        leaq    (%rax,%r10,4), %rax
        je      .L1
        .p2align 4,,10
        .p2align 3
.L10:
        addl    $123, (%rax)
        addq    $4, %rax
        cmpq    %rax, %r8
        jne     .L10
.L1:
        rep
        ret
        .cfi_endproc
.LFE886:
        .size   _Z4testRSt5arrayIiLm3EE, .-_Z4testRSt5arrayIiLm3EE
        .section        .rodata.cst16,"aM",@progbits,16
        .align 16
.LC0:
        .long   123
        .long   123
        .long   123
        .long   123

```
What the hell is happening here? Does it fail to do optimization from the start or is it trying to do something very clever? Is this a known bug / if not should it be reported?

Any insights highly appreciated.

---

### Post by Bachstelze on 2012-12-02
You haven't given your compilation command (in particular, optimisation flags).

---

### Post by DonkeySalami on 2012-12-02
Yes, sorry. In both cases:
```
g++ -Wall -O3 -std=c++0x -S test.C
```

---

### Post by DonkeySalami on 2012-12-02
Alright, a little bit of more testing on AMD64: With the compiler options above the function
```
void test(int *a)
{
        int *end = a + 3;
        for(int *act = a; act < end; ++act) {
                *act += 123;
        }
}
```
gives the probably perfect
```
_Z4testPi:
.LFB886:
        .cfi_startproc
        addl    $123, (%rdi)
        addl    $123, 4(%rdi)
        addl    $123, 8(%rdi)
        ret
        .cfi_endproc
```
Which is all the more mysterious, since the template code in /usr/include/c++/4.7.2/array seems to do exactly that...?

---

### Post by MadCow108 on 2012-12-02
seems like the autovectorizer goes mad here
all that junk code you see is alignment, aliasing and stride checks
probably something wrong in the cost model, for an array of size 3 it should not try to autovectorize

compile with -fno-tree-vectorize gives you this much more sensibel result:
```
   0:	48 8d 47 0c          	lea    0xc(%rdi),%rax
   4:	48 39 c7             	cmp    %rax,%rdi
   7:	74 13                	je     1c <_Z4testRSt5arrayIiLm3EE+0x1c>
   9:	0f 1f 80 00 00 00 00 	nopl   0x0(%rax)
  10:	83 07 7b             	addl   $0x7b,(%rdi)
  13:	48 83 c7 04          	add    $0x4,%rdi
  17:	48 39 f8             	cmp    %rdi,%rax
  1a:	75 f4                	jne    10 <_Z4testRSt5arrayIiLm3EE+0x10>
  1c:	f3 c3                	repz retq 

```

and with -funroll-loop the perfect:
```
0000000000000000 <_Z4testRSt5arrayIiLm3EE>:
   0:	83 07 7b             	addl   $0x7b,(%rdi)
   3:	83 47 04 7b          	addl   $0x7b,0x4(%rdi)
   7:	83 47 08 7b          	addl   $0x7b,0x8(%rdi)
   b:	c3                   	retq   

```

you should do some benchmarking if its really slower and file bug report

---

### Post by trent.josephsen on 2012-12-02
Edit: nvm, MadCow knows a lot more than I do

---

### Post by MadCow108 on 2012-12-02
as a workaround you can disable the vectorizer just for the functions you know the array is very small:

```
__attribute__((optimize("-fno-tree-vectorize")))
void test(std::array<int, 3> &a) 
{
        for(int &i: a)
                i += 123;
}

```

it can also be done with pragmas instead of __attribute__

interestingly it seems to not get that the loop iteration is constant when vectorizing
```
-ftree-vectorizer-verbose=5
4: Profitability threshold is 4 loop iterations.
4: LOOP VECTORIZED.
```

but when unrolling it knows it are only 3 iterations, definitely looks like a bug
possibly its already fixed: [http://gcc.gnu.org/ml/gcc-patches/2012-10/msg00512.html](http://gcc.gnu.org/ml/gcc-patches/2012-10/msg00512.html)

---

### Post by DonkeySalami on 2012-12-02
Thank you very much!

I was expecting something like this, seeing three versions of the loop, one with SSE instructions. For now, I will turn off the vectorizer for my whole application, because given my use cases I can not see how the long code would ever be advantageous. I'm not doing number crunching. ;)

---

### Post by DonkeySalami on 2012-12-03
Not that it matters a lot, but it seems that the g++ optimizer has problems with templated code. For example:
```
#include <array>
#include <algorithm>

bool test1(const int *a)
{
        const int *end = a + 3;
        for(const int *act = a; act < end; ++act) {
                if(*act == 123)
                        return true;
        }
        return false;
}

bool test2(const std::array<int,3> &a)
{
        return std::any_of(a.begin(), a.end(), [](int i){ return i == 123; });
}
```
Compiled with the options given above on IA32 I get for test1() the very nicely optimized
```
_Z5test1PKi:
.LFB2666:
        .cfi_startproc
        movl    4(%esp), %eax
        cmpl    $123, (%eax)
        je      .L4
        cmpl    $123, 4(%eax)
        je      .L4
        cmpl    $123, 8(%eax)
        sete    %al
        ret
        .p2align 4,,7
        .p2align 3
.L4:
        movl    $1, %eax
        ret
        .cfi_endproc
```
But for test2(), which should after template expansion actually give exactly the same, I get the not terrible, but much worse:
```
_Z5test2RKSt5arrayIiLj3EE:
.LFB2667:
        .cfi_startproc
        movl    4(%esp), %eax
        cmpl    $123, (%eax)
        leal    12(%eax), %edx
        je      .L32
        cmpl    $123, 4(%eax)
        leal    4(%eax), %ecx
        je      .L31
        leal    8(%eax), %ecx
        xorl    %eax, %eax
        cmpl    $123, (%ecx)
        je      .L31
        rep
        ret
        .p2align 4,,7
        .p2align 3
.L31:
        cmpl    %ecx, %edx
        setne   %al
        ret
        .p2align 4,,7
        .p2align 3
.L32:
        cmpl    %eax, %edx
        setne   %al
        .p2align 4,,2
        ret
        .cfi_endproc
```
This code is pretty irrational: In line 3 it loads edx with eax+12 and at label .L32 it compares edx with eax. It repeats the same thing with edx and ecx. It looks like using templates does turn the optimizer off?

---

