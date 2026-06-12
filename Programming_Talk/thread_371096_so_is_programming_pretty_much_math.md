---
title: "so is programming pretty much math??"
date: 2007-02-26
forum: Programming Talk
---

### Post by billdotson on 2007-02-26
I have been reading *How to think like a Computer Scientist: (The Python Book)* and I am at section 3.5  So far it seems like there is a lot of math involved.. is all programming math or is he using examples showing you that you should know the basic PEMDAS order structure and since math first so well with PEMDAS those are the examples?

How much time would you say it takes of reading and trying examples and things in Python to be able to write a useful program.

---

### Post by tht00 on 2007-02-26
> **billdotson said:**
> I have been reading *How to think like a Computer Scientist: (The Python Book)* and I am at section 3.5  So far it seems like there is a lot of math involved.. is all programming math or is he using examples showing you that you should know the basic PEMDAS order structure and since math first so well with PEMDAS those are the examples?

How much time would you say it takes of reading and trying examples and things in Python to be able to write a useful program.

No.  There _can_ be a lot of math in programming, it depends on what it is.

Most programs I write (basic apps) don't have much more math than iterating through loops and the such.  However, knowing how to do the math in code can be extremely valuable.

On the other hand, games tend to have a lot more math.  I wrote an asteroids game in visual basic 6 (back in the day) and that had quite a bit of math in it (collision detection, physics of spacecraft, etc).

So, programming is a lot more than math -- it's simply a series of instructions.

As far as being able to write a 'useful' program, that depends on a lot of things -- how fast you understand and pick up concepts, what language(s) your using, and what you're wanting to code.

I'm not familiar with Python, but I'd imagine it's a lot like learning any other language.  Start by writing small (rather useless) programs and figuring out _how_ to do things.  Then eventually, you'll be able to put together things you are learning to make something useful.  Take small bites so you aren't overwhelmed, but big enough that you are stretched (and not bored).

---

### Post by yaaarrrgg on 2007-02-26
I think one could answer the question either way and be correct.  It depends on what your idea of math is, and what kind of software you will be writing.   

All  programming really has it's roots in math.  At bottom, all the CPU is doing is simple arithmetic ....

Although on a day to day basis, I don't really use much from my Math degree when programming. :)

---

### Post by billdotson on 2007-02-26
so unless you are writing a calculator or something it is not any extremely complex math.. mostly simple algebra used for grouping thing together or something of that nature?  Just as long as it is not like doing a pre-calculus or calculus class or something.

---

### Post by malfist on 2007-02-26
You can be, it just depends on what you are doing. Say your working for a reasearch agency you would be using lots of math. Games use lots of math, other things not so much. Utilites usually do not take much math.

---

### Post by Tomosaur on 2007-02-26
As others have pointed out - if your project requires math, then you'll use math. You will still need basic maths, but you don't really need to make calculations. Loops are one example - you only need to know how many times you want something to happen. The 'maths' you would use then, follow this style:
```

variable c = 0
while c < 5
  do something
  c = c + 1

```
This would mean that something is done while c is less than 5. At the end of each iteration, c gets incremented by 1. As soon as c is 5, the loop stops.

Of course, you'll probably need to do things a little more complex than that, but most projects which don't have a real maths requirement don't really extend beyond simple multiplaction and stuff like that. You don't need to be a maths genius, is the point. Just as long as maths isn't completely alien to you, you should be able to get by.

EDIT: As for the calculator - no, you wouldn't even need to be great at maths for that. The point of a computer calculator is that the computer works out the answer. The only reason you would need maths to create a calculator is during the testing stage. If you knew the language well enough, then you could theoretically program a calculator without testing it, and thus without the need to work out solutions on your own. Obviously, not testing your product is a bad idea, but in the calculator case - it's not the programmer who has to work out the solution to an equation, it's the computer. All you need to do really is just map the buttons to different operators, and make sure the computer knows which order to calculate things. This is of course, for a basic calculator, with only the simplest of operators (namely +, -, /, % and *). For scientific calculators, you would need to know the algorithms for other operators or functions - because programming languages generally only provide the operators just mentioned.

---

### Post by Mirrorball on 2007-02-26
It all depends on what kind of programming you are doing, there can be a lot of math or very little. At work I write simulations and I couldn't have written them if I didn't know calculus and even a little physics. At home I write web applications and it only uses basic math. But make sure you know **integer division** and **remainder** and their uses. There is a lot of stupid code written by programmers that don't know these things. For instance, *n* is an even number if *n* % 2 == 0 (if you divide n by 2, the remainder is zero). There are programmers that don't know how to test for a negative number (*n* is negative if *n* < 0, it should be obvious).

---

### Post by g8m on 2007-02-26
I am terrible at math. 

But I can make programs.

