---
title: "C just makes my brain ache"
date: 2008-05-02
forum: Programming Talk
---

### Post by tom66 on 2008-05-02
I've never got on with C, or C++. It's the pointers and dynamic memory that gets me. I understand while, for, variables, classes, structs, templates, but it's the memory part which I'm weak on.

I'm great with many scriptable languages, Perl, PHP, SQL, JavaScript, a bit of Python and Ruby, even Spreadsheet Formula, but compiled languages are my weak point. My question is, are there any worthwhile e-books that I can learn from? Or, considering a limited budget, can someone suggest a good book to read or borrow from my local library (I live in the UK)? 

Thanks!

---

### Post by samjh on 2008-05-02
C++ Tutorial: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)
C and C++ Tutorials: [http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)
Thinking in C++ by Bruce Eckel: [http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html)

Lecture notes on C pointers and arrays (part 1): [http://www.cs.um.edu.mt/~cstaff/courses/lectures/csa2060/c6.html](http://www.cs.um.edu.mt/~cstaff/courses/lectures/csa2060/c6.html)
(part 2): [http://www.cs.um.edu.mt/~cstaff/courses/lectures/csa2060/c7.html](http://www.cs.um.edu.mt/~cstaff/courses/lectures/csa2060/c7.html)
Lecture notes on C memory management: [http://www.cs.um.edu.mt/~cstaff/courses/lectures/csa2060/c8a.html](http://www.cs.um.edu.mt/~cstaff/courses/lectures/csa2060/c8a.html)

Wikibook on C pointers: [http://en.wikibooks.org/wiki/C_Programming/Pointers_and_arrays](http://en.wikibooks.org/wiki/C_Programming/Pointers_and_arrays)
Wikibook on C memory management: [http://en.wikibooks.org/wiki/C_Programming/Memory_management](http://en.wikibooks.org/wiki/C_Programming/Memory_management)

---

### Post by CptPicard on 2008-05-02
First of all, you shouldn't worry too much about that and just code in higher level languages if you're comfortable in them. We've had a lot of discussions of the merits of manual memory management and pointers... search the forum, you'll find the threads.

But, certainly as a matter of advancing your general understanding, pointers are an important abstraction. Would be interesting to know what exactly it is you feel like you have issues with...

The easy explanation really is that the computer's memory can be thought of as a long sequence of numbered boxes where you can put stuff into. A pointer is simply a box that holds the number of some other box -- it is a variable that "points to" some other location in memory.

Dynamic memory management is just a call to the OS to reserve a block of RAM for your use. The OS responds with a pointer to the beginning of that block -- it is the address of the first byte of memory that you've been allocated. Of course, in due time, you will have to give that memory back too.

---

### Post by dwhitney67 on 2008-05-02
> **CptPicard said:**
> 
The easy explanation really is that the computer's memory can be thought of as a long sequence of numbered boxes where you can put stuff into. A pointer is simply a box that holds the number of some other box -- it is a variable that "points to" some other location in memory.

Exactly!  I usually envision a row (or a column if that is more preferable) of mail boxes at the post office.  Each box has a number (an address) and it may or may not contain a value (mail).  The pointer (the postman's thoughts?) contain the address (box number) where he plans to stuff the incoming mail.

Anyhow, software is abstract, unlike real-world things such as bridges, roads, toasters, etc.  It is easiest to understand pointers by drawing a picture of a box, or multiple boxes for larger memory allocations, onto paper/whiteboard.  Then things will become a little clearer.

---

### Post by thefestival on 2008-05-02
I've found that learning a low level assembly language will help in understanding memory/stacks in C if not C++.

I'm going through C myself right now and hope I 'bond' to it better than I did with C++.

Like you, I've until recently preferred interpreted languages and scripting such as Python and Bash scripting.

---

### Post by pmasiar on 2008-05-03
Pointers and recursion are abstractions which  can be used to separate skill level. Joel Spolsky is very unhappy about colleges teaching Java instead of C(++), because it is harder to tell skill level of Java programmer  (even smart one might not grok pointers).

---

### Post by LaRoza on 2008-05-03
> **tom66 said:**
> I've never got on with C, or C++. It's the pointers and dynamic memory that gets me. I understand while, for, variables, classes, structs, templates, but it's the memory part which I'm weak on.

I'm great with many scriptable languages, Perl, PHP, SQL, JavaScript, a bit of Python and Ruby, even Spreadsheet Formula, but compiled languages are my weak point. My question is, are there any worthwhile e-books that I can learn from? Or, considering a limited budget, can someone suggest a good book to read or borrow from my local library (I live in the UK)? 

Thanks!
See my wiki.

Pointers are simple concepts to understand, but seem strange to programmers new to a language that uses them. Reading over an assembly tutorial (see my wiki) will help you realize that C is just assembly with a syntax that is cross platform.

C is a language that allows you to get close to the hardware. This has definate advantages, but it does slow down programming for problem solving. 

With your experience, I suggest getting K&R as your C book. K&R is the only C book I have (and the internet) now.

[http://en.wikipedia.org/wiki/The_C_Programming_Language_(book](http://en.wikipedia.org/wiki/The_C_Programming_Language_(book))

Just reading over assembly tutorials can improve your understanding of C, I recommend trying it. Note, there is rarely a time when you actually have to program in assembly.

---

### Post by ecs_pf5 on 2008-05-03
That's a good reminder :)

If you're in the UK Tom > [http://tinyurl.com/5esce7](http://tinyurl.com/5esce7)  I keep on meaning to get a copy,  I can never quite get my head around pointers either so you're not alone. I understand the concept of the pigeonholes as memory locations but I always get a sort of sinking feeling that there's some additional epiphany I never quite reach[B] :(
[/B]

---

### Post by LaRoza on 2008-05-03
> **ecs_pf5 said:**
> That's a good reminder :)

If you're in the UK Tom > [http://tinyurl.com/5esce7I](http://tinyurl.com/5esce7I) keep on meaning to get a copy,  I can never quite get my head around pointers either so you're not alone. I understand the concept of the pigeonholes as memory locations but I always get a sort of sinking feeling that there's some additional epiphany I never quite reach[B] :(
[/B]

Link doesn't work.

The memory box comparison is OK, but I don't like it much. I guess when you learn assembly, the model is not needed, as pointers are totally logical in those languages.

---

### Post by ecs_pf5 on 2008-05-03
sorry, fixed ^

---

### Post by roma2 on 2008-05-03
I HIGHLY recommend Thinking in C++ by Eckel.... Don't have the link handy, but you can Google it to get the author's homepage, where he gives the book away free now in PDF format... both volumes. Fantastic read if you struggle with OOP concepts. I am using it to springboard from C and assembly into C++.

---

### Post by LaRoza on 2008-05-03
> **ecs_pf5 said:**
> sorry, fixed ^

I wonder if there is a difference between the UK and US version? 

> **roma2 said:**
> I HIGHLY recommend Thinking in C++ by Eckel.... Don't have the link handy, but you can Google it to get the author's homepage, where he gives the book away free now in PDF format... both volumes. Fantastic read if you struggle with OOP concepts. I am using it to springboard from C and assembly into C++.

I think the issue is going lower, not higher. Learning C++ will not help with C.

---

### Post by aamukahvi on 2008-05-03
Probably not what you're looking for, but have you considered C#? That's a compiled language (not in the sense that C is but anyway) and you avoid the pointers etc.

---

### Post by LaRoza on 2008-05-03
> **aamukahvi said:**
> Probably not what you're looking for, but have you considered C#? That's a compiled language (not in the sense that C is but anyway) and you avoid the pointers etc.

C# has pointers, but you have to use the "unsafe" keyword.

I don't think the issue is learning higher level languages, as the OP already has some experience (or a lot, it wasn't stated) in them.

---

### Post by nvteighen on 2008-05-03
> **LaRoza said:**
> ...Reading over an assembly tutorial (see my wiki) will help you realize that C is just assembly with a syntax that is cross platform.

Does this mean there's an actual one-to-one correspondence between C and assembly in a given platform?

---

### Post by LaRoza on 2008-05-03
> **nvteighen said:**
> Does this mean there's an actual one-to-one correspondence between C and assembly in a given platform?

In short: yes. 

In reality, the compiler does all sorts of optimizations that is almost always better than what a person could code by herself.

---

### Post by RIchard James13 on 2008-05-03
I learnt assembly before I learnt C and I still found pointers confusing. It was not until I had to implement certain data structures in C (linked lists) that I began to grasp how pointers in C are used. So I would tend to think that assembly is only part of the picture. You can write assembly programs that hardly use pointers at all. It is when you implement certain data structures and algorithms that they shine :KS

---

### Post by LaRoza on 2008-05-03
> **RIchard James13 said:**
> I learnt assembly before I learnt C and I still found pointers confusing. It was not until I had to implement certain data structures in C (linked lists) that I began to grasp how pointers in C are used. So I would tend to think that assembly is only part of the picture. You can write assembly programs that hardly use pointers at all. It is when you implement certain data structures and algorithms that they shine :KS

What kind of assembly is this? They aren't called pointers, but I haven't seen assembly not have a named location in memory (ie, a pointer) in some form.

A simple linked list is a good way to understand pointers I think.

The programming challenges in this forum (especially the first and fractions one) have examples of the user of pointers. My fractions submission was in C and used pointers. Warning: there is a pointer bug in the program at one point and I wrote it first thing in the morning in one sitting. I took a little pride in making things confusing, especially for the function to print fractions. I wanted to see how much I could do in a single statement.

---

### Post by StOoZ on 2008-05-03
> **LaRoza said:**
> See my wiki.

Pointers are simple concepts to understand, but seem strange to programmers new to a language that uses them. Reading over an assembly tutorial (see my wiki) will help you realize that C is just assembly with a syntax that is cross platform.

C is a language that allows you to get close to the hardware. This has definate advantages, but it does slow down programming for problem solving. 

With your experience, I suggest getting K&R as your C book. K&R is the only C book I have (and the internet) now.

[http://en.wikipedia.org/wiki/The_C_Programming_Language_(book](http://en.wikipedia.org/wiki/The_C_Programming_Language_(book))

Just reading over assembly tutorials can improve your understanding of C, I recommend trying it. Note, there is rarely a time when you actually have to program in assembly.


does C++ also considered as a low level language?? (write close to the hardware)

---

### Post by LaRoza on 2008-05-03
> **StOoZ said:**
> does C++ also considered as a low level language?? (write close to the hardware)

Not really. It can be used just like C, but that negates the purpose of C++. C++ is like C trying to be more.

C++'s core is very C like, with classes and some other things. In practice, external libraries (STL, Boost, QT) are used instead.

---

### Post by samjh on 2008-05-03
> **StOoZ said:**
> does C++ also considered as a low level language?? (write close to the hardware)

Neither C or C++ are truly low-level languages.  Strictly speaking, only machine opcode and assembly are low-level languages.  C, C++, etc., are high-level languages.

Having said that, C++ is capable of the same low-level memory and register manipulations as C.

Beware: C is not a subset of C++ and C++ is not a superset of C!  This is a common misconception.

C++ is mostly compatible with C in terms of syntax and primitive data types, but that's where the similarities end.  C++ uses most of C's syntax as well as C's primitive data types and standard libraries, but also includes high-level data structures like lists, stacks, queues, vectors; capability for generics; object-oriented coding, and more.  This can be seen in its standard libraries, C++ includes the C standard libraries as well as its own standard library which includes the Standard Template Library (STL).

LaRoza is right when he says C++ can be used like C, but that will defeat the purpose of using C++.

---

### Post by LaRoza on 2008-05-03
> **samjh said:**
> Neither C or C++ are truly low-level languages.  Strictly speaking, only machine opcode and assembly are low-level languages.  C, C++, etc., are high-level languages.


Assembly can be used in C directly, but I guess it depends on what qualifies as "low". I think it is a rather broad spectrum with no clear lines.

---

### Post by samjh on 2008-05-03
> **LaRoza said:**
> Assembly can be used in C directly, but I guess it depends on what qualifies as "low". I think it is a rather broad spectrum with no clear lines.

It's context dependent.  I think it's one of those things that has to change meaning as time passes.  Traditionally speaking, machine opcodes and assembly only qualified as "low level" and everything that came after was "high level".  In this day and age, that interpretation is probably becoming fast outdated.

Personally, I prefer:
Low level = opcode and assembly
Mid level = Ada, C, C++, PL/1... ie. languages that can directly manipulate memory and processor registers, but also possess high-level abstraction features.
High level = C#, Java, Python, Ruby... separates direct hardware manipulation from the programmer entirely, possessing only high-level abstraction features.

---

### Post by LaRoza on 2008-05-03
> **samjh said:**
> It's context dependent.  I think it's one of those things that has to change meaning as time passes.  Traditionally speaking, machine opcodes and assembly only qualified as "low level" and everything that came after was "high level".  In this day and age, that interpretation is probably becoming fast outdated.

Personally, I prefer:
Low level = opcode and assembly
Mid level = Ada, C, C++, PL/1... ie. languages that can directly manipulate memory and processor registers, but also possess high-level abstraction features.
High level = C#, Java, Python, Ruby... separates direct hardware manipulation from the programmer entirely, possessing only high-level abstraction features.

Rather restrictive I would think.

C#, Java and Python are on different levels. C# does have the ability to use pointers, Java doesn't and is restricted to the JVM.

---

### Post by RIchard James13 on 2008-05-03
> **LaRoza said:**
> What kind of assembly is this? They aren't called pointers, but I haven't seen assembly not have a named location in memory (ie, a pointer) in some form.

I should have been more clear. Basic pointers like memory locations are very commonly seen in Assembler, every useful program needs them. However to use pointers in the same way that they are used in C is a bit different.

The first example of a pointer in 6502 Assembly
```
      lda #$00 ; immediate mode does not point to memory
      sta $900F ; stores value of a at location $900F

```

Consider this usage of pointers in C
```
int *p;
int *a;
int i=5;
a=&i;
p=a;
*p=6;
```

Rewrite that in assembly and I end up with
```
      lda #$05
      sta i
      lda #$06
      sta i
```
Since i is always a pointer to begin with you don't need to copy it until you start altering the value of the copies

The next piece of C code alters a pointer.
```
int *p;
int i[2];
p=i;
*p=5;
p++;
*p=6;

```

Then the 6502 code would look like this
```
      ; int *p; int i[2]; p=i;
      lda <i ; load low byte of variable i
      sta $01
      lda >i ; load high byte of variable i
      sta $02
      ; *p=5;
      ldy #$00
      lda #$05
      sta ($01),y
      ; p++;
      inc $01
      ; *p=6;
      lda #$06
      sta ($01),y
```
That is pointer usage in assembler. As opposed to just referring to all memory location uses as pointers. One is simple the other is complex.

You don't have to use that sort of abstraction in assembly all the time. Especially if you are just doing simple things.

---

### Post by aamukahvi on 2008-05-03
> **LaRoza said:**
> C# has pointers, but you have to use the "unsafe" keyword.

I don't think the issue is learning higher level languages, as the OP already has some experience (or a lot, it wasn't stated) in them.

I thought the issue was "scripting vs. compiled" so that's why I suggested C#. Compiled (CIL, yes), and with garbage collection. If you really want to get dirty then you can ;)

---

### Post by LaRoza on 2008-05-03
> **aamukahvi said:**
> I thought the issue was "scripting vs. compiled" so that's why I suggested C#. Compiled (CIL, yes), and with garbage collection. If you really want to get dirty then you can ;)

Shell scripts can be compiled, and C can be interpreted.

---

### Post by CptPicard on 2008-05-03
> **pmasiar said:**
> Pointers and recursion are abstractions which  can be used to separate skill level. Joel Spolsky is very unhappy about colleges teaching Java instead of C(++), because it is harder to tell skill level of Java programmer  (even smart one might not grok pointers).

Although I wouldn't want to go down the path of a certain thread we had some time ago where it was argued that pointers have something Really Special to them. They don't.. they're just an implementation issue of particular languages. They are not magical wands of computation as was claimed, and HLLs are not any worse for not having them.

To demonstrate: Having pointers in a HLL is trivial. Consider a Python list of stuff. Now, at some point of this Python list is an integer. You take the integer and index into the list. Voilà, you just used a pointer, and it doesn't differ in any meaningful way from a C pointer.

---

### Post by pmasiar on 2008-05-03
> **samjh said:**
> 
Low level = opcode and assembly
Mid level = Ada, C, C++, PL/1... ie. languages that can directly manipulate memory and processor registers, but also possess high-level abstraction features.
High level = C#, Java, Python, Ruby... separates direct hardware manipulation from the programmer entirely, possessing only high-level abstraction features.

assembly is level by itself - it is not much of a language and does not have much of syntax.

C is arguably more 'low-level' than Ada or C++. PL/1 is basically union of features of three main languages from early 60ies (Algol, Fortan, Cobol). Including C and C++  in same group does not make sense at all. How compares OOP in C vs C++? If not, how they can be in same group?

C# is Java.NET, but including Java with dynamic languages like Python and Ruby does  not make sense again: how you define new operation in Java? What about closures, generic functions and multiple inheritance? If C# and Java are HLL, then Python and Ruby are VHLL :-) Then there are SDHLL (super-duper HLL) languages like Lisp and Forth, not constrained to single paradigm, able to significantly change and redefine itself, including syntax.

---

### Post by samjh on 2008-05-03
> **pmasiar said:**
> assembly is level by itself - it is not much of a language and does not have much of syntax.

C is arguably more 'low-level' than Ada or C++. PL/1 is basically union of features of three main languages from early 60ies (Algol, Fortan, Cobol). Including C and C++  in same group does not make sense at all. How compares OOP in C vs C++? If not, how they can be in same group?

C# is Java.NET, but including Java with dynamic languages like Python and Ruby does  not make sense again: how you define new operation in Java? What about closures, generic functions and multiple inheritance? If C# and Java are HLL, then Python and Ruby are VHLL :-) Then there are SDHLL (super-duper HLL) languages like Lisp and Forth, not constrained to single paradigm, able to significantly change and redefine itself, including syntax.

I'd have more than three levels if I wanted that kind of detail.  All I used for my classification is the language built-in ability to manipulate memory and CPU/MC registers directly (and to a lesser extent, poll CPU/MC pins).  Object-orientation and dynamic data types are completely irrelevant to the criteria I've applied.

Opcodes and assembly manipulate memory and registers directly, but don't do much else.

C, C++, Ada, and PL/1 are all capable of manipulating memory and registers, while also including higher-level features that opcodes and assembly do not have.

Python, Ruby, Java, and C# do not have the capability to directly manipulate memory and registers, hence I've classified them at the highest level.

---

### Post by LaRoza on 2008-05-03
> **samjh said:**
> 
Python, Ruby, Java, and C# do not have the capability to directly manipulate memory and registers, hence I've classified them at the highest level.
Python can use embedded C, and has ctypes. C# does have memory pointers like C's, but I am unsure of their capabilities.

---

### Post by samjh on 2008-05-03
> **LaRoza said:**
> Python can use embedded C, and has ctypes. C# does have memory pointers like C's, but I am unsure of their capabilities.

Interesting.  I wonder if ctypes in Python are capable of using register addresses in a C header file and setting them.  For instance:
#include "someweirdmcu.h"
...
char temp;
...
DDRB = 0xff;
...
PORTB = temp;

On the other hand, embedded C is C, not pure Python. ;)

---

### Post by LaRoza on 2008-05-03
> **samjh said:**
> Interesting.  I wonder if ctypes in Python are capable of using register addresses in a C header file and setting them.  For instance:
#include "someweirdmcu.h"
...
char temp;
...
DDRB = 0xff;
...
PORTB = temp;

On the other hand, embedded C is C, not pure Python. ;)

Check it out (I never used it) [http://docs.python.org/lib/module-ctypes.html](http://docs.python.org/lib/module-ctypes.html)

C code doing C things in a Python source file is not Python? There is not such thing as pure Python.

---

### Post by pmasiar on 2008-05-03
> **samjh said:**
> C, C++, Ada, and PL/1 are all capable of manipulating memory and registers, while also including higher-level features that opcodes and assembly do not have.

Python, Ruby, Java, and C# do not have the capability to directly manipulate memory and registers, hence I've classified them at the highest level.

Your levels are quite arbitrary, and you did not mentioned it in original post.

Not sure what do you mean - I did not touch C and PL/1 for 15 years :-) How you can manipulate registers in PL/1? Or you mean bit operations and shifts? Isn't the whole point of a higher language to abstract away  CPU architecture?

---

### Post by RIchard James13 on 2008-05-03
> **samjh said:**
> Personally, I prefer:
Low level = opcode and assembly
Mid level = Ada, C, C++, PL/1... ie. languages that can directly manipulate memory and processor registers, but also possess high-level abstraction features.
High level = C#, Java, Python, Ruby... separates direct hardware manipulation from the programmer entirely, possessing only high-level abstraction features.

You have confused what you can do in a language with how you have to do it.

---

### Post by samjh on 2008-05-04
> **LaRoza said:**
> Check it out (I never used it) [http://docs.python.org/lib/module-ctypes.html](http://docs.python.org/lib/module-ctypes.html)

C code doing C things in a Python source file is not Python? There is not such thing as pure Python.

Looking at the docs, it looks Python alright.

I thought you meant inline C code in Python, in which case it wouldn't be Python.

So ctypes lets Python call functions from shared libraries.  Very nice. :)

[quote=pmasiar]Your levels are quite arbitrary, and you did not mentioned it in original post.

Not sure what do you mean - I did not touch C and PL/1 for 15 years How you can manipulate registers in PL/1? Or you mean bit operations and shifts? Isn't the whole point of a higher language to abstract away CPU architecture?[/quote]Sorry, I should have been clearer.

As for PL/1, I've never used it myself.  It's just what I was taught in an overview of various programming languages.  PL/1 was originally designed for heavy industrial applications, such as robotics, and therefore possess similar capabilities for system programming as C.  At least that was the theory.  I'm open to corrections. :)

[quote=Richard James13]You have confused what you can do in a language with how you have to do it.[/quote]I've confused nothing.

Look at it this way: would someone be able to program the calculator sitting on my desk - a Casio fx-100s - using C# or Java?  I think not.  But they will probably be able to use C.

It doesn't matter that all programming languages fundamentally carry out operations by manipulating memory and registers.  The question is how much control over the hardware does a language provide to the programmer?

In Assembly or C, a programmer can specify that the value in variable temp be written to memory address 0x7F89, then moved to 0x01F6 which happens to provide access to pins 1 to 7, of which 6 is connected to a serial bus.  You cannot do that in Java or C#.

---

### Post by LaRoza on 2008-05-04
> **samjh said:**
> 
I thought you meant inline C code in Python, in which case it wouldn't be Python.


I didn't give a link to it, but you can use C code inline with Python. (Like asm with C)

If that is not "Python" then what is it? Tkinter isn't Python either, it is Tcl/Tk. Python itself is C, so that isn't Python either.

---

### Post by samjh on 2008-05-04
> **LaRoza said:**
> I didn't give a link to it, but you can use C code inline with Python. (Like asm with C)

If that is not "Python" then what is it? Tkinter isn't Python either, it is Tcl/Tk. Python itself is C, so that isn't Python either.I don't know if you're being serious or disingenuous.  If a source file has substantial content in another programming language, both languages should be mentioned.  In the context of my previous posts, I'm talking about firmware, which will obviously require substantial close-to-the-metal content.

A source file with Python and inline C code is a "Python source file with inline C".  Not just "Python".

If I wrote a C source file with inline Assembler code, I'm not going to present it in a meeting as just "C".  It is "C with inline Assembly".

A ramjet rocket with a solid-fuel booster is not just a ramjet.  It's a "ramjet with a solid-fuel booster stage".

Everything depends on context.  If you gave me a 1000 SLOC Python source file with 5 lines written in C, I can easily forgive you calling it just "Python".  On the other hand, if the 1000 SLOC Python sourece file had 500 lines of C, then I'd like you to mention the fact that it has a sizeable C content within.

---

### Post by LaRoza on 2008-05-04
> **samjh said:**
> I don't know if you're being serious or disingenuous.  If a source file has substantial content in another programming language, both languages should be mentioned.

A source file with Python and inline C code is a "Python source file with inline C".  Not just "Python".

If I wrote a C source file with inline Assembler code, I'm not going to present it in a meeting as just "C".  It is "C with inline Assembly".

A ramjet rocket with a solid-fuel booster is not just a ramjet.  It's a "ramjet with a solid-fuel booster stage".


Obviously, the bulk of the code will be in the primary language. 

Using C, one can do somethings very low level with a bit of inline assembly. With Python, it is the same way. I don't know how that is not considered Python being able to go low level when it has to.

---

### Post by samjh on 2008-05-04
> **LaRoza said:**
> Using C, one can do somethings very low level with a bit of inline assembly. With Python, it is the same way. I don't know how that is not considered Python being able to go low level when it has to.

I don't know what the full capabilities of Python's ctypes library is.

If I see someone programming a hand-held calculator or a desktop telephone using Python and ctypes, then I'm more than willing to say it is suitable for low-level programming.

What we consider low-level might differ.  For me, it means kernel and device drivers for operating systems, or firmware inside a processor or microcontroller.

---

### Post by LaRoza on 2008-05-04
> **samjh said:**
> 
What we consider low-level might differ.  For me, it means kernel and device drivers for operating systems, or firmware inside a processor or microcontroller.

Would would a module in C, being used in Python be called?

There is a driver for the USB missile launcher in Python, which requires some lower level use.

---

### Post by RIchard James13 on 2008-05-04
> **samjh said:**
> 
Look at it this way: would someone be able to program the calculator sitting on my desk - a Casio fx-100s - using C# or Java?  I think not.  But they will probably be able to use C.


That is only because the FX-100 does not have Java or C# on it. Also Java and C# on a PC probably don't have the right library for interfacing with the FX-100 hardware. If one was to write a Java runtime for a FX100 properly then in Java you could access all it's functionality.

> 
It doesn't matter that all programming languages fundamentally carry out operations by manipulating memory and registers.  The question is how much control over the hardware does a language provide to the programmer?


If you are referring to low level control access then I agree. But you can't use that to divide languages between low and high level. 

> In Assembly or C, a programmer can specify that the value in variable temp be written to memory address 0x7F89, then moved to 0x01F6 which happens to provide access to pins 1 to 7, of which 6 is connected to a serial bus.  You cannot do that in Java or C#.

Are you sure you can't do that in Java or C#? Maybe you assume they can't because they don't do it the same way C or Assembly does it, but they still can process I/O.

I don't want to be contentious but I don't agree that the difference between a high and low level language is in the way they access hardware. The difference lies in the amount of coding it takes to implement certain complex data structures (like lists).

---

### Post by LaRoza on 2008-05-04
> **samjh said:**
> 
In Assembly or C, a programmer can specify that the value in variable temp be written to memory address 0x7F89, then moved to 0x01F6 which happens to provide access to pins 1 to 7, of which 6 is connected to a serial bus.  You cannot do that in Java or C#.
C# has C like pointers, but I do not know their capabilities.

---

### Post by samjh on 2008-05-04
> **RIchard James13 said:**
> If you are referring to low level control access then I agree. But you can't use that to divide languages between low and high levelThat was the criteria traditionally used to divide programming languages.  In computer science, it still is one of the key criteria.  If you look up the terms in a computer science text, you're more than likely to find definitions that stratify languages according to their abstraction away from hardware.

> Are you sure you can't do that in Java or C#? Maybe you assume they can't because they don't do it the same way C or Assembly does it, but they still can process I/O.I'm not entirely sure about C# (just 80% sure), but I'm almost certain it isn't possible in Java.

> I don't want to be contentious but I don't agree that the difference between a high and low level language is in the way they access hardware. The difference lies in the amount of coding it takes to implement certain complex data structures (like lists).You're not disagreeing with my personal opinion, but just computer science history.

I have already stated in an earlier post (which was a reply to Pmasiar) that I'd have used more levels if that was the desired detail.  But that was not my intention.  I also stated that "high level" and "low level" are phrases that change meaning over time.

---

### Post by pmasiar on 2008-05-04
> **samjh said:**
> In Assembly or C, a programmer can specify that the value in variable temp be written to memory address 0x7F89, then moved to 0x01F6 which happens to provide access to pins 1 to 7, of which 6 is connected to a serial bus.  You cannot do that in Java or C#.

I am not expert on C# or Java but I would bet (because both are used for system programming) both have a way to manipulate memory address directly. Heck, all Basic dialects on microcomputers had PEEK and POKE. It is not a rocket science to let computer know that some variable should be allocated at certain address.

More interesting would be case of Forth, which integrates Assembler. Writing assembler (program converting mnemonic instruction into binary) is quite simple exercise in Forth. Also, Forth is such flexible language that even basic concepts like variable and constants, are defined in Forth - so you can modify them for your own purposes, as you need. Ie I used this feature (modifying internal registers) to build interface to special graphic coprocessor. Does it means that Forth is low-level? Forth is way to flexible to say that - it is extremely high-level language, a language to design customized high-level languages, easily.

I must admit that this discussion is waaay of-topic, and I can hardly follow it anymore - what is anyones point. Maybe we should invoke blub, and decide that every programming language feature what blub programmer does not need to use today should not be considered as valid distinguishing factor when evaluating languages, and ignored?

---

### Post by CptPicard on 2008-05-04
> **LaRoza said:**
> 
The memory box comparison is OK, but I don't like it much.

I was just talking to Wybiral on IRC about this, and it's too bad I was too slow to actually point this out bluntly in the thread with Shining Arcanine -- it would have demolished his argument... the memory box analogy is nothing but sort of intellectual sugar on top of the really trivial idea that:

*Pointers are equivalent to indices into an array.*

Corollary: pointers do not yield anything computationally special into a language, as they can always be reproduced in terms of an array.

That they would, is a really annoying misconception a lot of LLL advocates have :)

You just have this humongous underlying RAM array you index into. If you do C and already understand arrays, a pointer should be trivial to grasp. The pointer's value is a number that indexes the array, and dereferencing the pointer is merely another way to do an ram_array[pointer_value]. Of course, C makes this rather explicit by the fact that "arrays degenerate to pointers".

---

### Post by samjh on 2008-05-04
> **pmasiar said:**
> I must admit that this discussion is waaay of-topic, and I can hardly follow it anymore - what is anyones point. Maybe we should invoke blub, and decide that every programming language feature what blub programmer does not need to use today should not be considered as valid distinguishing factor when evaluating languages, and ignored?

It is certainly way off-topic, and there is no point.  The only reason why I kept posting is because of some people jumping down my throat (so it seemed) when I classified programming languages according to an old-school criteria.  It's certainly not the only way to classify them.

I now retire from this thread. ):P

---

### Post by pmasiar on 2008-05-04
OK just for the record, Java **can** access [absolute address](http://dictionary.zdnet.com/definition/absolute+address.html), like memory location, peripheral device, or location within a device, (to be able to access peripherals and be used for embedded systems, like mobile phones). So by definition of esteemed samjh, Java is low-level language. Does it make sense to anyone? It does not to me, so the definition (and categorization based on it) is meaningless.

---

### Post by samjh on 2008-05-04
> **pmasiar said:**
> OK just for the record, Java **can** access [absolute address](http://dictionary.zdnet.com/definition/absolute+address.html), like memory location, peripheral device, or location within a device, (to be able to access peripherals and be used for embedded systems, like mobile phones). So by definition of esteemed samjh, Java is low-level language. Does it make sense to anyone? It does not to me, so the definition (and categorization based on it) is meaningless.
Out of retirement.

Dear esteemed Pmasiar, that was not my definition.  My particular version had:
> Low level = opcode and assembly
Mid level = Ada, C, C++, PL/1... ie. languages that can directly manipulate memory and processor registers, but also possess high-level abstraction features.
High level = C#, Java, Python, Ruby... separates direct hardware manipulation from the programmer entirely, possessing only high-level abstraction features.So if Java can do absolute addresses, it will be a mid-level language. ;)  Makes sense to me.

It would not make sense under the historic definition however.

---

### Post by CptPicard on 2008-05-04
This is just semantic bickering. It's like Shining Arcanine claiming that C is a high level language because that's where he prefers to draw the line.

If one tries to communicate meaningfully, fighting over distinctions like that is pointless. The most important issue is to understand what the other side is trying to say :)

---

### Post by LaRoza on 2008-05-04
> **CptPicard said:**
> 
The most important issue is to understand what the other side is trying to say :)

And what is that supposed to mean?

---

### Post by |{urse on 2008-05-04
C is hard to learn if it's the last thing you learn. But i've read alotta your posts and you're a pretty intelligent nerd, you already understand OO and procedural programming. I took C in college and it owned me, i got everything but pointers and when something was by val or by ref. once you are able to know whats by value and whats by reference at a glance then you've got half of C in the bag ^^. An awesome book is C++ Programming Today by Barbara Johnston also the o'reilly book rocks. Personally I found myself using [www.cplusplus.com](www.cplusplus.com) more than my books.

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/) <------ !

---

### Post by RIchard James13 on 2008-05-05
My point was this

Blub Blub Blub Blub Blub Blub Blub Blub Blub Blub Blub Blub Blub 

I think the OP's question had something to do with how should I tackle the problem of the difficulty of pointers in C. The rest of the thread including most of my posts seem to have been diverging towards the question of what makes a HLL not a LLL and visa versa, which has nothing to do with the OP's question. Personally I blame Pink Ponies :-\"

---

### Post by CptPicard on 2008-05-05
> **LaRoza said:**
> And what is that supposed to mean?

That it is important to discuss *bona fide* -- that is, with the understanding that either side is trying to understand what the intent of the opposite side is. Otherwise there is the risk of just degenerating into a debate on semantics...

---

### Post by LaRoza on 2008-05-05
> **CptPicard said:**
> That it is important to discuss *bona fide* -- that is, with the understanding that either side is trying to understand what the intent of the opposite side is. Otherwise there is the risk of just degenerating into a debate on semantics...

It was supposed to be ironic...

---

### Post by CptPicard on 2008-05-05
> **LaRoza said:**
> It was supposed to be ironic...

Maybe... but it is far too common around here for people to stick to insignificant semantic details as if they really meant something as regards the argument, so it's worth pointing out...

---

### Post by tseliot on 2008-05-05
> **LaRoza said:**
> It was supposed to be ironic...
Sorry but:
[PHP]>>> import irony
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named irony[/PHP]

:lolflag:

---

