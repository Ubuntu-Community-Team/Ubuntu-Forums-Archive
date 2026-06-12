---
title: "[C++] Const int question"
date: 2011-01-08
forum: Programming Talk
---

### Post by t1497f35 on 2011-01-08
Hi folks,
In a [book]("http://www.starstonesoftware.com/OpenGL/") the author uses **#define** in C++ source code instead of **const int** to define an int that doesn't change because he says **const int** is evaluated at runtime, so** #define** makes for fewer CPU cycles at app start. Is it true?

---

### Post by NovaAesa on 2011-01-08
That would depend on both the target platform and the amount of optimization you tell the compiler to use.

---

### Post by t1497f35 on 2011-01-08
Well, say on a typical x86/x86_64 desktop Linux computer compiled with -O2 with a recent gcc compiler.

---

### Post by worksofcraft on 2011-01-08
Well conceptually speaking the book is correct:

The #define is done by a pre-processor, so the value is inserted as an immediate operand into instructions that compiler generates. OTOH the "const int" occupies a memory location (you can take it's address) and so in theory the processor must first read the address from it's instruction and then fetch the value from that memory location before it can be used.

However in theory by telling the compiler that it is const and assuming the compiler does know what value it has... then it should be clever enough to substitute the known value as an immediate operand.

OTOH, Personally I would use enum to define a symbolic constant value :D

---

### Post by MadCow108 on 2011-01-08
> **worksofcraft said:**
> The #define is done by a pre-processor, so the value is inserted as an immediate operand into instructions that compiler generates....
Which still requires the computer to fetch the constant from memory even when it is located directly in the expression after preprocessing.
Unless the compiler can use the constant to rewrite the expression into an instruction which does not need the constant, but this can be done for non-define constants too.
example
```

#define A "somevery long string"

// no way to not save this in memory somewhere
my_strstr_with_impl_unknown_to_th_compiler(A, runtimesubstring);

#define B 1 // or (static) const int B = 1
// this can get transformed to c++ which translates directly to machine code
// the 1 does not need to occupy memory
c += B;

```

=> There is no difference with a decent compiler.

---

### Post by NovaAesa on 2011-01-08
The best bet would be to write two simple programs, one using define and one using const int. Then compile both programs to assembly code rather than machine code and see if the two assembly codes are the same/very similar. Then you'll know exactly what the compiler is doing.

I'm agreeing MadCow108, it should make no difference. With const int, you also get the added bonus of also having a symbol that can be used when debugging. And defines can be messy :P

---

### Post by worksofcraft on 2011-01-08
> **MadCow108 said:**
> Which still requires the computer to fetch the constant from memory even when it is located directly in the expression after preprocessing.
...
=> There is no difference with a decent compiler.

It isn't a question of what is better, or what a "good" compiler can do.

The OP wanted to understand what the difference is and while I could talk about l-values and r-values, I agree that looking at the assembler makes it much clearer:

```

extern const int iThing;
#define OTHERTHING 2

int main() {
	int myVar = 0;
// assembler immediate mode operand instruction generated:
//	movl	$0, -4(%rbp)

	myVar += OTHERTHING;
// single immediate operand assembler instruction generated:
//	addl	$2, -4(%rbp)
// see it does NOT need to fetch the address of the 2

	myVar += iThing;
// 2 instructions needed including fetch with address
	movl	iThing(%rip), %eax
	addl	%eax, -4(%rbp)

	return myVar;
}

```

even if there **had been** a single instruction like...
```

       addl      iThing(%rip), -4(%rbp) ; hypothetical

```

It would STILL involve at least one extra memory cycle to get the address of "iThing" instead of just getting the immediate value that it wants to add.

p.s. It becomes much more important when you work with "volatile" variables. Consider two concurrent threads, both incrementing the same variable. If one interrupts the other just between the instructions that fetch the value and store back the new result... meh... whatever, work it out for yourself

---

### Post by t1497f35 on 2011-01-11
> **worksofcraft said:**
> 
p.s. It becomes much more important when you work with "volatile" variables. Consider two concurrent threads, both incrementing the same variable. If one interrupts the other just between the instructions that fetch the value and store back the new result... meh... whatever, work it out for yourself
We're talking about "const int", **not (volatile) const pointers**. And, afaik, one is not supposed to change the value of const (ints) no matter how smart one is and since one is only supposed to read the value of the const (int) - it doesn't matter how many threads read it at a time.

