---
title: "New to C++ some basic questions"
date: 2008-04-06
forum: Programming Talk
---

### Post by MikeSz on 2008-04-06
Ive just tried completing a basic program that ive taken from a textbook (Sams - Teach Yourself C++), I downloaded Geany from the repositories, typed my program in exactly and tried to run it.  The compiler gave me an error - 'Compilation failed.  /bin/sh: g++ not found'  

Ive been back into Synaptic and downloaded the latest G++ that I could find and it downloaded about 7 files.  Ive gone back into Geany, loaded my program back up and get the same error.  

Am I missing something daft?  

By the way, in my compiler I also get another little message that pops up first, that reads 'g++ -Wall -c "hw.cpp" (in directory: /home/zer0cool)

---

### Post by smartbei on 2008-04-06
```

sudo aptitude install build-essential

```

Have fun!

(unless that is what you did (I wasn't exactly sure from your post)).

---

### Post by aks44 on 2008-04-06
[FAQ: Compiling your first C & C++ programs](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by MikeSz on 2008-04-06
Thanks for the tip.  Ive done what you've suggested -  although I now have another problem. Ive attached a screenshot.  I have no idea what that means or how to fix it,

---

### Post by Caduceus on 2008-04-06
It's endL not end1. With a lower-case 'l'

---

### Post by Can+~ on 2008-04-06
> **MikeSz said:**
> Thanks for the tip.  Ive done what you've suggested -  although I now have another problem. Ive attached a screenshot.  I have no idea what that means or how to fix it,

I'm not a C++ expert (since I rely on C mostly). But you're trying to define a variable inside std? What is end1? Also, shouldn't be easier to use namespace std?

*edit* ooh.. end1 = endl.

---

### Post by MikeSz on 2008-04-06
> **Caduceus said:**
> It's endL not end1. With a lower-case 'l'

That would explain that then!  lol.  Thanks.  Its printed "1" in the book (exactly as ive just typed it!) so doesnt look like an "l"

Many thanks

---

### Post by Shining Arcanine on 2008-04-06
I would suggest learning C before learning C++. C++ was designed to extend C, so it can be really useful to know C before learning C++.

---

### Post by MikeSz on 2008-04-06
I did wonder about that - though the book says you can pick up some bad habbits and confuse yourself if you try to migrate from one to the other - it says you're better off learning C++ from scratch so I'l give it a go and see how I do!  No doubt il be in here a few times :lolflag:

---

### Post by Shining Arcanine on 2008-04-06
There are two different schools of thought on this. The first is that learning C++ requires C. The second is that learning C++ should have nothing to do with C. The tradditional approach to learn C and then learn C++. That is the approach that my university takes in the courses that it still offers on C/C++.

I suggest that you at the very least get a copy of The C Programming Language to use as a reference:

[http://www.amazon.com/Programming-Language-Prentice-Hall-Software/dp/0131103628](http://www.amazon.com/Programming-Language-Prentice-Hall-Software/dp/0131103628)

Amazon is not the cheapest place to get the book (the amazon market place is better), but at least you have the ISBN number. All of the C standard libraries are available to you in C++ as well as all of the C language's features. Having some sort of reference for C is bound to be useful.

---

### Post by aks44 on 2008-04-06
> **Shining Arcanine said:**
> I would suggest learning C before learning C++. C++ was designed to extend C, so it can be really useful to know C before learning C++.

> **Shining Arcanine said:**
> All of the C standard libraries are available to you in C++ as well as all of the C language's features.

Here we go again... :lolflag:

The problem with learning C first then later moving to C++ is that during the transition phase between the two, one will happily mix C and C++ constructs without realizing that the different paradigms are *not* compatible, leading to unstable code.

eg. what's wrong with this code (which is typical C-programmer's C++ code)?

```
Foo* i = new Foo();
Foo* j = new Foo();
delete j;
delete i;
```

Most forum regulars already know where I'm heading with that example, but I'll leave it up to you to try & figure it out... :)

---

### Post by Caduceus on 2008-04-06
```
Foo* i = new Foo();
Foo* j = new Foo();
delete j;
delete i;
```

Most forum regulars already know where I'm heading with that example, but I'll leave it up to you to try & figure it out... :)[/QUOTE]

I'm not great at C++, but you're using the pointer on Foo instead of I and J?

---

### Post by smartbei on 2008-04-06
@Caduceus:
Not sure exactly what you meant, but that's not it :).

BTW - you have a missing start quote tag in your post.

---

### Post by Caduceus on 2008-04-06
I haven't learned about Pointers, so it was a guess :P

I noticed the quote thing, I deleted too much off of the start of the quote.

---

### Post by aks44 on 2008-04-06
> **Caduceus said:**
> you're using the pointer on Foo instead of I and J?

Nope, in this context [COLOR="DarkRed"]Foo* i;[/COLOR] or [COLOR="DarkRed"]Foo *i;[/COLOR] are strictly equivalent, it's only a matter of personal preference. ;)

As far as I'm concerned I find that it better suits my mind to read/write "[COLOR="DarkRed"]i is of type pointer-to-Foo[/COLOR]" rather than "[COLOR="DarkRed"]dereferencing i yields an object of type Foo[/COLOR]", but that's just me.


The code I posted really is incorrect as far as C++ goes (even though it compiles fine and may run as expected most of the time). The catch is, an equally structured C snippet would not have that flaw.

---

### Post by MikeSz on 2008-04-06
My God, have I created a monster with this thread? lol.  DIdnt want to start any debates going (especially ones that never get resolved!)

If I am going to be completely honest, I did C back at college (ten years ago), ive forgotten most of it, and the reason we didnt do C++ was, and I remember the tutor telling us, is that if we moved from procedural to object oriented it would confuse the hell out of us.  Ten years later, I was in a well known book store looking for programming books so I can get back into it, and the best looking one (Sams - Teach yourself C++ in 21 days) says at the beginning that you're better off starting from scratch with it - I've had a flit (im actually on day three already) and it does baby-walk you through everything so its easy to understand.

I only ever learned Pascal and Cobol at college so I'm hoping this will be fresh, though not completely and utterly foreign to me :lolflag:

---

### Post by scourge on 2008-04-06
> **aks44 said:**
> eg. what's wrong with this code (which is typical C-programmer's C++ code)?

