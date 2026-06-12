---
title: "quick c++ binary operator question"
date: 2009-09-14
forum: Programming Talk
---

### Post by blake82 on 2009-09-14
Hi Folks,

I have 2 quick questions for ya

(1)

given this operation:
```
int x=0;
int y=0;
if(x == y) doSomething();
```
all else being equal, will this comparison be faster if x & y are chars? (since ints are 4 bytes, chars are 1)

(2)

given this operation:

```
void function(char x){
    //
    if(x == 0x10) doSomething();
}
```

will c++ do any sort of type conversion in the comparison above?? I know that while a hex value is just a representation of binary data, it will be expressed as an integer (in cout etc). Will c++ just do a bit by bit comparison above?


I'm writing an audio application which is evaluating hundreds of thousands of conditional statements per second, and I'm looking for a way to speed them up. I figure if I just do binary comparisons against some predefined hex values, and compare 1 byte(char) instead of 4 bytes(int) each time, I should notice a nice bump in efficiency.

Let me know if I'm on the right track, or if there are any other tricks I should look out for.

Thanks!

Blake

---

### Post by dwhitney67 on 2009-09-14
> **blake82 said:**
> ...

I'm writing an audio application which is evaluating hundreds of thousands of conditional statements per second, and I'm looking for a way to speed them up. I figure if I just do binary comparisons against some predefined hex values, and compare 1 byte(char) instead of 4 bytes(int) each time, I should notice a nice bump in efficiency.

...

Huh?  If you have a 32-bit machine, then this implies that your machine has 32-bit registers.  Why not use the full-power of these when making comparisons?

If you have a need to perform "hundreds of thousands" of comparisons per second, then I would recommend that you revisit your applications requirements.  It would seem odd that an audio application has to perform as many calculations as say, a nuclear weapons simulator.  But hey, what do I know!  Some s/w apps today are freakin' amazing, yet killing the crap out of my CPU.

---

### Post by blake82 on 2009-09-14
Well it's a synthesizer, not a jukebox

Regarding the number of comparisons, if your sample rate is 96khz, and your doing 6 comparisons per sample, then you're already doing close to 600,000 comparisons per second. Actually, given my event handling and parameter modulation systems, I'm probably doing a lot more than that!

Anyway, I had asked because I just don't know, and I'm having trouble googling my way to an answer. I'm pretty familiar with the DSP stuff, but not so much with lower level cpu stuff.

Would any of the ideas in my original post speed things up? If not, do you have any thoughts on what would?

Thanks,

Blake

---

### Post by johnl on 2009-09-14
In general it is faster to do operations at the native word size of the CPU.  However what you should do is profile your code, and find out where your code spends the most time.  Optimize where it makes sense.

---

### Post by MindSz on 2009-09-14
blake82, I've had to do some stuff that needs to be super fast (sampling in a single-board computer's ADC at around 32kbs) and I've found that changing doubles to integers and integers to chars makes a world of difference.

I've also found that using masks in some parts helps a lot.

EDIT: Also, if you need to perform any mathematical operations in your code, try replacing them for bitwise operators (e.g. instead of doing (a * 2), do (a << 1))

---

### Post by blake82 on 2009-09-14
Thanks MindSz!

@johnl
Yes, I'm attacking the functions that were taking up the most time.

The issue is that there are several modules (adsr envelope generators in particular) that need to calculate their output differently depending on what state they're in, and they also need to detect when it's time to switch their state.

---

### Post by dribeas on 2009-09-15
> **blake82 said:**
> 
The issue is that there are several modules (adsr envelope generators in particular) that need to calculate their output differently depending on what state they're in, and they also need to detect when it's time to switch their state.

You could use function pointer tables to control the state and just use a dereference

```

typedef int (*function)(void);

int first_state();
int second_state(); ...

function state_op[] = { first_state, second_state, ... };

void exec()
{
   while (1) {
     current_state = state_op[ current_state ](); // will exec first_state when current_state==1
   }
}

```

This will switch the condition and jump into an indirection. Now you will need to test conditions inside the functions, but you might get a small bump in performance from avoiding the initial switch.

---

