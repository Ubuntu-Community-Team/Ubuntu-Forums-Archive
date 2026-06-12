---
title: "Strong Typing vs. Strong Testing"
date: 2008-10-29
forum: Programming Talk
---

### Post by pmasiar on 2008-10-29
Edit:

To understand context, please read [Strong Typing vs. Strong Testing](http://www.mindview.net/WebLog/log-0025)

> **Delever said:**
> I suggest choosing language where compiler checks the most and which have good choices of IDEs. Java.(...)

Second choice in this case (for me) would be Python. It is not strong typed, so compiler will check less. It can be argued that you can achieve more neat tricks this way, but we are talking stability, not tricks :). 

This it standard opinion of someone trained in statically typed languages, like Java, but right out of school, without experience in "industry strong" programming.

1) Python is strongly, but dynamically typed: for weakly typed, try JavaScript or Perl, where  2 + "3" is legal.

2) Stability is achieved by testing, not by strong typing. If agile language allows you to write code faster, you have more time to write tests, so your code will be more reliable.

3) Java is adding generics and stuff recently, because it makes code simpler and clearer. Runtime introospection can substantially simplify your code, even generate big chunks of it. And with JIT-compilation, compiler can use dynamic type info to generate fast code, it is just matter of resources, and Python recently has them.

> And I still have to find good IDE for it. Up to Eclipse's Java level.

You need such IDE when your main focus is write more lines of code. But measuring productivity in LOC/day is like measuring progress of plane building in kilograms :-) For me, better editor is the one which allows me to refactor easier, so I have **less** code ;-)

> Both Java and Python have enough tools for communication over Internet so I see them equal here too.

Yes, just try to create simple "hello world" application in Python/Django or Python/Turbogears (less than hour, including install: just follow the tutorial), and compare it with Java/Struts. It took me couple of weeks (and pay $50 for commercial plugin for Eclipse) to wrap my mind around brain-damaged concepts of web programming in Java (and I programmed CGI in Perl for years before).

---

### Post by Delever on 2008-10-29
> **pmasiar said:**
> This it standard opinion of someone trained in statically typed languages, like Java, but right out of school, without experience in "industry strong" programming.

1) Python is strongly, but dynamically typed: for weakly typed, try JavaScript or Perl, where  2 + "3" is legal.

2) Stability is achieved by testing, not by strong typing. If agile language allows you to write code faster, you have more time to write tests, so your code will be more reliable.

3) Java is adding generics and stuff recently, because it makes code simpler and clearer. Runtime introospection can substantially simplify your code, even generate big chunks of it. And with JIT-compilation, compiler can use dynamic type info to generate fast code, it is just matter of resources, and Python recently has them.

> And I still have to find good IDE for it. Up to Eclipse's Java level.

You need such IDE when your main focus is write more lines of code. But measuring productivity in LOC/day is like measuring progress of plane building in kilograms :-) For me, better editor is the one which allows me to refactor easier, so I have **less** code ;-)



Yes, just try to create simple "hello world" application in Python/Django or Python/Turbogears (less than hour, including install: just follow the tutorial), and compare it with Java/Struts. It took me couple of weeks (and pay $50 for commercial plugin for Eclipse) to wrap my mind around brain-damaged concepts of web programming in Java (and I programmed CGI in Perl for years before).

I was Java developer like 3 years ago, and had no choice but to use Java. After that I migrated to C#, so probably I assumed too many things Java still doesn't have. Just don't name my opinion "standard", i hate that :D.

I remember working with Java in 15 developer team, honestly it was quite a mess, and strong typing saved from CVS Merge mistakes hundreds of times. You just can't build it until you fix it.

---

### Post by pmasiar on 2008-10-29
> **Delever said:**
> I remember working with Java in 15 developer team, honestly it was quite a mess, and strong typing saved from CVS Merge mistakes hundreds of times. You just can't build it until you fix it.

Read [http://www.mindview.net/WebLog/log-0025](http://www.mindview.net/WebLog/log-0025) "Strong Typing vs. Strong Testing"

I called your opinion "standard" because this kind of lack of understanding is standard on this forum, it is not FAQ but FRU (Frequently repeated untruth ;-) )

---

### Post by slavik on 2008-10-29
Here's my 2cents of no industry experience what so ever ...

1. Implementation at best is as good as the design.
2. typing has nothing to do with testing, good testing procedures will find problems no matter the type of typing.
3. I work on supporting Java applications and why do I see OOM exceptions (2GB of heap) and stuck threads? I am sure if the same devs used Python, the same issues would arise.

the type of typing used in a language might increase development speed, but it will not make an application better.

---

### Post by Delever on 2008-10-29
> **pmasiar said:**
> Read [http://www.mindview.net/WebLog/log-0025](http://www.mindview.net/WebLog/log-0025) "Strong Typing vs. Strong Testing"

I called your opinion "standard" because this kind of lack of understanding is standard on this forum, it is not FAQ but FRU (Frequently repeated untruth ;-) )

You know, I love Python ([some of my work here]("http://forums.civfanatics.com/showthread.php?t=180995")). However, I want and wait better IDE to do bigger work. Testing - yes, but I want more certainty that I haven't made some stupid typo in some part of code which is only rarely executed. Things like that.

---

### Post by pmasiar on 2008-10-29
Re: title: "Java vs. Python ... again?"

Better title IMHO would be: "Strong Typing vs. Strong Testing". If not: "Java vs. Python ... forever!" :-)

---

### Post by jespdj on 2008-10-29
> **pmasiar said:**
> It took me couple of weeks (and pay $50 for commercial plugin for Eclipse) to wrap my mind around brain-damaged concepts of web programming in Java (and I programmed CGI in Perl for years before).
Spending $50 was ofcourse totally unnecessary, Eclipse has good support for developing Java web applications, you don't need any commercial third-party plugins for that.

---

### Post by LaRoza on 2008-10-29
> **jespdj said:**
> Spending $50 was ofcourse totally unnecessary, Eclipse has good support for developing Java web applications, you don't need any commercial third-party plugins for that.

Apparently, it is worth that, to him.

---

### Post by snova on 2008-10-29
> **pmasiar said:**
> 2) Stability is achieved by testing, not by strong typing. If agile language allows you to write code faster, you have more time to write tests, so your code will be more reliable.

