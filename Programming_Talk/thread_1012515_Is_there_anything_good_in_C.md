---
title: "Is there anything good in C?"
date: 2008-12-15
forum: Programming Talk
---

### Post by 7raTEYdCql on 2008-12-15
I recently posted something on the speed of python. I like the language myself. 

But was just thinking about the following. Does C have any good points? I mean down here in India i still wonder why C is always thought to as a first language to programming. When there are so many others out there.

Any opinion anybody?

---

### Post by jimi_hendrix on 2008-12-15
speed, being international psuedo-code language, not insanely complex, close to the system, and most programmers know at least a bit of it...

most games or game engines use C/C++

also its the main influence for most languages...(or at least i think so...)

as in you would find python and java code relativly closer to C then to smalltalk

and you can write modules for python in C i think...

---

### Post by monkeyking on 2008-12-15
Well, I know some programming languages.
But I've never used python.

So let me ask the same question,
does python have any good points?

---

### Post by namegame on 2008-12-15
Almost every language in existence has good points.

Python: easy to learn and quite useful for laying down your ideas quickly.
C: Systems Programming, one of the "faster" languages
C++: A LOT of games, again, considered to be "fast"
Lisp: Artificial Intelligence

Honestly, I could go on forever...no language is really better than any other, although specific tasks cater to specific languages, as I listed above.

---

### Post by iQuizzle on 2008-12-16
of course C has good parts...that's why python is written in it :P

but you'll find the limitations quickly of writing in "pure python" if you get into large nested loops. but this problem is easily solved! write the bulk of your code in the nice syntax of python and if you encounter a situation where you need a function to operate quickly, you can write it in C, compile it and call it **directly** into python (look up "python extensions").

---

### Post by OutOfReach on 2008-12-16
I've found while learning C that you can do a lot more things with it that you couldn't do with Python. It is also more closer to the system as other people have said.

---

### Post by jimi_hendrix on 2008-12-16
> **OutOfReach said:**
> I've found while learning C that you can do a lot more things with it that you couldn't do with Python.

like segfault :)

but seriously you can do ALOT of low level stuff in C...

---

### Post by mssever on 2008-12-16
> **jimi_hendrix said:**
> like segfault :)
You can segfault Python, too. I've done it. And I never figured out what was wrong, except that it only segfaulted on my laptop, and not on other machines...

---

### Post by Greyed on 2008-12-16
> **i.mehrzad said:**
> But was just thinking about the following. Does C have any good points?

It is a good systems language.  It is also one of the most used languages around.  However I think that is a matter of inertia more than anything else.

---

### Post by u-slayer on 2008-12-16
> **Greyed said:**
> It is a good systems language.  It is also one of the most used languages around.  However I think that is a matter of inertia more than anything else.

I'm curious Greyed. What other system languages do you use and what do you think about them?

---

### Post by jimi_hendrix on 2008-12-16
ASM is the best system language

---

### Post by Greyed on 2008-12-16
I don't.  My point was not that it was a widely used systems language because of inertia.  It was that it was widely used, full stop, because of inertia.  IE, while there are a good many projects suited for C there are quite a few that would be better served to be written in another language but are written in C because it is what everyone else uses.  Kinda like how Windows has maintained its stranglehold on the desktop.  The average joe looks at what everyone else uses and uses it even though there may be better, lesser used options available.

---

### Post by OutOfReach on 2008-12-16
> **jimi_hendrix said:**
> like segfault :)


Who would forget about that? :)
I could never shoot myself in the foot with Python, even if I tried.

---

### Post by samjh on 2008-12-16
> **i.mehrzad said:**
> But was just thinking about the following. Does C have any good points? I mean down here in India i still wonder why C is always thought to as a first language to programming. When there are so many others out there.

Any opinion anybody?

Yes, C has some good points:
* Speed
* Simplicity (of language, not code)
* Control
* Accessibility

C was and is a very important language in computer science.  I cannot think of even one important algorithm that has not been implemented in C (even poorly).  Almost all major operating systems contain some C code, or are written entirely in C.  Such a vast array of historical experience and industry usage, the small size and relative simplicity of the language, and its dependence on the competence of the programmer to make right design and implementation decisions, makes C a good choice for teaching students about computer programming.  It's a kind of "tough love" way to teach programming, but it is undoubtedly effective.

---

### Post by mmix on 2008-12-16
c is portable machine language

> Why have a machine language?

Many readers are no doubt thinking, ``Why does Knuth replace MIX by another machine instead of just sticking to a high-level programming language? Hardly anybody uses assemblers these days.''

