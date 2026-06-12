---
title: "Scientific programming"
date: 2008-03-09
forum: Programming Talk
---

### Post by Stochastics on 2008-03-09
Hi everyone,

I want to know from all the experts around what is the better/faster programming language to learn (it can be more than one) for scientific computing. 

Thanks in advance.

Stochastics

---

### Post by Fbot1 on 2008-03-09
What kind of scientific programming?

---

### Post by CptPicard on 2008-03-09
Well, better and faster can be contradictory. A lot of people here will suggest Python for ease of use and ease of learning, but it's certainly not the fastest, unless you can code on top of some specifically optimized C libraries.

Matlab is very much used for general mathematics. For symbolic-functional mathematical computation, one might consider a Lisp or some other functional language...

---

### Post by lnostdal on 2008-03-09
Common Lisp is often used .. you can do fancy "scientific stuff" like create custom languages with it .. ie. [http://www.lambdassociates.org/](http://www.lambdassociates.org/) .. there are many examples out there .. people do this to suit specific programming needs that seldom show up when doing "normal programming"(#1)

it also has very good performance seeing as implementations with native optimizing compilers exist .. performance of optimized lisp code is in some cases close to, and sometimes faster than optimized C code .. (..i'm talking about the SBCL implementation in particular here)

it has good support for numerical type stuff .. bignums and rational numbers are built in .. seamless and transparent transition from machine-type native representation of numbers to bignum representation as needed .. etc. .. usually very handy for "scientific stuff"

in general, it is extremely flexible .. Common Lisp is a programmable programming language

[http://wiki.alu.org/The_Road_to_Lisp_Survey](http://wiki.alu.org/The_Road_to_Lisp_Survey)
[http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/)
[http://www.paulgraham.com/onlisp.html](http://www.paulgraham.com/onlisp.html)


#1: but lisp makes re-programming the language so easy that i find i often do it even when doing "normal programming" .. it's (some call it meta-programming) not something i think about as anything special any longer

---

### Post by Lster on 2008-03-09
I've been programming in C to solve the puzzles on *Project Euler*. I've found it good solution but I have also been using *Python* and *BC*. Pick a tool that suites the job... :)

---

### Post by Stochastics on 2008-03-09
> **Fbot1 said:**
> What kind of scientific programming?

Numerical analysis. Numerical solutions of linear/nonlinear/stochastic ordinary/partial differential equations, integral equations arising in electrodynamics. I want to implement my own, finite-difference/finite-element solver to understand how it works. I know Matlab, Mathematica and Maple and this programs are great, but when you want to generate alot of random paths (for stochastic differential equations), these tends to become slowly...

I will try Python and/or Fortran i guess...what i need to install in Ubuntu to be ready ?

Thanks.

---

### Post by slavik on 2008-03-09
for scientific computing: Haskel, FORTRAN, List. FORTRAN isn't being used much anymore. Haskel can be run on a cluster (where it automatically parallelizes what it can)

---

### Post by CptPicard on 2008-03-09
> **Stochastics said:**
> 
I will try Python and/or Fortran i guess...what i need to install in Ubuntu to be ready ?


My hunch is Python will be too slow. Unfortunately you may have to use C to code your solver, but the problem with C is that its primitives are just... too primitive -- you need quite a bit of data structures/algorithms implementation of your own -- all the way from scratch actually.

This is why this kind of stuff is not usually implemented by the end-user, but is in a ready-made library ;)

---

### Post by LaRoza on 2008-03-09
> **slavik said:**
> for scientific computing: Haskel, FORTRAN, List. FORTRAN isn't being used much anymore. Haskel can be run on a cluster (where it automatically parallelizes what it can)

Fortan is used a lot! It is used on almost all super computers, and is still taught. Fortran 77 may be old (it is the version I use), but Fortran is still in development, Fortran 2008 is due soon I hear. (Fortran 2003 is the latest I think)

Fortran is extensively used in the scienctific and math areas.

---

### Post by slavik on 2008-03-09
> **LaRoza said:**
> Fortan is used a lot! It is used on almost all super computers, and is still taught. Fortran 77 may be old (it is the version I use), but Fortran is still in development, Fortran 2008 is due soon I hear. (Fortran 2003 is the latest I think)

Fortran is extensively used in the scienctific and math areas.
Haskel is the Python of scientific computing ;)

---

### Post by Fbot1 on 2008-03-09
> **Stochastics said:**
> Numerical analysis. Numerical solutions of linear/nonlinear/stochastic ordinary/partial differential equations, integral equations arising in electrodynamics. I want to implement my own, finite-difference/finite-element solver to understand how it works. I know Matlab, Mathematica and Maple and this programs are great, but when you want to generate alot of random paths (for stochastic differential equations), these tends to become slowly...

There isn't any that really do that well, I think Clean might be good. I guess it really depends on how much you want to get in to it.

---

### Post by Stochastics on 2008-03-09
> **LaRoza said:**
> Fortan is used a lot! It is used on almost all super computers, and is still taught. Fortran 77 may be old (it is the version I use), but Fortran is still in development, Fortran 2008 is due soon I hear. (Fortran 2003 is the latest I think)

Fortran is extensively used in the scienctific and math areas.

Is there something i need to install in Ubuntu to be able to program in Fortran 2003 ? I know there is a GNU Fortran compiler in Ubuntu, but i think it's a bit old i guess...

Thanks.

Stochastics

---

### Post by Stochastics on 2008-03-09
> **slavik said:**
> Haskel is the Python of scientific computing ;)