I liked that point especially.

In general, my means of doing things in Python is to defer type-checking as much as possible, which usually means it ends up in the interface, where it ought to be. Why should the engine care about where data is coming from? It's more generic that way besides; portable to any different UI.

---

### Post by Reiger on 2008-10-29
Dynamic typing is not really a variation on a theme, compared to Strong typing. You cannot compare those.

Static typing does not mean Strong typing, not by a large stretch. Any language allowing a cast is by definition not Strongly typed; it is what makes dynamic typing different from strong typing: dynamic typing consists of nothing but (dynamic) casts as required.

Strong typing can be very useful when combined to Static typing; to avoid the need for (many) a code test altogether: you can *more easily* write *provably correct* code, by virtue of the fact that this combination allows for simple, provable (by induction), definitions which are a *lot* harder to achieve in weakly, dynamically typed languages. The example of 2 + "3" being a case in point: such ambiguity is impossible in Statically, strongly typed languages.

---

### Post by slavik on 2008-10-29
> **Reiger said:**
> Dynamic typing is not really a variation on a theme, compared to Strong typing. You cannot compare those.

Static typing does not mean Strong typing, not by a large stretch. Any language allowing a cast is by definition not Strongly typed; it is what makes dynamic typing different from strong typing: dynamic typing consists of nothing but (dynamic) casts as required.

Strong typing can be very useful when combined to Static typing; to avoid the need for (many) a code test altogether: you can *more easily* write *provably correct* code, by virtue of the fact that this combination allows for simple, provable (by induction), definitions which are a *lot* harder to achieve in weakly, dynamically typed languages. The example of 2 + "3" being a case in point: such ambiguity is impossible in Statically, strongly typed languages.
This is a very good point.

Just to note: a strongly statically typed language that is used the most: Ada. Military uses it and so does the airline industry, Ada is what controls Radars and airplane flight systems.

Also, Ada catches many errors during compile time, that otherwise would be only happen during the runtime in C.

---

### Post by Delever on 2008-10-30
What strong typing does not save from: need for good system design.

For example, very common runtime errors are that some object is accessed before it was created, some structure which should contain something does not contain it yet. That results in some nasty long exceptions. Yeah, you need to check if object is not null. Please. :)

In python, I imagine you need to write good comments/documentation, so if others use some function, they know what it can handle and what it returns. And every time you use some function, you must make sure you do it right. When program is in development, there probably needs to be some way to handle function behavior changes, like, writing new function version so that older does not break.

So it seems for me that python overall needs better programmers to plan things better and handle changes better. Otherwise, you need more testing.

Common way to handle some change with strong typing: you simply change the function, then try to build, get gazilion of errors, then click on every error, look at the code that uses it, and change what is needed.

---

### Post by CptPicard on 2008-10-30
> **Delever said:**
> 
So it seems for me that python overall needs better programmers to plan things better and handle changes better. Otherwise, you need more testing.

I really am not all that sure of this... it seems to me that the supposed benefits of static typing when it comes to catching errors beforehand are overestimated, and that static typing itself requires a lot of extra design and planning that is there only because of the type system (see all the OOP patterns), but that is then revered simply because it makes people feel all professional because they're doing all this design.. :)

When you've got a duck-typed language like Python, you get genericity *by default* into your design without having to design for it -- and by extension, your Python code handles *changes correctly by default 90% of the time if your code does what you mean*, and I have a feeling that this probably scares some people who are used to the rigours of static typing. 

It's not as bad as it sounds though... when you properly modularize your code, there actually is not all that much code in each single piece to begin with, so it is much easier to just simply *see* it is right. And then when you change something, provided that you are passing a "duck" to your function, things just work... whereas in static-typed languages you would indeed get compiler-barfs and would have to introduce some sort of architecture to extend your type system appropriately.

---

### Post by jespdj on 2008-10-30
> **LaRoza said:**
> Apparently, it is worth that, to him.
Maybe, but to me his post came across as if when you want to develop Java web applications with Eclipse, you can only do that by buying a commercial, third-party plugin - which is not the case.

---

### Post by pmasiar on 2008-10-30
> **Delever said:**
> In python, I imagine you need to write good comments/documentation, so if others use some function, they know what it can handle and what it returns. And every time you use some function, you must make sure you do it right. When program is in development, there probably needs to be some way to handle function behavior changes, like, writing new function version so that older does not break.

So it seems for me that python overall needs better programmers to plan things better and handle changes better. Otherwise, you need more testing.

Common way to handle some change with strong typing: you simply change the function, then try to build, get gazilion of errors, then click on every error, look at the code that uses it, and change what is needed.

I am not sure if you read namesake blog post by Bruce Eckel - I put link more prominently and into first post of the thread. Your "gut feeling" is directly against Eckel's (and mine), so instead of me trying to verbalize it, why won't you argue against Eckel's expert opinion?

---

### Post by pmasiar on 2008-10-30
> **jespdj said:**
> Maybe, but to me his post came across as if when you want to develop Java web applications with Eclipse, you can only do that by buying a commercial, third-party plugin - which is not the case.

Java/Struts is so overcomplicated, hard to grasp and hard to configure that spending $50 to save couple hours of work was good investment, IMHO. I am only sorry I wasted time, should buy the plugin sooner. 

I am comparing Struts to Turbogears, which is **so** much easier to comprehend.

---

### Post by SeanHodges on 2008-10-30
> **pmasiar said:**
> I am comparing Struts to Turbogears, which is **so** much easier to comprehend.

In *your* opinion.

---

### Post by Delever on 2008-10-30
> **pmasiar said:**
> I am not sure if you read namesake blog post by Bruce Eckel - I put link more prominently and into first post of the thread. Your "gut feeling" is directly against Eckel's (and mine), so instead of me trying to verbalize it, why won't you argue against Eckel's expert opinion?

In my mind, I am the best expert.

However, after actually reading that, I completely agree now. If you are using unit tests in both languages, python wins.

---

### Post by CptPicard on 2008-10-30
> **SeanHodges said:**
> In *your* opinion.

Well, Java web app development *is* horribly complex... it was particularly nasty a few years back when you had to set everything up manually from ant scripts to app server... tools have made it much easier recently, I almost can't remember anymore how annoying Java used to be :)

---

