---
title: "looping vs. recursion"
date: 2007-08-30
forum: Programming Talk
---

### Post by slavik on 2007-08-30
question to readers: do you think that recursion is important to teach to beginners? (is it on same level of importance as looping?)

my rant: yes and yes. every loop can be a recursion, but not every recursion can be a loop. think of the Fibonacci sequence.

calc (n) { return calc(n-1)+calc(n-2); }

doing the same with loops is a bit difficult (unless you want to generate the entire sequence before hand).

EDIT: but in a case where recursion can be done with a loop, loops are faster.

---

### Post by Lord Illidan on 2007-08-30
First looping, I'd say..but recursion is also important.

---

### Post by CptPicard on 2007-08-30
After basic structures and functions, recursion is *the* issue you need to tackle next. Ability to formulate recursive structures to arbitrary depth -- that is, for functions to call themselves -- is what makes recursive languages, eh, recursive. From the theory of computation perspective, this is a very important feature! If you drop recursion, you actually lose big time in the expressiveness and power of your language (at least you will be forced to introduce explicit stack to maintain Turing-equivalence) -- and interestingly, if you introduce recursion, that's pretty much all you need in your language *in general*, and all the rest is just syntactic sugar (check out lambda calculus)...

So once you've brought up functions, certainly you will tell the n00b that "btw, a function can call itself and that is where the Real Ultimate Power is for any programming language. And no, you're not getting any more power by using Assembly."

And I don't understand why generating the Fibonacci sequence in a loop is difficult... it's not. And it's actually more efficient than the recursive definition, as the recursion does more work (consider that for f(n), f(n-2) gets called, and it gets called for f(n-1) as well, so it's called twice).

---

### Post by KaeseEs on 2007-08-30
The importance of teaching recursion varies, like a lot of things, based on why the student is learning to program.  

For instance, for a budding embedded programmer, it may best to avoid getting in the habit of using recursion entirely, because recursion of any nontrivial depth(read: usefulness) will grow the stack insanely, which is a Bad Thing on resource-starved systems (many of which don't even have a hardware stack).

On the other hand, many algorithms are essentially recursive, and best expressed using recursion, rather than shoehorning them into an iterative model - recursion can certainly express some things quite tersely...

... which leads to my final point - when you teach recursion, teach philosophical comments at the same time.  The maintainers of your students' code (assuming they'll keep coding after they're done with the class) will thank you for knowing what the hell that block of code is *supposed* to do!

---

### Post by CptPicard on 2007-08-30
> **KaeseEs said:**
> The importance of teaching recursion varies, like a lot of things, based on why the student is learning to program.

There is absolutely no programmer worth his salt who isn't taught recursion, or why it is a fundamental concept. I wouldn't want to trust my life into the hands of some embedded device that was programmed by someone who had to avoid learning recursion so that he wouldn't fill up the stack.. ;)

Once you introduce functions in general, there is no avoiding the question of "hmmm what happens if I call the function itself". If you don't teach recursion, you trivially end up with an infinite loop (practically, until you're out of stack, of course).

I would say in this case it all goes the other way around -- an embedded programmer will have to knowledgeable about how recursion is implemented using an explicit stack, or how a tail recursion can be converted into a loop. It just means that the guy knows recursion *better* than the average Joe.

---

### Post by kknd on 2007-08-30
Fibonacci is a case where recursion is VERY explosive. Try calc the 80º fib number with a recursive algo (like yours). Then try it under the iterative way.

With data structures, you can **always** convert a recursive method into a iterative method.

---

### Post by CptPicard on 2007-08-30
> **kknd said:**
> 
With data structures, you can **always** convert a recursive method into a iterative method.

But I would really find it somewhat backwards to find a programmer write something in a non-function-call language, happily manipulating a stack on the heap, and not having at least some kind of an idea of recursion :p

Of course, with your usual stack-based programming language, you've got an implicit data structure there to back you up, so it's not much different... but it's instructive to note that lambda calculus doesn't have anything except function definition and application... stacks, implicit or explicit, are just an implementation detail.

---

### Post by bogolisk on 2007-08-30
> **CptPicard said:**
> I would say in this case it all goes the other way around -- an embedded programmer will have to knowledgeable about how recursion is implemented using an explicit stack, or how a tail recursion can be converted into a loop. It just means that the guy knows recursion *better* than the average Joe.