Such people are entitled to their opinions, and they need not bother reading the machine-language parts of my books. But the reasons for machine language that I gave in the preface to Volume 1, written in the early 1960s, remain valid today:

    * One of the principal goals of my books is to show how high-level constructions are actually implemented in machines, not simply to show how they are applied. I explain coroutine linkage, tree structures, random number generation, high-precision arithmetic, radix conversion, packing of data, combinatorial searching, recursion, etc., from the ground up.
    * The programs needed in my books are generally so short that their main points can be grasped easily.
    * People who are more than casually interested in computers should have at least some idea of what the underlying hardware is like. Otherwise the programs they write will be pretty weird.
    * Machine language is necessary in any case, as output of many of the software programs I describe.
    * Expressing basic methods like algorithms for sorting and searching in machine language makes it possible to carry out meaningful studies of the effects of cache and RAM size and other hardware characteristics (memory speed, pipelining, multiple issue, lookaside buffers, the size of cache blocks, etc.) when comparing different schemes.

Moreover, if I did use a high-level language, what language should it be? In the 1960s I would probably have chosen Algol W; in the 1970s, I would then have had to rewrite my books using Pascal; in the 1980s, I would surely have changed everything to C; in the 1990s, I would have had to switch to C++ and then probably to Java. In the 2000s, yet another language will no doubt be de rigueur. I cannot afford the time to rewrite my books as languages go in and out of fashion; languages aren't the point of my books, the point is rather what you can do in your favorite language. My books focus on timeless truths. 

---

### Post by CptPicard on 2008-12-16
> **i.mehrzad said:**
> Does C have any good points?

> **monkeyking said:**
> 
does python have any good points?

Man.. this almost looks like intentional trolling :)

> **jimi_hendrix said:**
> 
also its the main influence for most languages...(or at least i think so...)

I think you'd have to go further back... look at Algol for the C-style block-structure inspiration.

> **namegame said:**
> 
Lisp: Artificial Intelligence

This is overhyped, because back in the day they really believed that switching over to symbolic computation would help with the underlying problems of AI. They ended up being of more general algorithmic nature of course, so changing languages didn't help... however, they managed to invent a language that *generally**yields very well to hard problem-solving... even solving problems that don't have anything to do with AI.

> 
Honestly, I could go on forever...no language is really better than any other, although specific tasks cater to specific languages, as I listed above.

I really don't believe this. There indeed are some specific fields where indeed some more specialized language does better, but then there is also the very *general task* of modelling and solving problems, where you need a general-purpose programming language, and I really do think that a lot of other languages do better at this than "other languages".


> **iQuizzle said:**
> of course C has good parts...that's why python is written in it :P

It doesn't have to be, although CPython is.

> **OutOfReach said:**
> I've found while learning C that you can do a lot more things with it that you couldn't do with Python.

Such as? (pointers don't count, they're just computationally analogous to array indexes).

---

### Post by nvteighen on 2008-12-16
C is a great low-level language and very useful if you use it for that purpose: it's widely adopted, it has a huge amount of libraries available, it is a sane language, it is quite simple to learn (though not to use), etc. There are reasons why C is still among us and has no sign of extinction/obsolence yet.

Of course, if you use C for higher-level stuff, you'll see how quickly C becomes an obstacle.

---

### Post by namegame on 2008-12-16
> **CptPicard said:**
> 


This is overhyped, because back in the day they really believed that switching over to symbolic computation would help with the underlying problems of AI. They ended up being of more general algorithmic nature of course, so changing languages didn't help... however, they managed to invent a language that *generally**yields very well to hard problem-solving... even solving problems that don't have anything to do with AI.


I understand, I guess it's just one of my common misconceptions. In my VERY limited Computer Science Classes, anytime AI is mentioned, either a professor or Graduate Teacher Assistant, seems to feel compelled to mention Lisp. So I guess I just automatically associate AI with Lisp and vice versa.  

> 
I really don't believe this. There indeed are some specific fields where indeed some more specialized language does better, but then there is also the very *general task* of modelling and solving problems, where you need a general-purpose programming language, and I really do think that a lot of other languages do better at this than "other languages".



I understand what you mean. I was just trying to avoid the general flame-war that can happen when someone asks these sort of questions.
I was just trying to say that every language has it's merits *and* demerits. When someone asks a generalized question it's hard to not give a generalized answer and that is what I was trying to do.

---

### Post by dain3 on 2008-12-16
Programming languages are considered good depending on what you intend to do with them.For instance the windows and linux operating systems are built using C because the language is easily converted to bite code "0s and 1s".It is considered good for the Operating Systems because of it's efficiency when run

---

### Post by kcode on 2008-12-16
C is closer to the system, is very much justified by the fact that the kernel of nearly(or may be all) all the operating systems existing on earth, is written in C. While languages like python, C++ etc are used for application programming which is justified by the fact that most of programming challenges in different websites and forums are solved using python, which is closer to the programmer.

---

### Post by pmasiar on 2008-12-16
I wonder why people fell compelled to write half-trivial and 10% wrong explanations after far better and deeper explanation by far more informed posters were provided. Not like I deny you the opportunity to reiterate what was already (and better) said, just curious... :confused:

