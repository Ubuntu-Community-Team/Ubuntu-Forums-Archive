---
title: "Why do we need &lt;= and &gt;="
date: 2010-12-16
forum: Programming Talk
---

### Post by ki4jgt on 2010-12-16
I've seen those two in several different languages and have never had to use them. I've written several programs which deal with math related functions and have always gotten along just fine with just plain =, >, <
So why do languages include them?

---

### Post by Reiger on 2010-12-16
<= and >= are partial ordering operations, so they are indispensable in logically structuring sets. Once you start defining implementations for these operators over arbitrary objects (data types) and start sorting such data these operators are reliable in ways that < and > are not, for instance you can compute equality like this: a <= b and b <= a.

---

### Post by Vaphell on 2010-12-16
because why not? it's a convenience feature and some people use it.
by the same logic you don't really need ++ because you can replace it with +=1, yet it's very useful.
when all you need in a given scenario is x<=y condition, why would you want x<(y+1) or !(x>y) or (x<y)||(x=y)? It's cool to know De Morgan's laws but languages work for the programmer, not the other way around.

---

### Post by trent.josephsen on 2010-12-16
Convenience.

It's possible to implement all the conditional operators with < and !.  For that matter, it's possible to implement a universal (Turing-complete) computer with [only one instruction](http://en.wikipedia.org/wiki/One_instruction_set_computer), but it's a lot of unnecessary work.

Why have an integer multiplication operator when you can do the work with +?

---

### Post by Tony Flury on 2010-12-16
to make the code neater instead of having to do : 

[CODE]
if a == b or a > b then
[CODE]

you could actually argue that you don't need == and that you only need **>** and **<** and a **not **- but people would think that is silly.

---

### Post by StephenDavison on 2010-12-16
Not just convenience, but fewer machine instructions.  Thinking back to my System/370 Assembler class, there are separate machine instruction mnemonics for those comparison operators.  Less than or equal was one instruction versus multiple to do say negation of a comparison, or addition and comparison.

Edited to add:
The ultimate result would depend on the compiler and the machine instruction set, but then you don't always have to rely on the compiler to optimize for you.

---

### Post by KdotJ on 2010-12-16
> **trent.josephsen said:**
> 
Why have an integer multiplication operator when you can do the work with +?

Why bother? We can just work out the multiplication in our head and hard code the result... Lol
This is a question I never thought if to be honest, I would of thought anyone who has done a fair bit of programming would tell you that such operators are indispensable...

---

### Post by Simian Man on 2010-12-16
The only logical operator you really need is just <.  The other 5 can be easily written in terms of it.  However, if you cut out all the things that you don't need, you'll just end up in the Turing tar pit.

---

### Post by Sweet Mercury on 2010-12-16
> **ki4jgt said:**
> I've seen those two in several different languages and have never had to use them. I've written several programs which deal with math related functions and have always gotten along just fine with just plain =, >, <
So why do languages include them?

I assume you're referring to the fact that:
*(a >= b)* is logically the same as *(a > (b-1))* given that *a* and *b* are integer values.

Outside of integers, it would take a mountain of work to make the statements logically equivalent.

I guess you could say:
*(a >= b)* is logically the same as *(a > (b-x))* where *x* represents the smallest unit to which you can assign your variable.

---

### Post by ki4jgt on 2010-12-16
> **Tony Flury said:**
> to make the code neater instead of having to do : 

```

if a == b or a > b then
[CODE]

you could actually argue that you don't need == and that you only need **>** and **<** and a **not **- but people would think that is silly.

That's my argument!
forgive me, I just started learning Python. I'm still stuck on BASIC so I'm going to write in BASIC for a sec :-)

[CODE]
LET INDEX = 1
WHILE INDEX < 100
    PRINT INDEX
    LET INDEX = INDEX + 1
WEND

```

I have never needed to use >= or <= before!
Can someone give me some simple code where you might need to use <= or >=? Please and thank you.

---

### Post by Simian Man on 2010-12-16
> **Sweet Mercury said:**
> Outside of integers, it would take a mountain of work to make the statements logically equivalent.

No it wouldn't.  (a >= b) is logically equivalent to !(a < b).

---

### Post by Queue29 on 2010-12-16
> **ki4jgt said:**
> 
Can someone give me some simple code where you might need to use <= or >=? Please and thank you.

Try reading the thread?

Technically you could do every conceivable operation using nothing but NAND or NOR, but that wouldn't be much fun. But you want an example. 

How about: "Print the numbers from 3 to N inclusively".

```

for( int i=3; i<=N; ++i)
    printf("%d\n", d);

```

I believe the above is more straightforward than not using <=, which might look like this:

```

for( int i=3; i<N+1 ++i)
    printf("%d\n", d);

```

It feels like putting a band-aid right in the middle of my for-loop.

---

### Post by trent.josephsen on 2010-12-16
You don't need NOR, either -- you can implement it with NAND.  Or you could go the other way around, and implement NAND with NOR.

---

### Post by nvteighen on 2010-12-16
Why? Because of expressivenes. It's the same reason why we like to use symbolic programming languages instead of punching holes into cards or using binary. >= and <= express a very common relation in one single atomic sign. Moreover, they are operators that were invented in Maths, not in programming.

---

### Post by ki4jgt on 2010-12-16
> **Queue29 said:**
> Try reading the thread?

Technically you could do every conceivable operation using nothing but NAND or NOR, but that wouldn't be much fun. But you want an example. 

How about: "Print the numbers from 3 to N inclusively".

```

for( int i=3; i<=N; ++i)
    printf("%d\n", d);

```

I believe the above is more straightforward than not using <=, which might look like this:

```

for( int i=3; i<N+1 ++i)
    printf("%d\n", d);

```

It feels like putting a band-aid right in the middle of my for-loop.

LOL, Yeah, I read the thread. I was having a blond moment thanks :-) I've been having a lot of those here lately. I'm thinking about having myself checked out. I've been forgetting things, losing interest in things and my IQs went from 133 to around 70??? I'm practically having to force myself to learn Python. I'm only 22 so I don't know what's going on. Thanks though. I don't really remember what my point was here, so I just forget about it til I start feeling better :-)