Agree,

[list]
[*] an embedded programmer checks the generated assembly from any non trivial code (and hot-path code.)
[*] gcc knows how to convert tail-recursion code into loop anyway.
[*] Many Scheme implementations would GC the (stack-)frames anyway so long recursion might not use that much space for (stack-)frames.
[/list]

---

### Post by KaeseEs on 2007-08-30
> **CptPicard said:**
> There is absolutely no programmer worth his salt who isn't taught recursion, or why it is a fundamental concept. I wouldn't want to trust my life into the hands of some embedded device that was programmed by someone who had to avoid learning recursion so that he wouldn't fill up the stack.. ;)

Once you introduce functions in general, there is no avoiding the question of "hmmm what happens if I call the function itself". If you don't teach recursion, you trivially end up with an infinite loop (practically, until you're out of stack, of course).

I would say in this case it all goes the other way around -- an embedded programmer will have to knowledgeable about how recursion is implemented using an explicit stack, or how a tail recursion can be converted into a loop. It just means that the guy knows recursion *better* than the average Joe.


Re-read my post - I specified that somebody who is going to be coding for a resource-limited system shouldn't get into the 'habit' of using recursion, not that they shouldn't know how!  I apologize if my wording was ambiguous, but recursion is essentially an algorithmic/mathematic concept, and lack of knowledge of it is a handicap.


Also, to bogolisk:  if you're using Scheme on a microcontroller, you're in a rather interesting situation to begin with!

---

### Post by cybrid on 2007-08-30
I think recursion is an important theme to teach to programmers, because it helps a lot to accustom  the brain to always try to break a problem into smaller ones to solve it, besides being a common mathematical tool.

---

### Post by CptPicard on 2007-08-30
> **KaeseEs said:**
> Re-read my post - I specified that somebody who is going to be coding for a resource-limited system shouldn't get into the 'habit' of using recursion, not that they shouldn't know how!  I apologize if my wording was ambiguous, but recursion is essentially an algorithmic/mathematic concept, and lack of knowledge of it is a handicap.

Yes, I can (almost) understand where you are coming from. Of course the OP was asking about how much programming beginners should be exposed to the concept of recursion, which I am sure we both can agree is a slightly ludicrous question -- as if the issue could be ignored :) So I answered that no, an embedded programmer shouldn't be exposed to the concept any less while learning :)

Anyway, just to point this out, although I am not an expert on embedded programming... recursion is, anyway, a fundamental feature of real programming, regardless of how you implement the stack... you just can't get rid of it. On real hardware, you must stick your stack somewhere, and if you don't have one, you're not Turing-complete... of course you don't want to do a recursive solution if there is an iterative solution just for the fun of it, but often there really is no avoiding the resource use, even though you might not have a hardware stack.

---

### Post by pmasiar on 2007-08-30
> **kknd said:**
> With data structures, you can **always** convert a recursive method into a iterative method.

Yup, it was my first paid job in programming: in university, staff programmer had hard time to fit processing of a photography of human face into available memory (with ratter deep recursive algorithm). Couple tricks did it nicely, one of then was to convert recursive algorithm to iterative, having my own stack (much cheaper on resources).

Ahh, those good old times when program had to fit into 100K! :-)

---

### Post by triptoe on 2007-08-30
I am a beginning programmer and while recursion looks really interesting... for the fibannoci sequence I found it much easier to use iterative.

Here is my code for fibannoci:

```
i = 1
i2 = 1

for count in range(1,25):
        i3 = i
        i += i2
        i2 = i3

print i


```

and here is recursive:

> def finbon(n):
        if n == 0 or n ==1:
                return n
        else:
                return finbon(n-1) + finbon(n-2)

print finbon(input("Enter: "))


The recursive is too slow unless you use hints but that just makes it terribly complex imo

---

### Post by slavik on 2007-08-30
but when you use a functional language (is prolog considered a functional lang?) there are ways to make the interpreter/compiler to easily see that it can reuse the stack and therefore your recursion becomes a loop :)

---

### Post by exile on 2007-08-31
I can't see any valid reason for not teaching it. Showing beginner programmers the theory and techniques behind such concepts is essential to turn them into professionals. After all who knows when they will be required to support or migrate recursive code in the future?

---

### Post by CptPicard on 2007-08-31
> **slavik said:**
> but when you use a functional language (is prolog considered a functional lang?)