Maybe you are trying to retell the same in own words, so we can nitpick misunderstandings? 

Like that there do exist OS written in non-C language (even in Java: and how people wrote OS before C was even invented?), or that both C and Python are equally simple to convert to mythical 0s and 1s, namely, language parser/compiler does it? Or that even source code consists from the same 0s and 1s as a file on your disk?

---

### Post by wmcbrine on 2008-12-16
C is a *great* language, but I don't think it should be anyone's first. Personally, it was the fourth language I used seriously, which made me really appreciate it when I finally took it up (after BASIC, assembly and Pascal).

But nowadays I'm more of a Pythonista. :)

---

### Post by Cracauer on 2008-12-16
> **i.mehrzad said:**
> I recently posted something on the speed of python. I like the language myself. 

But was just thinking about the following. Does C have any good points? I mean down here in India i still wonder why C is always thought to as a first language to programming. When there are so many others out there.

Any opinion anybody?

Do you mean "what's the point of C when you have C++" or
"what's the point of C/C++ when you have more comfortable languages"?

---

### Post by 7raTEYdCql on 2008-12-16
> **Cracauer said:**
> Do you mean "what's the point of C when you have C++" or
"what's the point of C/C++ when you have more comfortable languages"?

Ya that is what i am asking. I mean i know C(fairly well). Not programmed anything big in it. But now that i am learning Python, am finding how useless C is. <Not trying to hurt anyone.>

---

### Post by slavik on 2008-12-16
for that matter, why do we need ASM? :-\

Please realise that C was born in the 70's and back then it was a high level language, as high level as we consider Perl/Python/Ruby/PHP to be. Even when assembly language came out it was a big thing, because before that, people programmed with switches in binary (or a hole puncher and a paper tape, this is before PASCAL/FORTRAN and the fancy punch cards).

EDIT: Not knowing C is like studying politics while ignoring history, or studying English while ignoring Shakespeare. IMO, any half-decent programmer can at least understand C code.

---

### Post by dwhitney67 on 2008-12-16
> **wmcbrine said:**
> C is a *great* language, but I don't think it should be anyone's first. Personally, it was the fourth language I used seriously, which made me really appreciate it when I finally took it up (after BASIC, assembly and Pascal).

But nowadays I'm more of a Pythonista. :)

Same here... my first programming language was BASIC, then Fortran 77, and then Pascal.  Finally, C came along, not by choice, but because a matter of course-work at my university.

Almost 19 years later, knowledge of C and C++ (and *nix) are still helping me earn my bread-n-butter.

---

### Post by L-mental on 2008-12-17
> 
Quote:
Originally Posted by Cracauer View Post
Do you mean "what's the point of C when you have C++" or
"what's the point of C/C++ when you have more comfortable languages"?
Ya that is what i am asking.

Question: Do you mean A or B?
Answer: Yes.
:confused:

???
Please, just to know what your question is, can you tell us if do you mean "what's the point of C when you have C++" or "what's the point of C/C++ when you have more comfortable languages"?

---

### Post by pmasiar on 2008-12-17
> **slavik said:**
> Please realise that C was born in the 70's and back then it was a high level language,

C was back then and still is **system programming** language: for implementing operating systems - more like portable assembly language, and in no means high-level language. Even back then there were languages with higher abstractions (like Lisp, Prolog, APL), C never intended to compete with those.

slavik> Even when assembly language came out it was a big thing, 

yes, but programming only in assembler before FORTRAN - it was early fifties. Stone Age. :-)

BTW I did it, so I know what I am talking about, just in case ;-)

> EDIT: Not knowing C is like studying politics while ignoring history, or studying English while ignoring Shakespeare. IMO, any half-decent programmer can at least understand C code.

"Understand C" might mean different things:
(1) to be able to look at C code and have a fell what code does, 
(2) to really grok the code and appreciate subtle tricks, 
(3) to be able to write efficient C code.

Many half-decent scientist can be fully competent Python programmers and "understand C" in sense (1), but not in (2) or (3). C is not a Holy Grail, it is good language to implement efficient low-level code if you care about such things -- and complete waste of time if you don't. It's nice to know to understand how CPU does tricks, but for a geneticist researching DNA knowledge of C adds very little.

---

### Post by ussndmac on 2008-12-17
Having started programming with machine code, when we got an assembler we considered it a high level language.

Over the years I've learned and forgotten more programming languages than most know ever existed.

I guess I'm kinda jaded, but so many have been the "last language we'll ever need" and have faded into the arcain. Most have just been what the current reigning accademia wizards have proffered. You can write object oriented code with C, FORTRAN, or assembly...if you so choose.

In general, once you get low level experience, you should be able to do your job with whatever language is available and you can find docs for.