Is there a Haskel implementation in Ubuntu ?

Stochastics

---

### Post by pmasiar on 2008-03-09
numpy calls the same C libraries, just calls them from Python. So you have almost speed of C, and almost full power of Python. For statistics, there is RPy - binding to R. Unless you need to develop your own algorithms, these days there is hardly need to use low-level language like C or Fortran.

Python was designed for scientific computing from the very beginning (to call C libraries doing the computations).

It is good to have C as second language, in those rare cases when library is missing, but C/Fortran/(whatever low level language) should **not** be a first choice, IMHO.

---

### Post by LaRoza on 2008-03-09
> **Stochastics said:**
> Is there something i need to install in Ubuntu to be able to program in Fortran 2003 ? I know there is a GNU Fortran compiler in Ubuntu, but i think it's a bit old i guess...

Thanks.

Stochastics

[http://gcc.gnu.org/onlinedocs/gfortran/Fortran-2003-status.html](http://gcc.gnu.org/onlinedocs/gfortran/Fortran-2003-status.html)

---

### Post by pmasiar on 2008-03-09
> **Stochastics said:**
> Is there a Haskel implementation in Ubuntu ?

You forgot to mention your current programming skill... but I would not recommend Haskel between first 3 languages to learn. It is ... rather different. :-)

I suggest learning in this order: 1) Python, 2) C, 3) whatever you need after that - maybe Fortran.

---

### Post by lnostdal on 2008-03-09
> **Stochastics said:**
> Is there a Haskel implementation in Ubuntu ?

Stochastics

yes, it's in the repositories:
```

sudo aptitude search ghc

```

( [http://www.haskell.org/ghc/](http://www.haskell.org/ghc/) )

---

### Post by LaRoza on 2008-03-09
> **lnostdal said:**
> yes, it's in the repositories:
```

sudo aptitude search ghc

```

( [http://www.haskell.org/ghc/](http://www.haskell.org/ghc/) )

Or hugs, it has less, but is easy to use.

---

### Post by Stochastics on 2008-03-09
> **pmasiar said:**
> You forgot to mention your current programming skill... but I would not recommend Haskel between first 3 languages to learn. It is ... rather different. :-)

I suggest learning in this order: 1) Python, 2) C, 3) whatever you need after that - maybe Fortran.

As a mathematical-theoretical physicist, i know the usual : Mathematica, Matlab and Maple. I want to move forward and learn some common and practical programming language. I will use your advice for 1) Python, 2) C and 3) Fortran.

Thanks !

Stochastics

---

### Post by euler_fan on 2008-03-09
The only reason to possibly reverse that order would be your areas of interest.

If you're familiar at all with the computational meteorology realm, the Advanced Regional Prediction System (APRS) out of U Oklahoma is done in Fortran 77/90.

I make this observation strictly because weather means fluid dynamics which means most of what you were talking about earlier (dynamical systems, O/P-DE's, finite element and finite difference methods, etc).

---

### Post by slavik on 2008-03-09
If you're a mathematics person, I would strongly suggest not starting with Python or C, they give you no benefit for when you want to learn functional languages.

I would say Scheme then Haskel.

---

### Post by pmasiar on 2008-03-09
> If you're a mathematics person, I would strongly suggest not starting with Python or C, they give you no benefit for when you want to learn functional languages.

I would say Scheme then Haskel.

It is funny that person who complains at every turn about me "blindly" promoting Python, is so eager to suggest **not** learning Python that ignores any additional info OP provided:

> **Stochastics said:**
> As a mathematical-theoretical physicist, i know the usual : Mathematica, Matlab and Maple. I **want to move forward and learn some common and practical programming language**.

yes I know: now you will argue that Scheme or Haskel are "common and practical programming languages", like Python or C... Some people will never grow up.

---

### Post by slavik on 2008-03-09
> **pmasiar said:**
> It is funny that person who complains at every turn about me "blindly" promoting Python, is so eager to suggest **not** learning Python that ignores any additional info OP provided:



yes I know: now you will argue that Scheme or Haskel are "common and practical programming languages", like Python or C... Some people will never grow up.
the OP is a mathematician first, programmer second. the subject says "scientific programming" and Haskel is much more common in the scientific computing than Python will ever be. :)