Nope, it's a "logic language".

A really nasty beast at that, I almost flunked my symbolic programming class because of it, although I was pretty good at the Scheme half. I still don't understand some of those ideas about matching lists' heads and tails...

> there are ways to make the interpreter/compiler to easily see that it can reuse the stack and therefore your recursion becomes a loop

Tail recursion, that is... recursion that doesn't do anything after the recursive function call returns. func(x) { something; something else; func(x+1);  //nothing here } is equivalent to just looping over the values of x it gets during the recursion chain.

---

### Post by abadfish on 2007-08-31
Generally, the embedded programmer will avoid recursion unless there was a way to guarantee the functioin would recurse (is that even a word? :) ) a few times at most.  The biggest reason being that any function call adds to the call stack which, in turn, forces the processor to do a context switch.  This is high overhead and will likely make the embedded program, especially one in a multi-threaded real-time OS, miss its real-time requirements.  In the embedded world, a late answer is also a wrong answer.  So even if you did whatever fancy had your own stack or whatever, the overhead of a recursive call is too costly.

---

### Post by bogolisk on 2007-08-31
> **abadfish said:**
> Generally, the embedded programmer will avoid recursion unless there was a way to guarantee the functioin would recurse (is that even a word? :) ) a few times at most.

tail-recursion doesn't grow stack! And gcc can recognize most tail-recursive code.

>  The biggest reason being that any function call adds to the call stack which, in turn, forces the processor to do a context switch.

Hmmm, context-switch??? in most architectures it's a 1 instruction (and likely 1 cycle because it's a L1-write) to setup a new stack frame, RISC ISAs would likely add another instruction (1 cycle) to save the return address.

> This is high overhead and will likely make the embedded program, especially one in a multi-threaded real-time OS, miss its real-time requirements.

I don't think it's a time thing, but rather a space thing. 

>  In the embedded world, a late answer is also a wrong answer.  So even if you did whatever fancy had your own stack or whatever, the overhead of a recursive call is too costly.

Believe me, one iteration of recursion is nothing compare to calling C++ virtual call: touching the cache line containing the object, the cache line containing the vtable and  the cache line containing the function body. In the worse case it would be 3 cache lines to write out and 3 cache lines to load!!!!

---

### Post by pmasiar on 2007-08-31
> **exile said:**
> I can't see any valid reason for not teaching it. Showing beginner programmers the theory and techniques behind such concepts is essential to turn them into professionals. After all who knows when they will be required to support or migrate recursive code in the future?

I read somewhere about fundamental concepts in programming, each one **order of magnitude** more complicated, IIRC it was those:
0) Variable assignment
1) Loop
2) Function and argument
3) Variable scope
4) Recursion
5) Closures
6) OOP
7) Concurrency, parallel systems

YMMV :-)

---

### Post by bogolisk on 2007-08-31
> **pmasiar said:**
> I read somewhere about fundamental concepts in programming, each one **order of magnitude** more complicated, IIRC it was those:
0) Variable assignment
1) Loop
2) Function and argument
3) Variable scope
4) Recursion
5) Closures
6) OOP
7) Concurrency, parallel systems

YMMV :-)

OOP would be in "Computer Engineering" and not "Computer Science" like the others. All the above items, except OOP, can be used in a proof or some quantitative tests (benchmarks).

---

### Post by slavik on 2007-08-31
> **CptPicard said:**
> Nope, it's a "logic language".

A really nasty beast at that, I almost flunked my symbolic programming class because of it, although I was pretty good at the Scheme half. I still don't understand some of those ideas about matching lists' heads and tails...



Tail recursion, that is... recursion that doesn't do anything after the recursive function call returns. func(x) { something; something else; func(x+1);  //nothing here } is equivalent to just looping over the values of x it gets during the recursion chain.

I was in a similar situation, one thing I like about prolog though is the restrictive programming (is that the proper name? I forget what it is called now) that basically tells you give me all numbers that fit certain criteria (very easy to write a sudoku solver this way)

---

### Post by CptPicard on 2007-09-01
> **slavik said:**
> I was in a similar situation, one thing I like about prolog though is the restrictive programming (is that the proper name? I forget what it is called now) that basically tells you give me all numbers that fit certain criteria