### Post by Reiger on 2008-10-30
> **Delever said:**
> What strong typing does not save from: need for good system design.

Actually no language, no tool, nothing will save from the need for good system design. You can write in many languages something to the effect of:

```

fib 0 = 1
fib 1 = 1
fib n = fib (n-1) + fib (n-2)

```

However this is badly designed: this generates 2 calls to fib per call to fib, and hence creates exponential complexity in your code. For small fib you'll wonder why you system takes so long for this trivial taks, for large fib you will get stack overflow.

Getting away with bad/ugly design may be easier in some languages than in others, it doesn't make the 'others' inherently inferior to the 'some'.

The benefit over one typing system compared to the other depends much on the implementation of that typing system. 

For instance Haskell's static typing system paired to its strong typing makes for something difficult to grapple with at first, yet very rewarding when you can throw away much of the unit testing by virtue of "the compiler accepted it, ergo it is correct". Of course that still gives you the ability to write ugly code, but that is something you'll learn to avoid more from experience than any typing system can influence.

One would similarly argue that a weak dynamically typed language allows you to write similarly concise code but requires a good bit more testing when it comes to handling the cases casting can't mend. The earlier ambiguous JavaScript example is in fact completely un-ambiguous in similar languages as Perl and PHP where the string concatentation operator and the addition operator are two distinct symbols. As we all know, Perl can easily venture beyond ugly: when it's 'obfuscated'.

---

### Post by pmasiar on 2008-10-30
> **Reiger said:**
> when you can throw away much of the unit testing by virtue of "the compiler accepted it, ergo it is correct". (...)
One would similarly argue that a weak dynamically typed language allows you to write similarly concise code but requires a good bit more testing 

I strongly disagree: static typing can catch only the most trivial types or errors, and in no way can eliminate unit testing. I am curious: did you read expert Bruce Eckel's article linked above? Are we talking about same thing?

And dynamic typing has **nothing** common with weak typing, as you can see: Python is one of many dynamically yet strongly typed languages. 

It's hard to argue with someone whose posts show such gaping difference in understanding basic facts, so I will not waste time arguing.

---

### Post by pp. on 2008-10-30
> **pmasiar said:**
> I strongly disagree: static typing can catch only the most trivial types or errors, and in no way can eliminate unit testing. I am curious: did you read expert Bruce Eckel's article linked above? Are we talking about same thing?

And dynamic typing has **nothing** common with weak typing, as you can see: Python is one of many dynamically yet strongly typed languages. 

It's hard to argue with someone whose posts show such gaping difference in understanding basic facts, so I will not waste time arguing.

Did you actually read the post you are quoting from?

"doing away with much of the unit testing" is not saying "to eliminate unit testing". It is saying "eliminating part of unit testing".

The phrase "weak dynamically typed language" can easily be understood to mean "a language which is both weakly and dynamically typed". It most certainly does not imply that weakly typed and dynamically typed are the same thing. Also, that's a bit beside the point because that sentence essentially said that it is possible to do concise code independently of strength and dynamicity of typing system.

It's all right if you think arguing is a waste of time, but please don't shift the blame around.

---

### Post by Alasdair on 2008-10-30
Haskell's type system is considerably more powerful than Java's. Many things that would be runtime errors in Java can be picked up at compile time in Haskell. Furthermore pure Haskell code can be concisely and easily checked using quickcheck, which relies on Haskell's type system for most of it's awesomeness. All you have to do is specify some properties the function must adhere to, and then the checker bombards it with random data that conforms to the function's type signature (which could contain all sorts of fancy algebraic data types). It's a really powerful way of unit testing code, and it relies on static typing to work!

See, static typing = even stronger testing!:)

---

### Post by pmasiar on 2008-10-30
> **pp. said:**
> "doing away with much of the unit testing" is not saying "to eliminate unit testing". It is saying "eliminating part of unit testing".

How big part of total errors will strong typing catch? 30%? No way it is 70%, so it diminishes need of unit testing only in a minor way (and only the trivial tests).

> The phrase "weak dynamically typed language" can easily be understood to mean "a language which is both weakly and dynamically typed". It most certainly does not imply that weakly typed and dynamically typed are the same thing. 

Yes, but the difference if huge, and most people with limited experience do not see the difference - certainly from that post the difference is not obvious to poster.

---

### Post by slavik on 2008-10-30
I'm sorry, you do realise that you are comparing a "static typing" versus "strong testing", right?

Please tell me what is the exact point you are arguing over ...

---

### Post by Alasdair on 2008-10-30
Yes, we appear to be debating static typing vs strong testing (why not have both?). I know the title says strong typing, but that's a a pretty useless and ill-defined term that can mean anything from full static typing to simply having a sound type system.

---

### Post by CptPicard on 2008-10-30
> **Reiger said:**
> 
However this is badly designed: this generates 2 calls to fib per call to fib, and hence creates exponential complexity in your code.

This here is a completely algorithmic problem, which is always totally language independent, so it does not make for a very good example... and by definition from computability theory these sorts of algorithmic mistakes cannot in general case be caught by the compiler.

---

### Post by pmasiar on 2008-10-30
> **Alasdair said:**
> Yes, we appear to be debating static typing vs strong testing (why not have both?)

As article says, strong testing in language with dynamic typing is substantially more productive than with static typing, and more reliable than relying on static typing alone to discover the bugs.

Why debating? As is obvious from the posts above, Eckel's opinion is far from accepted, or even understood. Misleading "opinions" appear quite often (like the one what started this discussion before it was stemmed into separate thread). IMHO it is FAQ, or better FRU (Frequently Repeated Untruth). That's why.

---

### Post by slavik on 2008-10-30
actually, it does depend on the language ... since the language of mathematics doesn't have stacks and memory ... it only has functions and symbols. this is more of a computer problem ;)

---

### Post by slavik on 2008-10-30
> **pmasiar said:**
> As article says, strong testing in language with dynamic typing is substantially more productive than with static typing, and more reliable than relying on static typing alone to discover the bugs.

Why debating? As is obvious from the posts above, Eckel's opinion is far from accepted, or even understood. Misleading "opinions" appear quite often (like the one what started this discussion before it was stemmed into separate thread. IMHO it is FAQ, or better FRU (Frequently Repeated Untruth). That's why.
so, your argument is "strong testing with a dynamically typed language" vs. "strong testing with a statically typed language" ???

