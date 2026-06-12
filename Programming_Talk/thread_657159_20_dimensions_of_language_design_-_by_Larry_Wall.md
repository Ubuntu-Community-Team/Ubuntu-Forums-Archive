---
title: "20 dimensions of language design - by Larry Wall"
date: 2008-01-03
forum: Programming Talk
---

### Post by pmasiar on 2008-01-03
Edit:

Instead of creating new thread, I decided to add one more post to this one.
Maybe I should go back to past and change it to "interesting reads" :-)
Maybe I will ask admins to do that

--------

I just found article [Programming is Hard, Let's Go Scripting...](http://www.perl.com/pub/a/2007/12/06/soto-11.html) by [http://en.wikipedia.org/wiki/Larry_Wall](http://en.wikipedia.org/wiki/Larry_Wall)

Excellent read about 20 dimensions to consider when designing/using programing language (with witty explanations how it works), which decisions is he making for Perl6, and why. Ie:
- Parts of the code could be written other language dialects (even in Klingon), if you wish. Nested!
- Many languages decide stuff at compile. Perl can execute code during compile phase (and decide according to results).
- No class could decide by itself to be "final" - but application can, at runtime, for optimization.
- Larry's look at syntax, where "Each symbol has to justify its existence according to Huffman coding."

Larry has interesting and commendable goal with Perl6, now I understand why it takes so long. As always,  Larry's talk is entertaining, enlightening, fun and smart. But I also can see why I will not be eager to switch to Perl6 anytime soon (even if available): I do not want to handle **that** many degrees of freedom by myself, or in a program who someone else wrote (or myself year ago).

Anyway, IMHO well worth the read, even for C/Java-and-nothing-else people, to understand your choices (and consequences) better.

Accidentally, it shows what might happen if trained linguist/anthropologist, instead of translating bible to an unknown tribe in Africa, will start designing programming language instead (after winning of "Obfuscated C" contest). :-)

Enjoy!

---

### Post by evymetal on 2008-01-05
Thanking you too.

Whew, it was long though. Here are my favorite bits:

> 
the professor announced we would be implementing our own language, called PL/0. After thinking about it a while, we announced that we were going to do our project in BASIC. The professor looked at us like were insane ... Nobody else in the class finished their compiler either. We not only finished but added I/O extensions, and called it PL 0.5. That's rapid prototyping.

(I used to code BASIC a lot, and it's good to hear people really sticking up for it)

> in the long run JavaScript might actually turn out to be a decent platform for running Perl 6 on.

> 
So basically, multiple dispatch is like democracy. It's the worst way to do late binding, except for all the others.

(Churchill quote for those who don't know it, and very aptly quoted/modified IMO)

---

### Post by pmasiar on 2008-01-16
Another interesting article: [Java: Evolutionary Dead End](http://www.artima.com/weblogs/viewpost.jsp?thread=221903) by Bruce Eckel.

Bruce discussed new features, like generics, with Josh Bloch. He argues that Java should stop adding features and become stable like C.

"The only control we have over complexity is abstraction: hide the parts that don't matter ("divide and conquer" is a variation). The paradox of of Java is that a critical aspect of the complexity problem was ignored; code readability was not considered an important issue. It seems that if the IDE writes the code for you, then it doesn't matter if that code is needlessly complex."

His post pointed my interest to [Scala](http://en.wikipedia.org/wiki/Scala_%28programming_language%29). Hmm, interesting. Not Jython, but close - and more functional. When 5 years from now CPU will have 80 cores, running 1 process will be running 1% of CPU. And functional programming seems to be the only way to run multiple threads and still remain sane. All non-functional languages will be called "dysfunctional" :-)

Another interesting read, IMHO.

---

