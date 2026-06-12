---
title: "About Lisp"
date: 2010-06-04
forum: Programming Talk
---

### Post by medic2000 on 2010-06-04
I am learning programming for 2 months. Currently i am working with python. I am trying to do the Programming Challenges in this forums and its very enjoyable for me. 

Yesterday i have learned that there is an old language called Lisp. Some say it is the most powerful language. Is it true? I searched and saw even there is not so much IDE for Lisp. There is an Emacs one but i use Vim. And for outer libraries how is the support? Is it poor? 

How would be like to learn the Lisp? Is it a wise move?

---

### Post by badperson on 2010-06-04
I don't know that a lot of current systems are written in lisp, but some are for sure. 

You should definitely checkout The [Structure and Interpretation of Computer Programs]("http://mitpress.mit.edu/sicp/full-text/book/book.html"), which is in pretty much everyone's top three computer science books of all time. 

There are some lectures online, and I think Berkeley has some of their CS lectures on youtube that go through Scheme (a dialect of LISP). 

Also, Common Lisp has a lot of libraries available. 
bp

---

### Post by rrashkin on 2010-06-04
LISP, like so many things, seemed like a good idea at the time.  Like Esperanto, it never really got the legs it may have (hypothetically) deserved.

---

### Post by nvteighen on 2010-06-04
Lisp it's more than language... it's rather a language family whose two major dialects are Common Lisp and Scheme. The funny part is that it wasn't created as a computer programming language, but as an algorithmic notation... but a "rebel" student of its creator implemented it on a computer and well... there it started.

Lisp's strongest feature is that Lisp code is also Lisp data and viceversa. What this means is that you get a metacircular/metalingual language that's able to modify itself as you like, either at compile-time or at runtime.

Initially, it was born to be pure-functional (because it was meant to be a mathematical notation), but it quickly adopted multiparadigm features... Usually, Lisp programs are functional (stateless) in their majority and imperative (state-driven) in parts.

Now, of Scheme and Common Lisp, the former is the older (1972). Scheme is a very simple language, its standard is terribly minimalist and that brings out a lot of problems... for instance, it makes Scheme a terrible language for production, as all implementations conform just to a small set of common features and then give you a lot of non-standard extensions you can't live without. But, Scheme is definitely much better than Common Lisp for learning Lisp and functional programming, because it's much easier and simpler.

Scheme interactive implementations available: MIT/GNU Scheme (R5RS and R4RS + extensions), PLT Scheme (R6RS, backwards compatible with R5RS and R4RS, + extensions), Ypsilon (a pure R6RS... no extensions), MIT Scheme48 (not sure what standard it follows). There are other implementations that are meant for designing embedded scripting devices, like GNU Guile (which is used in GIMP, for example).

Common Lisp was born in the early 80s, mainly by the same people that designed Scheme plus some other well-known guys like Richard M. Stallman :) Its standard is much more complete and production-oriented. Common Lisp, for examples, includes a standard OOP system (more powerful than usual OOP systems; Smalltalk copied it and Objective-C has something similar), etc. Of course, it has much more stuff to learn and also, it has some complexities that can overwhelm someone without Lisp training. The other great advantage is that implementations don't differ that much... just that SBCL is almost unbeatable.

Hope to have helped. If you'd like to see how (Common) Lisp looks like, look at my sig, at the Common Chess project... :p

---

### Post by tbastian on 2010-06-04
> **medic2000 said:**
> 
Yesterday i have learned that there is an old language called Lisp. Some say it is the most powerful language. Is it true?

How would be like to learn the Lisp? Is it a wise move?

In my experience there is no one language that can be described as 'the most powerful language'. Every language has its pros and cons. LISP is great for AI related programming, but I wouldn't write a (for example) word processor in LISP.

I did a bit of Scheme a while back, and it is WEIRD if you're used to procedural programming, but (my professor says) it makes you a better programmer if you learn it.

To summarize: don't learn it if you're only interested in learning a single language that will be good for everything. Learn it if you need to do AI, or want to mess with your mind a little.

---

### Post by medic2000 on 2010-06-04
Thank you all and special thanks to nvteighen for long description. Last night i had already looked the history and family of Lisp. I really want to know about this:
Have you ever experienced the power of Lisp(Common Lisp)? I am planning to make websites and website based applications, could Lisp take me a step forward than others?
Is it good than Python, Perl and Ruby?
And most important thing is i dont care it is "weird". If it is the most powerful no problem. Read the article if you haven't done before. It is about Lisp and its powers.
[http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)

Note after the edit: nvteighen your code of CommonChess seems very clear and short which is a good thing. I think i will learn Common Lisp :)

---

### Post by soltanis on 2010-06-04
> **medic2000 said:**
> 
Yesterday i have learned that there is an old language called Lisp. Some say it is the most powerful language.

Dude, you make it sound like it's a legend. You speak about it with such awe.

Lisp is powerful indeed. "Most powerful" doesn't really exist; programming paradigms can be so different that comparing them is really useless. Lisp, or I should say, Common Lisp, which is the one you should be using if you want to get anything done (Scheme is mostly an annoying academic toy), is a functional programming language. That being said, it does have object oriented bindings, but they're not the same kinds of objects that you see in other languages.

More than any other language, Lisp I've found requires you to think, and usually it makes you think of a great solution to a problem you only thought was difficult because you made it difficult. Also, like Python, every Lisp has an interactive interpreter (called the Read-Eval-Print Loop, REPL, which Python borrowed from Lisp, really), which makes getting set up and running tests a snap.

Will it catapult you ahead of everyone else? Lisp is great, but it's a little weak when it comes to parsing typical data (strings) compared to other languages. It's *awesome* when it comes to parsing itself, but most people view it as not really a language worth using, so it is lacking in some of the support it deserves.

My recommendation is learn it, take its lessons to heart, then use what you learned from it in languages such as Python (which has many features it borrowed from Lisp on its functional side). You will become a true master of the Programming Force if you do so.

---

### Post by tbastian on 2010-06-04
> **soltanis said:**
> Dude, you make it sound like it's a legend. You speak about it with such awe.

Lisp is powerful indeed. "Most powerful" doesn't really exist; programming paradigms can be so different that comparing them is really useless. Lisp, or I should say, Common Lisp, which is the one you should be using if you want to get anything done (Scheme is mostly an annoying academic toy), is a functional programming language. That being said, it does have object oriented bindings, but they're not the same kinds of objects that you see in other languages.

More than any other language, Lisp I've found requires you to think, and usually it makes you think of a great solution to a problem you only thought was difficult because you made it difficult. Also, like Python, every Lisp has an interactive interpreter (called the Read-Eval-Print Loop, REPL, which Python borrowed from Lisp, really), which makes getting set up and running tests a snap.

Will it catapult you ahead of everyone else? Lisp is great, but it's a little weak when it comes to parsing typical data (strings) compared to other languages. It's *awesome* when it comes to parsing itself, but most people view it as not really a language worth using, so it is lacking in some of the support it deserves.

My recommendation is learn it, take its lessons to heart, then use what you learned from it in languages such as Python (which has many features it borrowed from Lisp on its functional side). You will become a true master of the Programming Force if you do so.

Well said!

---

### Post by eeperson on 2010-06-04
> **medic2000 said:**
> I am planning to make websites and website based applications, could Lisp take me a step forward than others?
Is it good than Python, Perl and Ruby?


If your interested in web development you may also want to take a look at Clojure which is a newer Lisp dialect.  It has a pretty nice web framework called Compojure.  It also has the potential advantage that it can interoperate with Java libraries.

---