---

### Post by worksofcraft on 2011-01-11
> **t1497f35 said:**
> We're talking about "const int", **not (volatile) const pointers**. And, afaik, one is not supposed to change the value of const (ints) no matter how smart one is and since one is only supposed to read the value of the const (int) - it doesn't matter how many threads read it at a time.

so you don't think you would want to ever add a const int to a volatile one then? :confused:

I'll put it another way then.

A #define is not an [lvalue]("http://en.wikipedia.org/wiki/Value_(computer_science)"). A const int is and it takes extra memory cycles to access one... so answer to your question: What the book said is correct.

---

### Post by t1497f35 on 2011-01-11
> **worksofcraft said:**
> 
I'll put it another way then.

A #define is not an [lvalue]("http://en.wikipedia.org/wiki/Value_%28computer_science%29"). A const int is and it takes extra memory cycles to access one... so answer to your question: What the book said is correct.

Well, turns out that's _**not**_ quite true, not always at least.

I just compared the assembly outputs when using a **const int** vs **#define** and they're equal. The compiler pre-computes the stuff when possible and inserts the result (in this case 122) directly - which is how I thought it _should_ be in the non-sophisticated scenario I was wondering about.

Compiled with "g++ -O2 -S".
```

#include <iostream>

//next line replaced by #define num 117 accordingly
const int num = 117; 

int main() {
    int z = num + 5;
    std::cout << z << std::endl;
    return 0;
}

```Assembly when using **#define**:
```

    .file    "test.cpp"
    .text
    .p2align 4,,15
.globl main
    .type    main, @function
main:
.LFB967:
    .cfi_startproc
    pushl    %ebp
    .cfi_def_cfa_offset 8
    .cfi_offset 5, -8
    movl    %esp, %ebp
    .cfi_def_cfa_register 5
    andl    $-16, %esp
    pushl    %esi
    pushl    %ebx
    subl    $24, %esp
    movl    $122, 4(%esp)
    movl    $_ZSt4cout, (%esp)
    .cfi_escape 0x10,0x3,0x7,0x75,0x0,0x9,0xf0,0x1a,0x38,0x1c
    .cfi_escape 0x10,0x6,0x7,0x75,0x0,0x9,0xf0,0x1a,0x34,0x1c
    call    _ZNSolsEi
    movl    %eax, %ebx
    movl    (%eax), %eax
    movl    -12(%eax), %eax
    movl    124(%ebx,%eax), %esi
    testl    %esi, %esi
    je    .L6
    cmpb    $0, 28(%esi)
    je    .L3
    movzbl    39(%esi), %eax
.L4:
    movsbl    %al, %eax
    movl    %ebx, (%esp)
    movl    %eax, 4(%esp)
    call    _ZNSo3putEc
    movl    %eax, (%esp)
    call    _ZNSo5flushEv
    addl    $24, %esp
    xorl    %eax, %eax
    popl    %ebx
    .cfi_remember_state
    .cfi_restore 3
    popl    %esi
    .cfi_restore 6
    movl    %ebp, %esp
    .cfi_def_cfa_register 4
    popl    %ebp
    .cfi_restore 5
    .cfi_def_cfa_offset 4
    ret
    .p2align 4,,7
    .p2align 3
.L3:
    .cfi_restore_state
    movl    %esi, (%esp)
    call    _ZNKSt5ctypeIcE13_M_widen_initEv
    movl    (%esi), %eax
    movl    $10, 4(%esp)
    movl    %esi, (%esp)
    call    *24(%eax)
    jmp    .L4
.L6:
    call    _ZSt16__throw_bad_castv
    .cfi_endproc
.LFE967:
    .size    main, .-main
    .p2align 4,,15
    .type    _GLOBAL__I_main, @function
_GLOBAL__I_main:
.LFB974:
    .cfi_startproc
    pushl    %ebp
    .cfi_def_cfa_offset 8
    .cfi_offset 5, -8
    movl    %esp, %ebp
    .cfi_def_cfa_register 5
    subl    $24, %esp
    movl    $_ZStL8__ioinit, (%esp)
    call    _ZNSt8ios_base4InitC1Ev
    movl    $__dso_handle, 8(%esp)
    movl    $_ZStL8__ioinit, 4(%esp)
    movl    $_ZNSt8ios_base4InitD1Ev, (%esp)
    call    __cxa_atexit
    leave
    .cfi_restore 5
    .cfi_def_cfa 4, 4
    ret
    .cfi_endproc
.LFE974:
    .size    _GLOBAL__I_main, .-_GLOBAL__I_main
    .section    .ctors,"aw",@progbits
    .align 4
    .long    _GLOBAL__I_main
    .local    _ZStL8__ioinit
    .comm    _ZStL8__ioinit,1,1
    .weakref    _ZL20__gthrw_pthread_oncePiPFvvE,pthread_once
    .weakref    _ZL27__gthrw_pthread_getspecificj,pthread_getspecific
    .weakref    _ZL27__gthrw_pthread_setspecificjPKv,pthread_setspecific
    .weakref    _ZL22__gthrw_pthread_createPmPK14pthread_attr_tPFPvS3_ES3_,pthread_create
    .weakref    _ZL20__gthrw_pthread_joinmPPv,pthread_join
    .weakref    _ZL21__gthrw_pthread_equalmm,pthread_equal
    .weakref    _ZL20__gthrw_pthread_selfv,pthread_self
    .weakref    _ZL22__gthrw_pthread_detachm,pthread_detach
    .weakref    _ZL22__gthrw_pthread_cancelm,pthread_cancel
    .weakref    _ZL19__gthrw_sched_yieldv,sched_yield
    .weakref    _ZL26__gthrw_pthread_mutex_lockP15pthread_mutex_t,pthread_mutex_lock
    .weakref    _ZL29__gthrw_pthread_mutex_trylockP15pthread_mutex_t,pthread_mutex_trylock
    .weakref    _ZL31__gthrw_pthread_mutex_timedlockP15pthread_mutex_tPK8timespec,pthread_mutex_timedlock
    .weakref    _ZL28__gthrw_pthread_mutex_unlockP15pthread_mutex_t,pthread_mutex_unlock
    .weakref    _ZL26__gthrw_pthread_mutex_initP15pthread_mutex_tPK19pthread_mutexattr_t,pthread_mutex_init
    .weakref    _ZL29__gthrw_pthread_mutex_destroyP15pthread_mutex_t,pthread_mutex_destroy
    .weakref    _ZL30__gthrw_pthread_cond_broadcastP14pthread_cond_t,pthread_cond_broadcast
    .weakref    _ZL27__gthrw_pthread_cond_signalP14pthread_cond_t,pthread_cond_signal
    .weakref    _ZL25__gthrw_pthread_cond_waitP14pthread_cond_tP15pthread_mutex_t,pthread_cond_wait
    .weakref    _ZL30__gthrw_pthread_cond_timedwaitP14pthread_cond_tP15pthread_mutex_tPK8timespec,pthread_cond_timedwait
    .weakref    _ZL28__gthrw_pthread_cond_destroyP14pthread_cond_t,pthread_cond_destroy
    .weakref    _ZL26__gthrw_pthread_key_createPjPFvPvE,pthread_key_create
    .weakref    _ZL26__gthrw_pthread_key_deletej,pthread_key_delete
    .weakref    _ZL30__gthrw_pthread_mutexattr_initP19pthread_mutexattr_t,pthread_mutexattr_init
    .weakref    _ZL33__gthrw_pthread_mutexattr_settypeP19pthread_mutexattr_ti,pthread_mutexattr_settype
    .weakref    _ZL33__gthrw_pthread_mutexattr_destroyP19pthread_mutexattr_t,pthread_mutexattr_destroy
    .ident    "GCC: (GNU) 4.5.1 20100924 (Red Hat 4.5.1-4)"
    .section    .note.GNU-stack,"",@progbits


```Assembly when using **const int:**
```

    .file    "test.cpp"
    .text
    .p2align 4,,15
.globl main
    .type    main, @function
main:
.LFB967:
    .cfi_startproc
    pushl    %ebp
    .cfi_def_cfa_offset 8
    .cfi_offset 5, -8
    movl    %esp, %ebp
    .cfi_def_cfa_register 5
    andl    $-16, %esp
    pushl    %esi
    pushl    %ebx
    subl    $24, %esp
    movl    $122, 4(%esp)
    movl    $_ZSt4cout, (%esp)
    .cfi_escape 0x10,0x3,0x7,0x75,0x0,0x9,0xf0,0x1a,0x38,0x1c
    .cfi_escape 0x10,0x6,0x7,0x75,0x0,0x9,0xf0,0x1a,0x34,0x1c
    call    _ZNSolsEi
    movl    %eax, %ebx
    movl    (%eax), %eax
    movl    -12(%eax), %eax
    movl    124(%ebx,%eax), %esi
    testl    %esi, %esi
    je    .L6
    cmpb    $0, 28(%esi)
    je    .L3
    movzbl    39(%esi), %eax
.L4:
    movsbl    %al, %eax
    movl    %ebx, (%esp)
    movl    %eax, 4(%esp)
    call    _ZNSo3putEc
    movl    %eax, (%esp)
    call    _ZNSo5flushEv
    addl    $24, %esp
    xorl    %eax, %eax
    popl    %ebx
    .cfi_remember_state
    .cfi_restore 3
    popl    %esi
    .cfi_restore 6
    movl    %ebp, %esp
    .cfi_def_cfa_register 4
    popl    %ebp
    .cfi_restore 5
    .cfi_def_cfa_offset 4
    ret
    .p2align 4,,7
    .p2align 3
.L3:
    .cfi_restore_state
    movl    %esi, (%esp)
    call    _ZNKSt5ctypeIcE13_M_widen_initEv
    movl    (%esi), %eax
    movl    $10, 4(%esp)
    movl    %esi, (%esp)
    call    *24(%eax)
    jmp    .L4
.L6:
    call    _ZSt16__throw_bad_castv
    .cfi_endproc
.LFE967:
    .size    main, .-main
    .p2align 4,,15
    .type    _GLOBAL__I_main, @function
_GLOBAL__I_main:
.LFB974:
    .cfi_startproc
    pushl    %ebp
    .cfi_def_cfa_offset 8
    .cfi_offset 5, -8
    movl    %esp, %ebp
    .cfi_def_cfa_register 5
    subl    $24, %esp
    movl    $_ZStL8__ioinit, (%esp)
    call    _ZNSt8ios_base4InitC1Ev
    movl    $__dso_handle, 8(%esp)
    movl    $_ZStL8__ioinit, 4(%esp)
    movl    $_ZNSt8ios_base4InitD1Ev, (%esp)
    call    __cxa_atexit
    leave
    .cfi_restore 5
    .cfi_def_cfa 4, 4
    ret
    .cfi_endproc
.LFE974:
    .size    _GLOBAL__I_main, .-_GLOBAL__I_main
    .section    .ctors,"aw",@progbits
    .align 4
    .long    _GLOBAL__I_main
    .local    _ZStL8__ioinit
    .comm    _ZStL8__ioinit,1,1
    .weakref    _ZL20__gthrw_pthread_oncePiPFvvE,pthread_once
    .weakref    _ZL27__gthrw_pthread_getspecificj,pthread_getspecific
    .weakref    _ZL27__gthrw_pthread_setspecificjPKv,pthread_setspecific
    .weakref    _ZL22__gthrw_pthread_createPmPK14pthread_attr_tPFPvS3_ES3_,pthread_create
    .weakref    _ZL20__gthrw_pthread_joinmPPv,pthread_join
    .weakref    _ZL21__gthrw_pthread_equalmm,pthread_equal
    .weakref    _ZL20__gthrw_pthread_selfv,pthread_self
    .weakref    _ZL22__gthrw_pthread_detachm,pthread_detach
    .weakref    _ZL22__gthrw_pthread_cancelm,pthread_cancel
    .weakref    _ZL19__gthrw_sched_yieldv,sched_yield
    .weakref    _ZL26__gthrw_pthread_mutex_lockP15pthread_mutex_t,pthread_mutex_lock
    .weakref    _ZL29__gthrw_pthread_mutex_trylockP15pthread_mutex_t,pthread_mutex_trylock
    .weakref    _ZL31__gthrw_pthread_mutex_timedlockP15pthread_mutex_tPK8timespec,pthread_mutex_timedlock
    .weakref    _ZL28__gthrw_pthread_mutex_unlockP15pthread_mutex_t,pthread_mutex_unlock
    .weakref    _ZL26__gthrw_pthread_mutex_initP15pthread_mutex_tPK19pthread_mutexattr_t,pthread_mutex_init
    .weakref    _ZL29__gthrw_pthread_mutex_destroyP15pthread_mutex_t,pthread_mutex_destroy
    .weakref    _ZL30__gthrw_pthread_cond_broadcastP14pthread_cond_t,pthread_cond_broadcast
    .weakref    _ZL27__gthrw_pthread_cond_signalP14pthread_cond_t,pthread_cond_signal
    .weakref    _ZL25__gthrw_pthread_cond_waitP14pthread_cond_tP15pthread_mutex_t,pthread_cond_wait
    .weakref    _ZL30__gthrw_pthread_cond_timedwaitP14pthread_cond_tP15pthread_mutex_tPK8timespec,pthread_cond_timedwait
    .weakref    _ZL28__gthrw_pthread_cond_destroyP14pthread_cond_t,pthread_cond_destroy
    .weakref    _ZL26__gthrw_pthread_key_createPjPFvPvE,pthread_key_create
    .weakref    _ZL26__gthrw_pthread_key_deletej,pthread_key_delete
    .weakref    _ZL30__gthrw_pthread_mutexattr_initP19pthread_mutexattr_t,pthread_mutexattr_init
    .weakref    _ZL33__gthrw_pthread_mutexattr_settypeP19pthread_mutexattr_ti,pthread_mutexattr_settype
    .weakref    _ZL33__gthrw_pthread_mutexattr_destroyP19pthread_mutexattr_t,pthread_mutexattr_destroy
    .ident    "GCC: (GNU) 4.5.1 20100924 (Red Hat 4.5.1-4)"
    .section    .note.GNU-stack,"",@progbits


```

