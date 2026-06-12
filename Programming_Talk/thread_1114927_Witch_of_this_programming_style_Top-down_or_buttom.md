---
title: "Witch of this programming style Top-down or buttom-up is the best ?"
date: 2009-04-03
forum: Programming Talk
---

### Post by hoboy on 2009-04-03
I know that here they are some very brilliant people.
My question is Witch of this programming style Top-down or buttom-up is the best ?
and witch one is suitable for object oriented programming.
Please some input or a link about Top-down design will be aprreciated, or good teacher like way of explaining Top-Down design.

---

### Post by Krupski on 2009-04-03
> **hoboy said:**
> I know that here they are some very brilliant people.
My question is Witch of this programming style Top-down or buttom-up is the best ?
and witch one is suitable for object oriented programming.
Please some input or a link about Top-down design will be aprreciated, or good teacher like way of explaining Top-Down design.

Well... I do a lot of programming for Motorola microcontrollers in assembly language.

I always write the "drivers" (low level stuff) first, then write a rather dumb "top end" to call the drivers in turn to accomplish the program's task.

For example, the "main()" of my program might be (in pseudo-code):

```

      jsr   init_lcd   ;initalize the lcd display
loop  jsr   readclock  ;read clock chip as bcd
      jsr   bcd2asc    ;convert to acsii
      jsr   display    ;show current time on lcd
      jsr   delay_1    ;wait one second
      jmp   loop       ;go around again

```

Now, the subroutines such as "init_lcd" and "readclock", etc... would all be pre-written and debugged "drivers" that did the actual hardware access, set and cleared bits, checked bits, read data into a buffer, etc...

After they are written, I can forget about the details such as "which bit means 'busy' on the LCD?"... all I do is call "display" and it works.

I guess this style is called "bottom up" programming because I write the bottom parts first.

But, over time I end up with a "library" collection of subroutines. It gets to the point that I don't have to write ANYTHING except the top end "main()" because I already have the low level stuff.

So, over time I guess it turns into "top-down" programming.

In C I do the same thing. I write my functions and then re-use them in other programs.

Don't know what else to tell you...

-- Roger

---

### Post by Drone022 on 2009-04-03
When I'm puting together a design I find I go top-down.

When I get to the implementation I seem to do it bottom-up.

---

### Post by hoboy on 2009-04-03
> **Krupski said:**
> Well... I do a lot of programming for Motorola microcontrollers in assembly language.

I always write the "drivers" (low level stuff) first, then write a rather dumb "top end" to call the drivers in turn to accomplish the program's task.

For example, the "main()" of my program might be (in pseudo-code):

```

      jsr   init_lcd   ;initalize the lcd display
loop  jsr   readclock  ;read clock chip as bcd
      jsr   bcd2asc    ;convert to acsii
      jsr   display    ;show current time on lcd
      jsr   delay_1    ;wait one second
      jmp   loop       ;go around again

```

Now, the subroutines such as "init_lcd" and "readclock", etc... would all be pre-written and debugged "drivers" that did the actual hardware access, set and cleared bits, checked bits, read data into a buffer, etc...

After they are written, I can forget about the details such as "which bit means 'busy' on the LCD?"... all I do is call "display" and it works.

I guess this style is called "bottom up" programming because I write the bottom parts first.

But, over time I end up with a "library" collection of subroutines. It gets to the point that I don't have to write ANYTHING except the top end "main()" because I already have the low level stuff.

So, over time I guess it turns into "top-down" programming.

In C I do the same thing. I write my functions and then re-use them in other programs.

Don't know what else to tell you...

-- Roger
Roger thanks for your time and effort.

---

### Post by ajackson on 2009-04-03
> **Drone022 said:**
> When I'm puting together a design I find I go top-down.

When I get to the implementation I seem to do it bottom-up.
I'd go along with this approach as often the lower down stuff are the building blocks of the higher level stuff (ie support functions, utilities, etc)

---

### Post by nvteighen on 2009-04-03
I like bottom-up much better than top-down, as I like to have control of what my abstraction "ladder" is looking like. At the end, it's clearer for me... But, of course, if I found something is easier or clearer using top-down, I'd use that...

