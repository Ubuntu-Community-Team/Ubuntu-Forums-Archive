---
title: "Could use help with my Programming Logic and Problem Solving class."
date: 2009-08-27
forum: Programming Talk
---

### Post by whoscheesemine on 2009-08-27
I recently began taking this Programming Logic and Problem Solving class. Now I don't know a whole lot about programming, but I do grasp a lot of the concepts. I am having trouble with a couple questions, because i do not feel as though my book goes over this part very well. When I learn I need to understand everything about what I'm learning. I was wondering if someone couple possibly explain in the simplest of terms the information I would need to know to answer the next couple questions. If anyone has an E-Book they'd recommend, I'm all over it.

```

Assume a simple machine uses four bits to represent its instruction set. How many different instructions can this machine have? How many instructions could it have if eight bits are used? How many if 16 bits are used?
```

and then...

```

Consider a simple machine with the following instruction set:

|Binary Code|Mnemonic|Meaning
|000           |CLR        |Clear the accumulator
|001           |ADD       |Add the contents of a specified memory location to the accumulator
|010           |SUB        |Subtract the contents of a specified memory location from the accumulator.
|011           |STO       |Store the contents of the accumulator in a specified memory location
|100           |MULT     |Mutiply the value in the accumulator by the contents of a specified memory location
|101           |LOAD      |Load the contents of a specified memory location to the accumulator
|110           |INC        |Add one to the accumulator
|111           |DEC        |Subtract one from the accumulator

Assume that this machine has eight memory locations whose addresses and contents are as shown:

Address:   000   001   010   011   100   101   110   111
Contents:   9              3                      5      2

Write machine language code to perform each of the following calculations. Store each result int he first empty memory location.
a. (5*9) + 3
b. (3+5) * 9
c. (5*3) + (2*9)
```

and as a bonus!

```
Write the assembly language equivalent for each of the calculation in the previous question. Assume that the memory addresses in Exercise 6 can be referred to as A, B, C, D, E, F, G, H, respectively.
```

---

### Post by CptPicard on 2009-08-27
What are the parts you have trouble with? For example in the first question... well, you have four bits of 0 or 1 to represent instructions. Therefore, they are 0000, 0001, 0010, 0011... and so on. How many different states can 4 bits be in?

(I feel for you for having a class where they teach "programming logic and problem solving" on the asm level...)

---

### Post by Can+~ on 2009-08-27
How many numbers can you produce with 4 digits in decimal?

```
10^4 = 10000
```

How many numbers can you produce with 4 digits in binary?

```
2^4 = 16
```

How many numbers can you produce with n digits in base B?

```
B^n
```

And this doesn't seem like problem solving to me, it's very machine related, which, yeah, can solve problems, but you don't need to understand the instruction set of a processor to solve a math problem.

---

### Post by |{urse on 2009-08-27
Heres how to perform basic math functions with asm, assuming 16bit.