---

### Post by Sweet Mercury on 2010-12-16
> **Simian Man said:**
> No it wouldn't.  (a >= b) is logically equivalent to !(a < b).

I don't always herp, but when I do, I derp.:redface:

---

### Post by unknownPoster on 2010-12-16
> **ki4jgt said:**
>  I'm only 22 so I don't know what's going on. 

Not sure what age has to do with anything. I'm 21 and there are programmers that are 18 that know more than me, but I am also more skilled than some programmers that are 40. 

After a certain point, age is just a number, the fact that you are 22 has no effect on your intellectual abilities at this point. Of course there is a "minimum" age to be able to grasp the concepts of programming. I wouldn't expect a 7 year old child to understand it, but that's not to say that a 15 year old couldn't be a skilled programmer. 

Barring the effects of aging such as dementia and Alzheimer's, there is no upper limit to "effective age" either. It all depends on the person.

Python is probably one of the easiest languages to understand. Recently, I was required to write a distributed system in python. I had no experience in the language before and I completed the project (1200+ lines of code) in about a month.

---

### Post by ki4jgt on 2010-12-17
> **unknownPoster said:**
> Not sure what age has to do with anything. I'm 21 and there are programmers that are 18 that know more than me, but I am also more skilled than some programmers that are 40. 

After a certain point, age is just a number, the fact that you are 22 has no effect on your intellectual abilities at this point. Of course there is a "minimum" age to be able to grasp the concepts of programming. I wouldn't expect a 7 year old child to understand it, but that's not to say that a 15 year old couldn't be a skilled programmer. 

Barring the effects of aging such as dementia and Alzheimer's, there is no upper limit to "effective age" either. It all depends on the person.

Python is probably one of the easiest languages to understand. Recently, I was required to write a distributed system in python. I had no experience in the language before and I completed the project (1200+ lines of code) in about a month.

IDK, I used to get stuff like that though right after I read it. Now I just feel like it's all a bunch of mumbo jumbo sometimes :-) Python very much resembles BASIC to me. I can't even read BASIC anymore, which why I said that.

---

### Post by Vox754 on 2010-12-17
> **ki4jgt said:**
> LOL, Yeah, I read the thread. I was having a blond moment thanks :-) I've been having a lot of those here lately. I'm thinking about having myself checked out. I've been forgetting things, losing interest in things and my IQs went from 133 to around 70??? I'm practically having to force myself to learn Python. I'm only 22 so I don't know what's going on. Thanks though. I don't really remember what my point was here, so I just forget about it til I start feeling better :-)

Lolwut? *cough* drugs *cough*


Seriously, reading this thread was like asking "why would I need five fingers in one hand if I already have four?"

---

### Post by ki4jgt on 2010-12-17
Exactly LOL I mean, who needs those darn opposable thumbs :-) LMBOROTF

---