---

### Post by euler_fan on 2008-03-09
> **slavik said:**
> If you're a mathematics person, I would strongly suggest not starting with Python or C, they give you no benefit for when you want to learn functional languages.

I would say Scheme then Haskel.

And if he's not going to be working with m/any problems which beg for a functional approach? I know people who are doing knot theory research in Python and R because they're relatively easy to use and let them get the job done efficiently. :)

Whatever happened to "right tool for the job"?

---

### Post by Fbot1 on 2008-03-09
> **pmasiar said:**
>  now you will argue that Scheme or Haskel are "common and practical programming languages", like Python or C... Some people will never grow up.

For the OP's purpose, Python really isn't either. I think Clean and maybe C or Pascal would be best (and that's a strong maybe).

> **euler_fan said:**
> I know people who are doing knot theory research in Python and R because they're relatively easy to use and let them get the job done efficiently. :)

Whatever happened to "right tool for the job"?

I think execution speed is also important here too.

---

### Post by lnostdal on 2008-03-09
i'm curious .. pascal was one of the first languages i learned when i was a kid .. do people still use it (do you, fbot1)? ..  and for what?

i can't think of a single reason why i'd recommend anyone pascal today .. it doesn't have anything to offer compared to even todays mainstream languages .. or am i missing something?

---

### Post by Fbot1 on 2008-03-09
> **lnostdal said:**
> i'm curious .. pascal was one of my first languages i learned when i was a kid .. do people still use it (do you, fbot1)? ..  and for what?

i can't think of a single reason why I'd recommend anyone pascal today .. it doesn't have anything to offer compared to even todays mainstream languages .. or am i missing something?

It is actually used in a few projects. I mess around with it. It's been extended so it's not like the old pascal. Of course there still isn't much of point in using it if you want to attract other programmers.

---

### Post by pmasiar on 2008-03-09
> **Fbot1 said:**
> I think Clean ... or Pascal would be best.

You may use different definition for "common and practical" than most people. :-)

---

### Post by slavik on 2008-03-09
Maybe they use Python because of R only supports Python?

---

### Post by euler_fan on 2008-03-09
> **slavik said:**
> Maybe they use Python because of R only supports Python?

FYI: [R]("http://www.r-project.org/")

From talking to them it's more the following:
1) They're not running anything on "big iron"--usually just a standard Dell workstation/desktop.
2) Python+openGL+a few other little things is just fine for the scale they're working at and what they're doing.
3) R can do the statistics fairly quickly and easily.
4) It's not worth their time to learn another language and reimplementing their work.
5) If it's going to take a while to compute, they're fine with doing something else for a while.
6) When somethings going to get run on big iron/ a supercomputer, they have collaborators who handle the code for that in something better suited for it.

---

### Post by slavik on 2008-03-09
> **euler_fan said:**
> FYI: [R]("http://www.r-project.org/")

From talking to them it's more the following:
1) They're not running anything on "big iron"--usually just a standard Dell workstation/desktop.
2) Python+openGL+a few other little things is just fine for the scale they're working at and what they're doing.
3) R can do the statistics fairly quickly and easily.
4) It's not worth their time to learn another language and reimplementing their work.
5) If it's going to take a while to compute, they're fine with doing something else for a while.
6) When somethings going to get run on big iron/ a supercomputer, they have collaborators who handle the code for that in something better suited for it.
if you're into heavy scientific computing, you run stuff on a cluster ... for which Python would not be very well suited (I am writing code in C and even having simple access to the system, it is not simple).

---

### Post by lnostdal on 2008-03-09
> **slavik said:**
> if you're into heavy scientific computing, you run stuff on a cluster ... for which Python would not be very well suited (I am writing code in C and even having simple access to the system, it is not simple).

disclaimer: i don't really care either way .. c vs. python .. or whatever

but, well, clustering does not "mean" c

