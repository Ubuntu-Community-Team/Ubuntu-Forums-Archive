---
title: "Intel x86 Asm Help Plz (Simple If You Know It)"
date: 2010-10-13
forum: Programming Talk
---

### Post by Syndacate on 2010-10-13
Hey,

I do believe this is a place where I can ask a generic programming question, I do apologize if it's wrong.

I'm working on my systems programming I project, and I'm getting my *** kicked around.  I just CAN'T figure out this stupid language!!!  I need help with understanding which syntactic sugar causes it to treat what as what, namely pointers vs their respective values.

So I have some code here, short in short, **I'm getting passed a pointer to a struct who's 8th byte is a char*** (2 4 byte ints come before it), I take two of these and do a **strcmp()** on them.

Now, the thing is, we're ALLOWED to use the std C lib, in which case I CAN just call strcmp, but that's the easy way, and I don't like that.  So I'm doing it manually.  It seems to be working for all except ones that are left (but I'd have to look at the test drivers again for that one :-P).

My question is more simplistic than all of this, though, it goes like this:
```
   movl   8(%ebp), %ecx  #Copy addr of 1st arg to ecx
   movl   12(%ebp), %edx  #Copy addr of 2nd arg to edx

   movl   8(%ecx), %eax  # Copy addr of 1st char in byte array into eax
   movl   8(%edx), %ebx  # Copy addr of 1st char in OTHER byte array to ebx
   
   movl   (%eax), %eax
   movl   (%ebx), %ebx  # Do these two lines de-reference it so eax now hold the first characters of each byte array?
#  If so, is there any way to reference them again?  lea seems to just do some adds and multiplies to a base addr
```

I get that $ = literal, and % = register, and #(addr) offsets then dereferences it, what i don't get is:
- **does "(<register with addr>)" dereference it?**
- **How do I reference it again?  Or can I NOT since it's not a pointer, it's bits in a register?**

Maybe I'm thinking of this too much like C, and it's pwning me.  I'm not new to C, I'm not new to asm (although I'm new to x86), but I knew MIPS prior (PS:  RISC >>>> CISC ANY day).  I'm kind of at a loss here.

The only thing I can think of is allocating some space on the stack, via the following code (or something similar), and keeping it there:
```

   subl   %esp, 8  ## Allocate some space on the stack
   movl   8(%ecx), -4(%ebp)  ## Throw 1st char* on the stack
   movl   8(%edx), -8(%ebp)  ## Throw 2nd char* on the stack

   cmpl   %eax, %ebx    # Compare them
   <Call or jump To Routine To Handle GT/LT/both == NULL>
   incl   -4(%ebp)      ## Increment 1st char*
   incl   -8(%ebp)      ## Increment 2nd char*

```

If that does it, how could I add 2 to that each time (every other letter)?  Would this do it?

```

   addl   2, -4(%ebp)
   addl   2, -8(%ebp)

```

I assume no, right, because that would dereference them and increment their value by 2 - so how do I increment THEM?  Do I have to load them into registers first, if so, how do I do that w/o de-referencing them?  Do I use their literals, like?

```

   add   $2, $eax   # I do want the LITERAL value (the address), but it is also a register

```

This won't work, because it will grab their values, increment them twice, then store them back.
```

   movl   -4(%ebp), %eax
   addl   $2, %eax
   movl   %eax, -4(%ebp)

   movl   -8(%ebp), %ebx
   addl   $2, $ebx
   movl   %ebx, -8(%ebp)

```

All the auto-magic/phase of the moon dereferencing of values is KILLING me - you start asking yourself if what you're incrementing is an address or a value.  Starting to lose my head over it.

After writing this, I have things a little more straight, I think, so I think the end question is:
- **How do I increment or offset an address - the equivalent of the [] operator in C.**  You can't do anything like this, right?

```

   addl   $1, $-4(%ebp)
   addl   $1, $-8(%ebp)

```

Not even going to bother trying that it looks so illegal, but I'm trying to get it to count those offsets as their address, NOT the value there :(.

TIA guys, sorry if the post is long.  Any help is really appreciated.

---

### Post by ibuclaw on 2010-10-13
Question, why not call strcmp? gcc has it as a builtin...
```

# Assumes %eax and %ebx hold the two strings for comparison.
movl    %ebx, (%esp)
movl    %eax, 4(%esp)
call    strcmp
testl   %eax, %eax
jne     .NOMATCH
# strcmp returned success
.NOMATCH
# strcmp returned fail

```

Or are you *really* trying to do reinvent the wheel yourself? :)

---

### Post by Syndacate on 2010-10-13
> **ibuclaw said:**
> Question, why not call strcmp? gcc has it as a builtin...
```

# Assumes %eax and %ebx hold the two strings for comparison.
movl    %ebx, (%esp)
movl    %eax, 4(%esp)
call    strcmp
testl   %eax, %eax
jne     .NOMATCH
# strcmp returned success
.NOMATCH
# strcmp returned fail

```

Or are you *really* trying to do reinvent the wheel yourself? :)

> **Syndacate said:**
> Now, the thing is, **we're ALLOWED to use the std C lib, in which case I CAN just call strcmp, but that's the easy way, and I don't like that.  So I'm doing it manually.**  It seems to be working for all except ones that are left (but I'd have to look at the test drivers again for that one :-P).

Already answered :).

I'm more concerned about how to increment pointers as everything seems to dereference them.. (see OP).

---

