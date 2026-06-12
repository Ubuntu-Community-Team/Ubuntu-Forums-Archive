---
title: "non used return values"
date: 2008-09-03
forum: Programming Talk
---

### Post by monkeyking on 2008-09-03
The following code compiles and works.
(with a warning using -Wall)

```

int returnCheck(int a){
  printf("a:%d\n",a);
  return 7;
}
int main(){
  returnCheck(3);
  return 0;
}

```

What happens to the return value, is it just being optimized,
can it result in undefined behavior,
thanks in advance

---

### Post by LaRoza on 2008-09-03
The return value is just stored in a register (probably). If it isn't used, it isn't used.

It won't result in any strange behavior.

---

### Post by loganwm on 2008-09-03
I'm not sure what you're asking? (Can you rephrase it?)

Out of curiousity, why does your function always return "7"?

What are you trying to accomplish?

---

### Post by LaRoza on 2008-09-03
The return value is just stored in a register (probably). If it isn't used, it isn't used.

It won't result in any strange behavior.

---

### Post by Cypher on 2008-09-03
Expanding on what LaRoza said..on most CPU's, the registers R3, R4, R5, etc. are used for parameters. The return of a function is stored in R3 when the function returns to the caller. If the return value was stored in a variable then the contents of R3 would've been moved to whatever memory that variable occupied. If the return value was not stored, then R3 would get overwritten by any number of instructions that follow essentially overwriting the contents.

So if you don't care about a return value of a function, then just don't store it and it's fine. However, it is generally good practice to check the return value of a function if it returns one. If there is some function that is absolutely guaranteed to succeed without fail, then you can "void" it's return value and move on..

---

### Post by LaRoza on 2008-09-03
> **Cypher said:**
> Expanding on what LaRoza said..
twice. Sorry. The forums were acting up and it posted twice.

---

### Post by monkeyking on 2008-09-03
> **loganwm said:**
> I'm not sure what you're asking? (Can you rephrase it?)

Out of curiousity, why does your function always return "7"?

What are you trying to accomplish?

In the previous functional programming languages I've encountered,
My example code wouldn't make sense.

In perl my example code would result in a change of a hidden var called $_.

So I was just wondering what c++ think and does, when you call a function that returns a value, and you don't assign a variable to this value.

The function returns 7 because 7 is the 4th prime. Or just because I need to return something.

@cypher very informative thanks

---

### Post by LaRoza on 2008-09-03
> **monkeyking said:**
> In the previous functional programming languages I've encountered,
My example code wouldn't make sense.

In perl my example code would result in a change of a hidden var called $_.

So I was just wondering what c++ think and does, when you call a function that returns a value, and you don't assign a variable to this value.

The function returns 7 because 7 is the 4th prime. Or just because I need to return something.

It is in the register as stated. It actually does have an effect if you read that register (or something else does).

Example:

```

~/p$cat p.c
#!/usr/bin/tcc -run

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv)
{
    return puts("Hello world");
}
~/p$./p.c
Hello world
~/p$echo $?
12
~/p$

```
The return value of puts is "12" (verified by printing its return value earlier), and it is in the register. (This being main, you can also not return anything, and the value of the return value of the last function will be in that register and used.)

---

### Post by snova on 2008-09-03
> **Cypher said:**
> ... on most CPU's, the registers R3, R4, R5, etc. are used for parameters. The return of a function is stored in R3 when the function returns to the caller. If the return value was stored in a variable then the contents of R3 would've been moved to whatever memory that variable occupied. If the return value was not stored, then R3 would get overwritten by any number of instructions that follow essentially overwriting the contents .... 

What kind of processor are *you* using? I can't speak for everybody, but that does **not** sound like an x86.

