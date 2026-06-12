---
title: "Where too start...?"
date: 2009-11-15
forum: Programming Talk
---

### Post by Red Rule on 2009-11-15
First of; yes I read the sticky. ;)

But I still can't decide " what language is bets for me?"
Perhaps because I over think it too much, perhaps not.
I'm a hobbyist programmer, and I'm considering studying computer science.
(2 more years of high school before I'm off to the university.)
If I am going to make my living coding, I'd like to go in the more scientific direction.
(make a change and all that). Now most of my coding experience has been in C++, C# and a little bit of Java, (and WoW AddOns) all under windows. 
(although it doesn't really matter for Java or WoW does it?)

Now my personal preference based on that would be c++, it comes most " natural" to me.
And I know it's useful for little/semi-large projects, but what about the true scientific research (genome studies, NASA etc) is is useful in those areas?
Good OpenGL support would be nice too, I do like the " occasional"  game or two and it would be fun to make one. 

And apart from what language I'll pick: how does one go about making GUI programs under Linux? Do you call a specific program/lib per OS (i.e. Redhat/Ubuntu differ from one another) Do you call Gnome or KDE, you call something else, or you just use the Linux/GNU core?

Sorry for the wall of text, here's some popcorn for reading all of it:popcorn:

---

### Post by CptPicard on 2009-11-15
> **Red Rule said:**
> 
I'm a hobbyist programmer, and I'm considering studying computer science.
(2 more years of high school before I'm off to the university.)
If I am going to make my living coding, I'd like to go in the more scientific direction.

Considering that you already have exposure to "C-derivatives" and taking that part of your post into account, I would suggest you look into some rather different languages at this point...

Namely, for the "scientific computation" part, Haskell, which will teach you pure-functional programming and tools which will come in handy solving data-parallelizable mathematical problems in particular, and for a language that will give you more insight into programming languages' design elements in general, Lisp.

> 
Now my personal preference based on that would be c++, it comes most " natural" to me.

Trying out something that feels "unnatural" usually tends to broaden your perspective, then. :)

> 
And I know it's useful for little/semi-large projects, but what about the true scientific research (genome studies, NASA etc) is is useful in those areas?

Well, why not, but in those fields you'll be more interested in the algorithmics involved, not the language which you implement in. And in that case, a higher-level language, as long as it is performant enough, is likely preferable.

>  Do you call Gnome or KDE, you call something else, or you just use the Linux/GNU core?

It's the GUI toolkit you need to use. For KDE, Qt (and KDE libs)... for Gnome, GTK.

---

### Post by Red Rule on 2009-11-15
> **CptPicard said:**
> Considering that you already have exposure to "C-derivatives" and taking that part of your post into account, I would suggest you look into some rather different languages at this point...

Namely, for the "scientific computation" part, Haskell, which will teach you pure-functional programming and tools which will come in handy solving data-parallelizable mathematical problems in particular, and for a language that will give you more insight into programming languages' design elements in general, Lisp.

Trying out something that feels "unnatural" usually tends to broaden your perspective, then. :)

  Hmm you make a good point, and studying these might help me choose where/what too study, but on the other had, the whole system seems based upon scientific I/O, simplistic data reading and output, useful to learn, but I'm not sure about what " solo-projects" I could apply it too, can this be used to create " full programs"  (i.e. with a gui), or do you have to combine it with other languages(and then feed the data trough?).
After A quick browse of both sites, only GTK seems to support Haskell.

---

### Post by Can+~ on 2009-11-15
You should forget entirely about interfaces at first and just work out in the shell. Getting the syntax right is more important than getting a pretty interface.

And I also agree with CptPicard on having a run with functional languages, it's such a paradigm shift.

---

### Post by CptPicard on 2009-11-15
[http://en.wikipedia.org/wiki/Lambda_calculus](http://en.wikipedia.org/wiki/Lambda_calculus)

In particular in the case of Lisp, LC is a form of formal logic that is essentially a fundamental formal description of computable functions. It is mathematics, not another kind mathematics.

Complaints about notation (syntax) really are very superficial... but if you feel like the S-expression syntax of Lisp bothers you, Haskell is more normal math-looking, and actually behaves mathematically in the "pure-functionality" sense...

---

### Post by grayrainbow on 2009-11-15
Considering that you'll going to study CS, find out what language will be use in the university and go with exactly the what differ most(no need to repeat something twice if you get it first time :) ). First year usually is Scheme for many US universities(but as I know from some time MIT use python), and C for other parts of the world. Eventually you wont get without C and some form of assembly when you study low level stuff (it's really stupid to try learning what hardware give to programmer in something "higher" level then C). 

C++ is not for "semi large" projects, it's for really huge and/or time critical projects, that's why you got notion of private code in classes and namespaces.

GUI programming - a lot of library usage. Qt and GTK are for making windows and related stuff, for me Qt got better tools, and thats what only matter when you do standard GUI. For simulations - OpenGL, it's a "standard" and got variations in lot architectures.

About "true scientific" research... [https://www.llnl.gov/llnl/research/](https://www.llnl.gov/llnl/research/) , btw most of machines in that lab run flavor of Linux, and C compilers(some may have and Fortran). European Space Agency is known to use Ada for some of its projects.

P.S. And most of all - Learn from Unix: learn only one thing at first, and learn it well!
Good Luck! And have fun :)

---

