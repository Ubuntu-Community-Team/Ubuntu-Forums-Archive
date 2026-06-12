---
title: "Mips Assembly"
date: 2009-10-22
forum: Programming Talk
---

### Post by johnb820 on 2009-10-22
So for my computer organization class, we have been given the task of programming several floating point operations in mips assembly using only core integer instructions. My question is not how to do this but rather if anyone has any advice as to organizing my code. Assembly is so abstract and even commenting every line is not helping me organize my thoughts. I was curious whether anyone had any tips for how they programmed in assembly, especially when you start working with a dozen registers at the same time, it is very easy to get overwhelmed.

---

### Post by Can+~ on 2009-10-22
Ugh, you brought me bad memories about that (I also learnt MIPS assembly).

Before even starting a homework with Assembly, I created a .c file where I defined 32 global variables (an array), and used them as if this were registers, just for having a more "abstract" way to see the problem. Then I broke them down into the corresponding instructions.

I also have truckloads of books/manuals about MIPS, if you're interested. I think I posted them somewhere else...

*edit* [http://ubuntuforums.org/showpost.php?p=7944864&postcount=3](http://ubuntuforums.org/showpost.php?p=7944864&postcount=3)

---

### Post by johnb820 on 2009-10-22
I appreciate it. I guess it's just frustrating taking 20 lines to add two IEEE 754 fp conforming integer values. I write a few lines (with comments), use 5 registers and then look over it and can't remember what value the registers should be. It's too many things for my brain to remember at the same time. Of course it all just ends up being spaghetti by the time I'm finished.

---

### Post by vandorjw on 2009-10-23
I also had to write an assignment in Mips for school. I had to implement binary search algorithm.
I got most of the coding done, but I have trouble pushing anything into my array.
I was hoping some one can help me fix my code, or point me to some resources...

EDIT:
I figured out my majour problem, which is that specific registers have specific jobs...didn't realize this.

IRT: OP, My suggestion is to just code up the bare-bone structure and fill in as you go.
If you are already given the algorithms, write out what you would do to implement it in "C" or a language you're familiar with.
Then, step by step, "translate"  your "C" code to Mips,

---

### Post by vandorjw on 2009-10-23
This is an improved version of code I have soo far,
It still contains an error, If someone can point out to me how to get rid of it, thanks in advance.

-CC7

---

### Post by Arndt on 2009-10-23
> **cc7gir said:**
> This is an improved version of code I have soo far,
It still contains an error, If someone can point out to me how to get rid of it, thanks in advance.

-CC7

Can you describe the error?

(In what way do specific registers have specific jobs?)

---

### Post by vandorjw on 2009-10-23
Sure,

My majour problem is that I cannot write anything to the stack.
When I run my mips code in spim it sort of works,  but my entries don't get saved.

Example:
> 
Enter a number:
9
Exception occurred at PC=0x0040006c
  Unaligned address in store: 0x10010026
  Exception 5  [Address error in store]  occurred and ignored


Register $16 is the starting address of the array.
Register $17 i wanted to use like a pointer to where the top of the stack is.

$18 = n; $19 = l; $20 = m; $21 = x; $22 = r. (These are my variables.)
$2 takes user input, and then I want to put that into the array.

Hope that helps.

For now my biggest problem is saving the user input.

Thanks CC7

---

### Post by Arndt on 2009-10-23
> **cc7gir said:**
> Sure,

My majour problem is that I cannot write anything to the stack.
When I run my mips code in spim it sort of works,  but my entries don't get saved.

Example:


Register $16 is the starting address of the array.
Register $17 i wanted to use like a pointer to where the top of the stack is.

$18 = n; $19 = l; $20 = m; $21 = x; $22 = r. (These are my variables.)
$2 takes user input, and then I want to put that into the array.

Hope that helps.

For now my biggest problem is saving the user input.

Thanks CC7

It's been 18 years since I wrote MIPS assembler... Is array1 actually word (4-byte) aligned?

---

### Post by vandorjw on 2009-10-23
> **Arndt said:**
> It's been 18 years since I wrote MIPS assembler... Is array1 actually word (4-byte) aligned?

I don't know for certain, I believe it is.. 
I want it to be able to store up to 1000 integers, so I assigned it a .space 4000
I think I fixed the problem of not being able to store things...
Except when I get to my negative number, it doesn't like that one.

example
> 
Enter a number:
1
Enter a number:
2
Enter a number:
3
Enter a number:
4
Enter a number:
5
Enter a number:
-2
Exception occurred at PC=0x004000a8
  Bad address in data/stack read: 0x30031fdc
  Exception 7  [Bad data address]  occurred and ignored
negative one


Notice how it prints negative one at the bottom.. its only supposed to do that if the absolute value of the negative number is not found in the list of numbers entered previously.

I'll post my new code, the comments are a bit cleaned up now.

I feel like i am soo close....

---

### Post by vinodvvk on 2011-02-11
Hi,
I am gonna work with MIPS in near future. I am assigned with the work of exploring simulator for MIPS. I tried SPIM but not sure how to work with that. I am desperately in need of your help.

1. I found SPIM supports only assembly language. I need to use C code as well. Is there any cross compiler which can be used along with SPIM to convert my C code to assembly language.
2. Is it possible to execute more than one file(.s files) in SPIM??
3. Is it possible to create new work space instead of directly opening a file
4. Is SPIM obsolete or it can be used for MIPS??

thanks in advance.

Regards,
[COLOR=#888888]vinod[/COLOR]

---