In truth very little has changed. You need to open/read/write files, display/input/interpret info. Labview has offered a "new" way to define the programs, so much so, that it is used as the language for Leggo Mindstorms. 

What the Internet has done is take programming out of the hands of the "wizards" and made it usable (though with some effort) to the masses.

But, this is just MHO...

Mac

---

### Post by Cracauer on 2008-12-17
> **i.mehrzad said:**
> Ya that is what i am asking. I mean i know C(fairly well). Not programmed anything big in it. But now that i am learning Python, am finding how useless C is. <Not trying to hurt anyone.>

OK, that answered the question. But not much :)

---

### Post by Greyed on 2008-12-17
> **pmasiar said:**
> "Understand C" might mean different things:
(1) to be able to look at C code and have a fell what code does, 
(2) to really grok the code and appreciate subtle tricks, 
(3) to be able to write efficient C code.


Well, I consider myself a competent Python coder but my C is sub part.  I could barely get by on the scale of 1.  I know why, too.  Pointers.  Just don't get 'em.  Which is really odd since I have no problem with the exact same concepts in Python.  I mean I understand why the following is bad juju.

[php]
a = [1,2]
b = a
b[0] = 3
[/php]

On the other hand I really think there should be four levels.  Being aware of how C impacts your code or the code of others.  The perfect example came up today.

A customer had a problem where they were taking a value, applying some formulas to it to split out taxes and such then spit out a receipt.  They were surprised to see that it worked for 20,000.00 but 25,000.00 broke.  My co-worker looked at it but was stumped.  It took me about 30 seconds to realize what was happening and then about another 30-40m to prove it, explain it to my coworker and write down an explanation for our customer.

How it broke was that the 25,000.00 amount turned into a negative amount.  Since this is a financial application using floating point math is verboten.  So that 25,000.00 is really a 2,500,000 integer internally.  To obtain the tax they multiplied that amount by 1000 then divided by 1150 then subtract the resulting amount from the base amount and call it a day.

2,500,000 times 1000 is 2,500,000,000.  31 bits is 2,147,483,648.  31 bits is significant since a signed long uses the 32nd bit to store the sign.  0 for positive, 1 for negative.  Since 2.5bil is over 2.14 (and change)bil it hits that 32nd bit and that wonderful positive number becomes a negative.  Divide and that was the negative number.  Subtract the negative number from the positive and the tax is way out of whack.

What took me so long to prove it was that I have not, in my 10 years of Python, needed to know about ctypes.  So Python was doing the sensible thing and if I pop over a bit barrier it just kept counting upwards.  Once I found ctypes...

[php]
>>> from ctypes import *
>>> a = c_long(2500000 * 1000)
>>> a
c_long(-1794967296)
>>> a.value / 1150
-1560842
>>> 2500000 - -1560842
4060842
[/php]

The math all fit since they were seeing their 25,000.00 turn into -15,608.42 and be taxed 40,608.42.

Where'd I learn all of that?  A week long C course 6 years ago.  I couldn't write a C program from memory now if I wanted to.  And I did since I installed TCC to verify my idea before finding ctypes.  But the gotchas (that you do sometimes want) like this stuck with me and, from time to time, make me look smarter than I am to my peers.  :lolflag:

So I'll admit some knowledge of the underlying structure, especially data structures, can help even in high level languages where such things are masked by sensible automation.

---

### Post by nvteighen on 2008-12-17
> **slavik said:**
> 
Please realise that C was born in the 70's and back then it was a high level language, as high level as we consider Perl/Python/Ruby/PHP to be. Even when assembly language came out it was a big thing, because before that, people programmed with switches in binary (or a hole puncher and a paper tape, this is before PASCAL/FORTRAN and the fancy punch cards).

EDIT: Not knowing C is like studying politics while ignoring history, or studying English while ignoring Shakespeare. IMO, any half-decent programmer can at least understand C code.

I agree. 

You will only be absolutely aware of how the programming technologies evolved to what he have now, what stuff got extincted (and why), etc. I don't mean you have to learn FORTRAN, COBOL, BASIC or C, but at least have some knowledge about them... C is a major point in programming languages development, so it's worth to know what it is, how it was born and what it contributed.

---

### Post by pmasiar on 2008-12-17
> **Greyed said:**
> my C is sub part.  I could barely get by on the scale of 1.  I know why, too.  Pointers.  Just don't get 'em.  Which is really odd since I have no problem with the exact same concepts in Python.

Python does not have pointers but references.