---

### Post by worksofcraft on 2011-01-11
Yes like I explained before the compiler can optimize it in some circumstances.

However quite often people put #define in header files that are included in **multiple modules** but if you use a const int in a header file. The C compiler will reject it and complain of** multiple definitions**.

Thus you have to **declare** it as extern and **define** it only in one module. When you do that the compiler can't optimize it anymore, which is the assembler I showed you before.

Hum... too much nitrous oxide... perhaps I was going too fast...
[IMG]http://images.wikia.com/crashban/images/c/cf/Tnt.jpg[/IMG]
ANyway I really don't feel like explaining why C++ compiler doesn't complain of multiple definitions so I'll let you work it out for yourself now OK

---

### Post by GeneralZod on 2011-01-11
In C++, in contrast (I think?) to C, treats const ints as having internal linkage, so that can be put into header files.  The change was motivated pretty much explicitly by the desire to get rid of #define's as much as possible :)

---

### Post by nvteighen on 2011-01-11
Maybe I'm in minority, but I think this debate is pointless. 

You're comparing #define constant values vs. const int... This means, you're comparing a preprocessor directive which introduces a constant value everywhere where called and which is compiled and also assembled as a constant value (if the macro is called in legit places). And const int declares constant integers, which is assembled into a constant value.

So, the only differences about #define's and const int's are the linking and type safety problems... Two issues more related to the way C++ is implemented than to the concept of const-ness.

---

### Post by worksofcraft on 2011-01-11
> **GeneralZod said:**
> In C++, in contrast (I think?) to C, treats const ints as having internal linkage, so that can be put into header files.  The change was motivated pretty much explicitly by the desire to get rid of #define's as much as possible :)

Yes, indeed, internal linkage... that means every module into which you include it gets it's own instance.

All these instances occupy memory that is to be initialized when program starts.

OTOH as I already mentioned, one can alternatively use enum... enum does not produce lvalues so they don't occupy memory and don't need to be initialized. They don't use preprocessor either.

And thus once again I see I shoulda just left it at my first post and then left it up those who read books to decide for themselves if they are actually interested to understand what concept the author is trying to communicate :shock:

---