```
Foo* i = new Foo();
Foo* j = new Foo();
delete j;
delete i;
```

I have to admit it, I made that mistake a few times when I was learning C++. If someone is still wondering what's wrong, here's a hint: Foo is not a function.

I've also seen C programmers mistake the 'return' statement for a function. Or maybe they just want to confuse me by writing 'return(0)'.

---

### Post by Jessehk on 2008-04-06
> **scourge said:**
> 

I've also seen C programmers mistake the 'return' statement for a function. Or maybe they just want to confuse me by writing 'return(0)'.

```

return 0;

```

is equivalent to 
```

return(0);

```

and both are perfectly valid.

---

### Post by scourge on 2008-04-07
> **Jessehk said:**
> ```

return 0;

```

is equivalent to 
```

return(0);

```

and both are perfectly valid.

I know it's valid. I just don't understand why people make it look like a function call when it's not. Seriously, why would you write 'return(0)' instead of 'return 0'?

---

### Post by Shining Arcanine on 2008-04-07
> **Caduceus said:**
> [QUOTE=aks44;4666011]```
Foo* i = new Foo();
Foo* j = new Foo();
delete j;
delete i;
```

Most forum regulars already know where I'm heading with that example, but I'll leave it up to you to try & figure it out... :)

I'm not great at C++, but you're using the pointer on Foo instead of I and J?[/QUOTE]

The pointer is left to right associative, so it will go on j instead of Foo, regardless of where it should go from a psychological standpoint.

However, since this is C++, why not simply do an allocation on the stack with:

```
Foo i, j;
```

I am right now learning C++ (in addition to Java and Fortran; someone please shoot me now), so I might be a bit off with this, but C++ is a dynamic language (in contrast to C and Fortran, which are static languages), so stack allocations can be done anywhere and they avoid the need to do memory management. With stack allocations, the allocators and deallocators are called automatically, so unless you need either a linked list, an array that is dynamically resized as the program runs or an array that gets created in one place and destroyed in another that could not be done according to scoping rules, I really do not see the point of doing a heap allocation. It will only make the code more garbage prone.

Edit: I do see a point of a heap allocation. I just remembered that some objects are huge, so it could be advantageous to use the heap instead of the stack in such circumstances to avoid doing memory copies.

> **MikeSz said:**
> My God, have I created a monster with this thread? lol.  DIdnt want to start any debates going (especially ones that never get resolved!)

If I am going to be completely honest, I did C back at college (ten years ago), ive forgotten most of it, and the reason we didnt do C++ was, and I remember the tutor telling us, is that if we moved from procedural to object oriented it would confuse the hell out of us. 

You know some amount of C. This means that the next language wars on this forum have been averted. Good job. :)

> **scourge said:**
> I know it's valid. I just don't understand why people make it look like a function call when it's not. Seriously, why would you write 'return(0)' instead of 'return 0'?

They do that for the same reason people would write "print ('some text');" in place of "print 'some text';" in PHP, personal preference, although to be quite honest, I have never seen "return (0);" used in place of "return 0;".

---

### Post by LaRoza on 2008-04-07
> **Shining Arcanine said:**
> 
However, since this is C++, why not simply do an allocation on the stack with:

I am right now learning C++ (in addition to Java and Fortran; someone please shoot me now), so I might be a bit off with this, but C++ is a dynamic language (in contrast to C and Fortran, which are static languages), so stack allocations can be done anywhere and they avoid the need to do memory management. With stack allocations, the allocators and deallocators are called automatically, so unless you need either a linked list or an array that gets created in one place and destroyed in another that could not be done according to scoping rules, I really do not see the point of doing a heap allocation. It will only make the code more garbage prone.


The use of the keyword "new" is specific to C++. C++ is NOT a dynamic language. It is static.

C++ doesn't have a garbage collector, so you have to manually manage memory, unless you use auto pointers.

You don't see the point of doing a heap allocation? Then you don't understand C++.

---

### Post by Shining Arcanine on 2008-04-07
> **LaRoza said:**
> The use of the keyword "new" is specific to C++. C++ is NOT a dynamic language. It is static.

C++ doesn't have a garbage collector, so you have to manually manage memory, unless you use auto pointers.

You don't see the point of doing a heap allocation? Then you don't understand C++.
I thought that the definition of a dynamic language was one where variables can be declared anywhere throughout the execution of a block, and not exclusively at the top. That is in contrast to C and Fortran, where variables must always be declared at the top (although Fortran does not have a stack, so it differs from C in that regard).

Checking Wikipedia, it seems that a much broader definition is in use, but that is the one that I learned:

[http://en.wikipedia.org/wiki/Dynamic_language](http://en.wikipedia.org/wiki/Dynamic_language)

By the way, I do see the point of doing a heap allocation, but not in the context provided earlier. There is something about creating a variable, doing nothing with it and then destroying it in the same scope that says do it with stack allocation to me.

---

### Post by LaRoza on 2008-04-07
> **Shining Arcanine said:**
> I thought that the definition of a dynamic language was one where variables can be declared anywhere throughout the execution of a block, and not exclusively at the top. That is in contrast to C and Fortran, where variables must always be declared at the top (although Fortran does not have a stack, so it differs from C in that regard).


Dynamic typing is not found in Java, Fortran,  C, or C++.

C allows variables to be defined anyway, when following the c99 standard.

Fortran may not either. I use Fortran 77, but there are much new versions. Fortran 90, Fortran 95, Fortran 2003, and Fortran 2008 have much more thant Fortran 77.

---

### Post by pmasiar on 2008-04-07
> **Shining Arcanine said:**
>  C++ is a dynamic language (in contrast to C and Fortran, which are static languages)

Not sure what do you mean by this. Dynamic what? All 3 are statically typed. Dynamic (non-stack) memory management, like using heap?

---

### Post by LaRoza on 2008-04-07
> **Shining Arcanine said:**
> 
Checking Wikipedia, it seems that a much broader definition is in use, but that is the one that I learned:

[http://en.wikipedia.org/wiki/Dynamic_language](http://en.wikipedia.org/wiki/Dynamic_language)


C++ isn't a dynamic language by that definition either.

> **pmasiar said:**
> Not sure what do you mean by this. Dynamic what? All 3 are statically typed. Dynamic (non-stack) memory management, like using heap?

See wiki link, but I don't know how the others were described as "static".

@Shining Arcanine, are you taught this or are you just saying these things? That wikipedia article specifically states C++ isn't a dynamic language.

---

### Post by DariusS on 2008-04-07
> **scourge said:**
> I know it's valid. I just don't understand why people make it look like a function call when it's not. Seriously, why would you write 'return(0)' instead of 'return 0'?

My understanding (currently taking c++ class) is that the return (0); is the end of the function main, and as with all functions, it is returning a value (integer, if int main(), etc... ) to the program that called the function, the operating system. in windows, the return (0) statement lets windows know that the function or program ran cleanly.
this is just how my professor explained it to me.

---

### Post by DariusS on 2008-04-07
just as an afterthought, I use g++ for debugging/running simple code that I write in gedit. having an IDE for learning c++ wasn't necessary for me.

if interested, check out this helpful page that explains how to use g++ to compile and link in the CLI.
[http://homepages.gac.edu/~mc38/2001J/documentation/g++.html](http://homepages.gac.edu/~mc38/2001J/documentation/g++.html)

---

### Post by pmasiar on 2008-04-07
@OP:

I don't believe anyone can learn C++ in 21 days - all you can do in that time is to become familiar with the syntax. It takes years to become profficient in a language, including libraries and effective use of language idioms.

Of course you need to start with a book for beginners, many will be good for first pass. Excellent series for first intro book into any are is "Head First" series, but there is only one for Java, not for C++. But you need more than single intro book.

C++ specifics is OOP programming, I highly recommend "Head first OOP & Design", it is focused on Java but it is close enough to C++. 

Another approach might be to learn and understand OOP in simple and forgiving language, like Python, then move to stricter language. It depends on your timeframe. To know agile and flexible "scripting" language to quickly manage texts  and files is very valuable, if you don't know such language now you should consider learning it anyway.

Excellent advanced book (your 2nd or 3rd) is "Thinking in C++" by Bruce Eckel. He participated in designing C++ and teaches C++, Java and OOP&D around the world. He suggests to become familiar with C syntax before learning C++, but not become too expert in C itself, because C++ is different. Bruce provides short video intro to C for free, to make his training of C++ easier. "Thinking in C++" does not explain trivial things, but "why's" of the language design, options and decisions to make, and their consequences.

---

### Post by LaRoza on 2008-04-07
> **DariusS said:**
> My understanding (currently taking c++ class) is that the return (0); is the end of the function main, and as with all functions, it is returning a value (integer, if int main(), etc... ) to the program that called the function, the operating system. in windows, the return (0) statement lets windows know that the function or program ran cleanly.
this is just how my professor explained it to me.

Yes, but return is a keyword, and not a function. The parentheses are not needed.

---

### Post by Zugzwang on 2008-04-07
> **LaRoza said:**
> Dynamic typing is not found in Java, Fortran,  C, or C++.
[..]

Sure, but Shining Arcanine didn't talk about dynamic typing but on "dynamic languages" - whatever that is. ;-) The wikipedia page isn't very clear about this either.

And regarding the stack/heap allocation issue: Probably Shining Arcanine refers to the coding style in which you try to avoid using pointers *in your program* altogether. You *can* write programs this style extremely successful. Without the pointers, you then rely on references and you allocate storage via the STL vector or list classes. Of course, there are still a lot of pointers & heap allocation behind the scenes (since references are technically pointers as well), but we simply assume that the STL implementation doesn't have any bugs, so we don't run into the memory allocation/deallocation mess.

@DariusS: "return (0);" is *strictly* equivalent to "return 0;", so it doesn't make a difference. However, "return (0);" looks like a function call which is isn't, so most style guides will not allow this. And this has nothing to do with the function main (for Windows, you're often using WinMain anyway).

---

### Post by LaRoza on 2008-04-07
> **Zugzwang said:**
> Sure, but Shining Arcanine didn't talk about dynamic typing but on "dynamic languages" - whatever that is. ;-) The wikipedia page isn't very clear about this either.


Yes it is. C++ doesn't have the listed features, and the last line in the article says C++ isn't part of that group. Quite clear to me...

> **pmasiar said:**
> 
I don't believe anyone can learn C++ in 21 days - all you can do in that time is to become familiar with the syntax. It takes years to become profficient in a language, including libraries and effective use of language idioms.


Good article on that: [http://norvig.com/21-days.html](http://norvig.com/21-days.html)

---

### Post by Shining Arcanine on 2008-04-07
> **LaRoza said:**
> @Shining Arcanine, are you taught this or are you just saying these things? That wikipedia article specifically states C++ isn't a dynamic language.

I actually learned it at some point between reading things online and talking to professors. The reading I am citing dates back to a crazy attempt I made at learning C# in high school, so my recollection is likely to be error prone. The professors I am referencing agreed that C requires all variables to be declared at the top of blocks in contrast to Java and C++. Those two things came together to form that definition of a dynamic and static languages in my head. 

I will familiarize myself with the definition on Wikipedia, but I know that C89 and C++ differ in that C requires all stack variables to be declared at the top of a block while C++ allows stack variables to be declared anywhere. There has to be some terminology to describe that restriction or the lack of it. Here is a code example that is valid in C++, but not in C (although C99 permits it now):

```
int i;

i++;

int j;
```

All of the C programming I have done is in C89, as my university has not transitioned to C99 yet, so perhaps that is the source of some of the confusion.

---

### Post by Zugzwang on 2008-04-07
> **LaRoza said:**
> Yes it is. C++ doesn't have the listed features, and the last line in the article says C++ isn't part of that group. Quite clear to me...


Sorry if my post was unclear: It referred to post #23 in which you quoted Shining Arcanine with his/her definition of "dynamic" and answered that C++ isn't dynamically typed although Shining Arcanine didn't talk about typing. The Wikipedia article isn't clear what *dynamic programming* really means (not that C++ isn't dynamic - I totally agree here)

However, it is stated that C++ doesn't *generally* fall into this category. Maybe that's because it's also stated that:
> 
However, Erik Meijer and Peter Drayton caution that any language capable of loading executable code at runtime is capable of eval in some respect, even when that code is in the form of dynamically linked shared libraries of machine code. They suggest that higher-order functions are the true measure of dynamic programming, and some languages "use eval as a poor man's substitute for higher-order functions.

BOOST adds some support for higher order functions AFAIK and then you can call it dynamic according to that definition. ;-) But I don't want to be picky here since most programmers won't ever use this, so you're of course right.

---

### Post by Shining Arcanine on 2008-04-07
> **Zugzwang said:**
> Sorry if my post was unclear: It referred to post #23 in which you quoted Shining Arcanine with his/her definition of "dynamic"
"His" is correct. Anyway, my definition was wrong and I am happy to admit that, although I do not believe anything else in post 20 was wrong.

Getting back to the original topic (or perhaps the original tangent):

```
Foo* i = new Foo();
Foo* j = new Foo();
delete j;
delete i;
```

There is no point of doing a heap allocation only to free it, when you can do a stack allocation:

> Foo i, j;

Correct me if I am wrong, but I really do not see the need for a heap allocation in this context. Both the constructors and destructors get called either way and allocating the object on the stack here is much cleaner than allocating it on the heap.

---

### Post by LaRoza on 2008-04-07
> **Shining Arcanine said:**
> "His" is correct. Anyway, my definition was wrong and I am happy to admit that, although I do not believe anything else in post 20 was wrong.

Correct me if I am wrong, but I really do not see the need for a heap allocation in this context. The destructors get called either way and allocating the object on the stack here is much cleaner than allocating it on the heap.

Out of curiosity, who was correct? Erik Meijer and Peter Drayton?

I really haven't followed the code, but it is likely not needed.

However, the heap allows for more memory, so if this object is large it may be needed.

---

### Post by smartbei on 2008-04-07
Wow this definately went on a tangent.

The point of the code sample:
```

Foo* i = new Foo();
Foo* j = new Foo();
delete j;
delete i;

```
Was to demonstrate code that might be written by good C programmers new to C++. The point (I believe I understood what aks44 meant) is that 'new' can and will throw an exception if the allocation fails, something the C programmer does not take into account (malloc just returns NULL). The stack really has nothing to do with this, as the code was meant to demonstrate a point.

---

### Post by pmasiar on 2008-04-07
> **Shining Arcanine said:**
> C requires all variables to be declared at the top of blocks in contrast to Java and C++. Those two things came together to form that definition of a dynamic and static languages in my head. 

Seems to me like you mix together: 
- memory allocation (stack vs heap), 
- variable scope, 
- limits on syntax due of compilation optimization (declaration on top of block to avoid multiple pass compilation), 
- binding the variable name to it's type (static typing vs late binding, AKA dynamic or duck typing).

These are completely different and independent concepts.

---

### Post by CptPicard on 2008-04-07
> **pmasiar said:**
> 
These are completely different and independent concepts.

Indeed they are, although in general, "dynamic" languages could loosely be called the ones that allow for some or all of the features. That is, languages where you can make use of a runtime system and where what the compiler writes into the binary is not everything you'll ever get.

This is pretty much the general line where the difference between HLL's and LLL's are drawn around these days, maybe C++ excluded...

---

### Post by aks44 on 2008-04-07
> **smartbei said:**
> The point of the code sample:
```
Foo* i = new Foo();
Foo* j = new Foo();
delete j;
delete i;
```
Was to demonstrate code that might be written by good C programmers new to C++. The point (I believe I understood what aks44 meant) is that 'new' can and will throw an exception if the allocation fails, something the C programmer does not take into account (malloc just returns NULL).

Exactly... :)

Side note: there have been debates here about whether a program should gracefully degrade when facing memory outages, and I feels there's no need to start them again. That's the very reason why I used a class (Foo) in the sample: as we don't know anything about that class, we *_have to_* expect its constructor to (sometimes) throw. Easy way to dodge arguments about whether we should care about **new** throwing, because a constructor that throws is perfectly sane code. :p

My point being, as smartbei explained it, that the first allocation can be successful while the second one throws... boom, you've got a memory leak.

The main difference between C and C++ is that C++ supports multiple execution paths (namely, "normal" code and exception handling code), which is pretty hard to get right on itself.

If one is additionally misled by a purely cosmetic syntax similarity that makes him believe C++ is just C with OO, then all hell breaks loose.

---

### Post by scourge on 2008-04-07
> **aks44 said:**
> My point being, as smartbei explained it, that the first allocation can be successful while the second one throws... boom, you've got a memory leak.

Oh, that's right. I thought it was the use of empty parenthesis, which in stack allocation would declare a function that returns an object of class Foo. It works correctly with dynamic allocation, but that still doesn't seem like a good practice.

---

