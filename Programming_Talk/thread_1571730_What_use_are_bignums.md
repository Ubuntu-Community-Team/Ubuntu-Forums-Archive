---
title: "What use are bignums ?"
date: 2010-09-10
forum: Programming Talk
---

### Post by worksofcraft on 2010-09-10
You know, some high level languages like Python can automatically change your numbers into so called bignums. These are integers that can grow indefinitely to accommodate whatever precision is required.

My computer has a 64 bit architecture and is quite capable of doing 64bit integer calculations without **any** use of bignums.

So... just what does 64 bits of accuracy offer? Let us put it in perspective: Do you think the distance from Christchurch to Auckland in millimeters would be kind of over the top?

Well let me tell you that doesn't even scratch the surface of 64 bits arithmetic! What we have in 64 bits is the capability to record the distance from Christchurch... not to Auckland... not to the Outer Hebrides... but to the Moon... 23 times and back :shock:

Not in millimeters, not in micrometers, but right down to the very last **nanometer**!

So... can anyone actually explain what kind of "asset" *are* these bignums that can take me beyond that 64 bit integer precision?

---

### Post by schauerlich on 2010-09-10
Quick, what's factorial(100)?

While you're devising an algorithm to calculate it a few bits at a time, I'll use this and sip some Dr. Pepper.

```
(define (fact n)
  (define (fact-iter k acc)
    (if (= 0 k)
       acc
       (fact-iter (- k 1) (* acc k))))
  (fact-iter n 1))
```

P.S. Remember when a gig of RAM was obscenely huge? pretty soon 64-bit will be like 16.

---

### Post by worksofcraft on 2010-09-10
> **schauerlich said:**
> Quick, what's factorial(100)?

While you're devising an algorithm to calculate it a few bits at a time, I'll use this and sip some Dr. Pepper.

```
(define (fact n)
  (define (fact-iter k acc)
    (if (= 0 k)
       acc
       (fact-iter (- k 1) (* acc k))))
  (fact-iter n 1))
```

P.S. Remember when a gig of RAM was obscenely huge? pretty soon 64-bit will be like 16.

Well um... I do wonder why I would want to calculate fatorial 100. I mean, I would seriously question my algorithm if it involved a number like that which I couldn't offset against some divider somewhere... However, assuming I really did, is there any particular reason I should not use the standard floating point functionality that my processor supplies?
```

>>> def factorial(n):
...     if n == 1:
...             return 1
...     else:
...             return n*factorial(n-1)
...
>>>factorial(100.0)
9.3326215443944102e+157

```

seems good enough to me :popcorn:

---

### Post by Barrucadu on 2010-09-10
> **worksofcraft said:**
> seems good enough to me :popcorn:

```
> (define (fact n)
  (define (fact-iter k acc)
    (if (= 0 k)
       acc
       (fact-iter (- k 1) (* acc k))))
  (fact-iter n 1))
> (fact 100)
93326215443944152681699238856266700490715968264381621468592963895217599993229915608941463976156518286253697920827223758251185210916864000000000000000000000000
>
```

What if you needed to know it exactly? Some algorithms require huge numbers, just because you haven't used them doesn't mean that they have no purpose.

---

### Post by worksofcraft on 2010-09-10
> **Barrucadu said:**
> ```
> (define (fact n)
  (define (fact-iter k acc)
    (if (= 0 k)
       acc
       (fact-iter (- k 1) (* acc k))))
  (fact-iter n 1))
> (fact 100)
93326215443944152681699238856266700490715968264381621468592963895217599993229915608941463976156518286253697920827223758251185210916864000000000000000000000000
>
```

What if you needed to know it exactly? Some algorithms require huge numbers, just because you haven't used them doesn't mean that they have no purpose.

Fair enough... next time I need to know the **exact** number of nanometers from Christchurch to the moon and back I'll keep it in mind, but I'll probably just use floating point calculations where I don't really need quite that many digits precision ;)

---

### Post by fct on 2010-09-10
[quote=worksofcraft]Well um... I do wonder why I would want to calculate fatorial 100. I mean, I would seriously question my algorithm if it involved a number like that which I couldn't offset against some divider somewhere... However, assuming I really did, is there any particular reason I should not use the standard floating point functionality that my processor supplies?[/quote]

Yep:

[http://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic#Applications](http://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic#Applications)

[http://gmplib.org/](http://gmplib.org/)

> The main target applications for GMP are cryptography applications and research, Internet security applications, algebra systems, computational algebra research, etc.

This is an example of practical cryptography turned into a math+programming challenge:

[http://projecteuler.net/index.php?section=problems&id=182](http://projecteuler.net/index.php?section=problems&id=182)

---

### Post by StephenF on 2010-09-10
> **worksofcraft said:**
> Fair enough... next time I need to know the **exact** number of nanometers from Christchurch to the moon and back I'll keep it in mind.
[http://www.lmgtfy.com/?q=large+numbers&l=1](http://www.lmgtfy.com/?q=large+numbers&l=1)

---

### Post by CptPicard on 2010-09-10
Also, it's not just a matter of having huge integers, but the side-issue of wanting to have exact arithmetic that is exact in decimals/fractions...

---

### Post by Bachstelze on 2010-09-10
> **CptPicard said:**
> Also, it's not just a matter of having huge integers, but the side-issue of wanting to have exact arithmetic that is exact in decimals/fractions...

Yup, because rounding errors are [bad]("http://en.wikipedia.org/wiki/Ariane_5_Flight_501"). :)

---

### Post by MadCow108 on 2010-09-10
> **worksofcraft said:**
> Fair enough... next time I need to know the **exact** number of nanometers from Christchurch to the moon and back I'll keep it in mind, but I'll probably just use floating point calculations where I don't really need quite that many digits precision ;)

to use your example:
I ahve the distance to crater X the moon and the distance to crater Y too.
Now I want to know the height difference of the craters.
So you do this:
dist_y - dist_x
And already you have a problem: Loss of significance.
The two distances are almost the same, so you lose lots of your information in this simple calculation when using finite precision.
And now consider more complex problems with long chains of calculation each propagating the errors...

To overcome this one either uses a different algorithm or higher/arbitrary precision.
There is a whole field of mathematics which deals with this:
[http://en.wikipedia.org/wiki/Numerical_analysis](http://en.wikipedia.org/wiki/Numerical_analysis)

If you are working on scientific programs, knowing these problems and how to solve them is an absolute must!
Here is an good and long article:
What Every Computer Scientist Should Know About Floating-Point Arithmetic
[http://docs.sun.com/source/806-3568/ncg_goldberg.html](http://docs.sun.com/source/806-3568/ncg_goldberg.html)

---

### Post by schauerlich on 2010-09-10
> **worksofcraft said:**
> Well um... I do wonder why I would want to calculate fatorial 100. I mean, I would seriously question my algorithm if it involved a number like that which I couldn't offset against some divider somewhere... However, assuming I really did, is there any particular reason I should not use the standard floating point functionality that my processor supplies?
```

>>> def factorial(n):
...     if n == 1:
...             return 1
...     else:
...             return n*factorial(n-1)
...
>>>factorial(100.0)
9.3326215443944102e+157

```

seems good enough to me :popcorn:

And you're using a bignum, it's the mantissa of that float. :)

---

### Post by worksofcraft on 2010-09-10
> **MadCow108 said:**
> 
...
To overcome this one either uses a different algorithm or higher/arbitrary precision.
There is a whole field of mathematics which deals with this:
[http://en.wikipedia.org/wiki/Numerical_analysis](http://en.wikipedia.org/wiki/Numerical_analysis)

If you are working on scientific programs, knowing these problems and how to solve them is an absolute must!
...

I totally agree. When designing an algorithm one would do far better to have an understanding of the issues surrounding ill conditioning and find an implementation that avoids it instead of blindly depending on infinite precision.

IMO use of bignums should be a **conscious** design decision. Like when one has a **genuine** application for them. An explicit bignum class is fine, but not something your compiler may insert indiscriminately.

So far I think the only valid excuse mentioned for using bignums would be in cryptography.

> **schauerlich said:**
> And you're using a bignum, it's the mantissa of that float. :)

Um... well I don't blame you for not noticing, this... Indeed if I had typed "factorial(100)" without the ".0" it would have used bignums, but as it is, check the less significant digits against the Lisp bignum output given earlier: You will see that it has made cumulative rounding errors because it was using the processor's native floating point processor and not the Pythonic bignum emulation.

You see my opinion is that it would be much **better** if the programmer was encouraged by the language to be aware of the performance/accuracy trade-off in the two implementations so that an intelligent choice can be made which one is most appropriate ;)

---

### Post by Wybiral on 2010-09-10
In Python at-least (and probably other high-level languages that use them) they don't just give you a bignum. It converts to bignum when your register-sized integer would overflow. If you do for some reason get to that point, IMO, that's what you'd want to happen. Everything continues to run on just fine. As it should, the math you coded will keep working, it's math, independent of register size.

---

### Post by Simian Man on 2010-09-10
> **worksofcraft said:**
> IMO use of bignums should be a **conscious** design decision. Like when one has a **genuine** application for them. An explicit bignum class is fine, but not something your compiler may insert indiscriminately.
What compiler inserts bignums indiscriminately?  Python only converts numbers to bignums when they actually overflow - a situation in which native integers are obviously not sufficient.

> **worksofcraft said:**
> So far I think the only valid excuse mentioned for using bignums would be in cryptography.
Good for you.  There are a lot of other uses for them in advanced mathematics - a field where you rarely allow any imprecision.

> **worksofcraft said:**
> Um... well I don't blame you for not noticing, this... Indeed if I had typed "factorial(100)" without the ".0" it would have used bignums, but as it is, check the less significant digits against the Lisp bignum output given earlier: You will see that it has made cumulative rounding errors because it was using the processor's native floating point processor and not the Pythonic bignum emulation.
You misunderstood him.  He said that the mantissa portion of the float is stored as a bignum.  I don't know if that's true, but either way you didn't understand him :).

---

### Post by Wybiral on 2010-09-10
> **worksofcraft said:**
> You see my opinion is that it would be much **better** if the programmer was encouraged by the language to be aware of the performance/accuracy trade-off in the two implementations so that an intelligent choice can be made which one is most appropriate ;)

The wise programmer will need to know, in the event that a bottleneck is created by it. But the wise programmer should not be prematurely optimizing her code down to machine-specific implementations. Especially if she's not writing for just one machine. And especially when rounding errors and integer overflow have nothing to do with her equations.

---

### Post by CptPicard on 2010-09-10
> **worksofcraft said:**
> When designing an algorithm one would do far better to have an understanding of the issues surrounding ill conditioning and find an implementation that avoids it instead of blindly depending on infinite precision.

You know, I'm a theoretical algorithms guy by education. At its purest the field has very little to do with actual programming, and you just strike me as the low-level guy who equates algorithms with choosing bit sizes of data types. That... is just irrelevant in the big scheme of things. 

If you need bitsets, you want bitsets in one form or the other. What you're pushing here is just pointless though... knowing the range of your data sounds just sort of trivial. Trivial enough to be handled by the VM if it is suitable. If it is not, then use your own specific datatype definition.

In any case, I would never judge an algorithmics guy based on any of this; it's a triviality.

EDIT: O HAI Wybiral, missed you, brother!

---

### Post by worksofcraft on 2010-09-10
> **CptPicard said:**
> You know, I'm a theoretical algorithms guy by education. At its purest the field has very little to do with actual programming, and you just strike me as the low-level guy who equates algorithms with choosing bit sizes of data types. That... is just irrelevant in the big scheme of things. 

If you need bitsets, you want bitsets in one form or the other. What you're pushing here is just pointless though... knowing the range of your data sounds just sort of trivial. Trivial enough to be handled by the VM if it is suitable. If it is not, then use your own specific datatype definition.

In any case, I would never judge an algorithmics guy based on any of this; it's a triviality.

EDIT: O HAI Wybiral, missed you, brother!

If you want to solve problems in the abstract then you do so symbolically, without ANY calculations and probably without even a computer.

Once you have solved it, you reach a symbolic formula.

You don't actually submit any of this to the "VM" until you have specific data. Only then do you want to compute a specific result and that is when the actual computations are no longer "irrelevant trivia".

It strikes me you may be confusing the two totally separate issues: One is theoretical science, the other is the science of computing.

Let me give you an example:

Einstein worked out that theoretically E = mc^2
He used lots of symbolic formulas but absolutely NO calcutions and the method of calculating was irrelevant to his theory.

Now if I were tasked to calculate the Energy stored in a particular mass using Einstein's formula I would not have to understand ANY of his theory. To the computer scientis, THAT  would be the irrelevant trivia: I would be concerned with the magnitude and accuracy of the quantities involved and how best to perform said calculation for it's intended purpose.

---

### Post by worseisworser on 2010-09-10
> **worksofcraft said:**
> I totally agree. When designing an algorithm one would do far better to have an understanding of the issues surrounding ill conditioning and find an implementation that avoids it instead of blindly depending on infinite precision.

IMO use of bignums should be a **conscious** design decision. Like when one has a **genuine** application for them. An explicit bignum class is fine, but not something your compiler may insert indiscriminately.

No, this is a premature optimization; the root of all evil.

The default (implicit) should _always_ be safety; then one trade some safety for speed as one get to know or understand the problem one deal with well enough. Often, the actual bottlenecks move to different locations at the end anyway.

If you are dealing with something trivial you might get away with planning things ahead, but trivial things are by nature not very interesting; so what's this discussion about again?

Whether you agree with this is totally uninteresting to me by the way but I'm pretty sure most, the majority FWIW, agrees with me and knows about this stuff; it is considered basic knowledge anyway.

[http://en.wikipedia.org/wiki/Program_optimization#When_to_optimize](http://en.wikipedia.org/wiki/Program_optimization#When_to_optimize)

You propose declaring what is bignum from the start, but this is redundant and in any case less than optimal considering the machine domain; performance. If you instead have a sane and safe default where things may float from int -> bignum automatically, then have an explicit optimization declaration available as an option leading to no automatic int -> bignum conversion (detection) for some variable -- you avoid being forced to do premature optimization. I do not expect you to understand why this makes total and obvious sense both with regards to the machine domain, the problem domain and with regards to software engineering; and I do not care either.

---

### Post by StephenF on 2010-09-10
I just realised the perfect tangent thread to this one would be "What's the point of non-segmented addressing schemes?"

I reckon bignum support could be coming to a future generation x86 CPU by way of the large caches that they sport. It seems a crime not to.

---

### Post by CptPicard on 2010-09-10
> **worksofcraft said:**
> If you want to solve problems in the abstract **then you do so symbolically**, without ANY calculations and probably without even a computer.

Once you have solved it, you reach a symbolic formula.

I get the feeling you do not understand the problem domain of computer science -- whether something is just solvable in the abstract, or whether by machine, is the *core* of the whole field.

Computer science works within the domain of *computable functions*. It is well known that this domain is quite restricted. 
What computer science works with is the general problem of what is symbolically solvable by machine in the first place (computability theory); and second, how efficient these solutions are computationally, if they exist (computational complexity theory).

This means that things like bit lenghts are fundamentally pretty meaningless. Computability is a very deep-rooted phenomenon...

---

### Post by worksofcraft on 2010-09-10
> **CptPicard said:**
> I get the feeling you do not understand the problem domain of computer science -- whether something is just solvable in the abstract, or whether by machine, is the *core* of the whole field.

Computer science works within the domain of *computable functions*. It is well known that this domain is quite restricted. 
What computer science works with is the general problem of what is symbolically solvable by machine in the first place (computability theory); and second, how efficient these solutions are computationally, if they exist (computational complexity theory).

This means that things like bit lenghts are fundamentally pretty meaningless. Computability is a very deep-rooted phenomenon...

I get the feeling that some accademics here fail to understand the very nature of computer science.

Perhaps you may think the algorithm calculating factorials right at the start of this thread is correct and that by using bignums it becomes "safe" and universally applicable?

Now just suppose we want to use it in calculation of bit error rates in optical communication systems and the forumla is some kind of statistical distribution of the number of photons available in the transmission duration of a single data bit.

So we are talking about division of factorial huge number by factorials of other huge numbers multiplied by tiny time durations. Imagine the problem if you try calculating fatorial (10^23) and then dividing it by something similar, just because it's all so safe with bignums? In reality we should have realized that for this application it be more appropriate to use an approximation named Poisson distribution, if I remember correctly.

Also I'm surprised nobody noticed the small issue of the type domain of the argument: What if I try factorial 1/3*3 ? small rounding error... equality n==1... need I explain? And then did I even pause to ask whether perhaps factorials of numbers with fractions are perfectly legitimate... and how are they to be calculated?

Very "deep-rooted" to computer science is also error propagation. Providing a result to 157 decimal places when that original 100 input parameter could be in error by up to 10% would be completely and utterly stupid.

Speaking of inappropriate and types. I find it also unnecessary to type cast other people on this forum as "low level guys who don't understand what they are talking about" without considering that perhaps it is just **you** who does not understand what they are talking about.  :popcorn:

---

### Post by Wybiral on 2010-09-10
> **worksofcraft said:**
> Perhaps you may think the algorithm calculating factorials right at the start of this thread is correct and that by using bignums it becomes "safe" and universally applicable?

No, not universally acceptable, but given the situation of an overflow error, instead of crashing, they allow your code to continue running correctly. This is very useful for code running out in the wild.

> **worksofcraft said:**
> So we are talking about division of factorial huge number by factorials of other huge numbers multiplied by tiny time durations. Imagine the problem if you try calculating fatorial (10^23) and then dividing it by something similar, just because it's all so safe with bignums?

Then that's one of those cases where, as you scale up, you realize you have a bottleneck. Nobody said bignum was the all-powerful cure for your numerical ailments. We've been saying that it makes sense for a language to cast into bignum when an integer goes out of range, to preserve the integrity of the results in a place where it CAN be preserved.

Whatever performance penalty you suffer at that point, it's much better than an absolute crash. If you have code running in the wild, you'll understand that point.

But any code will have a problem simply making it TO the wild if it's developer sits around fiddling bits, trying to predict all possible performance issues (without rigorous profiling and testing), and gaining decreasingly small amounts of "constant" performance increase to potential massively scaling problems.

---

### Post by Simian Man on 2010-09-10
> **worksofcraft said:**
> Now just suppose we want to use it in calculation of bit error rates in optical communication systems and the forumla is some kind of statistical distribution of the number of photons available in the transmission duration of a single data bit.

So we are talking about division of factorial huge number by factorials of other huge numbers multiplied by tiny time durations. Imagine the problem if you try calculating fatorial (10^23) and then dividing it by something similar, just because it's all so safe with bignums? In reality we should have realized that for this application it be more appropriate to use an approximation named Poisson distribution, if I remember correctly.
That's a very contrived example and also a total straw man.  You're arguing that bignums are useless because there are cases where they can be avoided?  Nobody said they'd automatically use them for something like this.  I really think you were under the impression that Python always uses bignums even when not needed and are now trying to justify this thread.

> **worksofcraft said:**
> Also I'm surprised nobody noticed the small issue of the type domain of the argument: What if I try factorial 1/3*3 ? small rounding error... equality n==1... need I explain? And then did I even pause to ask whether perhaps factorials of numbers with fractions are perfectly legitimate... and how are they to be calculated?
I did notice it, and I'm sure others did too, but as it was tangential to the argument I didn't point it out.

> **worksofcraft said:**
> Speaking of inappropriate and types. I find it also unnecessary to type cast other people on this forum as "low level guys who don't understand what they are talking about" without considering that perhaps it is just **you** who does not understand what they are talking about.  :popcorn:
Nearly every programmer I know of has gone through three stages.  In one they are learning and know that they are clueless.  In the second they have learned a fair amount, but greatly overestimate their abilities.  They "optimize" everything they can even when it is not needed or even harmful to the task at hand.  This is the group Cpt. Picard assigned you to - and I agree with him.

Then there are the programmers who have learned (often through bitter experience) that premature optimization is a waste of time at best and, more frequently, actually hurts what you're trying to develop.  Also they know that the code *you think* is the bottleneck doesn't always turn out to be.

---

### Post by worksofcraft on 2010-09-10
> **Simian Man said:**
> That's a very contrived example and also a total straw man.


No it isn't. Do you seriously think a recursive function won't crash your computer if you get it to call itself that many times?

It is a perfect example of what happens when you skip proper analysis and start typing in code on the pretext of "not optimizing too soon".

You and others making personal judgements don't know anything about my abilities. I don't know about your "3 categories of programmers" but I do believe there are some who think they know it all but in reality have such closed minds that they can produce nothing but mediocre repetition of standard patterns.

---

### Post by Reiger on 2010-09-11
Well be careful with contrive examples. They bite aggressively and leave a nasty sting:

Hence why you get Haskell programs like this:

```

-- main simply provides an event loop... 
main :: IO()
main = do
       -- code here
       main -- call itself, indefinitely: there is no base case

```

---

### Post by nvteighen on 2010-09-11
This is completely absurd.

I'm a Linguistics-student and I hope you know CompSci and Linguistics have influenced eachother in very benefitial ways. In a nutshell, Linguistics is about why people don't speak chaotically; CompSci is about abstract problem solving. CompSci needs to apply some theory on symbols (from Linguistics) and Linguistics needs to apply some basic theory on computability (from CompSci) to generate abstract linguistic structures (e.g. X-Bar Theory!)

Why do I tell you this? Look at this code:
```

/* gcc -o silly silly.m -Wall -Wextra -lobjc */

#import <objc/Object.h>
#import <stdio.h>

@interface Silly : Object
{
@public
    int number;
}

-(id)init:(int)start;
-(void)printSilly;

@end

@implementation Silly : Object

-(id)init:(int)start
{
    number = start;

    return self;
}

-(void)printSilly
{
    printf("Hey, this number is %d!\n", number);
}

@end

int main(void)
{
    id mySilly = [[Silly alloc] init:4];

    [mySilly printSilly];

    [mySilly free]; // I should have used GNUStep..

    return 0;
}

```

Ok, if you don't understand it is not because it doesn't work. It's because you don't know the language. Obviously. If you know Objective-C (btw, a great "C (just) with classes" language: low-level OOP, but nicely done), then you'll be able to tell what this stupid example does without having to compile it and executing it.

What I mean with this is that programming is much more about language than what it seems. **You** are dealing with symbolic data much more than you think: **you** code using a language and **you** think in the concepts that language gives to you. The computer is just a secondary thing that is able to run that code, but essentially, what'you ve done is to lay down some concepts in a formal-logical language.

And words are, as the philosopher John Locke said, marks for ideas that we can use to show our ideas to others or to remember your own. That's what you do whenever you use a language... including a program: the fact that you can simulate that idea in a computer is just the same as you can use Physics to build a bridge.

That's why low-level languages and concepts aren't the best to talk about CompSci. Ok, they're needed, but they are tied up to the implementation and therefore, less universal or, better said, you have to specify a lot of more things external to the language itself in order to have people understand what's going on.

That's the issue with bignums and that's what they are for: they're a step closer to how we expect numbers to work trying to avoid the limitations of the computer at best. That's why I love Lisp's idea to use fractions as default... it's perfect and simple.

---

### Post by worseisworser on 2010-09-11
> **worksofcraft said:**
> No it isn't. Do you seriously think a recursive function won't crash your computer if you get it to call itself that many times?

It is a perfect example of what happens when you skip proper analysis and start typing in code on the pretext of "not optimizing too soon".

You and others making personal judgements don't know anything about my abilities. I don't know about your "3 categories of programmers" but I do believe there are some who think they know it all but in reality have such closed minds that they can produce nothing but mediocre repetition of standard patterns.

We don't care about your abilities, others' abilities or our own abilities.

What we propose is exactly the opposite; that we do not know, and more importantly; that we can not know.

You miss the point over and over again...

---

### Post by worseisworser on 2010-09-11
PS: You might want to check out this thing called "tail recursion" ...

In any case I can easily crash my run-time even though it has support for sane memory management, bignums etc. etc. etc.; that is (again) not the point.

---

### Post by CptPicard on 2010-09-11
> **worksofcraft said:**
> I get the feeling that some accademics here fail to understand the very nature of computer science.

It is the study of different classes of problems and what kind of abstract machines are capable of solving those classes of problems. In the end, it is the study of what is computable by any (maximally capable, probably Turing machine equivalent) physical machine. After computability is established, it becomes interesting to study the efficiencies of different solution strategies to said problems given the abstract machines, or a mathematical generalization of computational efficiency (think Big-Oh).


> Perhaps you may think the algorithm calculating factorials right at the start of this thread is correct and that by using bignums it becomes "safe" and universally applicable?

If you're referring to the floating point issue that was IIRC in your own post; no, I ignored it as as a sign of your level of competence and just shrugged the whole thing off. Anyone credible wouldn't ry floating point in a factorial to begin with for obvious mathematical reasons. Also, as worseisworser pointed out, that you don't seem to have heard of tailcall elimination is also a bit interesting.


> 
Now just suppose we want to use it in calculation of bit error rates in optical communication systems and the forumla is some kind of statistical distribution of the number of photons available in the transmission duration of a single data bit.

I'd rather not. When I am dealing with a specific problem, I'll consider its requirements for what they are, and not think that they represent something generically applicable -- unless there really is a general underlying problem down there somewhere.

> 
Very "deep-rooted" to computer science is also error propagation. Providing a result to 157 decimal places when that original 100 input parameter could be in error by up to 10% would be completely and utterly stupid.

Not sure I've ever considered that to be a "computer science" issue in particular... whenever one is losing precision somewhere, this happens. Fact of life. But when you've got an arbitrary precision library to do things for you and you can/need to use it, it's all good, at least from my perspective.

> 
Speaking of inappropriate and types. I find it also unnecessary to type cast other people on this forum as "low level guys who don't understand what they are talking about" without considering that perhaps it is just **you** who does not understand what they are talking about.  :popcorn:

I've been on UF PT since 2006 and I've seen the "I'm a wizened bit-twiddler guy who focuses on specifically knowing my data type lengths and that's the most crucial/only thing that matters and everything else (that I don't bother understanding) is just a crutch for incompetents" type over and over again. We typically have one of them going every couple of months. It gets a bit old.

Also, why do you guys *always* (really!) add :popcorn: at the end of your posts when you feel like you've managed a snappy comeback? :)

---

### Post by worksofcraft on 2010-09-11
> **CptPicard said:**
> 
If you're referring to the floating point issue that was IIRC in your own post; no, I ignored it as as a sign of your level of competence and just shrugged the whole thing off. Anyone credible wouldn't ry floating point in a factorial to begin with for obvious mathematical reasons. Also, as worseisworser pointed out, that you don't seem to have heard of tailcall elimination is also a bit interesting.


I was referring to the Lisp implementation by schauerlich. It is a perfectly correct solution... when using integers. I hope you are aware that integers are a natural data type used for counting things.

My Pythonic version is merely because I find Python code far more readable and intelligible.

Both of them demonstrate several aspects of claims being made about what computer languages should and should not do: These algorithms were conceived, designed and implemented to work with integer data.

The designer did not actually want the compiler to try running them on floating point numbers, or any other data type for that matter.

The fact that it merrilly trundles off and does so, even returning a semi plausible result is an indisputable demonstration of what a _can of worms_ has just been opened here.

Secondly, your inability to grasp that optimization techniques such as *tail recursion elimination* are low level concepts, speaks volumes about your level of understanding of the domain of computer science:

Tail recursion optimization relates to low level hardware implementation issues... such as memory management and where results and function parameters are stored on the stack. It has **nothing** to do with abstract computability or correctness of the algorithm. A competent high level language implements it transparently.

FYI I have programmed several full applications in Prolog and I am consequently fully aware of how tail recursion can and even **has to be** optimized for the Prolog inference engine to be able to work. However the factorial implementation I made does not exploit tail recursion optimization for the reason stated above: It is low level compiler responsibility that is not part of the problem domain.

Now personally I find quite a few of the posts on this thread arrogant, condescending and even sneering in tone. Those are IMO not necessary, objectionable and not worthy of a response. OTOH, if you look at posts like the one by nvteighen, you will see that there is a much more constructive and compelling way to communicate your point of view and to carry on  an intelligent discussion.

---

### Post by worseisworser on 2010-09-11
What's your point again?

How does using a *float* in your previous example have anything to do with ints and bignums?

I mean; yes, we do not have full 100% idiot-proof safety for all cases and all things etc. yet; is this your point? If yes; how is this interesting and relevant when talking about the point in having bignums?

---

### Post by worseisworser on 2010-09-11
Wait, WHAT? ... Are you talking about lack of type checking now? *sigh*

Why do you talk in absolutes based on assumptions; why do you not ask questions instead? Where is your curiosity? So tiresome ...

```

CL-USER> (defun factorial (n &optional (a 1))
           (declare (rational n))
           (if (<= n 1)
               a
               (factorial (- n 1) (* a n))))
FACTORIAL

CL-USER> (factorial 100.0)

...
...

The value 100.0 is not of type RATIONAL.
   [Condition of type TYPE-ERROR]

Restarts:
 0: [RETRY] Retry SLIME REPL evaluation request.
 1: [*ABORT] Return to SLIME's top level.
 2: [TERMINATE-THREAD] Terminate this thread (#<THREAD "repl-thread" RUNNING {100399ABD1}>)

```


..so this is possible in dynamic languages too, but how is this even *remotely* related to anything here? ..and where are you coming from? C/C++ doesn't have an *even remotely* interesting type system! (..look at Haskell or Ocaml etc. for that..)



edit: In case *you* have trouble with `[rational]("http://www.lispworks.com/documentation/HyperSpec/Body/t_ration.htm")' I could have said `integer' which is a sub-type of `rational'.

edit2: Oh, and I can do compile-time type checking too; this was run-time only.

edit3: ..and further, if you do not want the int -> bignum switch to happen at all; declare things to take and return `fixnum'; `fixnum' is the "same as" int in C.

---

### Post by Wybiral on 2010-09-11
> **worksofcraft said:**
> Tail recursion optimization relates to low level hardware implementation issues... such as memory management and where results and function parameters are stored on the stack. It has **nothing** to do with abstract computability or correctness of the algorithm. A competent high level language implements it transparently.

Yes, it should be taken for granted. When you code in a high-level language, you want that kind of thing to be exactly that, transparent. Just like you want the handling of integer implementation to be just that... Transparent. You want your numbers to do the logical thing for numbers to do. Numbers don't wrap around or yield incorrect results in the real world just because some far away computer has limited register sizes. They don't do that in our minds either (unless we've trained ourselves to deal with the limitations of some specific platform).

In an ideal world, we would have something like bignum for recursion (the computer magically solving the issue of stack growth and recursion limitation for us). I would, at least. That's my #1 complaint about Python, actually, is the terrible recursion support.

Obviously, since we are running our solutions on limited machines, we do have to deal with some limitations. However, whenever we can grant ourselves freedom from having to think one step lower than we need to, we grant ourselves more freedom from code clutter and conceptual steps that are irrelevant to the solution to our original problem.

Low level clutter obfuscates our code's intentions. Sure, in adds some performance increase on some platforms, but it greatly reduces the performance of that code's ability to run on one very important platform... The human mind. Our ability to visually parse, mentally run, and logically analyze the solutions to problems represented by our code.

---

### Post by Wybiral on 2010-09-11
These are just examples, but the the ease at which you can quickly solve these problems using bignums should be taken as a valid point in this argument :
```
def fibonacci(n):
  a, b = 0, 1
  for i in xrange(n):
    a, b = b, a + b
  return a

print(fibonacci(100000))
```

And 10000! :
```
from operator import mul

def factorial(n):
  return reduce(mul, xrange(2, n + 1))

print(factorial(10000))
```

..and yes, notice how I did have to reword the solutions because of Python's recursion limitations, but I did NOT have to reword them to compensate for their being WAY larger than a modern register would hold. They're both pretty straight forward and mentally parsable. Exactly why bignum is used. And if I could have my way, the recursive forms would work exactly the same.

---

### Post by worksofcraft on 2010-09-11
> **Wybiral said:**
> Yes, it should be taken for granted. When you code in a high-level language, you want that kind of thing to be exactly that, transparent. Just like you want the handling of integer implementation to be just that... Transparent. You want your numbers to do the logical thing for numbers to do. Numbers don't wrap around or yield incorrect results in the real world just because some far away computer has limited register sizes. They don't do that in our minds either (unless we've trained ourselves to deal with the limitations of some specific platform).



Thank you Wybiral those are really good insights there and I feel I understand exactly what you mean about merits of bignums now :)

Just as a matter of interest even humans do sometimes like numbers to wrap round... even in our minds: Many years ago I had to make graphics routines on a bitslice processor as we were processing radar information... all our coordinates were in terms of range and bearing and involved a lot of angles. We scaled them so that PI was represented by 2^15 and thus all our angle calculations had free modulo arithmetic within 360 degrees. It might seem trivial now but when your processor is several thousand times slower than what we have today and only 16 bit it's quite a performance asset too!

---

### Post by Wybiral on 2010-09-12
> **worksofcraft said:**
> ust as a matter of interest even humans do sometimes like numbers to wrap round...

Definitely. It's all about the problem at hand. If the problem at hand is low level, like when you're writing a device driver, a compiler's code generator for some processor, or are forced to squeeze every ounce of performance out of some targeted platform, then your solution requires low level mental constructs. And in those cases, that no longer is cluttering the solution, that IS the solution.

But I rarely work on those problems. I mostly work on numerical/algorithmic/textual problems. And when I write those solutions the last thing I want is some code, irrelevant to expressing my solution, cluttering things up. The last thing I should be worrying about while solving things is what some processor might be doing with register EAX, because that's not part of my solution, that's not my problem.

---

### Post by CptPicard on 2010-09-12
> **worksofcraft said:**
> I was referring to the Lisp implementation by schauerlich. It is a perfectly correct solution... when using integers.

Damn, worseisworser got there faster, but now you've switched your argument to complaining about dynamic typing, if I'm following you.

>  I hope you are aware that integers are a natural data type used for counting things. [...] Now personally I find quite a few of the posts on this thread arrogant, condescending and even sneering in tone. 

Pot, kettle, eh?

> 
Both of them demonstrate several aspects of claims being made about what computer languages should and should not do: These algorithms were conceived, designed and implemented to work with integer data.

The designer did not actually want the compiler to try running them on floating point numbers, or any other data type for that matter.

The dynamic vs. static typing discussion has been going on for a long time; dynamic typing gives you genericity, while possibly producing runtime type errors. Not much that can be done with that.

My issue with your thinking is that your attitude is seems to be that we somehow do not *understand* these tradeoffs, and that you're here to educate us about them as if they were something new; while it's all in a sense a bit trivial, and you come across as having just thought about all of what goes into non-C languages... (I'm a bit surprised you've done Prolog, good for you...)

> 
The fact that it merrilly trundles off and does so, even returning a semi plausible result is an indisputable demonstration of what a _can of worms_ has just been opened here.

In order for it not to do so would require static typing. A programming environment cannot analyze the algorithm itself for such correctness, not at least in a general case. Just one of those dynamic-typing tradeoffs I was talking about. Of course there is the possibility to do a runtime check of the type.

> 
Tail recursion optimization relates to low level hardware implementation issues... such as memory management and where results and function parameters are stored on the stack. It has **nothing** to do with abstract computability or correctness of the algorithm.

Not really. In Scheme we're dealing with not having to create new environment frames. It is not a very low-level hardware implementation detail, and the general principle that a tail recursion can be converted to a loop is a insight in any programming language (of course, the tail recursion is, theoretically speaking, the somewhat more fundamental idea of the two). And language design is certainly one of those theoretical problems that get studied within CS.

But again, I was talking about a different issue; that it's you that seemed to actually miss that the tailcall is optimized, blaming schauerlich for assuming that he's not going to run out of stack. There was very little to do other than draw the conclusion that you're unaware of tail recursion removal.

>  A competent high level language implements it transparently.

Yes, agreed.

> It is low level compiler responsibility that is not part of the problem domain.

I am not sure where the disagreement is here, then, as it seems like it "opens cans of worms" in your view generally. I have always been of the opinion that HLLs should optimize whatever they can and let the programmer work on the problem. Of course this does not mean that the programmer must not understand his tools, which again seems to be the assumption of the "other side" typically...

---

### Post by GenBattle on 2010-09-12
I'm all for a bit of healthy discussion, but can we stop feeding the troll?

I would have to agree with the category cptpicard put you (worksofcraft) in; stage 2 programmer.

People have already linked perfectly valid reasons for why you need bignums. Crypto is the main one i would point out. Isn't there a monetary prize for discovering a prime number above a certain number of digits? I know the algorithms they use for that deal with insanely huge numbers.

In the end though, this thread is just the lament of a bored troll; it's not a valid question to ask why something should exist when you're already of the opinion it shouldn't, it's just meant to incite a flamewar between two groups of people with differing views, or maybe just to inflate your own ego.

---

### Post by worseisworser on 2010-09-12
GenBattle:
*Duty Calls*
[IMG]http://imgs.xkcd.com/comics/duty_calls.png[/IMG]

( from: [http://xkcd.com/386/](http://xkcd.com/386/) ) .... :)

---

### Post by worksofcraft on 2010-09-12
> **GenBattle said:**
> I'm all for a bit of healthy discussion, but can we stop feeding the troll?

I would have to agree with the category cptpicard put you (worksofcraft) in; stage 2 programmer.

People have already linked perfectly valid reasons for why you need bignums. Crypto is the main one i would point out. Isn't there a monetary prize for discovering a prime number above a certain number of digits? I know the algorithms they use for that deal with insanely huge numbers.

In the end though, this thread is just the lament of a bored troll; it's not a valid question to ask why something should exist when you're already of the opinion it shouldn't, it's just meant to incite a flamewar between two groups of people with differing views, or maybe just to inflate your own ego.

Personally I don't see why I should put up with adhominem attacks like this. If you have nothing constructive to add then I suggest you and certain others take your arrogant and conceited attitude and irrelevant opinions elsewhere.

---

### Post by nvteighen on 2010-09-12
> **worksofcraft said:**
> OTOH, if you look at posts like the one by nvteighen, you will see that there is a much more constructive and compelling way to communicate your point of view and to carry on  an intelligent discussion.

Thanks! :)

Ok, back to bignums, which is supposed to be the topic of this thread, although the UF PT threads go off-topic by nature (and how many times I myself was the cause of that!).

Wybiral makes a great point:

> **Wybiral said:**
> 
But I rarely work on those problems. I mostly work on numerical/algorithmic/textual problems. And when I write those solutions the last thing I want is some code, irrelevant to expressing my solution, cluttering things up. The last thing I should be worrying about while solving things is what some processor might be doing with register EAX, because that's not part of my solution, that's not my problem.

worksofcraft, having read several of your threads and discussed in them, sometimes I get the impression that you are driven by some mistrust... No, not mistrust on us, but on everything you're using to create your own code... For example, the whole thing about environment variables... Now, it is bignums and the fact that languages give you predefined sizes (although it seems you've finally got Wybiral's point).

I tend to see that the idea I quoted from Wybiral also has the following consecuence that also applies in sciences: if something works, you show assume it will work until you observe the contrary... in other words, when you're doing Astrophysics, you don't have that much time to waste reviewing every single previous hypothesis there is unless you catch an issue with one while working on your own. Think of this in low-level terms: it's inefficient! Team work is key for human evolution... using others' ideas and trusting them is one form of team work. For example, when I'm writing some paper and I cite someone because I think his idea is good for mine, I'm in some way "teaming up" with that author I cited. In programming, you can say this is the same: there are several bignum libraries like GMP... you've heard it's quite good (and it is) and you need that: use it, because GMP is the solution done by someone else for his own problem (overcome the limitations of C built-in types... there's no need to use that library in Lisp, for example).

When you propose things like having languages that let people absolute freedom for defining their own data types's sizes right from the bits, it makes me wonder what would happen if that was real. The language would be completely useless because in order to do anything, you'll be first overcoming the problem of defining a sane data type. Also, it'd be useless because it would be a hell to make ABIs compatible. Why one of the goals of CS is language design is because it's the first problem anyone encounters when programming: you need a logical-formal language... but you want to do something related to protein folding, not writing your language! So, the very act of using a language not written by you is a first step of abstraction and trust, because you decide to use the solution the language designer gave to that first primal problem of CS.

So, trust your platform a bit more ;)

(oh no... I went off-topic again...)

---

### Post by CptPicard on 2010-09-12
> **worksofcraft said:**
> OTOH, if you look at posts like the one by nvteighen, you will see that there is a much more constructive and compelling way to communicate your point of view and to carry on  an intelligent discussion.

I've been reading nvteighen's posts since he showed up here, and we've been together in most of the threads like this (we should probably dig some of them up for you to review so you'd better be on the same page with the thinking that has gone before here). He and his style are very familiar. He is *incredibly* patient and often verbose, something I do not always have the interest in when being more direct serves just as well.

---

### Post by worksofcraft on 2010-09-12
> **nvteighen said:**
> 
When you propose things like having languages that let people absolute freedom for defining their own data types's sizes right from the bits, it makes me wonder what would happen if that was real.

Like I said on that thread... I put it down to communication failure. It was never my intention to define data types down to individual bits. It was to tell the compiler that I wanted a data type **capable** of holding a certain range of values. It was for the compiler to have the freedom and responsibility to choose one of it's internal (machine/implementation) dependent types that would be most appropriate.

I do not think the proposed future C++ standard goes about it intelligently, by introducing things like char_16, char_32 and redefining char to be:  "both **at least** the size necessary to store an eight-bit coding of UTF-8 and large enough to contain any member of the compiler's basic execution character set."

Regardless if one understands what was being said. Some respondents were way too eager to start ridiculing, flaming and making personal attacks.

As for trust, that's the whole point of this thread. From the examples I mention it should be clear that several of the liberties taken in high level languages can result in a **false** sense of security and become a liability rather than an asset.

---

### Post by worksofcraft on 2010-09-14
Also all this discussion reminds me of a multi-task scheduler I wrote in C++ once. It used the standard functions "setjmp" and "longjmp" to rapidly switch between the contexts of concurrent tasks.

The critique I got was that setjmp was obsolete and that I should be using "throw" and "catch"... evidently the critics failed to grasp that I did not actually want to wind down the whole context of each task... but to preserve it intact so it could be resumed again later.

Attempting to explain this on that occasion proved utterly futile because they had closed their mind and were not going to listen. As these were my employers I wrote a new set of functions called mark_context and switch_context... mysteriously the code in them looked very similar to what was in setjmp and longjump  :D

---

### Post by worseisworser on 2010-09-14
As I see it there's a disconnect between the thing you want(ed) and several of the things you criticize.

edit: Perhaps I've grown tired and forgotten what it was you originally wanted because you've branched out many times in several threads. Something about UTF-8? Then chars/ints not being portable with regards to number of bits cross-machine? But then also specific types based on bits; int32 etc., not good enough even though those are portable with regards to bits cross-machine? ..and even further bit-fields or general bit-manipulation "not good enough", either; I don't even recall you ever replying to those suggestions? Then something about bignums; as if *those* had *anything* to do with these previous things? :roll:

So what's this about again really? I'm certainly not confused about any of these things if that is what you're implying with your story; I have more trouble following you.

---

### Post by worksofcraft on 2010-09-14
... I see it as a problem with other people not sticking to the topic. Other threads I wrote have been about other things but if you inject them here, just simply for the sake of having an argument then the discussion goes all over the place.

The real reality of computer programming is that most programs process real world data, and not abstract mathematical quantities. People who designed things like the Linux kernel and data communication protocols are not just dealing with "tedious irrelevant trivia" but a very real part of computer science.

It may not have occurred to you but some computer languages, like Pascal are quite particular about data types and there is a good reason for that. Converting things from one form to the other by default is IMO in real applications likely to create more problems that it solves.

---

### Post by Wybiral on 2010-09-14
> **worksofcraft said:**
> The real reality of computer programming is that most programs process real world data, and not abstract mathematical quantities. People who designed things like the Linux kernel and data communication protocols are not just dealing with "tedious irrelevant trivia" but a very real part of computer science.

I will repeat this, because it seems like the point hasn't quite gotten across. For people writing kernels, communication protocols, drivers, compiler code generators, etc, the platform specific details of bit formats and processor instructions ARE part of the problems you're trying to solve and are integral parts of the solution.

But for problems outside of those very specific domains, mathematical, algorithmic, textual problems... Those details just cloud the original problem and water down the solution. When I'm writing graph searching functions, parsing some relevant information out of text, solving computational geometry problems, etc, the last thing I want to worry about are those low-level, platform specific issues. I'd rather just focus on writing a clear, working solution.

> **worksofcraft said:**
> Converting things from one form to the other by default is IMO in real applications likely to create more problems that it solves.

Once again, the conversion happens when the integer would run over which would be WAY worse to happen than a minor slowdown from using a reasonably fast bignum implementation at that point. Fail/lose data integrity or slow down a bit? Which do you think your users would prefer to happen?

---

### Post by Reiger on 2010-09-14
To address a specific complaint about $language; the inability to specify an assertion on a type so that the compiler only admits values within a specific range:

... It requires more information than the compiler has. Pretty much requires an automated proof than each data value V submitted to function F in the program is within bounds, but to prove this you require to be able to prove this for each instance of V in each call to F. 

Humans can do that, because Humans have more than the raw syntax/semantics of a language to work with: they also grasp the design of a program intuitively because they are able to mentally restrict themselves to the same class of problems the program is trying to solve. A compiler/language implementation cannot do that, if it did it would be useless as a general purpose compiler/language implementation. 

Languages such as Ada/Haskell etc. come close in providing the compiler with necessary type information to spot many classes of errors, but to truly mess up is Human and to protected you against that is not something any useful compiler will be able to guarantee.

To address the complaint about not being able to generate a range of valid values... well actually that is a language level problem. In languages like Haskell or Python you can write generators/enumerating functions then use syntactic sugar like [1..100] to express a range of 1 to 100, as generated by the generator. So that is purely lacking a feature of Blub 1 in Blub 2, where it can be said that C/C++ is a notoriously bare bones version of Blub.

---

### Post by worksofcraft on 2010-09-15
> **Wybiral said:**
> I will repeat this, because it seems like the point hasn't quite gotten across.


I totally and categorically disagree with your point of view,  which is every bit as subjective as mine.

I don't believe in solving mathematical problems with actual numbers. I will do that symbolically. I don't use actual numbers in my formulas until I have some real world data to plug in and then I believe in the value of scaling my data set appropriately and knowing the accuracy of that data and consequently the accuracy of the computed result.

Looking at the applications I run on a daily basis... word processors, spreadsheet sheets web browsers compilers... I don't see many... no, make that ANY, that would benefit from having things changing from integers to floating point, to bignums to strings internally and I can't think of any that would have a use for bignums either.

p.s. and languages like Pascal and Java will throw an exception when values go out of range which I think is preferable than just converting it to something else and carrying on regardless.

---

### Post by matthew.ball on 2010-09-15
> **worksofcraft said:**
> I can't think of any that would have a use for bignums either.
You can't think of *any* reason to use bignums?

---

### Post by worksofcraft on 2010-09-15
> **matthew.ball said:**
> You can't think of *any* reason to use bignums?

Not in those applications that I run on a regular basis... that's why I asked the question originally.

---

### Post by matthew.ball on 2010-09-15
Ahh, you answered it there, in the applications *you* use there's no use for bignums. Just making sure you weren't saying bignums were useless :)

---

### Post by worseisworser on 2010-09-15
> **worksofcraft said:**
> ... I see it as a problem with other people not sticking to the topic. Other threads I wrote have been about other things but if you inject them here, just simply for the sake of having an argument then the discussion goes all over the place.

The real reality of computer programming is that most programs process real world data, and not abstract mathematical quantities. People who designed things like the Linux kernel and data communication protocols are not just dealing with "tedious irrelevant trivia" but a very real part of computer science.

It may not have occurred to you but some computer languages, like Pascal are quite particular about data types and there is a good reason for that. Converting things from one form to the other by default is IMO in real applications likely to create more problems that it solves.

Cool story bro. I mean, yes; just yes. Uhhuh? Mmh. Whatever.

---

### Post by worseisworser on 2010-09-15
> **worksofcraft said:**
> I totally and categorically disagree with your point of view,  which is every bit as subjective as mine.


No it is not. This is totally objective and well understood in the context of software engineering. You are *wrong* while Wybiral is *right*. There is no force here, in nature or elsewhere which can change this. No, just no; we cannot have a vote on this. We cannot have a sensible meeting, conversation or chat about this because it is a simple boring fact; common ground everyone needs to stand on. End of discussion, really.


> **worksofcraft said:**
>  don't use actual numbers in my formulas until I have some real world data to plug in

Is it *totally* impossible for you to imagine a scenario where you do not have this data available before Actual Execution in the real-world?

Let's imagine we're dealing with The Big Unknown here for a second;

[LIST]
[*]You will only get *one* shot at this because you will *kill* the people involved if you make a mistake.
[*]You will again only get one shot at this because you will *destroy* the equipment used if you make a mistake, and the cost (money or actual resources) does not warrant a second try.
[/LIST]

Have you ever dealt with something where Human lives where at stake, worksofcraft? Can you even imagine something like this; this kind of responsibility? What would you do, I mean; really?

No, this has nothing to do with your Word; this discussion is *about bignums or even software engineering or The Correct Attitude in _general_*.

You need to stop right now and say; "OK, yes I can totally see why bignums are useful in several cases, and how int->bignum or just bignum all the time makes sense." You need to regain your f'in integrity or honor or whatever and just End this weaseling around crap right now; you are wrong; bignums are very useful; get the .... over it Right Now or just leave.

You will kill people. You will blow up space ships; engines and the fuel near them; power plants; you will kill people in hospitals -- fill their bodies with radiation; missiles will explode before reaching their target, etc. etc. etc..


> **worksofcraft said:**
> p.s. and languages like Pascal and Java will throw an exception when values go out of range which I think is preferable than just converting it to something else and carrying on regardless.

INDEED; OMG; I DID NOT KNOW THIS!!11 .. SO DARN NICE!!111   No really; this, my brave, strong and smart Human friend; has caused **death**. Do you have what it takes to deal with that kind of ****; huh? .. or are you just playing around being all Mr. Educated Engineer dude down the hall or whatever ......

I'm all for birth control, but perhaps we should avoid killing the people who are as unfortunate to already be stuck here.

Unlike you with the "several clear examples you've provided" (where?) I, or we, can provide actual sources where death and/or massive losses with regards to resources was the end result, and I believe someone already linked to at least one source in this or some other thread; there are several other well known cases.


edit: 
Will a set of actual sources; Wikipedia articles; published papers etc., *end* this tedious boring issue for good? I will dig something up, if needed; but I think you have the "skillz" needed to Google around on your own tbh.. edit2: Here's one keyword for you; "ariane 5 flight 501" (64bit float --> 16bit int (..you know; instead of bignum..) --> overflow --> boom!).

---

### Post by Wybiral on 2010-09-15
The point I've been trying to make here is that source code is intended for humans to read and write. It is intended for us to be able to efficiently eye-parse and mentally execute to understand what's going on. If it weren't, we'd all be coding in machine language. When you're dealing with the computer directly (when the computer itself IS the problem) then it makes sense to think in terms of that machine. It makes sense to think about registers, bit formats, the stack layout, etc, and the language and linguistic constructs you use should mirror that problem domain.

But when you are not coding in that domain, it doesn't make sense anymore. It's noise. Garbage. Clutter. It should look like the solution to your problem, not like a platform specific "for computer eyes only" representation of your solution.

Nature doesn't care about 32/64 bit integers. A mathematician would laugh at you if you told her she had to prefix all of the variables in her equations with bit ranges just because some computer out there can't handle anything beyond that. That's nonsense. It's irrelevant to the math. Irrelevant to the problems she's trying to solve. When she adds *1* to *2,147,483,647* she expects *2,147,483,648*. Not *-2,147,483,648*. Because THAT is contrived, machine specific nonsense.

And why SHOULD it throw an exception? What good would that do your users? They don't care about integer sizes, try explaining that to them. They care that the program works. I'd rather my users experience a minor performance decrease when things get to that point than to just terminate or throw some error message at them. And I'd rather not code some hacky work around to deal with the numbers myself at that size. I don't have to. It exists. It's called "bignum"

---

### Post by Shippou on 2010-09-17
Hello.

I've been trying to hold myself from commenting on this thread (though I have read all of the messages posted here, including worksofcraft's creative(?) arguments and n people's opinions regarding the subject). Now, here's mine.

First, **Computer Science &#8802; Computer Programming**. The issue is like P and NP: P &#8834; NP, but this does not imply P &#8801; NP (heck, we do not even know if P &#8800; NP!). Similarly, computer programming is only a subset of computer science. 

Second, **Computer Science does not always mean programming**. I think this is one of the most common misconceptions about computer science. Although oftentimes (and it is somewhat given as a fact) most algorithms are implemented in software (or hardware), the designing of algorithms themselves SHOULD NOT depend on what machine the code will run on. In short, there should be a high degree of abstraction, meaning I should not care about how large an integer is, or how malloc addresses internal fragmentation vs external fragmentation.

Just to clarify on the point above, yes, in these types of algorithms, one DOES CARE about how machine limitations are addressed. But this is DURING the implementation phase, not during the planning phase (algorithm formulation). Sorry for being somewhat vague, but I think you know what I mean.

Another thing: there is such a thing as automata theory, a subbranch of computer science that deals with the mathematical description of a computer. In this field, no one really cares about concrete things such as registers and whatnot. Instead, these concepts are generalized in form of stacks, tapes, and head drives, but these are as well abstract. Hell, a Turing machine cannot even exist in real life! (Assignment to the reader: discover why). But even in these situations, algorithms can be designed: think of the Knuth-Morris-Pratt algorithm. Knuth himself wrote programs for a fictional processor, the MIX, and there is always his ever-present note that "these programs are mathematically-proven to be correct, but not tested on a real computer". You get my point.

Third, **Computer Science &#8800; Information Technology**. Another misconception, with an argument similar to the first point earlier.

Fourth, even in IT, **the focus of a program is to make things work, not how things work**. Yes, this is very counter-intuitive and a bane to human understanding, but then, if everyone focused on how, let's say, the Swing API worked up to the last detail, no work would be done. I am not saying that we should not study how things work, but for practical purposes, this should not be a main concern. To wit, this is also the main problem new users encounter with *nix: the (somewhat ever-present) need to learn how the OS works. (OMG, a flame bait!)

Another thing: in programming competitions, does one even care how efficient a program is? Given the time pressure, they don't; they focus only on how to make things work, not how things should work. As often said to students joining these competitions, **brute force is your friend**.

Fifth, **there is a concept called abstraction**. The goal of abstraction is to make certain things trivial, enabling the programmer to work on more important things. This does not only apply to CS but to other fields as well: processors, diodes, resistors and multiplexers are taken for granted to just work. As often said, "Do not reinvent the wheel." Unfortunately, CS people *always* reinvent the wheel. 

Sixth, and related to the point above, is **the 4 pillars of OOP: abstraction, encapsulation, inheritance and polymorphism**. Self-explanatory for your average CS guy/gal.

Now, back to the main issue: ** What use are bignums ?**

Previous posters have mentioned the field of crypto as an application. Honestly, I can't think of another application. I bet graphics rendering would be one (though this is on the concept of floats, not integers).

What I do find entertaining (and irritating at the same time) in this thread though is how a really simple question (what use are bignums) turned out to be a discussion of the benefit of abstraction (bignums) vs the need for the freedom for the programmer to choose on how to implement things. 

Now, what was that, and where did that come from?

Oh yeah, this post does come to mind.

> **worksofcraft said:**
> When designing an algorithm one would do far better to have an understanding of the issues surrounding ill conditioning and find an implementation that avoids it instead of blindly depending on infinite precision.

IMO use of bignums should be a **conscious** design decision. Like when one has a **genuine** application for them. An explicit bignum class is fine, but not something your compiler may insert indiscriminately.


From then on, the discussion revolved on the benefits of bignums and the purist notion that the programmer should be the responsible for his actions.

Personally, I tend to agree with this post:

> **Wybiral said:**
> 
Nature doesn't care about 32/64 bit integers. A mathematician would laugh at you if you told her she had to prefix all of the variables in her equations with bit ranges just because some computer out there can't handle anything beyond that. That's nonsense. It's irrelevant to the math. Irrelevant to the problems she's trying to solve. When she adds *1* to *2,147,483,647* she expects *2,147,483,648*. Not *-2,147,483,648*. Because THAT is contrived, machine specific nonsense.

And why SHOULD it throw an exception? What good would that do your users? They don't care about integer sizes, try explaining that to them. They care that the program works. I'd rather my users experience a minor performance decrease when things get to that point than to just terminate or throw some error message at them. And I'd rather not code some hacky work around to deal with the numbers myself at that size. I don't have to. It exists. It's called "bignum"

I think I need not expound anymore.

Yes, in certain applications, one does need to be concerned with these issues. Numerical computing comes to mind. But then, even in these types of applications, certain things are taken for granted.

Another thing:
> **worksofcraft said:**
> Like I said on that thread... I put it down to communication failure. It was never my intention to define data types down to individual bits. It was to tell the compiler that I wanted a data type **capable** of holding a certain range of values. It was for the compiler to have the freedom and responsibility to choose one of it's internal (machine/implementation) dependent types that would be most appropriate.


I'll be frank: if that's what you want, then go, no one's forcing you not to. In case of Python (and other languages that implement the same thing, for that matter), make sure that your numbers do not exceed -2^n to 2^n (where n is the number of bits a processor can support (e.g., 8, 16, 32, 64)). But don't complain that you have a very complex code, and more importantly, **don't impose what you want on us**.

There are VERY MANY and VERY OBVIOUS benefits of abstraction. Taking them away from a language because you don't like it is masochism. Anyway, you are not forced (in general) to use it, so don't. But you are assured that they're there, in case you change your mind.

These posts do come to mind (and are very entertaining to read, too):
[http://www.pbm.com/~lindahl/real.programmers.html](http://www.pbm.com/~lindahl/real.programmers.html)
[http://www.pbm.com/~lindahl/mel.html](http://www.pbm.com/~lindahl/mel.html)

And lastly, I also tend to find this post very appealing, concerning how things are turning out to be (wrt the original discussion):

> **GenBattle said:**
> I'm all for a bit of healthy discussion, but can we stop feeding the troll?


P.S.: what does wrt stand for, again? :?:

(I am not trying to be condescending, or [put synonyms of condescending here], just trying to make sense out of the (very tense) discussion.)

---

### Post by worksofcraft on 2010-09-17
> **Wybiral said:**
> 
Nature doesn't care about 32/64 bit integers. A mathematician would laugh at you if you told her she had to prefix all of the variables in her equations with bit ranges just because some computer out there can't handle anything beyond that.


Well speaking of nature... I thought my explanation about not measuring the distance to the moon in nanometers might make some sense to someone, but failing that, try the other way round: Would you attempt to measure the mass of an electron on your regular bathroom scales?

Now I don't care about 32/64 bit integers much either. What I do care about is the fact that they are integers and I do care about what range my values are in and I would like to know that the compiler will choose the right one.

You mention adding a 1 to a large number... but what if the compiler unbeknown to you has decided to change some part of your calculation into floating point arithmetic? Adding that one might not actually do anything because it is below the precision in which real numbers are stored :shock: Suddenly you are in a range of data where that algorithm you tried and tested fails miserably.

So personally I think having the compiler be a bit fussy about data types or at least do as it's told by the programmer is a good thing and it's more a matter of personal preference... or like a religious persuasion perhaps to some :D

---

### Post by worksofcraft on 2010-09-17
> **Shippou said:**
> 
I'll be frank: if that's what you want, then go, no one's forcing you not to. In case of Python (and other languages that implement the same thing, for that matter), make sure that your numbers do not exceed -2^n to 2^n (where n is the number of bits a processor can support (e.g., 8, 16, 32, 64)). But don't complain that you have a very complex code, and more importantly, **don't impose what you want on us**.


ehhh... impose on you? I don't think so.

I was just wanting a way to tell the C++ compiler that I have a data type which needs to store vales between 0 and 0x10FFFF (to be precise). Being offered "wide chars" that **might be** 32 bits, 16 bits or 8 bits depending on implementation doesn't seem like a very satisfactory solution to me TBH.

---

### Post by dwhitney67 on 2010-09-17
> **worksofcraft said:**
> ehhh... impose on you? I don't think so.

I was just wanting a way to tell the C++ compiler that I have a data type which needs to store vales between 0 and 0x10FFFF (to be precise). Being offered "wide chars" that **might be** 32 bits, 16 bits or 8 bits depending on implementation doesn't seem like a very satisfactory solution to me TBH.

In the context of C or C++...

Where have you found that a "wide-char", or specifically a wchar_t type, to be only 8-bits in size?  Or even 16-bits?

The max-value you indicated above would fit in 21 bits; barring that there is no data type with that size (unless you define one yourself), the next available size on most computers is 32 bits, or 4 bytes.  That is precisely the size I have found wchar_t to be on both 32-bit and 64-bit architectures.

Can you explain in layman's terms why the wchar_t data type is not fitting for your needs?

---

### Post by CptPicard on 2010-09-17
> **worksofcraft said:**
>  Being offered "wide chars" that **might be** 32 bits, 16 bits or 8 bits depending on implementation doesn't seem like a very satisfactory solution to me TBH.

Didn't you want a data type that gets specified more abstractly ("this needs to hold a wide-char") and then the compiler chooses actual bit length... and nothing is switched behind your back mid-computation.

By the way, Reiger's point about proving ranges for values in a program being a very hard problem is an excellent one. This is exactly why a lot of the overflow issues really are bugs that need to be rooted out by the human programmer -- there just simply is no good solution outside of doing runtime checks automatically all the time, which would then result in an error condition just as much as an overflow would.

Really, if one emphasizes the need to know one's bit lengths, it's just as good to use self-specified architecture-specific sizes in reasonable multiples (like you usually do in C) instead of dreaming about some "tightly fitting" special bit-length data types, that would just probably cause these unavoidable by compiler overflow bugs  probably even more than needlessly "big" data types would...

---

### Post by Shippou on 2010-09-17
> **worksofcraft said:**
> Well speaking of nature... I thought my explanation about not measuring the distance to the moon in nanometers might make some sense to someone, but failing that, try the other way round: Would you attempt to measure the mass of an electron on your regular bathroom scales?


Um, isn't the mass of an electron (and the distance to the moon, for that matter) NOT integer, but are floats?

And with regards to the imposing thing I've said earlier, I  was under the impression (given also my interpretation of your previous posts regarding the subject) that you want to do this. That's why I've written that part.

Anyways, the point is bignums have their uses, though they may be esoteric to the average programmer. However, battling whether bignums are useless or not (the topic seem to deviate to this discussion over time) is, IMHO, like the discussion of gotos being boon or bane. (As a side note, [this]("http://en.wikipedia.org/wiki/Goto#Criticism_and_decline") is a very interesting read about the subject.) Also, this is intellectual m*st*rb*t**n at its best.

---

### Post by Queue29 on 2010-09-17
> **Shippou said:**
> Um, isn't the mass of an electron (and the distance to the moon, for that matter) NOT integer, but are floats?



All rational numbers can be represented as integers, since they're just divided out by a power of 10 when they are represented as decimal numbers.

---

### Post by Shippou on 2010-09-17
> **Queue29 said:**
> All rational numbers can be represented as integers, since they're just divided out by a power of 10 when they are represented as decimal numbers.

Nice. But then, floats are handled differently as compared to ints, and because of the nature of hardware errors are inherent in floats (round-off errors, truncation errors).

> **worksofcraft said:**
> It was to tell the compiler that I wanted a data type **capable** of holding a certain range of values. 

You can go with enums. :p

> **worksofcraft said:**
> 
You mention adding a 1 to a large number... but what if the compiler unbeknown to you has decided to change some part of your calculation into floating point arithmetic? Adding that one might not actually do anything because it is below the precision in which real numbers are stored :shock: Suddenly you are in a range of data where that algorithm you tried and tested fails miserably.


ints to floats? Well, I don't know about you, but IMO any compiler that does this is buggy.

> **worksofcraft said:**
> 
So personally I think having the compiler be a bit fussy about data types or at least do as it's told by the programmer is a good thing and it's more a matter of personal preference... or like a religious persuasion perhaps to some :D

+1.

The point is, they have their uses, however esoteric they may be. APL comes to mind. :)

---

### Post by worksofcraft on 2010-09-17
> **dwhitney67 said:**
> In the context of C or C++...

Where have you found that a "wide-char", or specifically a wchar_t type, to be only 8-bits in size?  Or even 16-bits?

Can you explain in layman's terms why the wchar_t data type is not fitting for your needs?

Well apart from the fact that was on a different thread and I can't remember where I saw that at the time but think I posted the link... cba to check cuz quick google of wchar_t throws up plenty more such as:


[http://www.cppreference.com/wiki/keywords/wchar_t](http://www.cppreference.com/wiki/keywords/wchar_t)

"... therefore development of portable applications cannot assume that popular character representation, such as Unicode, can fit into a wchar_t ..."

[http://en.wikipedia.org/wiki/Wide_character](http://en.wikipedia.org/wiki/Wide_character)

"The width of wchar_t is compiler-specific and can be as small as 8 bits. Consequently, programs that need to be portable across any C or C++ compiler should not use wchar_t for storing Unicode text. "

and also says Python's documentation (so not just C/C++), "It depends on whether wchar_t is "compatible with the chosen Python Unicode build variant" on that system." Whatever that means :confused:

In layman's terms, the so called *"standard"* is  like having a handbook that says "we don't really know what this product does". So perhaps one particular instance is good for what I want, but the handbook is definitely not worth printing.

---

### Post by worksofcraft on 2010-09-17
> **Queue29 said:**
> All rational numbers can be represented as integers, since they're just divided out by a power of 10 when they are represented as decimal numbers.

Yes :)

In Python there is also a "decimal" number type. Allegedly  producing different results, from computations done with binary. 

Thus programmers are forced to consider all these low level details with only the most tenuous indication of what type of number different parts of their equations may or may not be working with and how efficient they may or may not be for the intended purpose :shock:

---

### Post by Wybiral on 2010-09-17
> **worksofcraft said:**
> You mention adding a 1 to a large number... but what if the compiler unbeknown to you has decided to change some part of your calculation into floating point arithmetic? Adding that one might not actually do anything because it is below the precision in which real numbers are stored :shock: Suddenly you are in a range of data where that algorithm you tried and tested fails miserably.

Using Python as an example (of a language I use most frequently, that does convert overflowed integers to bignum) it doesn't ever just cast your ints to floats or anything crazy like that. And if a function you're working on requires only integers, it's as simple as saying:

```

def function(arg):
  if not isinstance(arg, int):
    raise TypeError
  # Actual int-specific function here

```

You can write very type specific code if you want to. You can do the same thing in most Lisp implementations as well. But the type specificness isn't forcedly imposed on your ability to think about the problem. It's a good thing. But now we're getting of topic, "What use are bignums ?" ... They're useful for doing integer calculation above the machine-specific register size. And for "Why would a language automatically cast an overflowed integer to bignum ?" ... Because minor performance decrease is better than failure.

Don't want your numbers to be bignum?
```

def function(arg):
  if MIN_INT < arg < MAX_INT:
    raise ValueError
  # Actual int-specific function here

```

Problem solved. But why would you?

---

### Post by Shippou on 2010-09-17
> **worksofcraft said:**
> 
In Python there is also a "decimal" number type. Allegedly  producing different results, from computations done with binary. 


NOTE: **Decimals are not integers.** Integers are implemented as binary (the whole n) while decimals are BCD (Binary-Coded Decimal). Or at least, that's what I know.

> **worksofcraft said:**
> 
Thus programmers are forced to consider all these low level details with only the most tenuous indication of what type of number different parts of their equations may or may not be working with and how efficient they may or may not be for the intended purpose :shock:

I'm really confused: do you want a typeless language (like Ruby) or not (like C)? Or strongly-typed (like Ada), weakly typed (like C) or duck-typed (like Ruby) language? Because this has nothing to do with "What use are bignums ?"*[sic]*

---

### Post by CptPicard on 2010-09-17
By the way, Reiger's *excellent* point about the inability to actually prove by compiler the runtime ranges of values has important implications to this discussion.

As the compiler has at least serious issues doing such proofs (I can't recall if it is actually impossible -- it probably is in the general case) the only possibility would be constant runtime checks, or relying on the human programmer not to screw up. Here, defining as tight as possible ranges for the variables would just probably result in *more* overflow problems that would happen by just choosing from the architecture/compiler's predefined bit lengths or multiples/additive combinations thereof.

So it seems to me to just boil down to the general low-level guy's argument that you need to make it as hard for the programmer as possible as a matter of principle, and anyone who does not strive for that is just using a mental crutch...

---

### Post by worksofcraft on 2010-09-18
> **CptPicard said:**
> 
So it seems to me to just boil down to the general low-level guy's argument that you need to make it as hard for the programmer as possible as a matter of principle, and anyone who does not strive for that is just using a mental crutch...

Sounds to me like the high priest of academia doesn't like having his sacred idols questioned? However there are plenty of cases where lack of type safety is resulting in really obscure bugs that make things much harder for the programmer.

Bignums should simply be a separate class IMO... actually I'll see if I can recreate my first ever program in Python and see if anyone can fathom why it crashes :D...

---

### Post by worksofcraft on 2010-09-18
It was a program to test viability of generating pseudo random
digital noise at very high speed with a hardware shift register and an exclusive-or circuit... note, and yes electronics engineers can take umbrage at being referred to as "low level guys who deal in tedious trivia" :P

Try bits 20 and 21 should give a sequence of 4194302 iterations.
(using all combinations except for 0)

Sometime later... I'll give good old Python it's due... it hasn't crashed yet... hasn't solved the problem yet either though :(

I wonder why it's so excruciatingly slow :confused:

```

class shifter:
	def __init__(this):
		this.Shifter = 1
		this.bit1 = this.bit2 = 0
		this.getbits()

	def getbits(this):
		while this.bit1 == this.bit2:
			print 'identify two separate bits to xor'
			this.bit1 = 1 << input('1st bit:')
			this.bit2 = 1 << input('2nd bit:')

		# use up to most significant of those
		this.Mask = this.bit1
		if (this.bit1 < this.bit2):
			this.Mask = this.bit2
		this.Mask = (this.Mask << 1) - 1

	def xorbits(this):
		return bool(this.Shifter & this.bit1) is not bool(this.Shifter & this.bit2)

	def shift(this):
		nextbit = this.xorbits()
		this.Shifter <<= 1
		if (nextbit):
			this.Shifter += 1
		# finish when cycle starts repeating
		return (this.Shifter & this.Mask) > 1
		
Counter = 0 # count iterations
S = shifter() # create a shift register
# Proving that the cycle will always return to it's start point
# is left as an exercise
while S.shift():
	Counter += 1

print 'pseudo random sequence was', Counter, 'iterations.'

```

p.s. the title of this thread explains a lot ;)

---

### Post by Shippou on 2010-09-18
Seems like this thread is becoming more of like an ad hominem attack between posters. This thread really should be closed. Besides of being a waste of words, this is also a waste of database space.

In my opinion, this thread really is intended to be a flame war between bignum users and non-bignum ones, concealed cleverly in the innocent-looking question "What use are bignums ?"[sic] Why do I say so? The moment people say bignums can be used in this context (crypto for example), *someone* would then say "No, no! You can also emulate this via [datatype/algo/logic crap]. Then, we really don't need bignums!" When someone (and a lot of PATIENT people already did) point out the benefits of bignums and abstraction in general, and also of the hazards involving round-off errors and truncation errors and overflow errors and numerical whatnot (which is, BTW, MACHINE-DEPENDENT and, except in some number systems and coordinate planes (angles?), does not exist in mathematics) especially in mission-critical apps (yes, I have read about the ariane-5 disaster, thanks for the link), *someone* would not answer the issue, then waits for it to be *buried* with another new post about another topic.

Honestly, can we move on? Actually, the questioned was answered by the original poster himself/herself in this post:

> **worksofcraft said:**
> Not in those applications that I run on a regular basis... that's why I asked the question originally.

Also, interestingly, the one who insists bignums should be optional (or be removed) is the one who started the thread in the first place. Hmmnn, trying to up the bean count? :lolflag:

I am not trying to be rude here, just stating plainly what, I think, is going on. Honestly, I find this [megathread]("http://ubuntuforums.org/showthread.php?t=851794) much more worthwhile than this one (thanks for CptPicard for the link). 

Then, why I am posting things in this thread? I don't know, maybe the same reason why *someone* tries to keep this thread alive: to up the beans. :popcorn:

---

### Post by worseisworser on 2010-09-18
Yeah, this thread is done and over with. Every single "point" he has provided has been beaten to the ground several times, and now he's just repeating the same "points" while fishing.

edit:
Several of his "points" doesn't even make sense to begin with, and when addressed on this he doesn't even care; so the thread goes on.

---

### Post by Shippou on 2010-09-18
> **worseisworser said:**
> Yeah, this thread is done and over with. Every single "point" he has provided has been beaten to the ground several times, and now he's just repeating the same "points" while fishing.

edit:
Several of his "points" doesn't even make sense to begin with, and when addressed on this he doesn't even care; so the thread goes on.

+1

Hmmnnn... Seems like the "Report abuse" button really have its uses. :lol:

---

### Post by worksofcraft on 2010-09-18
> **worseisworser said:**
> Yeah, this thread is done and over with. Every single "point" he has provided has been beaten to the ground several times, and now he's just repeating the same "points" while fishing.

edit:
Several of his "points" doesn't even make sense to begin with, and when addressed on this he doesn't even care; so the thread goes on.

That's just pathetic.

I'm trying to have a sensible discussion complete with genuine and up front examples of the problems associated with things like bignums. Reading this thread is optional and snide smart *** remarks don't constitute a contribution.

---

### Post by worseisworser on 2010-09-18
> **worksofcraft said:**
> I'm trying to have a sensible discussion complete with genuine and up front examples of the problems associated with things like bignums.

No you're not.

---

### Post by CharlesA on 2010-09-18
I would suggest both of you [read the CoC]("http://ubuntuforums.org/index.php?page=policy").

Thread Closed.

---