"Declarative" programming. :) Yeah, it can fit some situations ok, but I just find that Prolog makes you spend most of your time trying to figure out how you're supposed to be declaring things so that you're not leaving something out, which makes things explode... or fine-tuning the search with cuts to get more speed, which takes a lot of the charm out of the declarative model, as you're just trying to turn any algorithm into a hack of a depth-first search, and having to understand a lot about how Prolog works under the hood in the process.

It really makes easy things hard, and makes you hope that you could just ¤#¤%# *tell it what to do* as imperatively it would be a piece of cake... :mad:

---

### Post by Lux Perpetua on 2007-09-01
> **slavik said:**
> think of the Fibonacci sequence.

calc (n) { return calc(n-1)+calc(n-2); }

doing the same with loops is a bit difficult (unless you want to generate the entire sequence before hand).Bad example, as others have pointed out, but I agree that recursion should be taught in intro-level programming courses. Recursion is an essential concept not only for computer science, but for problem-solving in general. In its most basic form, recursion is just the ability to reduce a problem to a simpler instance (or instances) of the same problem.

---

### Post by CptPicard on 2007-09-02
> **Lux Perpetua said:**
> Recursion is an essential concept not only for computer science, but for problem-solving in general. In its most basic form, recursion is just the ability to reduce a problem to a simpler instance (or instances) of the same problem.

This is what I've been nagging here about :) But I would go further and say that in it's most basic form, recursion is not a problem-solving technique, it's a *fundamental feature* of all [problems]("http://en.wikipedia.org/wiki/Recursive_language") that make you become a real programmer in order to solve them.

As far as loops vs. recursion go in computers, it doesn't matter where your stack is. If you aren't working with recursive structures, you aren't a programmer, period, but ... umm... finite state machine / stack automaton designer? :)

---

### Post by pmasiar on 2007-09-02
> **CptPicard said:**
> If you aren't working with recursive structures, you aren't a programmer, period, but ... umm... finite state machine / stack automaton designer? :)

LOL ... I know how to use recursion if I need it, but my web front-end for a database does not need it - so I am not a programmer? That's hard news to me... LOL. Where is "use right tool for the job" mantra?

---

### Post by CptPicard on 2007-09-02
Heh... ok, if you insist on nitpicking. You know what I mean -- if you're working with structures that exclude recursion, you're not a programmer. You might not be using it all the time, but the possibility has got to be there; otherwise you seriously restrict the class of problems you're dealing with...

---

### Post by Rplus9 on 2008-10-21
I'm quite interested in the power of recursion.  I'm teaching myself Prolog and I wrote this little program up (it's very rough) but I found it quite powerful.

I could blow out the fib(100000, X) and get an answer in less than a min.


```
/* fib Fn = Fn-1 + Fn-2 */
:- dynamic fibbo/2.
fib( X, Y ):- fibbo( X, Y ), !.
fib( 0, 0 ).
fib( 1, 1 ).
fib( X, Y ):-
    integer(X),
    X > 1,
    F1 is X - 1,
    F2 is X - 2,
    fib( F1, A1 ),
    fib( F2, A2 ),
    Y is A1 + A2,
    assertz( fibbo( X, Y ) ), !.
```

---

### Post by tbunix on 2008-10-21
of no import

as a COBOL programmer in the 80s I was of one of very few who had studied CS in college. I rose to the top of the heap because I was able to implement my own stacks and recurse through relational databases containing tree structures.

when I moved on to unix/c++ I kept my preference for iterative solutions

recurse for understanding
loop for hardware and language constraints

---

### Post by Reiger on 2008-10-21
> **slavik said:**
> question to readers: do you think that recursion is important to teach to beginners? (is it on same level of importance as looping?)

my rant: yes and yes. every loop can be a recursion, but not every recursion can be a loop. think of the Fibonacci sequence.

calc (n) { return calc(n-1)+calc(n-2); }

This example would go against your case to teach beginners, you have created an alogrithm with exponential complexity (enjoy your input of 10^100 for n! :D), whereas this problem can be solved with simple Math. In one would argue: teach math first, recursion second.

> doing the same with loops is a bit difficult (unless you want to generate the entire sequence before hand).

EDIT: but in a case where recursion can be done with a loop, loops are faster.

But yes recursion is important material beginners should sooner or later come to 'master': recusion is an essential feature in many complex data structures.

---

### Post by dribeas on 2008-10-21
> **slavik said:**
> think of the Fibonacci sequence.

calc (n) { return calc(n-1)+calc(n-2); }

doing the same with loops is a bit difficult (unless you want to generate the entire sequence before hand).

Or efficient. Your recursive implementation is SLOW (exponential on the number to calculate) while a for loop can be made in linear time.

I know it is just an example, but it is a good test on why algorithm complexity is important :)