---

### Post by Simian Man on 2009-04-03
> **Drone022 said:**
> When I'm puting together a design I find I go top-down.

When I get to the implementation I seem to do it bottom-up.

I agree.

---

### Post by CptPicard on 2009-04-03
It seems to me that OOP-designs tend to more more top-down, as you need to architecture first before you're able to actually write much code. This is one of the annoying features of obsessive OOP :)

Most of the time you're likely to use both approaches and meet somewhere in the middle. Especially in languages like Lisp you're able to both exercise "wishful thinking" as a design strategy -- that is, you write your code as if you already had the pieces you expect to have -- and then you dive in and actually write them, possibly breaking the design up in new ways as warranted.  Lisp also yields well to bottom-up process, as essentially everything can be cracked out into its own little design piece that works independently of the rest of the code...

---

### Post by Simian Man on 2009-04-03
> **CptPicard said:**
> Most of the time you're likely to use both approaches and meet somewhere in the middle. Especially in languages like Lisp you're able to both exercise "wishful thinking" as a design strategy -- that is, you write your code as if you already had the pieces you expect to have -- and then you dive in and actually write them, possibly breaking the design up in new ways as warranted.  Lisp also yields well to bottom-up process, as essentially everything can be cracked out into its own little design piece that works independently of the rest of the code...

And how is that different than any other language?

---

### Post by pmasiar on 2009-04-03
> **hoboy said:**
> I know that here they are some very brilliant people.
My question is Witch of this programming style Top-down or buttom-up is the best ?
and witch one is suitable for object oriented programming.
Please some input or a link about Top-down design will be aprreciated, or good teacher like way of explaining Top-Down design.

What is best? Answer is as always: it depends.

what kind of task you want to program? Are you familiar with the problem area (ie, did 2-3 similar projects)? Do you have defined set of features to implement?

Some tasks (more infrastructure-related, in general sense, like OS) you build from bottom up, adding abstractions, APIs and services as your users and your experience suggest it. 

Other tasks have defined user, requirements, and known methods and approaches, so top-down makes more sense.

Often you don't know either, and then "from the middle out" if the best: you implement some basic abstractions, research possible bottleneck (is better to fail early), making pilot implementation to be thrown away as learning experience.

Accidentally, recently I was at hilarious presentation by Larry Wall, he suggested improvement of waterfall model, and called if "whirlpool model" - you go in loops between test, code, design, and requirements, some loops smaller some bigger, as needed.

Read "Mythical man-month" and "Test driven development". Forum's FAQ and Wikipedia are better starting places than any random advice (because both contain more mature cluon fields :-) )

---

### Post by pmasiar on 2009-04-03
> **Simian Man said:**
> And how is that different than any other language?

