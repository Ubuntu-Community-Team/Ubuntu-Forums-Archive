---
title: "FP languages"
date: 2013-07-02
forum: Programming Talk
---

### Post by Dirich on 2013-07-02
Hello, I need help in deciding which functional programming language to study.

I would like to learn a functional programming language, for the pleasure of it and to learn about the FP paradigm (I already know imperative and object oriented).
I normally work with C/C++ and write physical simulation programs or some mathematical code, although occasionally I write thousands of lines of code to handle the inputs to my programs (a lot of checks to be sure to never run a useless simulation because of some human error in typing the inputs). It would be nice if I could also use the FP language to speed up some parts of my work, so I'd like for it to be compatible with C/C++ in an easy way (I am not sure if it could even be an issue these days, but just in case...).

I read the newest "old threads" about functional programming, but they were mostly about FP vs OO vs Imperative or they did not motivate why one FP language instead of another. I would really appreciate if you could motivate with some detail the reason behind your FP language suggestion, because, thanks to the wiki, I already know a lot of names, what I lack is the reason they "came to be" (their "specialization" or reason for lack of thereof - what they are "best" for).
Also if you could specify how "popular" the language is, I would be grateful: I sometime have to deal with programs written by others, so if, by chance, I could already know the language someone else chose for his program, it would be an unexpected, but much welcome, bonus (as previously implied, I work in a physics department).

Last note: I would prefer a purely FP language (I read that I could use Python or C++ as functional programming languages, i.e., I am not interested in that).

---

### Post by ofnuts on 2013-07-02
ECMAScript/JavaScript?

---

### Post by nvteighen on 2013-07-02
If you want 100% FP, without even the possibility to get imperative programming, then, Haskell or Clojure. Both are reasonably popular, i.e. you may not find as many jobs for Haskell or Clojure as for C, C++, Java, Javascript, et al., but you'll definitely find a lot of resources on the web for learning it.

---

### Post by Dirich on 2013-07-02
I read about Clojure and compared it to what I knew about Haskell. Beside the Java thing, which is no use to me since I will hardly move from C/C++ for performance reasons, the thing that hit me the most is the macro system from LISP, which should be the feature offered by Clojure under that very same name. From what I read Haskell has a GHC extension to allow metaprogramming, but somehow I feel, correct me if I am wrong, that for that I should use something more LISP-esque than Haskell.

Allow me to extend the questions in the first post (more suggestions on those are still welcome): is Clojure the best thing to learn if what I am interested in is to understand the power behind LISP macro system for metaprogramming?

P.S.
Haskell seems to be nearer to the academia needs and is purely functional, which should force me to really understand the paradigm, thus I am opting for that as a first one, but the LISP macro thing kinda hooked me up.

---

### Post by hdgarrood on 2013-07-02
I would also recommend learning Haskell. It forces you to think in a completely different way, which (for me) has been fun and also has improved the quality of code I write in imperative languages. I don't know Clojure, though. I think for getting started with FP, it probably doesn't matter which you pick.

> From what I read Haskell has a GHC extension to allow metaprogramming,  but somehow I feel, correct me if I am wrong, that for that I should use  something more LISP-esque than Haskell.
I think you should wait until you have a reasonable grasp of one FP language to start worrying about this.

---

### Post by Leuchten on 2013-07-02
I would also recommend Haskell if you want to force yourself to program purely functionally. However, if you want a less steep intro, I'd recommend Scala (like always). As far as functional programming features go, I can't think of any that haskell has that scala is missing.

A question for the Haskellites in this thread, does haskell have dependent types, or just agda?

---

### Post by nvteighen on 2013-07-02
> **Dirich said:**
> I read about Clojure and compared it to what I knew about Haskell. Beside the Java thing, which is no use to me since I will hardly move from C/C++ for performance reasons, the thing that hit me the most is the macro system from LISP, which should be the feature offered by Clojure under that very same name. From what I read Haskell has a GHC extension to allow metaprogramming, but somehow I feel, correct me if I am wrong, that for that I should use something more LISP-esque than Haskell.

Allow me to extend the questions in the first post (more suggestions on those are still welcome): is Clojure the best thing to learn if what I am interested in is to understand the power behind LISP macro system for metaprogramming?