```

unsigned long long fibo( unsigned int number )
{
   if ( number < 3 ) return 1;
   unsigned long long n = 1;
   unsigned long long n_1 = 1;
   unsigned long long n_2 = 1;
   for ( unsigned int i = 2; i < number; ++i )
   {
      n_2 = n_1;
      n_1 = n;
      n = n_2 + n_1;
   }
   return n;
}

```

Using 64 bit unsigned ints in a Core Duo 1.66GHz (g++ 4.1, no optimizer) the 40th fibonacci number took 2.6 seconds to calculate recursively, while the iterative approach was not measurable. I had to test for the 100.000th number to get a 0.002 seconds result (meaning that it took over 1 millisecond, all tests below yielded 1 millisecond) Now, the result is irrelevant (and false, 64 bits barely fit the 93th fibonacci number).

---

### Post by NovaAesa on 2008-10-21
For working out a specific term in the Fibonacci sequence you could always just use Binet's forumula. It allows the nth term of the sequence to be calculated in constant time.

I've only really had to use recursion in one situation - trees. I would hate to have to traverse a tree with iteration...

---

### Post by CptPicard on 2008-10-21
> **NovaAesa said:**
> I've only really had to use recursion in one situation - trees. I would hate to have to traverse a tree with iteration...

Well, a non-recursive implementation of quicksort is pretty vile as well... doable though!

---

### Post by Rplus9 on 2008-10-22
so if you had a compiler that would I guess keep you out of trouble as far as stack issues.

could you write efficient code ONLY using recursion instead of loops?

I'm asking this because I am finding that my Prolog code performs orders of magnitude faster (and is easier to write) than the programs I wrote in C for a software class.

What I'm really trying to find out is what magic is going on to make it so fast.  (like .002s-Prolog vs 18hours-C for a fib(61).

---

### Post by slavik on 2008-10-22
because older higher level languages (LISP, Prolog, etc.) come tail recursion optimization (which gcc should be able to detect and do if youwrite code in a certain way).

tailrecursion optimization reuses the stack frame from deeper processes for the return valf the shallower ones, so you end up running a loop without having to take upmore memory (since you have to preserve the registers and the caller's stackframe, adding at least 8-9 pushes and pops), and those that will argue about CPU's caching, keep in mind that caching works for reading not writing (since AFAIK x86 CPU caches are write-back and data may quickly become stale if therecursion is deep enough).

when doing a return in C, you want to have the function call in there, this way gcc will pickup tail-recursion, I think. I'd ask someone more familiar with gcc about writing tail-recursive code in C.

example of tail-recursion:
```

int add_one (int x) {
  if (x == 0) return 0;
  else return add_one(x-1)+1;
}
```

please note, the above code also follows the functional programming paradigm. :)

---

### Post by lisati on 2008-10-22
I'm mildly surprised that no-one has mentioned factorials (the first example of recursion I recall encountering) and the "tower of Hanoi" (the second example of recursion that I encountered, didn't understand it at the time.....)

Which is best? Depends on the problem.......along with constraints on the available resources.

---

### Post by run1206 on 2008-10-22
i learned looping first, then recursion.  i'd prefer looping over recursion 
btw, i can't stand the towers of hanoi problem. :lol:

---

### Post by dwhitney67 on 2008-10-22
When teaching a course (or a newbie programmer), it is not possible to teach looping and recursion without first introducing the concept of functions.

Generally general syntax is discussed first, followed by conditionals, then loops, and then functions.  At this point recursion can be introduced.

I have rarely ever used recursion; there is just not a need for it in most applications.

At the university level, many theoretical concepts are introduced to students, and from experience, many are never used in the real world unless you fall into a career that requires a particular need for you to know the extraneous concepts.

A little off-topic, but what is the intrinsic value of knowledge if it is not applied or not needed in one's current environment?  If you want to answer this question, think first... for instance, if a person lives in a community with no internet access, what difference does it make if they do not know how to surf the web, much less know how to use a computer?  Should this person be taught about computers anyways, or should this person be taught something more practical and useful?

