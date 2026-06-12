---
title: "Got 10 months time for learning new languages - Recommendations?"
date: 2009-09-05
forum: Programming Talk
---

### Post by enli on 2009-09-05
Hi, I am last year computer engineering student. Unfortunately I failed in a subject and hence I can't attend/finish the degree in this year (I will be allowed to attend college in July 2010). So that gives me about 10 months of free time which I intend to devote for learning new languages and master the stuff I already know.

Right now I am familiar with C, C++, Assembly, VB6, HTML, CSS, PHP at basic level as taught in college curriculum(India).

Since last 2-3 weeks I have been studying K&R and it is absolutely great book which taught me many new and complex things, as well as few coding practices to write shorter codes. I am starting with Java in 2-3 weeks for the preparation for one of my practical exam and also planning to give SCJP exam somewhere in Jan 2010. I also would like to contribute to open source community but have no idea where to start from. Maybe I will post question about this in another thread.

At this point I am confused to which programming languages I should learn which will prove helpful in landing myself a job after the completion of degree. I asked one of my relative who is already a .NET developer and he recommended me to learn ASP .NET as well as JavaScript.

**For those of who like to skip to the summary :**
Looking at [http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html) gives me an idea that I already know top languages but knowing them isn't sufficient but mastering them is much more important!! So I need recommendations on how do I spend next 10 months learning (new) programming languages and being expert at them.

---

### Post by hessiess on 2009-09-05
Lisp, Haskell and Pure functional programming.

---

### Post by Reiger on 2009-09-05
I don't see a pure functional language among your list of "things I know". They tend to give you really good value for money/time when you are in it for the learning experience...

And it is probably also worthwhile to learn some JavaScript, especially with regards to prototype's (which mixes particularly well with JavaScript's support for closures & anonymous functions). I think it is probably easiest if you pick up a pure functional language first (where stuff is what it advertises to be), then dabble in JavaScript because it is IMHO easier to pick up prototypes after you have seen some real functional languages (higher order functions & anonymous functions) instead of with a head full of the "old" C/C++/Java mindset.

JavaScript will give also give you a very nice additional tool for all sorts of web-based projects and currently the popular open source DE's KDE & GNOME seem to have a certain fondness for scripts as applets.

Finally if you have seen a "real" functional language with sufficient amount of interesting features & libraries you will probably also want to extend your knowledge to XSLT. Just because it is a nifty tool for XML manipulation that somehow manages to appear in all sorts of places.

---

### Post by falconindy on 2009-09-05
Python and Ruby are both excellent languages to know. Both are simple and elegant, with loads of community support and extensibility.

---

### Post by Can+~ on 2009-09-05
Python and learn about the functional paradigm, easy to do there.

---

### Post by uljanow on 2009-09-05
Try finding a job or start a project instead of learning new programming languages.

---

### Post by slavik on 2009-09-06
in my specific line of work, SHELL scripting and Perl go a long way.

---

### Post by falconindy on 2009-09-06
> **slavik said:**
> in my specific line of work, SHELL scripting and Perl go a long way.
Truth. Learning Bash or any other shell is probably one of the best things you can do if you're a Linux user. Expanding that to Perl creates almost endless possibilities. But alas, Perl does not love me. Nor do I love it.

---

### Post by nipunreddevil on 2009-09-06
python seems to be a good choice.Even Nasa and Google use it heavily.Google recommends C++ and Python.

---

### Post by CptPicard on 2009-09-06
Reiger, I certainly understand what you're driving at, but why the emphasis on purity? :) Haskell is nice and all that, but Lisp lets one get (most of) the idea of FP while allowing for more flexible solutions when mutable state is called for ...

---

### Post by enli on 2009-09-06
Thanks for overwhelming suggestions.

During my course in college I was introduced to XLisp and the teachers couldn't convince its application areas. I will explore this language later, if I get sufficient time on my hands. I read few articles about FP and specifically Haskel and it looks quite interesting.

Anyways, this is my To-Do list in order :
* Code all alogorithms ( Searching, Sorting ) either in C/C++
* Java
* Bash scripting
* Python
* Haskel
* Common Lisp
* Basic XSLT

---

### Post by Reiger on 2009-09-06
@Cpt Picard: You are right: one can of course go with an all-you-can-eat Lisp package. ;)