Because language **are** different (don't pull Turing completeness on me). Just try creating simple mock-up of any object in Java or C++, and compare it to Lisp, Forth, Perl or Python. Only then you will know what you are talking about.

---

### Post by CptPicard on 2009-04-03
> **Simian Man said:**
> And how is that different than any other language?

Well, it is. I can't think I could approach problems similarly in, say, Java, where architecture comes first much more. IDE refactorings help some, but in general, one needs to identify the objects and classes first. Static types reinforce this requirement.

I suspect this is one of those vague "you have to try it for yourself" issues, but when you have two things at your disposal -- functional-style programming tools (higher-order functions, lambda expressions) and a turing-complete all-encompassing macro system (that is, you can do any syntactic mangling within the language itself before compilation), you can both assume a lot from the little bits you expect to eventually have, and write those little bits in whatever way you please when you have to actually come up with them.

But, in a sense I do agree with you -- competent developers approach things from both directions as necessary in most languages.

---

### Post by hoboy on 2009-04-03
Thanks guy for lots of instrutives responses.

---

### Post by Simian Man on 2009-04-03
[QUOTE=pmasiar]Because language **are** different (don't pull Turing completeness on me). Just try creating simple mock-up of any object in Java or C++, and compare it to Lisp, Forth, Perl or Python. Only then you will know what you are talking about.[/QUOTE]

I know all of the languages you mentioned there -except Forth - in addition to Haskell, ML, and Erlang.  I know these languages are different, but all have the capacity for modular design in some manner.  In some languages objects are the primary tool and others its functions, but you can still create stubs and work from the top down, adding functionality as you go.  You can also write modules from the ground up building on previous layers.  I don't think language of choice really affects this all that much directly.


[quote=CptPicard]Well, it is. I can't think I could approach problems similarly in, say, Java, where architecture comes first much more. IDE refactorings help some, but in general, one needs to identify the objects and classes first. Static types reinforce this requirement.[/quote]

Well I for sure see your point here.  Java definitely seems to want you to have the scaffolding up before you really get cracking.  That's one of the reasons I hate Java, I end up fighting with the language and stupid inheritance hierarchies more than I am coding.

---

### Post by CptPicard on 2009-04-03
> **Simian Man said:**
> Well I for sure see your point here.  Java definitely seems to want you to have the scaffolding up before you really get cracking.  That's one of the reasons I hate Java, I end up fighting with the language and stupid inheritance hierarchies more than I am coding.

IMO it is a problem of the static-typed OOP paradigm in general and not just an issue of Java. I never was a huge object-believer; when I was learning in the late 90s and OOP was all the rage, I always felt like all this UML-bureaucracy was mostly bs. You end up having to create truly contrived concepts-in-terms-of-objects just to satisfy the ideology, and static typing is, in general, mostly an aid to the compiler, not to the programmer.

Now, objects do certainly exist in code... you have data, and data may, and often will, have type-system hierarchies. And operations need to be specialized according to the type of the data item. But to assume that all operations actually belong to some data item subtype is a trivialization. See Common Lisp's CLOS for an object-oriented system done right -- functions do not belong to data, but they get selected correctly based on specific types of *all* inputs.

Hmmh.. ok, that was offtopic. Anyway, add to that the flexibility you get from closures and the ability to do essentially any symbolic transformation before compilation (in terms of Lisp lists), and Lisp just... wins.

---

### Post by Simian Man on 2009-04-03
> **CptPicard]IMO it is a problem of the static-typed OOP paradigm in general and not just an issue of Java. I never was a huge object-believer said:**
> 
Well, I agree with you about the UML-OOP-Everything-must-be-in-a-class-hierarchy nonsense.  I hate that many CS departments seem to have taken up this tack in teaching the discipline.  The buzzwords may help get jobs, but it stifles thought in my opinion.

I don't agree with you on static typing, however.  I find that, if I make a mistake about what type something is, it's going to screw me up sooner or later.  Having the compiler checks in place make the error apparent at compile time as opposed to run time.  I like dynamic languages like Python and Lisp (I mostly just use Scheme) for small stuff, but for anything large enough, static typing is worth it in my opinion.  If you combine it with ML-style type inference, its a win-win :).

[QUOTE=CptPicard]
Now, objects do certainly exist in code... you have data, and data may, and often will, have type-system hierarchies. And operations need to be specialized according to the type of the data item. But to assume that all operations actually belong to some data item subtype is a trivialization. See Common Lisp's CLOS for an object-oriented system done right -- functions do not belong to data, but they get selected correctly based on specific types of *all* inputs.
Yeah, I love Common Lisp's multiple dispatch system.  In some ways Java and C# are actually pretty bad at OOP - what they are so highly touted for.

[QUOTE=CptPicard]
Hmmh.. ok, that was offtopic. Anyway, add to that the flexibility you get from closures and the ability to do essentially any symbolic transformation before compilation (in terms of Lisp lists), and Lisp just... wins.[/QUOTE]

Maybe I just need to play with Lisp more then.  Whenever I use it I'm impressed with it, but I just can't see myself using it for anything serious.

---

### Post by pmasiar on 2009-04-03
> **Simian Man said:**
> Having the compiler checks in place make the error apparent at compile time as opposed to run time.  I like dynamic languages like Python and Lisp (I mostly just use Scheme) for small stuff, but for anything large enough, static typing is worth it in my opinion. 