---

### Post by pp. on 2008-10-22
Typically, you use an iteration ('looping') when you serially process a number of elements. You use recursion when processing a number of elements partly in parallel or when you decompose a problem into a series of converging subproblems.

There is considerable overlap of the cases where one or the other is to be used. This is so because you can formulate the problem to be solved in different ways.

Good cases in point are, of course, the fibonacci series and the factorial function. Both are easily enough expressed either way.

In most cases, the transformation of an iteration into a recursion or vice versa is a straight forward application of a few transformation rules, where applicable to the target language.

Usually one favors the construct which is more easily applied for a given language.

> **Rplus9 said:**
> What I'm really trying to find out is what magic is going on to make it so fast.  (like .002s-Prolog vs 18hours-C for a fib(61).

A difference in speed of 7 orders of magnitude can not be explained by the choice of recursion vs. iteration and not usually by the choice of language. The program which takes 18h is clearly a faulty implementation. Unless, of course, the faster one is at fault by not producing correct results.

---

### Post by Reiger on 2008-10-22
> **dribeas said:**
> Or efficient. Your recursive implementation is SLOW (exponential on the number to calculate) while a for loop can be made in linear time.

I know it is just an example, but it is a good test on why algorithm complexity is important :)

```

unsigned long long fibo( unsigned int number )
{
   if ( number < 3 ) return 1;
   unsigned long long n = 1;
   unsigned long long n_1 = 1;
   unsigned long long n_2 = 1;
   for ( unsigned int i = 2; i < number; ++i )
   {
      n_2 = n_1;
      n_1 = n;
      n = n_2 + n_1;
   }
   return n;
}

```

Using 64 bit unsigned ints in a Core Duo 1.66GHz (g++ 4.1, no optimizer) the 40th fibonacci number took 2.6 seconds to calculate recursively, while the iterative approach was not measurable. I had to test for the 100.000th number to get a 0.002 seconds result (meaning that it took over 1 millisecond, all tests below yielded 1 millisecond) Now, the result is irrelevant (and false, 64 bits barely fit the 93th fibonacci number).

Sadly, this code won't work. Nor will any recursive definition for Fibonacci sequence, really: the mean part is that a Fibbonacci sequence is defined over negative indices also. Hence the only reliable way is the think-twice way (Math, I mean):

```

pheidias =  ((*0.5) $ 1+s5, (*0.5) $ 1-s5)
            where
            s5 = sqrt 5

phi  = fst pheidias 
phid = snd pheidias

fibprog z i m = (p*) $ floor $ (i*phi^r - m*phid^r) / sqrt 5 + 0.5
                where
                e = expon z
                r = fst e
                p = snd e

expon k
  | k    <0   = ((-k),(-1)^(-k))
  | otherwise = (k   , 1) 

fibonacci = \k -> fibprog k 1 1

```

EDIT: As NovaAesa pointed out, this formula (fibonacci) can be used on larger numbers (in GHCi):
```

GHCi, version 6.8.2: http://www.haskell.org/ghc/  :? for help
Loading package base ... linking ... done.
[1 of 1] Compiling Prime            ( prime.hs, interpreted )
Ok, modules loaded: Prime.
*Prime> :set +s
*Prime> fibonacci 1000
43466557686937336258183803107209364165582816600926638075851748474376312519441346571087379858081727011968016214581807565759604513386909669950650218161257887891004427441164382860724747010986805848899946421420032
(0.00 secs, 524920 bytes)

```

Similarly, you can't calculate binomial coefficients by means of recursion or looping since those, too, are defined over negative indices.

---

### Post by Reiger on 2008-10-22
> **dwhitney67 said:**
> At the university level, many theoretical concepts are introduced to students, and from experience, many are never used in the real world unless you fall into a career that requires a particular need for you to know the extraneous concepts.

The funny thing is that most of these concepts do apply to the real world: the concept of 'transactions' as far as databases are concerned, the concept of data-integrity etc. etc. are all very important to you when it concerns, say, your bank account. ;) 

You may not be 'aware' of it, but that should not suggest that it isn't there: over more than 2000 years ago an 'atom-theory' of sorts was concepted, and the funny thing is that after those 2000 years that concept of something 'whole and un-divisible' leads people to discover things like atoms, nuclear power plants, quarks etc. etc. 