[http://en.wikipedia.org/wiki/Reference_(computer_science](http://en.wikipedia.org/wiki/Reference_(computer_science))

Pointers have no clue about the type (like reference has), it is just plain memory address. Reference knows about the object it refers to.

[http://en.wikipedia.org/wiki/Pointer](http://en.wikipedia.org/wiki/Pointer)

If you want to play with real memory pointers in some shell environment, try FORTH. It has all the power (and typeless data) of ASM, but in shell, so you can play with it, try idea without writing half-a-page of scaffolding code.

---

### Post by pp. on 2008-12-17
> **Greyed said:**
> 
How it broke was that the 25,000.00 amount turned into a negative amount.

I can see how that might stump people. But why on earth doesn't the program report a carry overflow exception or some such?

> **pmasiar said:**
> FORTH. It has all the power (and typeless data) of ASM, but in shell, so you can play with it, try idea without writing half-a-page of scaffolding code.

I take it, then, that you were not overwhelmed with joy when writing in ASM? I liked it quite a lot, especially when it was MASM/370. FORTH is nice, too, of course. I even wrote a language once which I then called NEUF (for Not Entirely Unlike Forth).

---

### Post by pmasiar on 2008-12-17
> **pp. said:**
> I take it, then, that you were not overwhelmed with joy when writing in ASM? I liked it quite a lot, especially when it was MASM/370.

Why, I liked it too of course - I did not know any better :-)

I even wrote [http://en.wikipedia.org/wiki/Conway%27s_Game_of_Life](http://en.wikipedia.org/wiki/Conway%27s_Game_of_Life) in MASM/370. About 100 instructions (not counting macros for input/output), ASM is great for stuff like that. Because we did not have access to terminals, it used paper printout - and paper was limited, too. But it was popular! :-)

But I liked ASM for PDP/11 more. It was not that hard even to code directly in binary - octal codes made sense. Very neat! 

I forced myself to grok ASM command architecture for i8080 CPU, but when looking into 286 CPU command architecture I gave up. What a mess! Even thinking that all current CPUs are forced to emulate that mess makes me sick.

---

### Post by slavik on 2008-12-17
There was an article written in 1972 that discussed how real programmers used FORTRAN and PASCAL was a toy language (I am sure you read it), the article towards the end discussed how C might be decent and how it appears to fall between FORTRAN and PASCAL to be both simpler to learn than FORTRAN but more powerful than PASCAL.

Also, before C existed, PL/I was a very big thing, and I would argue that PL/I would be more suited for OS code than C.

Also, when I say "understand" in my previous post, I mean the difinition of it you give under (1). The idea is to understand what you are doing. Obligatory analogies follow:
If you code Jython, have some idea what the JVM does.
If you code CPython, have some idea what the C code might look like.
If you press the gas pedal, have some idea what the engine/transmission/fuel pump will do.
etc ...

simple piece of code:

```

$string = "";
while ($char = getchar()) {
  $string concat $char # ~=, .=, += ... Perl6, PHP/Python/Perl5, Java/C++
}

```

Depending on the language of choice, that above code will either be very fast or very slow ...

> **pmasiar said:**
> C was back then and still is **system programming** language: for implementing operating systems - more like portable assembly language, and in no means high-level language. Even back then there were languages with higher abstractions (like Lisp, Prolog, APL), C never intended to compete with those.

slavik> Even when assembly language came out it was a big thing, 

yes, but programming only in assembler before FORTRAN - it was early fifties. Stone Age. :-)

BTW I did it, so I know what I am talking about, just in case ;-)



"Understand C" might mean different things:
(1) to be able to look at C code and have a fell what code does, 
(2) to really grok the code and appreciate subtle tricks, 
(3) to be able to write efficient C code.

Many half-decent scientist can be fully competent Python programmers and "understand C" in sense (1), but not in (2) or (3). C is not a Holy Grail, it is good language to implement efficient low-level code if you care about such things -- and complete waste of time if you don't. It's nice to know to understand how CPU does tricks, but for a geneticist researching DNA knowledge of C adds very little.

---

### Post by Greyed on 2008-12-18
> **pp. said:**
> I can see how that might stump people. But why on earth doesn't the program report a carry overflow exception or some such?

Uh... why?  That is how signed integer math works in C.  The variable didn't overflow so there is no overflow to report.  In fact remember I said that this behavior is sometimes desirable?  It is used in some cryptographic algorithms; especially in the hashing functions.

---

### Post by pmasiar on 2008-12-18
> **Greyed said:**
> Uh... why?  That is how signed integer math works in C.  

This is how **CPU** works with signed integers (last time I checked, many years ago, but...): any test for overflow are extra instructions :-)

---

### Post by pmasiar on 2008-12-18
> **slavik said:**
> There was an article written in 1972 that discussed how real programmers used FORTRAN and PASCAL was a toy language 