For anything large, you will write tests suite, I would hope? The first and simplest one would be to check the type info?

Utility of static typing in application programs (as opposed to system utilities) is vastly oversold, IMHO. Just a thought.

---

### Post by CptPicard on 2009-04-03
> **Simian Man said:**
> The buzzwords may help get jobs, but it stifles thought in my opinion.

Fully agreed. In particular when it comes to CS, one should focus on the core concepts that relate formal logic, computability, languages and algorithms and mathematics... and it is such a pity that undergrads do not generally even get taught what a closure is, although it is such a fundamental concept!

> 
I don't agree with you on static typing, however.  I find that, if I make a mistake about what type something is, it's going to screw me up sooner or later.  Having the compiler checks in place make the error apparent at compile time as opposed to run time.

Well, this is the big debate about static vs. duck typing, and I guess we can read about it elsewhere. The core point from my POV is of course that 99% of the errors you talk about are totally trivial, and are essentially apparent right after you first try to run your program... benefits of genericity outweigh the risk. I do however fully acknowledge the simple runtime speed issue of checking types at runtime.


>  If you combine it with ML-style type inference, its a win-win :).

Now, type inference with a (pure) functional language really is a huge win, agreed. :)


> 
Maybe I just need to play with Lisp more then.  Whenever I use it I'm impressed with it, but I just can't see myself using it for anything serious.

I would suggest you do so -- it really bends to your will nicely and *you* are the limit (things like SBCL in particular). When it comes to typing btw, you should be aware that CL allows for type declarations as assertions -- you simply state that X is of type Y, and the compiler will make use of that information to produce better code -- and if the statement does not hold, you either get an error or a crash, depending on your safety level.

---

### Post by Simian Man on 2009-04-03
> **CptPicard said:**
> I would suggest you do so -- it really bends to your will nicely and *you* are the limit (things like SBCL in particular). When it comes to typing btw, you should be aware that CL allows for type declarations as assertions -- you simply state that X is of type Y, and the compiler will make use of that information to produce better code -- and if the statement does not hold, you either get an error or a crash, depending on your safety level.

Well that's a pretty nice compromise :).  What CL implementation do you recommend?

---

### Post by CptPicard on 2009-04-03
> **Simian Man said:**
> Well that's a pretty nice compromise :).  What CL implementation do you recommend?

SBCL, definitely.

I really like it how you can move easily between levels of abstraction -- as it is in the end native-compiled, at points where you really need speed you can write imperative-style code with strict type-declarations all you want, and hide that behind macros. On the other hand, when you don't need the speed and can make do with generic types, the compiler will just compile in type-checks and function dispatching and what have you. It is really very flexible. And of course all the time you have the really strong basic fundamentals of the language available... in particular, you can just grab any environment into a lambda and shove it away for later invocation. I really love closures ;)

If only there were decent GUI bindings, I would consider becoming a 100% lisper really... it is remarkable that in 50 years, there is nothing new under the sun.

---

### Post by lisati on 2009-04-03
> **hoboy said:**
> I know that here they are some very brilliant people.
My question is Witch of this programming style Top-down or buttom-up is the best ?
and witch one is suitable for object oriented programming.
Please some input or a link about Top-down design will be aprreciated, or good teacher like way of explaining Top-Down design.

I agree with some of the posters in this thread: IMO some of the talk made by proponents of a particular programming style is unmitigated hype.

Here's my two cents worth: the best way to go can be dictated by the nature of what you're trying to do and how best to get it done. 

My own style of programming (which can be a bit messy, and is influenced no doubt by learning on batch-job oriented mainframes and being exposed to top-down related methodoligies) is to start with a general appreciation of the task at hand, ask what things need to happen, and to progressively fill in details.

---

### Post by OutOfReach on 2009-04-03
I believe that the programming styles change with the language your using.
For example, when I used (and I still do) Python, I always liked top-down programming, it just felt natural.
When I write programs in C (as I am doing now) I tend to find that bottom-up is more comftorable.

---