---

### Post by Delever on 2008-10-30
> **slavik said:**
> so, your argument is "strong testing with a dynamically typed language" vs. "strong testing with a statically typed language" ???

I agreed that some time could be saved even if you have unit testing, just because programming language itself is more flexible. I don't have any practice actually doing this :). Future will tell.

---

### Post by slavik on 2008-10-30
think of it this way ... no matter how you write a program, you will test it the same way ... you will test correct input and also bad input ... then you look at the different parts and make sure that they recover from errors where they can or die as gracefully as possible where they can't or some such ... now, I really want to know what the argument here is ... what is the point of contention?

---

### Post by jdonnell on 2008-10-30
> **pmasiar said:**
> As article says, strong testing in language with dynamic typing is substantially more productive than with static typing
...
Eckel's opinion is far from accepted, or even understood. 


I actually agree with your point, but you are failing to listen to others and you are the one that isn't understanding. Java is not the only way to do static typing. People keep mentioning haskell and you keep refusing to listen. Haskell is nothing like java and many of the problems you complain about in java don't exist in haskell. I'm no expert on Haskell but I took a class on functional programming in college which used haskell. It was eye opening to say the least.

---

### Post by CptPicard on 2008-10-30
> **jdonnell said:**
> I'm no expert on Haskell but I took a class on functional programming in college which used haskell. It was eye opening to say the least.

You're assuming way too much ignorance on his part. :)

Yes, Haskell's type system is stricter but also more modern (in particular, type inference rocks), but Haskell also has the benefit of being a functional language, which Java is not.

I don't need to speak for pmasiar but he fully understands why functional languages deal better with stronger static type systems.

I would suggest you consider Lisp for a (partly/mostly) functional language that gives you just as much if not more of the eye-opening and is actually about as duckly typed as Python is.

---

### Post by slavik on 2008-10-30
lisp doesn't have types at all ... well it does, but it's only 1 type ... called a list ;)

---

### Post by pmasiar on 2008-10-30
> **slavik said:**
> I really want to know what the argument here is ... what is the point of contention?

See OP: "Second choice in this case (for me) would be Python. It is not strong typed, so compiler will check less. It can be argued that you can achieve more neat tricks this way, but we are talking stability, not tricks"

Strong static type checking is used as replacement of testing. Stability and quality can be achieved only by testing, and quite a few posters completely miss that.

And it **does** depend on language: If with Python I can code my app in 30% of the time, I have 70% more time for writing automatic tests.

---

### Post by pmasiar on 2008-10-30
> **jdonnell said:**
> Java is not the only way to do static typing. People keep mentioning haskell and you keep refusing to listen.

See OP. Can you see any Haskell mentioned in that context? 

We inoculated posters against being "speed kiddie" and "blub", next step is for average poster to recognize that quality and stability cannot be checked by static compiler: it has to be tested out. And if you do strong testing anyway, there is little reason to use statically typed language, unless the speed is one of crucial requirements: Dynamic language with strong testing is more productive environment. With better "speed to market" to boot 8-)

---

### Post by pp. on 2008-10-30
> **pmasiar said:**
> Stability and quality can be achieved only by testing, and quite a few posters completely miss that.

That's a - how do you call it - frequently repeated untruth. It is impossible to achieve quality by testing. You can detect absence of quality by testing.

Hence, testing is necessary for quality and stability, but not sufficient.

> **pmasiar said:**
> If with Python I can code my app in 30% of the time, I have 70% more time for writing automatic tests.

Is there any empirical base to the stated percentages of 30% and 70%, respectively?

Are there any studies which show whether additional coding time or additional testing time contributes more to said quality and stability, and under what circumstances?

It's all very opinionated.

---

### Post by LaRoza on 2008-10-30
> **slavik said:**
> lisp doesn't have types at all ... well it does, but it's only 1 type ... called a list ;)

Wrong. There is no List: [http://gigamonkeys.com/book/they-called-it-lisp-for-a-reason-list-processing.html](http://gigamonkeys.com/book/they-called-it-lisp-for-a-reason-list-processing.html)

---

### Post by pp. on 2008-10-30
> **slavik said:**
> lisp doesn't have types at all ... well it does, but it's only 1 type ... called a list ;)

Aren't there some kinds of atoms as well? Otherwise there had to be an infinite amount of memory or the lists would have to abound with circular references.

---

### Post by Reiger on 2008-10-30
> **CptPicard said:**
> This here is a completely algorithmic problem, which is always totally language independent, so it does not make for a very good example... and by definition from computability theory these sorts of algorithmic mistakes cannot in general case be caught by the compiler.

No but my point is that a lot of bad design is actually not bound to languages at all: compare a user input field on a JSP page that doesn't take care to sanitize input versus a user input field on a PHP generated webpage which doesn't take care to sanitize input.

If such a thing were now part of a CMS system, whatever the language the CMS is implemented in -- the CMS is now inherently insecure. In the context of the CMS that equals bad design. A CMS should be as secure as is possible because person A should not be able to modify person B's site, or hijack the CMS front end as a whole.

Similarly, if you can get the source code from a security-sensitive page on your screen as a user -- that is the result of bad design. Not catching errors is the result of bad design. Producing inherently over-complicated alogrithms is the result of bad design. Producing unmaintainable code is the result of bad design. And none of those issues can be said not to exist on the abstract level in whatever language you throw at it.

And though this computational example of mine is very simple but I find that bad design often lies in such simplistic approaches. For instance:

```

sum  = \x -> foldr (+) 0 x
-- vs. 
sum2 = \x -> foldl (+) 0 x

```

sum is of inherently bad design: it begins folding at the right end of the list, and hence a suitably large list generates a stack overflow quickly.

sum2 is of better design: it will start at the left, and at all times achieve a constant stack size. Just by choosing a different yet in this case equivalent folding function we achieve a lot better performance.

However, if you cannot be sure that the argument given to sum or sum2 is of finite length you will find that sum produces an exception rather than effectively locking up its thread.

And as strange as it may sound, but Haskell's type system can do some pretty amazing tricks: ever got the "Cannot construct the infinite type a -> [a]" ? Or similar? That means your compiler found out you included an infinite loop in your program. No less.

---