P.S.
Haskell seems to be nearer to the academia needs and is purely functional, which should force me to really understand the paradigm, thus I am opting for that as a first one, but the LISP macro thing kinda hooked me up.

Your goals are a bit mixed up, I thinl. If you all you want is to tackle Lisp macros, go for the more traditional Lisp dialects, i.e. Common Lisp and Scheme, and just avoid whatever that is imperative. There's a little problem with this, though: Common Lisp macros are the more traditional Lisp macros than the ones Scheme has, but the language is more complex and avoiding imperative idioms may be a bit hard. Scheme, on the other hand, makes it quite easy to avoid imperative idioms (avoid anything named with a trailing "!", like set!, delete!, etc.), but its macros are of a completely different type than Common Lisp ones... FYI, the latest Scheme specs (R6RS) uses a quite interesting syntax pattern matching that is a bit more complex than the direct symbolic manipulation in CL. Another additional problem of Scheme is that implementations are very different to each other because the specs are really minimal (23 keywords only!)... I'd go for PLT Scheme, as it supports R6RS (MIT/GNU seems to be stuck on a weird R4RS/R5RS mix).

Of course, you can learn both CL or Scheme for their macros and Haskell for hardcore, math-like FP.

---

### Post by CptPicard on 2013-07-02
I would have to interject here that I am not particularly sure that the idea of some language "forcing" you to do things in certain ways is a good thing, if some other language lets you approach the problem that way but does not necessarily force the point. Haskell is certainly "pure", but Lisp is more general-purpose and teaches you a lot of *other* interesting things about programming that Haskell can't, as its approach is so completely geared towards programs-as-pure-expressions... by all means do use Lisp pure-functionally to your heart's content if that is what you wish.

---

### Post by Mikeb85 on 2013-07-02
I'd recommend Clojure.  It has plenty of useful features and libraries for building useful things, and you can use any Java library very easily as well. 

If you don't like Lispy languages, then I'd use OCaml.  It's got nice syntax, a phenomenal compiler (compiles very fast binaries, can also compile to OCaml bytecode, JVM bytecode, to Javascript, LLVM, etc...), and a great feature set.

---

### Post by dazman19 on 2013-07-03
+1 for Haskell
You will learn to approach problems differently. There are many ways to solve problems. I absolutely hated haskell when i started it, i was very much an imperative programming kind of person. Now learning how to solve issues with Haskell or Prolog then and the kind of problems which can be solved, i think Haskell would be an excellent start. 

Just a word of caution. Its not quite like C/C++/Java/JS/PHP/C#/Python whatever... it will take a bit of getting your head around but you will be a better programmer for learning it or at least understanding it.

---

### Post by Dirich on 2013-07-03
I choose Haskell as first and something LISP-esque as second. But after reading all posts now I am a bit confused about what to choose in the LISP family, so I would like some additional advice on that.

I read [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html) (Blub paradox) and the [FONT=verdana][SIZE=2]Eric Raymond [/SIZE][/FONT]quote was what triggered my interest, which was enhanced by the cool success story of the author and his use of LISP (no dialect?).
I think (correct me if I am wrong), beside the functional paradigm, much of that depended on the macro system, so I am interested in which of the cited options (Common Lisp, Scheme, Clojure) could be more effective in that regard.
I guess, as always, there is not a "right" answer, so if you could give me some clue about the differences in the macro systems between the various options, I could reach a more educated choice (wiki failed me this time too).

P.S.
For my LISP-esque choice I am no more interested in the the language to be purely functional, since I already got Haskell for that. I want to use that to improve as a programmer.

---

### Post by CptPicard on 2013-07-03
If it is only the macro system you're interested in that regard, then the most important differences deal with this:

[http://en.wikipedia.org/wiki/Hygienic_macro](http://en.wikipedia.org/wiki/Hygienic_macro)

I wouldn't be too concerned about the differences between Lisps before you understand what they are; at that point you're competent enough to move between the different Lisps. My suggestion would be Clojure as that is currently the most practical Lisp; Common Lisp is really impressive in its own ways (the SBCL implementation in particular), and Scheme has this certain nice theoretical purity because it was created with teaching in mind.

---

