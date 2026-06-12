---
title: "Want to learn functional programming - ML, Lisp, Scheme?"
date: 2009-01-22
forum: Programming Talk
---

### Post by Zorgoth on 2009-01-22
Hi, I'm a math major (topology/analysis right now) and I'm wondering what a good functional programming language would be and how I could learn it.  I'm pretty familiar with C++ and for most purposes it works quite well.  I wouldn't even want to learn a new language if it had a nice easy built-in way to create functions at run-time, but it doesn't, although function pointers are nice things.  I do use programming in mathematics, but I'm also a bit of a hobbyist so I want something that can handle other things decently as well, including possibly graphics.

I know the computer science department and a lot of mathematicians use ML, and I've heard of Lisp and Scheme, and have some vague idea about lambda calculus and suchlike things.  I would like a good functional (preferably a little multi-paradigm) language that's easy for a math person/an object-oriented programmer to learn.

So to make a very long story short, I would like recommendations of good functional languages/implementations and particularly *any good complete online tutorials* that you know of.

---

### Post by Reiger on 2009-01-22
Haskell would be a good choice. It is designed to be very close to 'the real Math'. For a good tutorial try fiddling with Helium (an interpreter designed for teaching a special dialect (subset mostly) of Haskell)...

[http://www.cs.uu.nl/wiki/bin/view/FP/](http://www.cs.uu.nl/wiki/bin/view/FP/) (check the left sidebar)

---

### Post by Cracauer on 2009-01-22
Lisp, at least Common Lisp, is really a multi-paradigm programming language. 

People like me don't do any of the "real" functional programming in Common Lisp (other than what you naturally do for const-ness and thread-safety, which addresses the "don't stir up state if you don't have to", but which works in C++ the same way).

If you do this to have a practical thing for the future, I'd say Common Lisp. If you do it to stretch you programming mind and learn new concepts, I'd say you a language with extensive type system such as ML.

---

### Post by nvteighen on 2009-01-22
Scheme is a Lisp dialect, so... :p And it isn't pure-functional either.

But anyway, take also a look into Scheme... it's a great sandbox to explore stuff. Not very practical, but really enjoyable. And it makes you step into the Lisp world if needed.

If you look for a pure-functional Lisp, take a look at Clojure. It's a Lisp on top of the Java Virtual Machine, so you can interface with it and Java libraries and do some cool stuff: [http://www.clojure.org](http://www.clojure.org)

---

### Post by CptPicard on 2009-01-22
Well, I would say it's between some lisp and Haskell. It would be Haskell hands down if you didn't want to be a little bit multi-paradigm -- I must admit that although I very much enjoy functional programming (and yes, the ability to create functions at runtime is *the* only feature you actually ever need as per lambda calculus), Haskell is a bit too pure... you do need state every now and then, and having to do something like monads to get it is a bit over my head. As a mathematician YMMV.

---

### Post by jimi_hendrix on 2009-01-22
> **nvteighen said:**
> But anyway, take also a look into Scheme... it's a great sandbox to explore stuff. Not very practical, but really enjoyable. And it makes you step into the Lisp world if needed.


+1...i like scheme because its minimalistic and stretches your brain a little

---

### Post by mulletboyjay on 2009-01-22
I am also a Maths student, and after having learnt Java last year and liking it a lot, I took one of the CompSci options this year

We were told (and had to teach ourselves) about C (ansi C that is) and then we were given a piece of coursework we had to program in Lisp and pick a particular version (of lisp or scheme).

I chose Common Lisp (CLisp) and absolutely love it. It took me a couple of weeks to finally understand everything but now I think it works great.

I also know we will start using Haskell next year for it's mathematical purposes so I would suggest looking at both CLisp and Haskell like a few other people have suggested.

Hope this helps

---

### Post by CptPicard on 2009-01-22
I am really glad to hear that at least mathematicians understand the benefits of higher-level languages... ;)

Btw, as far as CL implementations go, SBCL is according to my understanding the strongest contender nowadays...

---

### Post by monkeyking on 2009-01-22
If you are a math major,
I would highly recommend the programming language R.
[http://www.r-project.org/](http://www.r-project.org/)

In the past it has been mostly used by statisticians,
but it has grown quite a lot in the last years
[http://www.nytimes.com/2009/01/07/technology/business-computing/07program.html](http://www.nytimes.com/2009/01/07/technology/business-computing/07program.html)

It stands on the shoulders on S/S-plus and scheme, has an interactive mode. And has a well defined foreign language interface.

---

### Post by Zorgoth on 2009-01-22
Thanks for all your replies!  I'll probably try out CLisp first I think; it sounds closest to what I'm looking for right now.  But with all these fun-sounding languages out there it's hard to decide which one... I might just learn all of them.

---

### Post by jimi_hendrix on 2009-01-22
check out Octave too...not exactly functional but built for math...

---

### Post by Cracauer on 2009-01-22
> **mulletboyjay said:**
> I chose Common Lisp (CLisp) and absolutely love it. It took me a couple of weeks to finally understand everything but now I think it works great.


Everything? Wow :)

Just kidding.

BTW, please don't use the term "Clisp" as an abbreviation of "Common Lisp". Clisp is a particular implementation of Common Lisp.

---

### Post by nvteighen on 2009-01-23
> **CptPicard said:**
> I am really glad to hear that at least mathematicians understand the benefits of higher-level languages... ;)


Not like one friend of us, right? ;)

---

### Post by Kilon on 2009-01-23
> **nvteighen said:**
> Not like one friend of us, right? ;)

Shhhhh.... you are going to wake him up!!!!

---

### Post by nvteighen on 2009-01-23
> **Kilon said:**
> Shhhhh.... you are going to wake him up!!!!
You don't know him. It was a guy called Lster who claimed to be a math guru and proposed that low level languages were the only thing worthful in programming.

---

### Post by Kilon on 2009-01-23
> **nvteighen said:**
> You don't know him. It was a guy called Lster who claimed to be a math guru and proposed that low level languages were the only thing worthful in programming.

so there are more than one. OMG!!! they are like gremlins, multiple with water!!!

---

### Post by CptPicard on 2009-01-23
> **Kilon said:**
> so there are more than one. OMG!!! they are like gremlins, multiple with water!!!

Yes, they pop up every now and then. You were not around to see the really important Language Wars -- I will have to dig up some threads for you to read. There was also a guy called Shining Arcanine who was also hell bent on demanding proof that high-level languages have interesting features that contribute to fruitful, insightful description of problem domains and problem solutions.

The funny thing is that their argument is almost always identical, and it is also obvious that a) they don't use high level languages b) the only languages they do use are C or C++, c) they are somewhat offended by the idea that some people see something worthy in things that are outside of their own scope and finally d) therefore, without even knowing whom they are talking about/to, they slap those other guys around for just simply being either lazy or incompetent, and that this is why they just resort to HLLs...

Then there was "billijoe" who suggested that my position comes from being *afraid of C*... ;)

---