### Post by jdonnell on 2008-10-30
> **pmasiar said:**
>  next step is for average poster to recognize that quality and stability cannot be checked by static compiler: it has to be tested out.

Like I said, I agree with you generally, but your tone and certainty are not backed up by your knowledge.

Some quality and stability can be checked by a strongly and statically typed language. For example take simple typos. The only way to guarantee that I haven't had a simple typo of a method or variable name in my dynamic code is to have a test that has absolute 100% coverage of every line. A statically typed language gives me this insurance for free. 

Again, I'm saying this as a person that prefers dynamic languages and believe that the trade off is worth it.

---

### Post by pmasiar on 2008-10-30
> **pp. said:**
> It is impossible to achieve quality by testing. You can detect absence of quality by testing.

I agree. But compiling is even less able to detect that, as poster quoted in OP suggested. So you are on my side of the original argument I guess?

> Is there any empirical base to the stated percentages of 30% and 70%, respectively?

Of course not. It is WAG. But ballpark numbers are about that. Delphi method by programming experts like mentioned Eckel say that - do you have any evidence they are wrong?

> Are there any studies which show whether additional coding time or additional testing time contributes more to said quality and stability, and under what circumstances?

under common sense? Is common sense permissible?

> It's all very opinionated.

Of course. So bring your opinions, anecdotal evidence, what you have - and let's learn from it. 

Poster in OP has no evidence at all to his opinion - I have endorsement by world-known expert on my side. ;-)

---

### Post by slavik on 2008-10-31
My language choice is backed by a linguist, take that! :)

Anyway ... pmasiar, are you saying that you can write better code in Python than others can in Ada? Guess what code runs on airplanes and on air traffic control systems. :)

---

### Post by Delever on 2008-10-31
Probably that's why:

[PHP]
import random

number = random.randrange(0,96000) #number between 0 and 96000

if number == 30840:
	dksfksdjkairinvnv.asjdhjadhdas()
else:
	print "Code is just fine"
[/PHP]

It just works!

I don't know about you, but writing unit tests that cover such things sounds like no fun. However, as I said, this has advantages, but probably not for Air traffic control systems...

---

### Post by pmasiar on 2008-10-31
> **slavik said:**
> My language choice is backed by a linguist, take that! :)

Yes, but that linguist did not have the mental discipline to weed out features to make language consistent and "orthogonal" - so using it on big systems is questionable.

> pmasiar, are you saying that you can write better code in Python than others can in Ada? Guess what code runs on airplanes and on air traffic control systems. :)

Sure, years ago people wrote OS in ASM, accounting in Fortran, and we cannot learn to be more productive, because they know better.  So we should forget about all C, Java, Python, Perl and Ruby and return to good old approaches, right? Will you give us exception to use Cobol? ;-)

I am not sure why the message is not getting through. Did you bothered to read the linked article? Or maybe you just do not want to understand?

All I am saying that new experience says that relying on static compiler check to make your program reliable is not enough, despite many people promoting that idea. And if you write strong tests, your code can be reliable even in dynamically typed language. And because with dynamic language you have less code written faster, your task to test all the code is simpler.

I guess all people who wanted to understand, did, and rest closed eyes (and minds). I am waiting to continue debate with some better arguments.

---

### Post by pp. on 2008-10-31
> **pmasiar said:**
> I agree. But compiling is even less able to detect that, as poster quoted in OP suggested

(..) Is common sense permissible?[/QUOTE]

Static typing, strong typing, unit testing and a sheaf of other topics are just tools and concepts which have their impact on the speed and reliability of the software development process and - by implication - on the quality of the product of said process, the developed software.

Saying that one of those tools can be substituted for by one of the remaining ones without carefully outlining the circumstances under which this will be true does not appear to be a useful statement to me.

Common sense does not enter at all into the discussion. OR (Operations Research) does not live by gut feeling and common sense. It's an engineering discipline much like a few others others.

One does not design planes by common sense. Common sense says that planes can't fly. In the same vein, one does not design processes and methods by common sense.

> **pmasiar said:**
> Poster in OP has no evidence at all to his opinion - I have endorsement by world-known expert on my side. ;-)

OP of this thread is you. 

Endorsements by world-known experts may not be worth the paper they aren't written on. The arcticle linked to in the OP of this thread just summarizes 'strong testing better than static typing' (not 'strong typing' as this thread says), without actually mentioning any particulars which would allow one to weigh that statement.

I remember having listened to a world-known expert bellowing with much conviction that a data transmission rate of 38.9 kb (thats kilo-Bauds or a bit more than 32 kb/s) is quite enough for any practical purpose. What is it that wants tranmitting at a rate faster than that, answer me that? IBM 3270 forever.

---

### Post by LaRoza on 2008-10-31
> **pp. said:**
> OP of this thread is you. 

This thread is split from another.

---

### Post by pp. on 2008-10-31
> **LaRoza said:**
> This thread is split from another.

What he means, then, is the OOP (the Original Opening Poster)?

---

### Post by pp. on 2008-10-31
sorry, double post.

---

### Post by LaRoza on 2008-10-31
> **pp. said:**
> What he means, then, is the OOP (the Original Opening Poster)?

I am not sure when it was split, or even where, so it may be (depending on the post) be truthful at the time.

About the subject, the strong typing of a language like Ada caused a program to crash (and incidently, the expensive vehicle it was guiding; Ariane-5). T

---

### Post by jdonnell on 2008-10-31
> **pmasiar said:**
> I have endorsement by world-known expert on my side. ;-)


You keep making this point, but it seems rather silly. First, it's an appeal to authority logical fallacy. Second, by this reasoning you should be using lisp and not python. Paul Graham is a bigger authority than Bruce Eckel or Guido ;)

---

### Post by LaRoza on 2008-10-31
> **jdonnell said:**
> You keep making this point, but it seems rather silly. First, it's an appeal to authority logical fallacy. Second, by this reasoning you should be using lisp and not python. Paul Graham is a bigger authority than Bruce Eckel or Guido ;)