My approach is, search for examples that match my needs, change some lines to my needs, write my name in it, ready, I made a program.

Programming is copying. But you cant let SCO know this, because they will sue you.

---

### Post by RedSquirrel on 2007-02-26
IMO, programming is mostly ***problem solving***, so it depends on the problem you are trying to solve (and its domain). If you're programming simulations or something like that, then sure, there will be some math involved.

There is math involved in analyzing how *efficient* your program is (e.g., how much time and memory your program uses). If you want to optimize your programs, it helps to know how to do that. On the other hand, if you're just making your own programs for fun, if they're horribly inefficient it won't be the end of the world.

---

### Post by pythonbite77 on 2007-02-26
Is programming at it's base level the implementation of computational logic? If so, what is logic? Is it not a branch of mathematical thinking? However, if areas like vectors and calculus bring you out in cold sweats, then don't worry, programming does not require such a level of mathematical ability. Unless of course your developing graphics apps which require at least a basic understanding of graph theory, which is underpinned by algebra. Don't forget, Computer Science is an extension of mathematical ideas. And of course, as has been said, Computer Science != Programming.

---

### Post by Lux Perpetua on 2007-02-26
I think of *computer science* as a branch of mathematics (a sort of "applied logic," as it were), but programming is another thing. **Edit:** actually, strong logic is a prerequisite for programming, but most other areas of math can probably be avoided if you're averse to math.

---

### Post by lnostdal on 2007-02-26
programming is art, engineering and science at the same time

[quote=billdotson]
How much time would you say it takes of reading and trying examples and things in Python to be able to write a useful program.
[/quote]
about a week

---

### Post by IYY on 2007-02-26
> **billdotson said:**
> I have been reading *How to think like a Computer Scientist: (The Python Book)* and I am at section 3.5  So far it seems like there is a lot of math involved.. is all programming math or is he using examples showing you that you should know the basic PEMDAS order structure and since math first so well with PEMDAS those are the examples?

How much time would you say it takes of reading and trying examples and things in Python to be able to write a useful program.

No, programming is not math. While the skills and intuition you learn in math are important in computer science, programming itself is an entirely different field. Even in its most theoretical essence, the algorithm is not quite a mathematical problem, because it has a notion of time and progress. As soon as you insert a loop into the mix, the problem is no longer mathematical in nature.

The truth is that you can become a decent programmer without knowing math, and you can be an excellent mathematician and find programming to be very difficult.

---

### Post by the_nomad on 2007-02-27
Real programming involves math and logic...

---

### Post by Zimmer on 2007-02-27
> **the_nomad said:**
> Real programming involves math and logic...

"HELLO WORLD"

Where's the maths?

The clue is in the words 'Programming Language'.  Learning to program generally requires the   use of the correct SYNTAX  and spelling of a new language to write instructions.
I would imagine that not many of the 18-25 year olds learning programming today will have much exposure to machine code since the speed of modern CPU's makes it less time consuming to write code in a modern 'language'.  

So, less 'maths/number crunching' I would say, more language ability coupled with an appreciation of Algebra (yes, a branch of Mathematics !) and Logic (a branch of Philosophy, originally).

..discuss... :)

---

### Post by Enselic on 2007-02-27
If you by 'math' mean, 'use logic' then yes. If you mean 'have a mathematical background', then no.

A program is simply instructions. You need the logic skills to deduce the result of a bunch of instructions. You need the logic skills figure out how to tell the computer to do a specific task.

All it takes is logical skill, and this, as any skill, can be practiced.

For the most part, the hard part of programming is not the logic, but to efficiently transform code into meaning, and vice versa. It's like reading, once you learn how to read fluently, it's easy as a pie.

It's the same with a programming language, once you painlessly and unconsciously transforms what you see into logic, programming isn't really that hard.

Practice practice practice.

---

### Post by pmasiar on 2007-02-27
> **billdotson said:**
> So far it seems like there is a lot of math involved.. is all programming math or is he using examples showing you that you should know the basic PEMDAS order structure and since math first so well with PEMDAS those are the examples?

There is a special branch of mathematics, "mathematical logic" which researches [grammar]("http://en.wikipedia.org/wiki/Grammar") of [formal languages]("http://en.wikipedia.org/wiki/Formal_language") . Some formal languages are used in real programming, other are just for research. But syntax of any programming language is described by grammar (except perl, where you need also smoke and mirrors ;-) ). [chomsky hierarchy]("http://en.wikipedia.org/wiki/Chomsky_hierarchy") describes hierarchy of grammars. grammar of Algol68 is described (or better, "generated") by grammar, so it is even more fun.

So in programming, you use different levels of "math" in these situations:

1) write valid statements in programming language - conforming to syntax
2) manipulate values of your variables storing different status of your objects
3) sometimes (but not always) you model complicated real-world situation described in complex mathematical structures (3D images, physics etc), then you have additional math requirements. 