The standard (well, it's not "standard" as far as I know, but more or less accepted, I think) is that the return value goes in EAX before returning to the caller. If you ignore the value, then your program simply proceeds to use EAX for something else, and it never bothers examining its contents. Nothing happens.

If something *did* happen, we'd be in trouble, because a number of commonly used functions in the standard library have a return that most people ignore. Take printf for example.

Interestingly, you *can* treat void functions as if they returned a value. When I tested it, it was zero. Nothing bad happened, and my little snippet worked just fine. But just to be on the safe side, I &'ed it with zero anyway.

---

### Post by LaRoza on 2008-09-03
> **snova said:**
> What kind of processor are *you* using? I can't speak for everybody, but that does **not** sound like an x86.

The standard (well, it's not "standard" as far as I know, but more or less accepted, I think) is that the return value goes in EAX before returning to the caller. If you ignore the value, then your program simply proceeds to use EAX for something else, and it never bothers examining its contents. Nothing happens.

I think it may be just a generalisation for those unfamiliar with the register names.

> 
If something *did* happen, we'd be in trouble, because a number of commonly used functions in the standard library have a return that most people ignore. Take printf for example.

Or puts.

---

### Post by monkeyking on 2008-09-03
This is quite interesting,

I'm having trouble reproducing, your example,
but I guess it's a gnu compiler vs tiny compiler.

```

./a.out
Hello world
$ $_
Hello world
thorfinn@rocco:~/tmp$

```

But thanks I'll remember this.

---

### Post by LaRoza on 2008-09-03
> **monkeyking said:**
> This is quite interesting,

I'm having trouble reproducing, your example,
but I guess it's a gnu compiler vs tiny compiler.

```

./a.out
Hello world
$ $_
Hello world
thorfinn@rocco:~/tmp$

```

But thanks I'll remember this.
What is the $_ for? The return value would be $?.

tcc is a compiler and an interpreter, however, the results shouldn't be that different.

---

### Post by LaRoza on 2008-09-03
Here is a better example. The function main returns no value. The function called (puts) has an ignored return value. However, the return value of puts is put into the register (sorry to those not familiar with C or English. That sentence makes sense) and because main isn't returning anything (which uses the same register) the value is still there.
```

~/p$cat p.c
#!/usr/bin/tcc -run

#include <stdio.h>
#include <stdlib.h>

void main(int argc, char **argv)
{
    puts("Hello world");
}
~/p$./p.c
Hello world
~/p$echo $?
12
~/p$

```

---

### Post by Cypher on 2008-09-03
> **snova said:**
> What kind of processor are *you* using? I can't speak for everybody, but that does **not** sound like an x86.

That **isn't** X86..I was speaking about ARM and PowerPC's, the two CPU's for which I've actually done ASM programming..X86 doesn't really see much action in the embedded space..

---

### Post by monkeyking on 2008-09-03
ok, I get it know I didn't know the return val was $?

---

### Post by LaRoza on 2008-09-03
> **monkeyking said:**
> ok, I get it know I didn't know the return val was $?

That is the return value of the last run command, useful for shell scripting mostly.

---

### Post by snova on 2008-09-03
> Here is a better example. The function main returns no value. The function called (puts) has an ignored return value. However, the return value of puts is put into the register (sorry to those not familiar with C or English. That sentence makes sense) and because main isn't returning anything (which uses the same register) the value is still there.

Ooh, that's a good example. Which gives me an evil idea. :twisted: Anybody who looked at my "structured" entry into the fifth programming contest (the second one) will have an idea of what to expect.

> That **isn't** X86..I was speaking about ARM and PowerPC's, the two CPU's for which I've actually done ASM programming..X86 doesn't really see much action in the embedded space..

I kinda thought so. I've never touched a CPU that wasn't an x86, so I don't know a lot about those architectures. They're probably more popular because they have more general purpose registers, among other things... It's the RISC vs. CISC debate again.

I wouldn't mind learning one though, because embedded programming looks like fun from afar.

---

### Post by jinksys on 2008-09-04
> 
What happens to the return value, is it just being optimized,
can it result in undefined behavior,
thanks in advance

Why are you asking us? Ask the compiler.

$ gcc -S source.c 
$ cat source.s 

Edited for readability.  Here is your returnCheck function in assembly. 
C style dictates that a function will return 32-bit int values using the %eax register (which you can see in your program as **movl $7, %eax**), 64-bit values using the edx:eax register pair, and floating point return values using the FPU ST(0) register. 

```

returnCheck:
	pushl	%ebp
	movl	%esp, %ebp
	subl	$8, %esp
	movl	8(%ebp), %eax
	movl	%eax, 4(%esp)
	movl	$.LC0, (%esp)
	call	printf
	movl	$7, %eax  <-- set %eax equal to 7
	leave
	ret

```

The exit code for a program is entered into the %ebx register prior to calling the exit syscall.  However, you will not find a **movl $0, %ebx** line in your program since you are using C and MAIN is technically a C function, so it also must send return values with EAX. (Later on EBX is set to this value before the C runtime libraries call the exit syscall.)

But to answer your question, no.  It won't mess anything up.  Just think of it as a variable that is set, but never used.

---