But even during those 2000+ years those concepts did have real-world implications in many philosophical and theological works. Plato & Aristoteles have touched many 'university level concepts' which continued to hold sway over scientific opion for over a millenium.

> A little off-topic, but what is the intrinsic value of knowledge if it is not applied or not needed in one's current environment?  If you want to answer this question, think first... for instance, if a person lives in a community with no internet access, what difference does it make if they do not know how to surf the web, much less know how to use a computer?  Should this person be taught about computers anyways, or should this person be taught something more practical and useful?

To get it out of the way: knowledge is not neccesariy the same as concepts. On the university level, the benefit of knowledge does not depend as much on one individual, it depends on the group of individuals as a whole: it may not make for much practical immediate benefit for one person to learn about computers if he or she will not see those during his or her life. But if from a group of 2000 people, 2 will proceed to discover new things about computers, then from a university level P.O.V. the education of those 2000 was well spent.

And it is not to say that in the course on computers the other 1998 didn't learn things they will eventually find practical real-world applications for. An example would be Math: perhaps the single domain cherised the most as one of abstract concepts completely un-usable in every-day life, virtually impossible to graps for people not inaugurated so to speak. Yet, funnily, Math is one of the most widely used disciplines in every day life: administrations depend on it, peoples live off Math by virtue of the few who can optimize company profits using advanced statistics. Think about this: abstract univeristy concepts employed by a few people create the opportunity for highly specialised companies to exist, employing many more non-university-educated people than university-educated people.

Who is to say that with our abstract university concepts that place without Internet access will remain so for the next 20 years? In casu: there is a MIT-student who has set up a company to offer a special kind of ISP which acts as a digital mailmen: regularly refreshing local web-caches in kiosks, updating the kiosks with answers to web-page requests (or say: online purchases!), and picking up/dropping mail for/from the outside world. Sure: it's not Internet as we know it, but it does open up new kinds of opportunities, jobs, markets for people who would otherwise have no access. And funnily enough: the use of being thaught about computers now becomes self-apparent.

---

### Post by pmasiar on 2008-10-22
> **dwhitney67 said:**
> I have rarely ever used recursion; there is just not a need for it in most applications.

Or more likely, apps you code in your day job do not use recursive data structures.

My day job is more different, so when I needed to visualize RDF file (for some semantic web presentation), recursive walk on a graph was most natural form to do it, and it took 15 lines on Python - but my colleague refused to try to understand how the code works, as long it works :-)

> many theoretical concepts are introduced to students, and from experience, many are never used in the real world 

Learning different and complex concepts builds "brain muscles" so next time you face some complex problem you can see patterns and do not have to reinvent the wheel. Same as lifting weights: IMHO point is not to move the iron weights around, but to have the muscles when you need them.

---

### Post by CptPicard on 2008-10-22
> **pmasiar said:**
> Learning different and complex concepts builds "brain muscles" so next time you face some complex problem you can see patterns and do not have to reinvent the wheel.

+1

The best thing I got from my university education was the ability to know when, where and how to hit the library -- and to be able to understand what I was reading once I did.

---

### Post by Rplus9 on 2008-10-22
I think you got a point, but I'd go a step further.  For a masters program I'm studying (essentially) comp-sci and I'm shocked at how un-engineering-like the discipline really is(Coming from an astronautical engineering background).  Most software projects are hit-or-miss and how often is any major software project universally accepted as a success (like say bridge building or electronics).

I'm fascinated with the concepts that my peers at work (software engineers) find "purely academic" or impractical for real design.  I figure that maybe somewhere in there is some new model (like how relational databases revolutionized and legitimized database software)

In Prolog, everything is recursive but my test-group is too small to really draw any concrete conclusions.  Likewise I predict that there is a recursive (and distributed) solution for all the common software solutions.
Most programmers I've met hate Prolog, mostly because it doesn't work the way they expect.  So that makes it even more appealing.

-Student of the absurd.

---

### Post by pmasiar on 2008-10-22
> **Rplus9 said:**
> maybe somewhere in there is some new model (like how relational databases revolutionized and legitimized database software)

CompSci can handle only about one paradigm shift a decade :-)

Next coming paradigm shift is likely agile + test driven development (using dynamic languages). Dynamic languages give you speed, and tests give you assurance that code is correct (test is dynamic checking - more relevant than static checking by compiler). Agile means faster loop, better response to what customer really neeeds (as compared to what she says she wants). Read wikipedia for more.