Just that it the alternative route gives you about 3 languages (Functional 1, probably Haskell; JavaScript; XSLT) you will be able to use; instead of 1. None of the 3 languages are by themselves very difficult to learn (and nor, I imagine, is Lisp) because they are all fairly "small" and "well defined" (exception being JavaScript which has some funky stuff but if you stick to a more formal approach of ending your statements and declaring your stuff properly then it shouldn't bite you). Plus at least with JavaScript & XSLT the OP can directly apply the new knowledge in other projects centering around the other languages on his CV, that is always a nice "bonus".

... Learning Haskell (or other pure functional languages) and JavaScript and XSLT doesn't exclude learning Lisp as well or vice versa, though. :P

---

### Post by CptPicard on 2009-09-06
The interesting bit in languages like Haskell and (in particular) Lisp really is the fact that the definition is small, but the ways of using them very interesting. Of course the selling point of Lisp in particular is that it really minimizes syntax to bare minimum while really allowing it to still implement pretty much anything; functional-programming concepts included.

The issue with purity is that it is a fairly rigid requirement... eventually the n00b will want to write a monad and that's pretty hard :p

---

### Post by karlmp on 2009-09-06
>>> print ('python_' * 100)
python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_
>>>:D

---

### Post by hessiess on 2009-09-06
> **karlmp said:**
> >>> print ('python_' * 100)
python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_python_
>>>:D

Python is mainly a procedural and object oriented language, which are both paradigms that the OP is lickly to have at least a working knowledge of. once you know a paradigm learning a language which uses those ideas is mearly an issue of learning the syntax, which isn't difficult. Howeaver learning a new paradigm like functional programming when you have only ever used Procedural and OO is sort of like learning to program from scratch again;)

---

### Post by slavik on 2009-09-07
> **nipunreddevil said:**
> python seems to be a good choice.Even Nasa and Google use it heavily.Google recommends C++ and Python.
they do? where is their official recomendation?

---

### Post by nvteighen on 2009-09-07
Hm... I also think the OP should go for some functional programming... but I'd rather start with Scheme rather than anything else. CptPicard already stated the advantages of Lisp over the pure-functional languages, but Scheme may be easier and smoother to start with than Common Lisp. Scheme makes it easier to stick to a functional paradigm, though at the trade-off of losing "practical power".

---

### Post by fiddler616 on 2009-09-07
> **slavik said:**
> they do? where is their official recomendation?
I'm not sure it's "official", but Google uses a lot of Python, they pay Guido to spend 50% of his time working on it, and Peter Norvig is quoted as saying, "Python has been an important part of Google since the beginning, and remains so as the system grows and evolves. Today dozens of Google engineers use Python, and we're looking for more people with skills in this language." ([http://www.python.org/about/quotes/](http://www.python.org/about/quotes/))

For more information, [let me Google that for you]("http://lmgtfy.com/?q=python+use+at+google").

Outside of sysadmin-ing, I'm not sure Perl is the best solution for much.

@OP If you know PHP, you're probably all right without Python and Ruby for now. As mentioned previously, it's just a syntax shift, not a paradigm shift.

---

### Post by slavik on 2009-09-07
so, they just use Python.

Where I work, we use lots of Perl and do not have problems with bad/unreadable code.

---

### Post by fiddler616 on 2009-09-07
> **slavik said:**
> Where I work, we use lots of Perl and do not have problems with bad/unreadable code.

In my experience, you have to really try to get nice-looking Perl, and it's almost as difficult to get ugly, obfuscated Python.

---

### Post by Mirge on 2009-09-07
> **fiddler616 said:**
> In my experience, you have to really try to get nice-looking Perl, and it's almost as difficult to get ugly, obfuscated Python.

Granted, it's been a few years since I've really dug into Perl... but I used to use it exclusively, and I seldom had problems like that... similar scenario, all code originated within the same company.

I'd say that your "you have to really try to get nice-looking Perl" statement is unfair to Perl, IMHO.

---

### Post by fiddler616 on 2009-09-07
> **Mirge said:**
> Granted, it's been a few years since I've really dug into Perl... but I used to use it exclusively, and I seldom had problems like that... similar scenario, all code originated within the same company.

I'd say that your "you have to really try to get nice-looking Perl" statement is unfair to Perl, IMHO.
I smells a flame war, so let's leave it at agreeing to disagree.

---

### Post by Mirge on 2009-09-07
> **fiddler616 said:**
> I smells a flame war, so let's leave it at agreeing to disagree.

Not real sure how I came across as starting a flame war... but ok.

---

### Post by fiddler616 on 2009-09-07
> **Mirge said:**
> Not real sure how I came across as starting a flame war... but ok.
You didn't--I'm just as guilty, if not more so.

---

### Post by j7%&lt;RmUg on 2009-09-07
I recommend bash scripting, python and ruby. All three are easy to learn but also very useful.

---

### Post by enli on 2009-09-08
I have experienced that bash scripting is extremly useful if one wants to increase the productivity, so I have added bash to my to-do list.

I am not sure about Ruby. I think instead of learning so many languages I could get good in ones I know. What do you thinl? That way I could start working on 2-3 projects I am planning on.

---

### Post by Alasdair on 2009-09-08
I'd recommend learning a functional language. Specifically Haskell. I've noticed a few others in this thread have recommended Lisp over Haskell, but I'd be inclined to disagree. Having written a small application in (Common) Lisp and then re-written it in Haskell, i'd unequivocally recommend Haskell over Lisp for the following reasons.

[LIST]
[*]More concise. Even though I made heavy (although appropriate) use of macros in my Lisp application, that same program ended up being 3x shorter in Haskell (1000loc vs 3000loc), with many more features.
[*]Faster. Part of the reason my lisp program was so much longer was that I had to optimize many parts of my code to use faster non-functional methods making extensive use of mutable state. With Haskell I was able to use all the high level functional concepts I wanted (specifically, zippers and comonads) and my Haskell program ended up being approximately 5x faster and using less memory.
[*]It's easier to write correct code. Static-typing, purity, and awesome tools like quickcheck all play a part in this.
[*]Better syntax. :P
[*][More libraries]("http://hackage.haskell.org/packages/hackage.html"). This only applies to Common Lisp. Last I checked it still had a mediocre selection of libraries. I tried Clojure and hated it (but it is built on the JVM) and I don't know anything about scheme beyond using it to script the gimp.
[*][Batteries Included.]("http://hackage.haskell.org/platform/") Self explanatory really, although I don't think the Haskell platform has been packaged for Ubuntu yet.
[*][It's not dead]("http://hackage.haskell.org/trac/haskell-prime/") unlike say, Common Lisp.
[*]Oh, and you can use [mutable state]("http://www.haskell.org/ghc/docs/latest/html/libraries/mtl/Control-Monad-State-Lazy.html") in a controlled fashion.
[*]Macros are neat, but Haskell has a lot of features Lisp lacks. Swings and roundabouts really.
[*]Haskell will force you to program in a functional manner, which is good for learning.
[/LIST]

Of course these are all my subjective opinions and experiences, so take from them what you will. Learning a functional language will broaden your mind no matter which one you choose, I just happen to like Haskell (a lot).

Some good learning resources:
[http://learnyouahaskell.com/](http://learnyouahaskell.com/)
[http://book.realworldhaskell.org/](http://book.realworldhaskell.org/)

---

### Post by Reiger on 2009-09-08
> **Alasdair said:**
> 
Some good learning resources:
[http://learnyouahaskell.com/](http://learnyouahaskell.com/)
[http://book.realworldhaskell.org/](http://book.realworldhaskell.org/)

In that vein Hal Daumé, Yet Another Haskell Tutorial: [http://www.google.com/search?client=opera&rls=en&q=daume+yet+another+haskell+tutorial&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=daume+yet+another+haskell+tutorial&sourceid=opera&ie=utf-8&oe=utf-8)

It's in PDF format (the link is a google search; for me it was the first hit) which makes it easy to print: handy if you, like me, prefer to read from paper rather than screen.

In particular he has a good introduction to Monads and tackles I/O early on. (Chapter 5, I think.)

---

### Post by hessiess on 2009-09-08
> 
More libraries. This only applies to Common Lisp. Last I checked it still had a mediocre selection of libraries. I tried Clojure and hated it (but it is built on the JVM) and I don't know anything about scheme beyond using it to script the gimp.


I agree with you theare, I like Common Lisp, but havent bean able to do anything with it thanks largly to the absance of good libuerys, and also the lack of standards between implementations.

---

### Post by CptPicard on 2009-09-08
Disclaimer -- I am not dissing Haskell, I like FP despite being more of a Lisper by spirit. :)

One has to of course remember that Lisp really is a multi-paradigm language, with (basic) functional-programming tools included. This is why I have a feeling that someone who is learning something might get a softer start to FP ideas in Lisp, which is in addition a language that allows for other kinds of interesting things as well (it really allows for "any" ideas...). The more Lisp I write, the more I actually rid myself from the idea of Lisp as "FP" (although functions as first-class objects with closures are a key feature). The syntax is what it is because it enables the data-is-code-is-data-macro system, which in itself is a very deep idea. What I'm trying to get at is that Lisp is a kind of crystallization of a minimum core with maximum of flexibility... learning to write things on it in various ways teaches you "everything you need to know", and FP ideas in the process.

But, of course, Haskell will do for the FP-learning purposes just great. I'd just want to avoid too great a wtf-experience with all the forcing of functional-programming due to purity. Hey, *I* don't know what the heck a comonad is, and sure couldn't use one to produce the miraculous shortening of source code. ;)

---

### Post by Alasdair on 2009-09-08
> This is why I have a feeling that someone who is learning something might get a softer start to FP ideas in Lisp.
Agreed, It would defiantly be a softer start. However I don't think learning Haskell is as hard as some people make it out to be. I was able to teach myself Haskell during the first year of my computer science course, as a final year student enli should have no problems. If I can learn it, anyone can. :)

To be fair to CL, most of my miraculous code-shortening was due to having some useful libraries available. The zipper example I gave was about how being able to reason about problems at a very abstract level while still being efficient is a big bonus. For the example I gave, with lisp I was mucking around with filestreams, while in Haskell I used a Zipper containing Lazy ByteStrings. That's a big leap in abstraction.

---