People change: [https://www.google.com/accounts/ServiceLogin?passive=true&service=groups2&continue=http://groups.google.com/group/comp.lang.lisp/msg/6f75cfb5a289d3f6&cd=US&hl=en](https://www.google.com/accounts/ServiceLogin?passive=true&service=groups2&continue=http://groups.google.com/group/comp.lang.lisp/msg/6f75cfb5a289d3f6&cd=US&hl=en)

---

### Post by LaRoza on 2008-10-31
> **jdonnell said:**
> You keep making this point, but it seems rather silly. First, it's an appeal to authority logical fallacy. Second, by this reasoning you should be using lisp and not python. Paul Graham is a bigger authority than Bruce Eckel or Guido ;)

Then, Python is a perfectly valid answer if going by Paul Graham: [http://www.paulgraham.com/lispfaq1.html](http://www.paulgraham.com/lispfaq1.html)

People change: [https://www.google.com/accounts/ServiceLogin?passive=true&service=groups2&continue=http://groups.google.com/group/comp.lang.lisp/msg/6f75cfb5a289d3f6&cd=US&hl=en](https://www.google.com/accounts/ServiceLogin?passive=true&service=groups2&continue=http://groups.google.com/group/comp.lang.lisp/msg/6f75cfb5a289d3f6&cd=US&hl=en)

---

### Post by jdonnell on 2008-10-31
i think you missed his point. He said to try something like python only if you couldn't use lisp, but that lisp is the right choice.

He also says that ruby is better than python ;)

---

### Post by LaRoza on 2008-10-31
> **jdonnell said:**
> He also says that ruby is better than python ;)

No, he has one sentence saying it is even more Lisp like. Also, he acknowledges Python is getting "more Lisp like", and this article is static.

---

### Post by pp. on 2008-10-31
> **LaRoza said:**
> this article is static.

"Static" like the noise heard on the radio between stations? :confused:

---

### Post by LaRoza on 2008-10-31
> **pp. said:**
> "Static" like the noise heard on the radio between stations? :confused:

Static has several uses, one is "not changing".

---

### Post by jdonnell on 2008-10-31
At this point I can't believe you are being sincere. PG clearly believes that lisp is more powerful and better than python. Again, if we are playing appeal to the authority then pmaiser should be using lisp

:popcorn:

---

### Post by jdonnell on 2008-10-31
"(But if they don't want to wait for Python to evolve the rest of the way into Lisp, they could always just...) " PG

[http://www.paulgraham.com/icad.html]("http://www.paulgraham.com/icad.html")

---

### Post by Alasdair on 2008-10-31
> **pmasiar said:**
> And because with dynamic language you have less code written faster, your task to test all the code is simpler.
This is your flawed assumption, it would be true if static language = Java, but that's not the case. I find Haskell to be a much more expressive and concise language than Python. The idea that static languages are always much less efficient in terms of programmer time is simply plain wrong, it's totally subjective.

If you want to play the my programming expert vs yours game, then there are plenty of actual experts using Haskell, in contrast to celebrities blogging about Python...

---

### Post by pmasiar on 2008-10-31
> **jdonnell said:**
> You keep making this point, but it seems rather silly. First, it's an appeal to authority logical fallacy.

It is shorthand so I don't have to write all that smart stuff they did. I am trying to argue against "static typing in C will make your programs safer". You guys for some reason chose to ignore that post, but heap on me when I disagree. So you all agree with 

[quote=Delever]I suggest choosing language where compiler checks the most and which have good choices of IDEs. Java.(...)

Second choice in this case (for me) would be Python. It is not strong typed, so compiler will check less. It can be argued that you can achieve more neat tricks this way, but we are talking stability, not tricks[/quote] 
at all points? Static typing == stability?

---

### Post by Delever on 2008-10-31
This is surely fun, I am probably that quoted OP :popcorn:

Can I suggest a solution? Like... we will never be able to actually measure this for all possible tasks?

---

### Post by pmasiar on 2008-10-31
> **pp. said:**
> OP of this thread is you. 


This thread was created from discussion by mod, OP shold be Delever, I answered to his (IMHO) wrong assumptions. 

> Endorsements by world-known experts may not be worth the paper they aren't written on. 

It's better than nothing? Better than opposing side has? I take expert over anonymous forum poster every time, unless poster can substitute some substance. 

You do, and my writing was little careless. I did not had time to write better response, and will have even less time now. 

> The arcticle linked to in the OP of this thread just summarizes 'strong testing better than static typing' (not 'strong typing' as this thread says), without actually mentioning any particulars which would allow one to weigh that statement.

I agree. Please you do better job than me.

Poster quoted in OP was wrong, refute his claims with better arguments than mine if you can. be my guest.

---

### Post by jdonnell on 2008-10-31
> **pmasiar said:**
>  I am trying to argue against "static typing in C will make your programs safer". You guys for some reason chose to ignore that post, but heap on me when I disagree. 

That's because I didn't read it. I've only read this post. If we're talking about Java/c/c++ then I completely agree with you. But Java/c/c++ are not the be all end all of static typing. You HAVE made in THIS thread arguments about static typing generally, and not about java/c/c++ specifically. People reacted to those claims.

> 
Strong static type checking is used as replacement of testing. Stability and quality can be achieved only by testing, and quite a few posters completely miss that.

> next step is for average poster to recognize that quality and stability cannot be checked by static compiler: it has to be tested out. And if you do strong testing anyway, there is little reason to use statically typed language

Clearly you were making claims about static typing generally and not about java/c/c++ specifically.

---

### Post by slavik on 2008-10-31
> **pmasiar said:**
> All I am saying that new experience says that relying on static compiler check to make your program reliable is not enough, despite many people promoting that idea. And if you write strong tests, your code can be reliable even in dynamically typed language. And because with dynamic language you have less code written faster, your task to test all the code is simpler.

So, you're saying that everyone should test their code very well. I agree with that. So, what is your point???

EDIT: please look at the attachment. choosing a tool has nothing to do with testing a solution, even if some tools allow you to have less testing.

---

### Post by nrs on 2008-10-31
Of course relying on static typing alone is insufficient, but it does have its advantages, and any competent programmer doesn't solely rely on it.  In order of preference: 
Static/Strong
Dynamic/Strong
Static/Weak
Dynamic/Weak :cry:

---

### Post by slavik on 2008-10-31
Let's not forget about languages that allow you to write programs that can be proven to be correct without any need for testing ...

---

### Post by jdonnell on 2008-10-31
> **slavik said:**
> Let's not forget about languages that allow you to write programs that can be proven to be correct without any need for testing ...

I wonder how such a language would work for a practical project. Most of the code I write is constantly dealing with input from the outside world. Data from a db, feeds from other sites, web services from other parts of the company. 

Most bugs in our code is a result of people not checking if something is nil/null. Here's an example from code I have open right now.

```

question.sides[0].members[0].user.long_name_with_title("\n")

```

.sides() and .members() are both db calls which could return nil. This is actually wrapped to ensure they exist.

---

### Post by slavik on 2008-10-31
Haskell is one. Also to note is that such proves do not involve validating input. The prove is that the program will solve the problem correctly.

---

### Post by pmasiar on 2008-10-31
> **slavik said:**
> Let's not forget about languages that allow you to write programs that can be proven to be correct without any need for testing ...

Let me guess: Perl? ;-)

@ all: guys, I am done with this topic, I don't have time to argue with people who refuse to read links and try to catch minor issues. 

Yes of course Haskell   is different. OP was talking about static typing in C being superior.

Have a nice day, I have interesting and urgent project - and in Python! 8-)