---

### Post by CptPicard on 2008-10-22
> **Rplus9 said:**
> I think you got a point, but I'd go a step further.  For a masters program I'm studying (essentially) comp-sci and I'm shocked at how un-engineering-like the discipline really is(Coming from an astronautical engineering background). 

Uh, well... depends on which half of CompSci you're dealing with to begin with, really. Sounds like you consider the part that is called "Software Engineering" and I suppose you're right. But to be honest, I have issues considering Software Engineering a proper academic discipline to begin with... it's more akin to vocational/professional training in best practices. The problem is that *anything* can be called "computer science" these days, no matter how non-academic the curriculum. 

Recently I actually got asked by a British doctor whether I'm a *web designer* after hearing I've got a M.Sc. in CS! ](*,) (ok, I know UK universities seem to be the worst offenders at degrading CS degrees' academic worth...)

I have issues recognizing as proper CompSci anything that isn't essentially algorithmics... the problem is that it often tends to stray very quickly into  mathematical analysis of the specific problem domain, but as long as you stay within the confines of trying to find a "mechanically computable solution", it's algorithmics.

Like, uh, [here's a book]("http://www.amazon.com/Algorithmic-Game-Theory-Noam-Nisan/dp/0521872820") I currently have as my bedside reading... gives a good idea of what I'm talking about.

---

### Post by hod139 on 2008-10-22
> **pmasiar said:**
> CompSci can handle only about one paradigm shift a decade :-)

Next coming paradigm shift is likely agile + test driven development (using dynamic languages)
Next big paradigm shifts on the computer science radar are, stream processing, multi-core/parallelization, and secure programming.

One may also argue for the inclusion of the semantic web in my short list, but I'm not sold on that being a new paradigm.

---

### Post by Rplus9 on 2008-10-23
there was an article on one of the linux news threads I browse (I wish I could find it but my google shearch arn't coming up with anything)

it was titled X = X + 1

it essentially was about how that little statement makes most programming possible but it is really just a crutch.  Once you use code like that you have to keep track of X and if you want to distribute it's even more "fun"

In Prolog, you can't do that (X = X + 1) so I figured there was a good chance that 5th gen lang was going to usher in this new shift.

Agile/SCRUM/and the others, that's more of a systems-engineering level shift (which is badly needed) but not fundamental to the way we understand software.

Phase 1: Prolog
Phase 2: ? (actually Linda and tuple space)
Phase 3: Profit!

---

### Post by CptPicard on 2008-10-23
> 
In Prolog, you can't do that (X = X + 1) so I figured there was a good chance that 5th gen lang was going to usher in this new shift.

It's called pure-functional programming... and it's been around quite a while. You can't do that in Haskell, for example.

It's a little bit sensationalistic to say that it makes most programming possible because it's obvious you can program without it... it really is the capacity to handle recursive structure (either in explicit data or implicitly as call stack) that makes or breaks a programming language.

---

### Post by nvteighen on 2008-10-23
> **Rplus9 said:**
> 
it was titled X = X + 1

it essentially was about how that little statement makes most programming possible but it is really just a crutch. (...)


Ok, so what about my project (see my sig), which doesn't have any single "X = X + 1" statement?

---

### Post by Rplus9 on 2008-10-24
well not so much that X = X + 1 but the fact that you may re-assign a value to X at any given point.  Logically this concept is "weird" because mathematically it can't be correct.  However serially you see how it works as a statement of "NOW X one more than it WAS" but that only works serially.

If you had 100 computers and you wanted to execute a loop 100 times, you'd have you couldn't get 100X the work done, there would be 99 idle computers at any given time.

With recursion

```

programX(100, []).
programX( X, [Y|Y1] ):-
   X1 is X + 1,
   programX(X1,Y1),
   do_something(X, Y).
programX(X,[]):-
   assert( oops(programX(X)) ).

```

the first step would be to generate X to 100 programs which could all "do_something(X, Y) as every X would be known.  
Best of all, look how easy that was!

disclaimer: I'm not arguing from experience or superior understanding, I'm just trying to get feedback on the strengths and weaknesses of this recursive only programming style.

---

### Post by CptPicard on 2008-10-24
[http://en.wikipedia.org/wiki/Purely_functional](http://en.wikipedia.org/wiki/Purely_functional)

---