people (you? .. i don't know) seem to talk about what they are currently working on or "focusing on" a lot of the time.. like coming home from the blackboard and teachers having learned something new and cool .. "this must be it!" .. "heavy scientific computing!" .. "i'm doing it!" .. "in c, for some reason!" ..  "it's hard in c, for some reason!" (not that that means that doing it in c is a (or the) problem or "wrong" in itself) .. but ==> "i bet that means it's harder (or wrong) in other languages, automatically!" ..?

.. please .. just stop it .. it's just noise ..

"..and this one time - at base camp.."

---

### Post by pmasiar on 2008-03-10
> **slavik said:**
> Maybe they use Python because of R only supports Python?

It is other way around. R has own language, which is very good at calculating stats, but not that good in reading files etc. So having RPy allows you all the flexibility of file massaging, and then all the flexibility of R stats calculations. Win-win.

---

### Post by slavik on 2008-03-10
the point was that for "real" scientific computing, a language like C or Python is just crap ... because YOU (the programmer) have to worry about how the application communicated between the various parts ...

---

### Post by pmasiar on 2008-03-10
> **slavik said:**
> if you're into heavy scientific computing, you run stuff on a cluster ... for which Python would not be very well suited.

That would be news to our university scientific computing cluster team. :-)

All they do is to use Python to split data for parallel tasks, run them on cluster (using whatever libraries they have for the task), then merge results. And they prefer Python to anything else! :-) They even use Python to generate optimized C code (linking to their C libraries) instead of writing one big complicated C code handling all the special cases. Or inject snippets of C code to libraries, to enable cluster synchronization.

---

### Post by slavik on 2008-03-10
> **pmasiar said:**
> That would be news to our university scientific computing cluster team. :-)

All they do is to use Python to split data for parallel tasks, run them on cluster (using whatever libraries they have for the task), then merge results. And they prefer Python to anything else! :-) They even use Python to generate optimized C code (linking to their C libraries) instead of writing one big complicated C code handling all the special cases. Or inject snippets of C code to libraries, to enable cluster synchronization.
Then ask them how easy it is to write parallel code and how much of the time they spend thinking about what happens.

with Haskel, the haskel compiler does all of that.

---

### Post by cb951303 on 2008-03-10
I once used [http://www.scipy.org/](http://www.scipy.org/) 
I find it to be very complete and professional

---

### Post by Fbot1 on 2008-03-10
> **pmasiar said:**
> You may use different definition for "common and practical" than most people. :-)

First off, way to improperly quote me. Also, I never suggested either was common. I don't see how that would matter anyway; most likely, only one person will look at the source.

---

### Post by pmasiar on 2008-03-10
> **Fbot1 said:**
> First off, way to improperly quote me. Also, I never suggested either was common. 

"common and practical" was something OP wanted. But why should **you** care what OP wants, right? :-)

> I don't see how that would matter anyway; most likely, only one person will look at the source.

One of the most important insights of Guido was that **program code is for communicating about algorithms between people, and communicating with computers is second priority**. But you very obviously missed that. :-(

---

### Post by fyplinux on 2008-03-10
Matlab is good for numerical programming , it is widely used for data analysis.

---

### Post by LaRoza on 2008-03-10
> **fyplinux said:**
> Matlab is good for numerical programming , it is widely used for data analysis.

Octave is a free Matlab like language, see my wiki.

---

### Post by Siph0n on 2008-03-10
LaRoza, I just tried to go to your wiki from my work computer (Windows XP, IE Version 6) and it asks me to save home, and doesn't show your site.... just thought i'd tell u....

---

### Post by LaRoza on 2008-03-10
> **Siph0n said:**
> LaRoza, I just tried to go to your wiki from my work computer (Windows XP, IE Version 6) and it asks me to save home, and doesn't show your site.... just thought i'd tell u....

Yes, see the "IE Version" link? That will work.

It is on my wiki, which is [http://laroza.pbwiki.com](http://laroza.pbwiki.com)

The reason for this is because I serve my homepage with the currect MIME type, which is not recognized by IE6 or 7, although every other modern browser has no problem with it.

---

### Post by mssever on 2008-03-10
> **LaRoza said:**
> The reason for this is because I serve my homepage with the currect MIME type, which is not recognized by IE6 or 7, although every other modern browser has no problem with it.

Would putting a meta tag in an IE conditional comment which overrides the Content-Type enable you to have only one version?

(Isn't IE annoying?)

---

### Post by LaRoza on 2008-03-10
> **mssever said:**
> Would putting a meta tag in an IE conditional comment which overrides the Content-Type enable you to have only one version?

(Isn't IE annoying?)

Yes, and yes.

---

### Post by Fbot1 on 2008-03-10
> **pmasiar said:**
> "common and practical" was something OP wanted. But why should **you** care what OP wants, right? :-)

Sure I do but like I said, there isn't really any that fit perfectly.

---

