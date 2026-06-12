---
title: "SBCL: _The_ Common Lisp implementation has just turned 1.0!"
date: 2006-11-29
forum: Programming Talk
---

### Post by lnostdal on 2006-11-29
SBCL compiles the most insanely flexible and programmable programming language known to man (or at least me) to native machine code with performance matching and sometimes exceeding C. It has just been tagged 1.0 in CVS and a release is just moments away. Do check this thing out; it is both mind-expanding and a great environment for production-work!

[http://digg.com/programming/SBCL_The_Common_Lisp_implementation_has_just_turned_1_0/](http://digg.com/programming/SBCL_The_Common_Lisp_implementation_has_just_turned_1_0/)

edit:
..btw.. here are some links to Common Lisp resources and other stuff:
[http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/)
[http://www.cl-user.net/](http://www.cl-user.net/)
[http://common-lisp.net/](http://common-lisp.net/)
[http://wiki.alu.org/The_Road_to_Lisp_Survey](http://wiki.alu.org/The_Road_to_Lisp_Survey)
[http://en.wikipedia.org/wiki/Common_Lisp](http://en.wikipedia.org/wiki/Common_Lisp)

..there are tons of resources out there!

---

### Post by po0f on 2006-11-30
lnostdal,

I would probably be more interested if I knew which *dialect* of Lisp was the most supported/popular/cross-platform/etc.  There's Lisp, which is supposedly the "father" of all the different dialects.  So, is Lisp itself a language?  Or just more of a specification?  (I've heard tell of Lisp being linked with emacs, which is eww.  :))

Then there's Common Lisp.  With a name like that, hopefully it'd be the most widespread, but I hear more about Scheme than Common Lisp.

If you would, describe a little bit about each (Lisp/CL/Scheme, and their relationship) please.  I would actually like to try at least one of these out, and I'm sure you'd like another convert.  :)

---

### Post by lnostdal on 2006-11-30
> **po0f said:**
> lnostdal,

I would probably be more interested if I knew which *dialect* of Lisp was the most supported/popular/cross-platform/etc.


Hi there :)

Sticking to Common Lisp; if I where to estimate based on what I've seen recent years while hanging on #lisp (at freenode) and comp.lang.lisp I'd say SBCL is the most widely used, supported and popular Common Lisp implementation on Linux. FreeBSD is also supported, while Win32-support is currently beta'ish but improving fast. (by the time my "Killer App" is ready it will run on Win32 also :))

..for Scheme I do not know. I haven't really used Scheme enough to say much here.


> **po0f said:**
> 
There's Lisp, which is supposedly the "father" of all the different dialects.  So, is Lisp itself a language?


When people say "Lisp" they can mean several things depending on context:

* Common Lisp
* Scheme
* ..other lisps..
* ..or "The whole Lisp family of languages" - including Scheme, Common Lisp and the others


They might also be talking about the very first original LISP-dialect and implementation (note uppercase) from 1958: [http://en.wikipedia.org/wiki/Lisp_%28programming_language%29](http://en.wikipedia.org/wiki/Lisp_%28programming_language%29)

When Common Lispers are being "lazy" they say "Lisp". When Schemers are being "lazy" they say "Scheme" - but some Schemers might say "Lisp" and actually mean Scheme. This depends on context and is usually not a problem when communicating with others.

Note that on USENET:

* comp.lang.lisp is for Common Lisp
* comp.lang.scheme is for Scheme


I believe that when people say "Lisp" without a context it is reasonable to assume they mean Common Lisp.


> **po0f said:**
> 
 (I've heard tell of Lisp being linked with emacs, which is eww.  :))


Yes, Emacs has a Lisp of itself called Elisp - and it is also very often used for editing/interacting with other Lisps outside Emacs; for example Common Lisp.

One use a "plugin" for Emacs called Slime when editing/interacting with a Common Lisp-implementation like SBCL:
  [http://common-lisp.net/project/slime/](http://common-lisp.net/project/slime/)

Emacs might have a large threshold when it comes to learning it. I am a former hardcore VIMer but did convert to Emacs+Slime for all my Common Lisp hacking and later also C/C++-hacking and this investment is something I do not regret whatsoever.

I'd definitively say an interactive environment _like_ Emacs+Slime is absolutely needed for Common Lisp/SBCL. I have yet to see or hear of anything similarly suitable for/in VIM. I'd also say Emacs+Slime is part of the change required in mindset for understanding or at least using Lisp effectively; it's worth the investment. :)


> **po0f said:**
> 
Then there's Common Lisp.  With a name like that, hopefully it'd be the most widespread, but I hear more about Scheme than Common Lisp.

If you would, describe a little bit about each (Lisp/CL/Scheme, and their relationship) please.  I would actually like to try at least one of these out, and I'm sure you'd like another convert.  :)

I'd say go for Common Lisp now. Some might argue that Common Lisp is big, cludgy and thus not suitable for beginners; but I say it has mostly the same features as Scheme and you do not need to learn all the features of Common Lisp to use its "Schemish" subset! This subset is similar enough for one to follow a "Scheme-book" like SICP while actually trying out the examples/exercises in a Common Lisp environment without much hassle:
  [http://mitpress.mit.edu/sicp/full-text/book/book.html](http://mitpress.mit.edu/sicp/full-text/book/book.html)

Common Lisp is multiparadigm and does not force a (more) exclusively functional style on you like Scheme does; this suits the "real world" better because sometimes you want to do Object Oriented programming (which Common Lisp has very good support for btw.), sometimes functional and sometimes something entirely different.Also see: [http://www.gigamonkeys.com/book/introduction-why-lisp.html](http://www.gigamonkeys.com/book/introduction-why-lisp.html); he talks a bit about this.

*Common Lisp is The Programmable Programming Language*: they wanted OOP? -- They implemented it without making changes to the compiler. They wanted aspect oriented programming? They implemented it without making changes to the compiler. Similar things and examples are common practice and everydayish in Lisp ... because it is The Programmable Programming Language. :-D 

Ubuntu is a great environment and active Lisp-implementations like SBCL makes it a lot greater. :)

---

### Post by Ubuntist on 2006-11-30
I'd like to be talked into using Lisp.  I've just been getting back to doing a bit of programming after years away from it, and I'm trying to decide in which language I can best express myself.  I've looked at Python, Ruby, Common Lisp and Scheme and find them all big improvements on what programming used to be.

The reason I'd like to be talked into using Lisp is that I have the sense that it offers passage to another world, if that's not too metaphysical.  All of the incredibly nifty AI kinds of programs written in Lisp have left an impression on me.

What's stopping me from adopting Lisp wholeheartedly is the nagging suspicion that, say, Ruby may be just as powerful and might in some ways be more modern.  This suspicion comes from looking, for example, at the benchmarks in the *Great Computer Language Shootout*.  The Ruby and Python codes in the *Shootout *are often at least as compact and succinct as the Lisp codes.  Compare, for example, the implementations of the nbody benchmark in the various languages.

This nagging suspicion is also reinforced by *Practical Common Lisp,* which, like many introductory texts these days, uses the construction of a music database as an example.  Again, the Lisp version of the database really does not seem so very different from the versions found in various introductions to Ruby and Python.

I *can* appreciate that Common Lisp's macros are from a higher plane and appear to have no equivalents in Ruby or Python.  But, not being terribly fluent with them, I wonder how much I would use them in practice.  My programming, by the way, tends to be pretty heavily numerical.  Astrophysics, finance and things like that.

My doubts about Lisp boil down to the suspicion that Lisp's aura was made in the 90s and before, when it truly was light years ahead of other languages.  But, in the 21st century, does it really stand head and shoulders above Ruby, for example?  Could it be that many of those really cool AI programs that impressed me so much in the past could be done just as well in Ruby?  Is there a systematic comparison out there somewhere between Lisp and Ruby?

---

### Post by lnostdal on 2006-12-01
> **Ubuntist said:**
> 
What's stopping me from adopting Lisp wholeheartedly is the nagging suspicion that, say, Ruby may be just as powerful


..it isn't.. ;) ..it lacks macros among other things .. and it lacks a native optimizing compiler..


> 
and might in some ways be more modern.  This suspicion comes from looking, for example, at the benchmarks in the *Great Computer Language Shootout*.  The Ruby and Python codes in the *Shootout *are often at least as compact and succinct as the Lisp codes.  Compare, for example, the implementations of the nbody benchmark in the various languages.


It is not always the compactness that makes Lisp (or any language!) great - it's "that something else". I'd say it is very seldom the _initial_ compactness that makes a language great. :)

Remember that `n-body' is representing a very simple task when you look at the design of its software-parts. It's basically a performance-benchmark and does not show how Lisp can be used to elegantly solve complex software design-problems.


> **Ubuntist said:**
> 
This nagging suspicion is also reinforced by *Practical Common Lisp,* which, like many introductory texts these days, uses the construction of a music database as an example.  Again, the Lisp version of the database really does not seem so very different from the versions found in various introductions to Ruby and Python.


You should take a look at the later chapters:
  [http://www.gigamonkeys.com/book/practical-an-id3-parser.html](http://www.gigamonkeys.com/book/practical-an-id3-parser.html)

I bet stuff like that gets ugly pretty fast in a language without macros.


> **Ubuntist said:**
> 
I *can* appreciate that Common Lisp's macros are from a higher plane and appear to have no equivalents in Ruby or Python.  But, not being terribly fluent with them, I wonder how much I would use them in practice.


They have turned the way I program and think upside down at all levels; they are extremely usefull. I think I'll just say give both Lisp and Ruby a try and decide for yourself. :)


> **Ubuntist said:**
> 
My programming, by the way, tends to be pretty heavily numerical.  Astrophysics, finance and things like that.


You'll find that SBCL has great performance when handling numbers - and I believe Ruby cannot compete here.


> **Ubuntist said:**
> 
My doubts about Lisp boil down to the suspicion that Lisp's aura was made in the 90s and before, when it truly was light years ahead of other languages.  But, in the 21st century, does it really stand head and shoulders above Ruby, for example?


Yes, there are still significant parts of Lisp that are lacking in Ruby.

---

### Post by styracosaurus on 2006-12-01
I am a Computer Science undergrad at a Big State School on the east coast of the U.S.; I learned a little Scheme in a 300 level class this semester.

I thought it was really neat, and since I remember Eric S Raymond suggesting in some essay that learning Lisp will make you a better programmer, and after reading this essay:
[http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)
I was really interested in Lisp and the derivatives of before entering the class. It's definitely a change from all the Java they use in a lot of the rest of the curriculum.

Okay, so I don't know what the real point of this post was. Lisp is cool? Yea, that was it.

---

### Post by Ubuntist on 2006-12-04
> **lnostdal said:**
> ..it isn't.. ;) ..it lacks macros among other things .. and it lacks a native optimizing compiler..




It is not always the compactness that makes Lisp (or any language!) great - it's "that something else". I'd say it is very seldom the _initial_ compactness that makes a language great. :)

Remember that `n-body' is representing a very simple task when you look at the design of its software-parts. It's basically a performance-benchmark and does not show how Lisp can be used to elegantly solve complex software design-problems.




You should take a look at the later chapters:
  [http://www.gigamonkeys.com/book/practical-an-id3-parser.html](http://www.gigamonkeys.com/book/practical-an-id3-parser.html)

I bet stuff like that gets ugly pretty fast in a language without macros.




They have turned the way I program and think upside down at all levels; they are extremely usefull. I think I'll just say give both Lisp and Ruby a try and decide for yourself. :)




You'll find that SBCL has great performance when handling numbers - and I believe Ruby cannot compete here.




Yes, there are still significant parts of Lisp that are lacking in Ruby.

Thanks very much, lnostdal, for your thoughtful reply.

---