[http://www.8052.com/add16.php](http://www.8052.com/add16.php)

hope it helps ^^

---

### Post by jimi_hendrix on 2009-08-27
The second question doesnt seem that hard, it looks like you are just substituting in the op codes and memory addresses in the equations.  I wouldnt know how to do that though since i dont know machine code.

---

### Post by MindSz on 2009-08-27
For the first Q you just need to figure our how many combinations you can achieve with 4 and 8 bits, where each bit can only take a 1 or a 0.

For the second Q, just write the machine code. For example, if you want to add two numbers, say 5 and 9, you do something like:

```
000     -> To clear the accumulator
101 110 -> Loads the 5 into the accumulator
001 000 -> Adds 9 to the accumulator
011 001 -> Stores accumulator in the first available mem location
000     -> Clears accumulator
```

For the third Q, you need to do the same but with the actual instructions, so:

```
CLR    -> Clears accumulator
LOAD G -> Loads register G (5)
ADD  A -> Adds register A (9)
STO  B -> Stores result
CLR
```

Btw, the instruction set for this problem has 3 bits. So that might give you a hint for the first problem.

---

### Post by whoscheesemine on 2009-08-27
> **Can+~ said:**
> How many numbers can you produce with 4 digits in decimal?

```
10^4 = 10000
```

How many numbers can you produce with 4 digits in binary?

```
2^4 = 16
```

How many numbers can you produce with n digits in base B?

```
B^n
```

And this doesn't seem like problem solving to me, it's very machine related, which, yeah, can solve problems, but you don't need to understand the instruction set of a processor to solve a math problem.

sweet thanks very much, that helped me to figure out the answer to the first question, which if I'm not mistaken is: 16, 256, and 65536. As for it not seeming like problem solving, I agree. This is just the introductory chapter, basically going over the history and stuff. The book I'm using is Microsoft Visual Basic .NET From Problem Analysis to Program Design.

> For the first Q you just need to figure our how many combinations you can achieve with 4 and 8 bits, where each bit can only take a 1 or a 0.

For the second Q, just write the machine code. For example, if you want to add two numbers, say 5 and 9, you do something like:

Code:

000     -> To clear the accumulator
101 110 -> Loads the 5 into the accumulator
001 000 -> Adds 9 to the accumulator
011 001 -> Stores accumulator in the first available mem location
000     -> Clears accumulator

For the third Q, you need to do the same but with the actual instructions, so:

Code:

CLR    -> Clears accumulator
LOAD G -> Loads register G (5)
ADD  A -> Adds register A (9)
STO  B -> Stores result
CLR

Btw, the instruction set for this problem has 3 bits. So that might give you a hint for the first problem. 

Thanks very much for the input, but alas even this is a bit advanced for me. I'm not sure how to actually even have it written. If I could see some kind of example it would really help. Wish i could find my scanner, so I could show you how poorly this book goes over this section. I'm in no way lazy or stupid, but I am having trouble grasping this.

---

### Post by Krupski on 2009-08-27
> **|{urse said:**
> Heres how to perform basic math functions with asm, assuming 16bit.

[http://www.8052.com/add16.php](http://www.8052.com/add16.php)

hope it helps ^^

I *think* the OP is supposed to write the "machine code" for a pseudo microprocessor that has the opcodes listed in the post.

So, for example, the problem "answer = (5*9) + 3" would go like this:

```

;columns are: address, opcode, operand
;note: this code assumes that the "mult"(iply) instruction places the result in the accumulator.

0000 0000           ;zero the accumulator (not really necessary)
0001 0101 0101      ;load accumulator with "5"
0003 0011 0100      ;store accumulator contents to address 100
0005 0101 1001      ;load accumulator with "9"
0007 0100 0100      ;multiply accumulator (9) with memory 100 (5)
0009 0011 0100      ;store the product at address 100
000B 0101 0011      ;load accumulator with "3"
000D 0001 0100      ;add accumulator to product of 5*9
000F 0011 0100      ;store the answer to address 100

;done. Answer resides in memory location 100

```


I might have messed up... I just did this by eye... but you get the idea?

-- Roger

(edit to add):

Here's a "real" assembler listing which may further explain what's "going on":

```

; note: "D" register is A+B (16 bits)
;
; 15 14 13 12 11 10 09 08 07 06 05 04 03 02 01 00
;|---------- A ----------|---------- B ----------|
;|---------------------- D ----------------------|
;

0000 86 12          ldaa    #$12    ;load accumulator A with hex 12
0002 C6 34          ldab    #$34    ;load accumulator B with hex 34
0004 3D             mul             ;D = A * B
0005 CE 0100        ldx     #$100   ;load X with hex 100
0008 02             idiv            ;integer divide X = D / X, remainder D

```

See?

The code "86" tells the processor "load accumulator A, and you'll find what to load at the next address.
The address is incremented and the processor reads "12" from memory and sticks it into A.
It then looks for another instruction and finds "C6" which means "load B with whatever comes next".
The address is incremented, the value "34" is read from memory and placed into B.
The next instruction tells the processor to multiply A times B, so it does. It places the result
  into the "X" register and the remainder into the "D" register
Then the processor reads the next instruction......

The CPU *clock* is what makes the processor act on each instruction, step by step.



Another way to think about it is... imagine you are a construction foreman. You are building a house. You have the plans in your hand (the program). You are the CPU.

So, you read the instructions and tell the worker:

* START
* GRAB (grab what?)
* A BRICK
* PLACE THE BRICK (where?)
* ON THE WALL
* IS HE DONE?
* NO, GO BACK TO START
* IS HE DONE?
* YES, GO (WHERE?)
* HOME
* -end of program-

Hope this helps...

---

### Post by lisati on 2009-08-27
Thanks for the opportunity to brush up on some stuff!

For the third question, part of the solution is about figuring out the 'correct' sequence of evaluating the different parts of an expression. The [mnemonic]("http://en.wikipedia.org/wiki/Mnemonic") I was taught (there are others) is [BOMDAS]("http://en.wikipedia.org/wiki/BOMDAS"), short for **B**rackets, **O**f, **M**ultiplication, **D**ivision, **A**ddition, **S**ubtraction.

---

### Post by Krupski on 2009-08-27
> **lisati said:**
> Thanks for the opportunity to brush up on some stuff!

For the third question, part of the solution is about figuring out the 'correct' sequence of evaluating the different parts of an expression. The [mnemonic]("http://en.wikipedia.org/wiki/Mnemonic") I was taught (there are others) is [BOMDAS]("http://en.wikipedia.org/wiki/BOMDAS"), short for **B**rackets, **O**f, **M**ultiplication, **D**ivision, **A**ddition, **S**ubtraction.

No need for memory crutches. Just do stuff in parentheses first.

SOMETIMES, when you least expect it, a compiler or interpreter will VIOLATE the standard order of operations and mess up your program.

If you always use parentheses to "force" the correct order, it will never screw up.

---

### Post by lisati on 2009-08-27
> **Krupski said:**
> No need for memory crutches. Just do stuff in parentheses first.

SOMETIMES, when you least expect it, a compiler or interpreter will VIOLATE the standard order of operations and mess up your program.

If you always use parentheses to "force" the correct order, it will never screw up.

OK then [s]smartypants :)[/s] - what is the answer to 3+6*9? 81 or 57?

---

### Post by Krupski on 2009-08-27
> **lisati said:**
> OK then [s]smartypants :)[/s] - what is the answer to 3+6*9? 81 or 57?

Well, since multiplication comes before addition, and since I don't trust the compiler, I would write it like this:

answer = (6 * 9) + 3;

and get "answer = 57".

:)

