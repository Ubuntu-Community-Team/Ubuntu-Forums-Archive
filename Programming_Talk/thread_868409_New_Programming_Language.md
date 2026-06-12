---
title: "New Programming Language"
date: 2008-07-23
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-07-23
I am not a guru of programming but i know how and what to do. I am very interested in Artificial Intelligence, not the theory but the practice. I commonly use it in every program i make (even if very little) and i would like to get better at it.

I also like making data structures and object oriented programming. I also enjoy forming algorithms to solve common tasks.

So ...

What would be another good language to learn, i was thinking LISP but i found it hard to get going, i didn't understand the concept of the language and documentation was sparse.

Also i have heard people say that i should become very good at one or two languages and not decent at multiple. But i feel that one can only get so good at a language but if i learn many then i will get concepts from all of them and reapply them else where.

i currently know
Java C++ Python C and BASH

---

### Post by tiachopvutru on 2008-07-23
It's only from word of mouth, but I hear that [Prolog]("http://en.wikipedia.org/wiki/Prolog") is useful for creating AI.

---

### Post by clash on 2008-07-23
So what exactly are you interested in ? 

If you want to do anything with AI then you need to learn a language like prolog. 

[http://en.wikipedia.org/wiki/Prolog](http://en.wikipedia.org/wiki/Prolog)

Be prepared for a total mind **** unless your a logic genius. :)

Heres a good tutorial to start off. 

[http://kti.ms.mff.cuni.cz/~bartak/prolog/contents.html](http://kti.ms.mff.cuni.cz/~bartak/prolog/contents.html)

---

### Post by Mr.Macdonald on 2008-07-23
Um I don't want to brag but logic is kind of my strong side. But other that logic, math (logic with numbers) and science (logic with stuff), i am completely stupid.

and at first glance i like the Prolog

thanks

---

### Post by Mr.Macdonald on 2008-07-23
I ran into a problem, i installed the swi-prolog package,

the prolog guide [here]("http://kti.ms.mff.cuni.cz/~bartak/prolog/genealogy.html") told me to type in "man(adam)." which i did and i got "ERROR: Undefined procedure: man/1"

???

---

### Post by clash on 2008-07-24
> **Mr.Macdonald said:**
> Um I don't want to brag but logic is kind of my strong side. But other that logic, math (logic with numbers) and science (logic with stuff), i am completely stupid.

.... eh ok. 

> I ran into a problem, i installed the swi-prolog package,

the prolog guide here told me to type in "man(adam)." which i did and i got "ERROR: Undefined procedure: man/1"

I don't think you read the guide properly. Please go back and spend some time with it.

Your not in the correct "mode" to enter facts/rules. Your in the mode for making requests/questions.

On the page. These;

    man(adam). 
    man(peter). 
    man(paul). 
      
    woman(marry). 
    woman(eve). 

are simple facts. adam, peter and paul are man(s). marry (I assume thats a typo) and eve are woman(s). 

The next part;

    parent(adam,peter). % means adam is parent of peter 
    parent(eve,peter). 
    parent(adam,paul). 
    parent(marry,paul). 

Is pretty self explanitory. i.e > see the comment.

These are rules.

    father(F,C):-man(F),parent(F,C). 
    mother(M,C):-woman(M),parent(M,C). 

So F is the father of C if F is a man and if F is a parent of C. 
So M is the mother of C if M is a woman and if M is a parent of C. 

Honestly, before you go diving into prolog what is your programming experience ? Because prolog is absolutely nothing like C/C++ etc. Its a completely different way of thinking. 

The biggest mistake I made when learning prolog was trying to think in terms of C.

---

### Post by Chickencha on 2008-07-24
You mentioned it, but I still say take a look at Common Lisp. I've been doing some things with it lately after programming in C++ for years and find it very interesting.

I think one of the things that throws so many people off balance about it is the fact that it's such a simple language. (Note, however, that "simple" and "easy" are not synonyms.) The syntax is very different from any other language I've seen, but it's incredibly consistent. It takes time for your brain to learn to parse it.

I don't know where you've looked for CL stuff, but there are some good resources available online.

The first two chapters of Paul Graham's _ANSI Common Lisp_ are available online. Just those two chapters contain a lot of good information: [http://paulgraham.com/acl.html](http://paulgraham.com/acl.html)

This is also a pretty good (complete) online book: [http://gigamonkeys.com/book/](http://gigamonkeys.com/book/)

---

### Post by era86 on 2008-07-24
Lisp would be a good language to learn.  I did some string manipulation in Lisp and it is much easier than some of the more popular languages out there.

Don't give up on it because you hit a roadblock!  Here is a book on some of the concepts of languages and their uses (Lisp is discussed as well):

[http://books.google.com/books?hl=en&id=CuNruImLiCcC&dq=concepts+of+programming+languages&printsec=frontcover&source=web&ots=JuGF9pLD-2&sig=Qk-wv-iKAqsMz9mOX318jypHVIw&sa=X&oi=book_result&resnum=1&ct=result](http://books.google.com/books?hl=en&id=CuNruImLiCcC&dq=concepts+of+programming+languages&printsec=frontcover&source=web&ots=JuGF9pLD-2&sig=Qk-wv-iKAqsMz9mOX318jypHVIw&sa=X&oi=book_result&resnum=1&ct=result)

---

### Post by Kadrus on 2008-07-24
I suggest learning an ML type of language,Standard ML,ML,Objective Caml,or another functional programming language like Haskell,Erlang,Scala,Mathematica.
MLs languages are very good for AI and implementation.
As to Lisp:
I think that it has failure in standardizing tail recursion,tt has basic suport for functional programming and it provides inadequate static checking.
I find Lisp to be good only in web dev nowadays because static checking is unimportant as web dev is done through dynamic interfaces.

---

### Post by SNYP40A1 on 2008-07-24
I think you should start with the theory or learn more about the theory.  The language is just an implementation of some theory...programming languages are themselves based on theories of computing.  Start with the theory and go from there.  I agree that it is better to master a few languages rather than try to be ok at all -- don't be a jack of all trades and master of none.

---

### Post by Mr.Macdonald on 2008-07-25
I Really like prolog, Its syntax and ideology is very different. I think i will try LISP for those reasons.

The problem with sticking to one language is that it can get very boring. I did Java for a long time and i just plain got sick of it. I bounce between languages as to relieve boredom while trying to master programing.
> don't be a jack of all trades and master of none. 
I feel that programming is a trade, and languages are just tools. No tool is perfect for everything and to master the trade you must be a master of all the tools.

Also how would one judge what a master of the language is?
And how do you judge a master programmer?

I don't think that knowledge of every package and library make one a master, because that would make the internet a master. But its far easier to judge a master programmer, one that could take any complex problem and make it simple for a user by using logic and efficient practices.

Btw I don't consider myself a master programmer, i am just saying what i believe (and it could very well be wrong, as any opinion).

---