### Post by Lux Perpetua on 2009-09-15
> **MindSz said:**
> EDIT: Also, if you need to perform any mathematical operations in your code, try replacing them for bitwise operators (e.g. instead of doing (a * 2), do (a << 1))Your example makes sense because multiplication (and division/modulus) are slow operations. However, a blanket statement like "replace arithmetic with bitwise operations" is misleading, since operations like addition and subtraction aren't much slower (being actually faster in some cases) than bit-manipulation operators. 
> **dribeas said:**
> You could use function pointer tables to control the state and just use a dereference

```

typedef int (*function)(void);

int first_state();
int second_state(); ...

function state_op[] = { first_state, second_state, ... };

void exec()
{
   while (1) {
     current_state = state_op[ current_state ](); // will exec first_state when current_state==1
   }
}

```

This will switch the condition and jump into an indirection. Now you will need to test conditions inside the functions, but you might get a small bump in performance from avoiding the initial switch.I'm not saying it's not worth trying, but the compiler may well choose to implement a switch statement this way (using the switch variable as an index into a jump table), so that sort of optimization might be better left to the compiler.

---

### Post by johnl on 2009-09-15
> **MindSz said:**
> EDIT: Also, if you need to perform any mathematical operations in your code, try replacing them for bitwise operators (e.g. instead of doing (a * 2), do (a << 1))

This is one of the very first optimizations a compiler will do for you.  The only thing you gain by doing this is making your source code a bit less readable.

Edit: in fact, I tested this and gcc will do this even at -O0 (optimizations disabled):

```

#include <stdlib.h>
#include <stdio.h>
int main(int argc, char* argv[])
{
    unsigned int x;
    scanf("%ud", &x);
    return x / 2;
}

```

```

gcc -Wall -O0 -S -m32 main.c

```

```

main:
        leal    4(%esp), %ecx
        andl    $-16, %esp
        pushl   -4(%ecx)
        pushl   %ebp
        movl    %esp, %ebp      
        pushl   %ecx
        subl    $36, %esp
        leal    -8(%ebp), %eax
        movl    %eax, 4(%esp)
        movl    $.LC0, (%esp)
        call    scanf           ;; here we call scanf
        movl    -8(%ebp), %eax  ;; move result to eax
        shrl    %eax            ;; <--- divide by two
        addl    $36, %esp
        popl    %ecx
        popl    %ebp
        leal    -4(%ecx), %esp
        ret


```

---

### Post by dribeas on 2009-09-16
> **Lux Perpetua said:**
> I'm not saying it's not worth trying, but the compiler may well choose to implement a switch statement this way (using the switch variable as an index into a jump table), so that sort of optimization might be better left to the compiler.

The magic there is not really the indirection, but the conversion from comparing with 'some predefined hex values' or using a state machine. The difference being that if the possible cases are not contiguous. 

```

void f( int i ) {
   switch ( i ) {
   case 0:
       break;
   case 10:
       break;
   case 100:
       break;
   default:
   }
}

```

Now, if you turn 'some predefined hex values' (as stated in the question) into a state machine then the case values will become contiguous. Also you have extra information that the compiler does not have: the limits. If the compiler does create an indirection table, it must first test the variable against the size of the table to avoid an overrun and then it will apply the indirection. I know this does not really make much of a difference, but it can provide small improvements.

---

### Post by jespdj on 2009-09-16
> **MindSz said:**
> EDIT: Also, if you need to perform any mathematical operations in your code, try replacing them for bitwise operators (e.g. instead of doing (a * 2), do (a << 1))

No!! Read this: [How Not To Optimize](http://www.informit.com/articles/article.aspx?p=1390173)

It explains in detail why, on modern CPUs, doing things with shifts etc. instead of multiplications can make things **slower**.

---

### Post by MindSz on 2009-09-16
@LuxPerpetua & johnl

I'm not saying what the compiler does or fails to do. I'm talking from experience. The code (at least in the embedded system it runs in) works faster (a lot faster), and that's the end of it.

It might be that the system's compiler is different or whatever; thruth is, I don't care. I just care that it works.

I don't know if it'll work for the OP, but it will at least give him something to try and think about.

EDIT: Thanks for sharing that link jespdj, it has been added to my bookmarks for reference :)

---