---

### Post by Delever on 2008-10-31
> **pmasiar said:**
> Let me guess: Perl? ;-)

@ all: guys, I am done with this topic, I don't have time to argue with people who refuse to read links and try to catch minor issues. 

Yes of course Haskell   is different. OP was talking about static typing in C being superior.

Have a nice day, I have interesting and urgent project - and in Python! 8-)

It's also enough for me to watch how you always put arguments of others against my opinion, because I somehow happen to be source of this topic. I also have nice project... oh wait, projects, in C++ and C#. C++ for learning, C# for living :)

---

### Post by LaRoza on 2008-10-31
> **jdonnell said:**
> At this point I can't believe you are being sincere. PG clearly believes that lisp is more powerful and better than python. Again, if we are playing appeal to the authority then pmaiser should be using lisp


He wasn't playing appeal to authority, just that those people make good arguments and are knowledgable.

The point isn't that $PERSON uses it therefore it must be good, it is $PERSON says this, go read what they say.

---

### Post by CptPicard on 2008-10-31
> **Delever said:**
> I also have nice project... oh wait, projects, in C++ and C#. C++ for learning, C# for living :)

Why would you use C++ for learning? It's a language that you may want to know the specifics of for use as a tool when you need it, but intellectually speaking, if you seek enlightenment, you really should be doing your learning on languages that let you focus on the problem and that have a more powerful set of primitives. Any lisp would do :)

> **LaRoza said:**
> He wasn't playing appeal to authority, just that those people make good arguments and are knowledgable.


Indeed. It's really funny how in these threads in particular those people who demand citations and references and are sticklers to "fact-based argumentation" (which means they get to dismiss everything that is being said on "procedural errors" and argue exactness to the point of everything that is said becoming moot -- see Lster) are the first to accuse one of argument from authority when references are actually given.

The whole point of referring to stuff other people already wrote is to avoid having to repeat oneself after having read interesting arguments from other people. And if the author is recognized to have actually achieved something in the field, he may indeed have something worthy to say.

---

### Post by Delever on 2008-10-31
> **CptPicard said:**
> Why would you use C++ for learning?


I meant.. I am learning it. Not use it for learning. Or maybe I use it for learning... how to work with boost, std library, etc.

Or, "English is not my native language, sorry for my English". :lolflag:

---

### Post by LaRoza on 2008-10-31
> **Delever said:**
> I meant.. I am learning it. Not use it for learning. Or maybe I use it for learning... how to work with boost, std library, etc.

Or, "English is not my native language, sorry for my English".:

You are using it and learning how to use it. 

Actually, of the people active in this conversion, I think most of us aren't native English speakers. I am, but three others aren't at least.

---

### Post by jdonnell on 2008-10-31
> **CptPicard said:**
> It's really funny how in these threads in particular those people who demand citations and references and are sticklers to "fact-based argumentation" ... are the first to accuse one of argument from authority when references are actually given.

Please show me where I have ever demanded citations. Please do or stop with the passive aggressive insults directed at me.

> 
so instead of me trying to verbalize it, why won't you argue against Eckel's **expert** opinion?

Sounds like he's claiming that Eckel's opinion is more valid because he is an "expert". Also, a link to someones opinion in their blog is not a citation to some sort of fact.

---

### Post by LaRoza on 2008-10-31
> **jdonnell said:**
> Please show me where I have ever demanded citations. Please do or stop with the passive aggressive insults directed at me.

Perhaps you don't see it, but any time someone with years of experience and higher degrees express opinions, they are often confronted with the "all opinions are equal" mentality, usually from those with less knowledge. They are often told to cite their sources, and when they do, they are accused of apealing to authority. There are few facts in this discussion. Obviously, most things "work", but what works the best or the best most often isn't so clear so the opinions of people who are well respected and knowledgable are valuable. It doesn't make sense to get an opinion as to whether "void main(void)" is valid C because there is a clear standard. In the same light, it makes little sense to ask for clear cut facts in stone for somethings that do not have standards.

> 
Sounds like he's claiming that Eckel's opinion is more valid because he is an "expert". Also, a link to someones opinion in their blog is not a citation to some sort of fact.
See? Of course it isn't a clear cut fact. No one is saying it is. If all opinions are equal, then I will not speak ever.

---

### Post by CptPicard on 2008-10-31
+1 LaRoza, I was going to post something like that but you got there first. Well put.

jdonnell, actually I saw your reaction coming and it is case in point -- you choose to stick to the detail of me having to prove to you that you have demanded citations (or verifiable "facts"), when it is the content of what I am saying is that I would expect to be considered. Of course I understand it is a handy line of attack, but it is also complete diversion... if I were a kid on playground, I would retort with "where did I ever refer to you specifically?" but let's not go there... I am not into that kind of one-upmanship, I seek to communicate here in bona fide.

As a matter of fact, I am mostly an outsider to the whole thread and haven't even really much from you yet, although I am looking forward to doing that.

Anyway, what is to be considered admissible "fact" is very flexible in particular among the people who tend to, statistically speaking here, argue from a position of more ignorance, as bona fide views of people who have been around are not considered valid. That is, they accept nothing, and just keep demanding more and more "proof". I am old enough to understand that if some guy who actually has proven he knows a lot of stuff, says something, I will carefully consider it without claiming it's false from the outset.