Abstract math thinking is good mental training for developing skills needed to handle complex object models, but ability to solve differential equations is useless per se (unless your program requires it).

Many programmer can work most of their careers using "math" in sense of 1) and 2) without even touching 3), are perfectly happy and forgot all precalculus if they ever knew it :-) 

Often the math part of programming is restricted to valid syntax and manipulating objects, and math is really simple (storing values and calling methods to change status) and running totals, nothing beyond math skills of 15 year old. But you still need to keep in your mind complex data structures, and understand how your code will work on them.

Programmer's thinking is little different from pure mathematican's thinking. math thinking is analytical: you use rules to transform eqations, dig deeper to solve problems. Programmer's thinking is synthetical; use bulding blocks (statements, library calls) to enhance your basic language, build structures which when bind together, will solve problem. It is more like building from mental lego blocks. 

Anecdotal evidence: I had a friend (postgrad in astronomy) who was solving complicated differential equations and them writing program using these solution to solve complicated astronomy problem. He told me after solving his problem in math, he needed about a week to switch his thinking to programming to write and debug programs to implement his solutions, and same week to get back to math. 

I myself used precalculus-level math only once in my ife: as high school teacher, I wrote a program which used random numbers to generate tests for my students :-) beyond that, integer numbers (or fixed point decimals for money) and occasional total, average and mean was more then enough for my problems.

> How much time would you say it takes of reading and trying examples and things in Python to be able to write a useful program.

It depends of your definition of "useful" :-) ... but within hours you should be able to write a loop which requires input, processes it and makes a (simple) action - like pick a shape, input measurements and calculate area. In this simple examples math is used - to perform some marginally useful transformation of input data.

For more useful actions on data, you need more complicated data structures and objects, but this knowledge is mostly language independent (so you need to learn it only first time).

For good online books to learn python check [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart) . I maintaint there also set of programming tasks, more complicated than examples in the book but still much simpler than real task you will need to solve later.

---

### Post by yaaarrrgg on 2007-02-27
@pmasiar  Very good points!  You explained this better than I could :)

Also, it gets even blurrier, since some philosophers (W.V. O. Quine, for example, "Two Dogmas of Epiricism") have done a lot to disolve the distinction between analytic and synthetic modes of thinking. 

What most people refer to as "what math is" is really a notion of Platonism combined with some branch (or branches) of math like Calculus.  Platonism is the view that mathematical statements like '2 + 2 = 4' exists independantly of humans, is eternally true, and timeless.   Personally, I don't hold this view.  Other schools of thought (Constructivism, Intuitionism, for example) see math more like a game, with rules that are invented, and game play that is voluntarily followed.  

Hence we can take the view that everything can be subsumed under mathematics (including computer science) ... and that math is really just another invention that humans find useful.  Iin other words, there's not a lot of difference between the long division algorithm that elementary children learn, and a sort algorithm, except one executes on paper, the other, on silicon.  Very much like a computer program at bottom .... except that math is software for our brains :)

---

### Post by Praill on 2007-02-27
Yes.
Programming is one of the only real world uses for math class. Remember how you used to always say 'when would i ever use this stuff?'?
Here you go! :lolflag:

---

### Post by hod139 on 2007-02-27
@pmasiar Well said.

---

### Post by tomchuk on 2007-02-27
Dijkstra:
> 
Programming is one of the most difficult branches of applied mathematics; the poorer mathematicians had better remain pure mathematicians.


---

### Post by greg.hagen on 2007-03-02
Programming is a lot like public speaking. If you are giving a speech (or writing a program) on math, engineering or physics you will need to know a lot of math. If you are giving a speech on something simple, or something that can be explained in terms of what your audience (the computer) already knows (libraries), then the math will be pretty easy.

If you REALLY want to get into programming, a discrete math course will cover all the neat stuff you might run into.

---

### Post by Darkness3477 on 2007-03-02
I asked this question to my math teacher at school who also happened to be the Schools sysadmin, and he said that whilst some programs are maths intensive, others are not. However, the same thought process that you use in maths is used in programming. Mostly logic, of course. 

I'm not sure if I explained myself exactly as clear as he did but you should be able to understand that. 

On a side note, I'd say that me learning to program (even at the most newbiest of stages) has improved my maths abilities. Only because I now look at problems in a different light. Also most of my programs involve some simple maths.

---

### Post by s1ightcrazed on 2007-03-02
Is programming math.... 

Short answer - no. 

Long answer:

Programming often requires math, to some degree or another, and I can't really think of a program or script that I have written that doesn't at least have rudimentary math in it. I don't think you can simply say that programming IS math, because it is not. Programming can be used to accomplish math, or programming logic can require math, but this does not make the opposite true. 

Just my 2C.

---