### Post by xbxb on 2010-10-13
Have a look at the CMPSB (Compare String) operand. Also have a look at the REP (Repeat String Operation) prefix.

---

### Post by worksofcraft on 2010-10-13
It is a long time since I wrote x86 assembler and also I was using Masm v4 (from Microsoft) and that has a different syntax.

However what I do remember is that on the x86 architecture different opcodes can only be used with particular registers:

e.g. the ax (eax today) register is an arithmetic accumulator it **cannot be used** for indexing memory locations. Addresses have to be placed in the si and di registers and looping counts in the bx register (which is implicit parameter of the *sob* instruction). I presume these are called esi, edi and ebx today and have a lot more bits in them, but probably still restricted to the same opcodes.

Do remember that the x86 was probably one of the most ill conceived and prematurely released processor architectures of all time as Intel tried to beat Motorola to the market with 16 bit processor. Today x86 processors actually have their own internal risc architecture and that is then microcoded to emulate all that x86 malarkey simply for historic reasons and binary compatability :shock:

---

### Post by xbxb on 2010-10-13
> **worksofcraft said:**
> Addresses have to be placed in the si and di registers and looping counts in the bx register (which is implicit parameter of the *sob* instruction). I presume these are called esi, edi and ebx today and have a lot more bits in them, but probably still restricted to the same opcodes.

Counts are in the CX, ECX register.

> **worksofcraft said:**
> Today x86 processors actually have their own internal risc architecture and that is then microcoded to emulate all that x86 malarkey simply for historic reasons and binary compatability :shock:

And that is one reason why Intel is the biggest and most successful silicon company in the world.

---

### Post by worksofcraft on 2010-10-13
> **xbxb said:**
> Counts are in the CX, ECX register.

And that is one reason why Intel is the biggest and most successful silicon company in the world.

Whatever... I thought the "subtract one and branch" instruction was one of those annoying special cases, but turfed out the manual years ago. As a design, x86 was a bit rushed IMO.

To me it only shows how marketing is much more important than technical excellence... could it be a parallel to predominance of Microsoft in the software industry perhaps? :shock:

---

### Post by Syndacate on 2010-10-15
> **xbxb said:**
> Have a look at the CMPSB (Compare String) operand. Also have a look at the REP (Repeat String Operation) prefix.

I was just trying to make my own, I got it to work - it's hella hard to debug :(.

> **worksofcraft said:**
> It is a long time since I wrote x86 assembler and also I was using Masm v4 (from Microsoft) and that has a different syntax.

However what I do remember is that on the x86 architecture different opcodes can only be used with particular registers:

e.g. the ax (eax today) register is an arithmetic accumulator it **cannot be used** for indexing memory locations. Addresses have to be placed in the si and di registers and looping counts in the bx register (which is implicit parameter of the *sob* instruction). I presume these are called esi, edi and ebx today and have a lot more bits in them, but probably still restricted to the same opcodes.

Do remember that the x86 was probably one of the most ill conceived and prematurely released processor architectures of all time as Intel tried to beat Motorola to the market with 16 bit processor. Today x86 processors actually have their own internal risc architecture and that is then microcoded to emulate all that x86 malarkey simply for historic reasons and binary compatability :shock:

Yeah, things have changed a bit since then.  Now eax, ebx, ecx, edx, esi, and edi can all be used as general purpose registers.  Though they do get stomped on by certain functions (such as 'loop' decrements the contents of %ecx).

To maintain backwards compatibility they still have the ax, bx, cx, dx, regs, but they only access the low order 16 bits, you need the prepended 'e' to access 32 bits, and I believe it's rax, rbx, etc. to access them in their 64 bit modes.  The op codes now have suffixes, ie. pushl vs pushb vs pushw vs pushq (blah).

Yeah, I hate this code, realistically, but it's what drives today's PC market :-\.

> **xbxb said:**
> Counts are in the CX, ECX register.

Yup.  Though you can put it anywhere, just if you want incrementing instructions (or decrementing, as the case may be) such as loop to work, they need to be in ecx.

[QUOTE=xbxb;9967600]And that is one reason why Intel is the biggest and most successful silicon company in the world.

Yeah, but the same x86 code, though not being "intel code" - should work on an AMD machine, no?

> **worksofcraft said:**
> Whatever... I thought the "subtract one and branch" instruction was one of those annoying special cases, but turfed out the manual years ago. As a design, x86 was a bit rushed IMO.

Yeah, there seems to be a lot of 'special oddities' in the language...it's kind of annoying..

> **worksofcraft said:**
> To me it only shows how marketing is much more important than technical excellence... could it be a parallel to predominance of Microsoft in the software industry perhaps? :shock:

Yeah, they definitely got in at the right time, only reason I'm coding this today :-P.

So thanks for the replies, guys, turns out:
- () takes the value of that register, ie.
- movl (%ecx), %ecx #Take the value pointed to by %ecx and store it in %ecx.
- You can't really reference stuff, so to speak, as there's not really any "pointers" per-se...I guess...I think...

So to increment a pointer passed in as an argument:
```

movl   8(%ebp), %ecx
movl   (%ecx), %edx

incl   %ecx    ### Increments the pointer by one
incl   %edx    ### Increments the value in the pointer passed in by one.

```

At least that's the way I'm understanding it - got my lookup function to work (almost done with this project now, yaaaay).  Thanks.

BTW:  The stack was from a x86 proc, but it was running Solaris.  Doesn't mean that much with the exception that the first argument is 8 down the stack from the base pointer.

---