You mean [Real Programmers Don't Use Pascal](http://www.pbm.com/~lindahl/real.programmers.html)? It is 80ties not 70ties. Pascal was not that popular (like Java is now) untill 80ties - it takes 10 years to penetrate.

slavik> Also, before C existed, PL/I was a very big thing, and I would argue that PL/I would be more suited for OS code than C.

Why? PL/1 was way too big and complex - and was vendor-dependent (IBM only - back then when IBM was as big as MSFT was before Google). C was **designed** to be portable, and is closer to CPU.

slavik> If you code Jython, have some idea what the JVM does.
slavik> If you code CPython, have some idea what the C code might look like.

How so? Unless you read the bytecode? All I care is semantics of my language, why I should care about the CPU? Isn't all the point of higher language to abstract the CPU away?

slavik> If you press the gas pedal, have some idea what the engine/transmission/fuel pump will do.

most people don't, and don't care.

BTW, even you, mod with experience, top-posting without trimming? Nobody cares about the netiquette anymore? :confused:

---

### Post by cl333r on 2008-12-18
> **i.mehrzad said:**
> I recently posted something on the speed of python. I like the language myself. 

But was just thinking about the following. Does C have any good points? I mean down here in India i still wonder why C is always thought to as a first language to programming. When there are so many others out there.

Any opinion anybody?
Google and use wikipedia and do benchmarks. In short, the right tool for the right job.

---

### Post by crazyfuturamanoob on 2008-12-18
The legendary Quake engine was written in C, that's why C is the best language out there.

---

### Post by nvteighen on 2008-12-18
> **crazyfuturamanoob said:**
> The legendary Quake engine was written in C, that's why C is the best language out there.
The best argument in this absolutely absurd thread.

---

### Post by pp. on 2008-12-18
> **pmasiar said:**
> This is how **CPU** works with signed integers (last time I checked, many years ago, 

I'll have to take your word on that. It does, however, strike me as a silly omission in the instruction set. Calling that an integer operation when it obviously violates the definition for additions and multiplications on integer values does not seem such a good idea. However, the /370 instruction set was the last one I had a close look at, and I seem to remember that it detected integer overflows quite nicely.

---

### Post by pmasiar on 2008-12-18
> **pp. said:**
> It does, however, strike me as a silly omission in the instruction set. Calling that an integer operation when it obviously violates the definition for additions and multiplications on integer values does not seem such a good idea. 

It depends od what your definition of integer is: is it a mathematic abstraction (where you can always add 1 to any number) or the practical integer as can be modelled in a limited memory of a CPU? CPU are not abstract, and they are retty limited for pragmatic reasons. 

Processor used to have single instruction (and fast) command, something like JUMP IF CARRYOVER, but it shold be added after arithmetics operations. 

Another ("better") possibility is to set up interrupts, but interruption table is specific to each process, and you have to reload (or at least remap) it whenever you switch processes - ie quite often, and it obviously increases the cost of switch. Then, you can have single instruction to remap whole area of interrupt mappings when you switch processes - and again you pay the price in cache misses. And it uses more memory. Seems like you cannot win ... :-/

See, once you understand how CPU works, you are anxious to forget about all the bit pushing and focus on the solving the problem in a higher language? :twisted:

---

### Post by pp. on 2008-12-19
> **pmasiar said:**
> See, once you understand how CPU works, you are anxious to forget about all the bit pushing and focus on the solving the problem in a higher language? :twisted:

Yes, I do understand how CPUs work, at least in general terms, and I like contemplating the whole stack of layers from CPU up (down?) to the very core of the problem domain. Also, I don't focus on solving the problem only. I focus on making the problem.

8-)

---

### Post by pmasiar on 2008-12-19
> **pp. said:**
> Yes, I do understand how CPUs work, at least in general terms, and I like contemplating the whole stack of layers from CPU up (down?) to the very core of the problem domain. 

Another good reason to read [The Humble Programmer](http://www.cs.utexas.edu/~EWD/transcriptions/EWD03xx/EWD340.html) - in no other applied scinece they would consider to be feasible to think is so many layers of abstractions at the same time. Home builder does not consider chemical reactions in bricks to be worth to double-check every time he lays brick. Why programmers should?

---

### Post by pp. on 2008-12-19
> **pmasiar said:**
> in no other applied scinece they would consider to be feasible to think is so many layers of abstractions at the same time. Home builder does not consider chemical reactions in bricks to be worth to double-check every time he lays brick. Why programmers should?

That's an easy one. First, most software development I have been able to observe (or judge the result of) does not qualify so much as applied science than some voodoo craft. Then, the theoretical framework and the toolset for software design are at this point in time rather flimsy.

Just think that the most relevant part of most software systems is actually written in an arbitrary serialized form and much of the so called research and academical dispute is absorbed by trivial variants of the very same idea, such as how the delimiters of a text should be represented with which to note the boundaries of serialized structure elements, and whether the specification of expected data types are to be noted as parameters of the code using that data or rather as part of the procedure to be used in the quality assurance after writing the code.

---

### Post by stchman on 2008-12-19
Pretty much everything that needs to be fast is written in C.  Operating systems, the Linux kernel, Office applications, drivers.

I learned C a long time ago.  I found it pretty easy to use.  The thing that took me the longest to get used to was pointers.

---

### Post by pmasiar on 2008-12-19
> **stchman said:**
> Pretty much everything that needs to be fast is written in C.  Operating systems, the Linux kernel, Office applications, drivers.

It of course depends if you already have the most  efficient algorithm - if you do, imlementing it in most efficient language like C helps. But what if you don't? 

Lots of "speed kiddies" are obsessed by raw speed but forgot to study **what** to implement. Implementing inefficient algorithm, even if the most efficient language, is waste of time. If you don't believe me, lets compare my quicksort in Python against your bublesort in C :-) Any bets on the outcome?

PyPy - Python in Python - is effort to write Python compiler in Python, so efforts to optimize compiler would be simplified (it is simpler to try different approach in Python than in C). And it is bringigng first fruits as I gather from occasional posts on planetpython.org.

---

### Post by Greyed on 2008-12-20
> **pp. said:**
> That's an easy one. First, most software development I have been able to observe (or judge the result of) does not qualify so much as applied science than some voodoo craft. Then, the theoretical framework and the toolset for software design are at this point in time rather flimsy.

Actually as both a semi-professional programmer and an aspiring-to-be professional writer I often equate programming more with art than science.  The feeling I get from writing a particularly cleaver solution in code is identical to when I write a particularly cleaver passage of prose.  In fact some other programmers, my betters more than my peers, often say that the elegant solution is often the right solution.  The same is true of good writing.  Elegance is often a marker of corectness.

But this does not refute PMaiser's point.  He mentioned the bricklayer.  The same statement could hold for the painter, the author or the sculptor.  Rarely do those who use the medium to create often need to be intimately familiar with the other abstractions of that medium, both micro and macro.

---

### Post by slavik on 2008-12-20
> **pmasiar said:**
> Another good reason to read [The Humble Programmer](http://www.cs.utexas.edu/~EWD/transcriptions/EWD03xx/EWD340.html) - in no other applied scinece they would consider to be feasible to think is so many layers of abstractions at the same time. Home builder does not consider chemical reactions in bricks to be worth to double-check every time he lays brick. Why programmers should?

I have a home to sell you. Asbestos in the ceiling and lead based paint on the walls ... ooh and the paint is chipping, too.

---

### Post by Greyed on 2008-12-20
Was that supposed to refute his point?  Because it doesn't.  It reaffirms it.  The home builders of that day used the common materials.  When they were found to be harmful (by someone other than the homebulders) and suitable replacements found (by someone other than the homebuilders) then the homebuilders used those materials.  At no time did the thousands of people that build these houses need to be aware of the properties of the materials they were working to be able to effectively work in them.  The change happened without them.

The same is true in Programming.  Do you honestly think that for the vast majority of my Python work I have to worry about whether it is on Windows or Linux on 32 bit or 64 bit CPU or an intel vs. a non-intel cpu?

---

### Post by slavik on 2008-12-20
You're joking, right?

Do you mean to tell me that a painter, giving lead paint will actually use it when painting something?!

Please don't complain when a piece of code you use often doesn't run faste nough because the programmer is too stupid to write decent code, because according to some people, it doesn't matter ...

---

### Post by Greyed on 2008-12-20
They did.  For years.  Because **noone** knew the implications.  It certainly wasn't the painters that figured out that lead based paints were bad.  I think you need to bone up on your history.

---

### Post by dynamethod on 2008-12-20
This Thread is now about Vampire Squid.

[img]http://img508.imageshack.us/img508/1245/image0146ko.jpg[/img]


Discuss.

---

### Post by slavik on 2008-12-20
So, your point is that someone working with a material does not need to know anything about it?

---

### Post by dynamethod on 2008-12-20
> **slavik said:**
> So, your point is that someone working with a material does not need to know anything about it?

Yus.  The scientists didnt swim with the vampire squid because it lives 3,000 ft under the sea.

---

### Post by Greyed on 2008-12-20
If that's what'll get you to move along and stop being foolish, then, yes.  If not then please go back and reread what I wrote.  It is rather clear what I meant.

---

### Post by nvteighen on 2008-12-20
slavik: your analogy is wrong.

Of course a painter has to know what he's using, but does a painter produce his/her paint by combining the chemical substances or does one rather just buy paint and use it? Unless the painter is interested in producing a new painting product he can't get from the existing ones, the second alternative is the most usual.

A programmer should do the same.

---

### Post by pmasiar on 2008-12-20
> **slavik said:**
> I have a home to sell you. Asbestos in the ceiling and lead based paint on the walls ... ooh and the paint is chipping, too.

not sure what you want to prove. When I was going to buy my current house, I hired inspector - expert in that abstraction layer. Then I painted it and put in hardwood floor (after consulting another abstraction layer specialist about exact tools and technology I should use).

I am not a fool who think knows it all like you assume everyone should - I prefer to consult some specialist for every abstraction layer I encountered. My expertise is in **living** in that house, not building it.

---

### Post by pmasiar on 2008-12-20
> **slavik said:**
> So, your point is that someone working with a material does not need to know anything about it?

you like winning your fights against the strawman? feels good to be a winner, right?

If you bothered to **read** what I posted without  your quite obvious bias against **anything** I post, language wars would be tamer.

Shame that mod is doing it, but it's on your conscience, not mine.

Have a nice day

---

### Post by slavik on 2008-12-20
> **nvteighen said:**
> slavik: your analogy is wrong.

Of course a painter has to know what he's using, but does a painter produce his/her paint by combining the chemical substances or does one rather just buy paint and use it? Unless the painter is interested in producing a new painting product he can't get from the existing ones, the second alternative is the most usual.

A programmer should do the same.
Artists who painted (a few centuries ago), made their own paint, that is one of the ways that museums and related specialists can figure out whether a work is a fake or not.

---

### Post by nvteighen on 2008-12-20
> **slavik said:**
> Artists who painted (a few centuries ago), made their own paint, that is one of the ways that museums and related specialists can figure out whether a work is a fake or not.
Because a "little" state called the Ottoman Empire blocked the access to the all materials... :p

---

### Post by mssever on 2008-12-20
> **slavik said:**
> Artists who painted (a few centuries ago), made their own paint, that is one of the ways that museums and related specialists can figure out whether a work is a fake or not.
It appears that you're missing the point. Those artists had to make their own paint because no paint that met their requirements was readily available. There was also a time when programmers had no choice but to push bits around, because suitable abstraction layers weren't available or practical.

These days, the situation's different. Painters can buy paint instead of wasting their time making their own. And programmers can use higher-level abstractions, instead of wasting their time making their own.

---

### Post by pp. on 2008-12-20
> **mssever said:**
> It appears that you're missing the point.... programmers can use higher-level abstractions, instead of wasting their time making their own.

Speaking of missing the point; there are still some projects where those programmers have an edge who have a deep seated understanding of the actual workings of the computer. That has nothing whatsoever to do with actually coding in the microcode of the CPU or re-flashing the disk drive's controller or other firmware related stuff. It's about understanding, not about routinely using.

---

### Post by Cracauer on 2008-12-21
> **mssever said:**
> It appears that you're missing the point. Those artists had to make their own paint because no paint that met their requirements was readily available. There was also a time when programmers had no choice but to push bits around, because suitable abstraction layers weren't available or practical.

These days, the situation's different. Painters can buy paint instead of wasting their time making their own. And programmers can use higher-level abstractions, instead of wasting their time making their own.

It really depends on how sophisticated you want to be.

Making your own paint is something a painter today would do to get what he/she wants.  Making their own guitars is something that modern guitarists do, at least when it comes to extensive modifications.  For what they want to do in the end they have to specialize more than off-the-shelf things, even with the variety today, provides.

It's the same thing as us Common Lisp people be willing to hack up the compiler, to use inline assembly, use own own allocator and do whatever else is required to get what we want.

You see, all these languages are touring-complete. And there are so many languages to choose from. But at some level you still need to push further.

Too bad the OP still didn't say what exactly his question is about ;)

---

### Post by nvteighen on 2008-12-21
> **Cracauer said:**
> 
Too bad the OP still didn't say what exactly his question is about ;)

Yeah, again pages and pages where everyone has posted... except the OP.

---

### Post by bruce89 on 2008-12-21
> **nvteighen said:**
> Yeah, again pages and pages where everyone has posted... except the OP.

Given the title of this thread, they'll be in a fire-proof shelter taking cover.

---

### Post by samjh on 2008-12-22
> **bruce89 said:**
> Given the title of this thread, they'll be in a fire-proof shelter taking cover.

The problem is not the title, but the intense debate which inevitably follows topics like this. ;)

It's healthy, but it can be overwhelming for someone who doesn't expect it.

Or we could assume that the OP is just busy, lost interest, or other mundane reason. :p

---

### Post by 7raTEYdCql on 2008-12-23
I am still there. I did read most of the messages in the thread(excepting those i couldn't understand). I didnt lose interest, but i lost opinion. I am not that programmer frenzy as youll guys seem to be, I have not even completed a year since i have started programming. Therefore i was more of a silent watchdog.

---

### Post by 7raTEYdCql on 2008-12-23
I am sorry i didnt title the thread appropriately. But i had thought twice (if not thrice) before starting this thread. I always wanted to ask something with regard to the need of "C". And i think i was given a treat.

I surely like, the way you guys spontaneously reply to however trivial a question is and are honestly very helpful.

I would like to tell each one of you'll posters a Thank You.

---