---

### Post by lisati on 2009-08-27
> **Krupski said:**
> Well, since multiplication comes before addition, and since I don't trust the compiler, I would write it like this:

answer = (6 * 9) + 3;

and get "answer = 57".

:)

Must be time to file a bug report with the compiler's developers since they "obviously" got it wrong..... ;) 

<off topic aside>For our next piece of friendly banter, might I suggest a brief discussion on getting a concise and precise definition of what "microcode" is? Is it the "behind the scenes" stuff that lets the cpu decode machine-code instructions or is it more like firmware and/or BIOS? (</off topic aside>

I mentioned the BOMDAS thing for just this reason, because if the OP is going to get into compiler design some time in the future it might be useful to know the "correct" order of evaluation.

---

### Post by Krupski on 2009-08-28
> **lisati said:**
> <off topic aside>For our next piece of friendly banter, might I suggest a brief discussion on getting a concise and precise definition of what "microcode" is?

There's a little joke.... "Intel processors were designed by programmers - Motorola processors were designed by engineers".

A Motorola processor is basically a state machine. That is, it's just a bunch of gates and flip-flops. It does what it's wired to to. No more, no less.

How it executes it's opcodes is "programmed" into it solely by the way the gates are "wired". There is no software inside the processor.

The downside of this is, the Motorola processors are "simple instruction set" processors. All the instructions are simple "load, store, compare, branch, jump, multiply, divide" and a few others... all SIMPLE.

The upside of this is... it's FAST. Most instructions only take a few clock cycles to execute.

Now, if you want to copy a block of memory using a Motorola processor, you need to write a code snippet to do so... like this (pseudo-code):

```

* load a byte counter
* point to source
* point to destination
> get a byte from source
* store a byte to destination
* increment source pointer
* increment destination pointer
* decrement counter
* are we done yet?
* no, go back and move the next one >
* yes, return

```

Now, this looks overly complex, but remember that each instruction only takes one, two or three clock cycles. MOST processor operations are not that complicated - therefore the "simple instruction set" processor "works" very fast for it's clock speed. That's the "upside" of the state machine design... speed.


Now, the Intel architecture. The Intel processors are "complex instruction set" processors, and they literally have a "program" inside them (the microcode) to execute instructions.

The Intel processors take many clock cycles to do even the simplest things, so they are slower for a given clock speed.

But, they contain complex instructions which make programming easier.

Consider the block move code again. In Intel-speak (pseudo-code):

```

* Load counter
* Point to source
* Point to destination
* REP MOVSB (repeat move string byte until counter=0)
* return

```

Programming-wise, the block move was simpler. But if you count up the clock cycles used to move a certain block, the Motorola processor will do it with less clock cycles (that is, the processor is "faster" for a given clock speed).

With a Motorola processor, it's operation is cast in stone... literally. If there's an error in the processor, tough beans. The only choice is to make a new processor mask.

With an Intel processor, one can simply upload an updated microcode file to the processor and "fix" any bug(s) it has.

Note that the microcode upload doesn't "stick", it must be re-loaded at each boot.

Usually, a motherboard BIOS sends a microcode update to the (Intel) processor at boot time.

Linux also has a microcode update utility (called "microcode.ctl") which does the same thing.

If your bios updates the microcode, and you do it again in Linux, it hurts nothing... you are simply re-writing the same data.

Lastly, note that the above describes older 68xx Motorola and 80x86 Intel processors. The newest Intel Core 2 processors have a much more efficient internal design and execute a lot more code per clock cycle.

But, they still use the "program inside the CPU" (microcode) design.

Being a "Motorola guy", I'm supposed to despise Intel... but I do have to admit the new Core 2 architecture really is pretty darn good.

Hope this explains what you wanted to know... and please feel free to ask more if you wish.

-- Roger

---

### Post by Krupski on 2009-08-28
> **lisati said:**
> Must be time to file a bug report with the compiler's developers since they "obviously" got it wrong..... ;) 


There HAVE been times when the order of operations was not what I expected.

I don't recall if it was in C or in Basic or what... but it DID come and bite me a few times... so now I do what Steve Qualline suggests in his book "Practical C programming": Put Parenthesis Around Everything!  :)

---

### Post by Mirge on 2009-08-28
> **Krupski said:**
> Well, since multiplication comes before addition, and since I don't trust the compiler, I would write it like this:

answer = (6 * 9) + 3;

and get "answer = 57".

:)

That's what I would have expected too.

Here's Python 3.1:

```

>>> 3+6*9
57
>>>

```Though, I agree with the notion of using parentheses. It will ensure the result that you want, and let others know your intentions. Just my opinion of course :).

---

### Post by Krupski on 2009-08-28
> **Mirge said:**
> That's what I would have expected too.

Here's Python 3.1:

```

>>> 3+6*9
57
>>>

```Though, I agree with the notion of using parentheses. It will ensure the result that you want, and let others know your intentions. Just my opinion of course :).

In GWBASIC:

```

GW-BASIC 3.24
(C) Copyright Microsoft 1983,1984,1985,1986,1987,1988
60300 Bytes free
Ok
? 3 + 6 * 9
 57
Ok

```

In C:

```

#include <stdio.h>

int main(void)
{
    int n = 3 + 6 * 9;
    fprintf(stdout, "answer is %d\n", n);
    return 0;
}

```

...returns "answer is 57"


(but I am still going to use parentheses)  :)

---