Most of the knowledge in the field is latent experience... it can be communicated and discussed about, attempting to give people a push in interesting directions, but it's not a formal science by a long shot. I think software development would be a solved quantity by now if we had some sort of formal theory that would turn it all into mathematics. Software Engineering is trying to do that, and I am not impressed at the results yet :)

---

### Post by samjh on 2008-10-31
I've stayed away from this discussion because I guessed (correctly) that it will dissolve into a roaring flame war.  I post this after reading only pmasiar and Bruce Eckel's article (which I've read before).

The title of both this thread and Eckel's article is non-constructive.  Why "Strong Typing vs Strong Testing"?  Surely anyone who is involved in writing anything more than trivial programs should endorse both strong typing AND strong testing (by strong typing, I'm using the correct term, not the twisted version Eckel used in his title)?

Another observation is that the OP and Eckel both ignore the problem space.  If I'm writing code to display a drop-down menu on a web page, such code doesn't need a language with strong typing.  On the other hand, code to control the trim angle of a fighter jet should have multiple levels of protection against unreliable execution, including static strong typing.

> **jdonnell]I wonder how such a language would work for a practical project. Most of the code I write is constantly dealing with input from the outside world. Data from a db, feeds from other sites, web services from other parts of the company.[/quote]I think Slavik is talking about languages designed for static code analysis, such as SPARK said:**
> Second choice in this case (for me) would be Python. It is not strong typed, so compiler will check less. It can be argued that you can achieve more neat tricks this way, but we are talking stability, not tricksPython is strongly typed, but it isn't statically typed.  Eckel's unfortunate use of twisted terminology isn't helping here. ;)

It's generally accepted in safety-critical software development that static typing is preferred over dynamic.  But safety-critical software development is also about analysing and mitigating risk, and whether the risk of using dynamically typed languages can be mitigated by any possible productivity gains and the ability to use the productivity gains to increase testing.  I have not seen any studies from safety-critical projects that says using dynamically typed languages have enough benefit, but who knows what the future holds?

---

### Post by LaRoza on 2008-10-31
> **samjh said:**
> 
The title of both this thread and Eckel's article is non-constructive.  Why "Strong Typing vs Strong Testing"?  Surely anyone who is involved in writing anything more than trivial programs should endorse both strong typing AND strong testing (by strong typing, I'm using the correct term, not the twisted version Eckel used in his title)?

This thread's title was made from the suggestion in a post by the now OP. This thread is an orphan (split from another topic).

---

### Post by jdonnell on 2008-10-31
> **LaRoza said:**
> 
See? Of course it isn't a clear cut fact. No one is saying it is. If all opinions are equal, then I will not speak ever.

Since you're educated you probably realize this statement of yours is a non sequitur. I never implied that all opinions are equal. I believe that the opinion should stand on it's merits but I was answered with "but bruce eckel is an expert". I even gave a precise example of where static type checking would prevent certain bugs for free where you'd need 100% test coverage to get the same confidence in a dynamic language. Pmaiser did not respond to my example which isn't surprising. Instead I've been insulted by him and others.

---

### Post by jdonnell on 2008-10-31
> **CptPicard said:**
> 
jdonnell, actually I saw your reaction coming and it is case in point -- you choose to stick to the detail of me having to prove to you that you have demanded citations (or verifiable "facts"), when it is the content of what I am saying is that I would expect to be considered

You keep claiming I've done things I've never done. You are confusing me with someone else. Where did I demand that you prove anything to me? As I said in my previous comment, I gave a specific example of where static typing prevents a common bug where dynamic type checking would require 100% test coverage to do the same. This is the latent experience you claim we should all share yet you ignore my example and insult me and claim I've said things I've never said (twice!).

---

### Post by slavik on 2008-11-01
> **LaRoza said:**
> This thread's title was made from the suggestion in a post by the now OP. This thread is an orphan (split from another topic).
the original title was "Python vs. Java ... again?" because that is what it always turns out to be. In any case, even though Java dynamically allocates objects and has garbage collection and such, I have seen some bad Java code in action ... I am sure Python can be misused in similar ways and I would hypothesize that it would be very easy, too.

---

### Post by pp. on 2008-11-01
/*

---

### Post by CptPicard on 2008-11-01
> **jdonnell said:**
> You keep claiming I've done things I've never done.

Actually, it is quite the other way around.

> As I said in my previous comment, I gave a specific example of where static typing prevents a common bug where dynamic type checking would require 100% test coverage to do the same.

Actually, I do not doubt at all that there are numerous specific examples one can attempt to use to prove something in general. The problem is that specialized situations are just that.

> This is the latent experience you claim we should all share yet you ignore my example and insult me and claim I've said things I've never said (twice!).

Where? If you imagine I have been insulting you, I apologize, but this has never happened as far as I am concerned.

---

### Post by LaRoza on 2008-11-01
> **slavik said:**
> the original title was "Python vs. Java ... again?" because that is what it always turns out to be.

Or they are just used as popular languages on either side of the fence (so to speak). 

It was renamed at the created OP's request.

---

### Post by slavik on 2008-11-01
But those are only 2 out of a whole lot of languages that can fit either category.

---

### Post by LaRoza on 2008-11-01
> **slavik said:**
> But those are only 2 out of a whole lot of languages that can fit either category.

That is true.

---

### Post by jdonnell on 2008-11-01
> **CptPicard said:**
> Actually, it is quite the other way around.

You never back up your words. I haven't made a single claim about you specifically other than the fact that you keep saying things about me that are untrue. This is now the third time you've done it. You claim you want to have discussions based on the merit of the opinion yet you keep resorting to personal insults about me specifically and people generally. 

Let's get back to the real issue and see if you mean what you say. I gave one example of a benefit of strong typing; typos. You say this is a "specialized situation". I'm not sure what that means, but I do know that people make typos very often! The only way to ensure that a typo doesn't happen in a dynamic language is to have absolute 100% test coverage. A static language gives you this guarantee for free. 

Let me say again that I'm not advocating staticly typed languages, I'm a rubyist after all. I believe the productivity boosts given by dynamic typing outweigh the benefits of static typing in most situations.

If I were making medical equipment that someones life depends on then I'd consider a static language. If I'm making a bloggy web 2.0 app I'd go with a dynamic language without a doubt.

---

