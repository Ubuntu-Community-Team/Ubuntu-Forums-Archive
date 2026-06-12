---
title: "Scheme on Ubuntu"
date: 2009-02-13
forum: Programming Talk
---

### Post by igneousquill on 2009-02-13
I'm new to programming and have been working mostly on learning Python to start.  A couple of developers at work suggested I look into scheme, but I can't get it installed on Ubuntu 8.10.  It attempts to install, but then fails.  Is this a known issue?  Is there some way I can get this going?  I'd like to use the MIT manual on this as a guide, but without scheme installed....

---

### Post by Simian Man on 2009-02-13
The thing about Scheme is there are many different implementations.  I like guile the best, but mzscheme and MIT scheme are popular too.  Which are you trying to install?

---

### Post by igneousquill on 2009-02-13
> **Simian Man said:**
> The thing about Scheme is there are many different implementations.  I like guile the best, but mzscheme and MIT scheme are popular too.  Which are you trying to install?

mit-scheme

---

### Post by Simian Man on 2009-02-13
Are you installing it from the package manager or from source?  In either event what errors are you getting?

---

### Post by igneousquill on 2009-02-13
I've tried both.  I'm at my work computer now (a mac) so I'll have to post the error when I get a chance this evening.

Thanks.

---

### Post by jimi_hendrix on 2009-02-13
check the stickies, this is a known issue

i use mzscheme without a problem though

---

### Post by igneousquill on 2009-02-13
> **jimi_hendrix said:**
> check the stickies, this is a known issue

i use mzscheme without a problem though

I'm doing fairly well with Python, so there may not be any point in pursuing this.  It just annoys me that I can't use it, and I was hoping for a work-around.

Thanks.

---

### Post by Simian Man on 2009-02-13
If you are new to Scheme, why worry about MIT Scheme?  The language is the same, so you could at least start learning with another implementation.  guile and mzscheme are both good.  There is also PLT Scheme which includes a nice gui environment.

---

### Post by igneousquill on 2009-02-13
> **Simian Man said:**
> If you are new to Scheme, why worry about MIT Scheme?  The language is the same, so you could at least start learning with another implementation.  guile and mzscheme are both good.  There is also PLT Scheme which includes a nice gui environment.

The only thing that drew my attention to scheme was the encouragement from my co-workers to take a look at it.  They specifically recommended "Structure and Interpretation of Computer Programs," but it seems as though this book follows mit-scheme.

---

### Post by jimi_hendrix on 2009-02-13
> **igneousquill said:**
> I'm doing fairly well with Python, so there may not be any point in pursuing this.  It just annoys me that I can't use it, and I was hoping for a work-around.

Thanks.

scheme isnt ment for development...its ment for learning and exploring ideas and opening the mind (correct the first statement if its wrong)

if you learn scheme and do some problem solveing with it and you will be a better hacker

---

### Post by Sorivenul on 2009-02-13
The implementation you use is largely irrelevant for starting out with Scheme. I currently use Ikarus, though Guile is just fine. Guile is available in the repositories, and Ikarus is also as of 8.10. Good luck!

---

### Post by igneousquill on 2009-02-13
> **jimi_hendrix said:**
> scheme isnt ment for development...its ment for learning and exploring ideas and opening the mind (correct the first statement if its wrong)

if you learn scheme and do some problem solveing with it and you will be a better hacker

That's the gist of what the developers where I work told me.  Since mit-scheme apparently won't work on Ubuntu, how about a variety that will and a good tutorial to go along with it?

Thanks.

---

### Post by Sorivenul on 2009-02-13
> **igneousquill said:**
> Since mit-scheme apparently won't work on Ubuntu, how about a variety that will and a good tutorial to go along with it?
As has been stated, there are many implementations that *will* work:[LIST]
[*]Guile
[*]Gauche
[*]Ikarus
[*]PLT
[*]Chicken
[/LIST]
Pick one. There are even more available.

As far as tutorials go, I've had very little issue following [SICP (Structure and Interpretation of Computer Programs)]("http://mitpress.mit.edu/sicp/") from MIT with any implementation. I guess it's much more than a tutorial, but if you are learning Scheme or programming concepts in general, I highly recommend it.

---

### Post by igneousquill on 2009-02-13
> **Sorivenul said:**
> As has been stated, there are many implementations that *will* work:[LIST]
[*]Guile
[*]Gauche
[*]Ikarus
[*]PLT
[*]Chicken
[/LIST]
Pick one. There are even more available.

As far as tutorials go, I've had very little issue following [SICP (Structure and Interpretation of Computer Programs)]("http://mitpress.mit.edu/sicp/") from MIT with any implementation. I guess it's much more than a tutorial, but if you are learning Scheme or programming concepts in general, I highly recommend it.

Cool.  In that case I'll give Guile or Ikarus a try over the weekend and try to follow along with SIPC.

Thanks for all the advice on this thread.

---

### Post by jimi_hendrix on 2009-02-13
i lost the link but there was another tutorial like SCIP, but with easier language, it was an ebook with a blue cover...

---

### Post by igneousquill on 2009-02-13
> **jimi_hendrix said:**
> i lost the link but there was another tutorial like SCIP, but with easier language, it was an ebook with a blue cover...

I don't remember seeing anything like that.  One tutorial that looks fairly straightforward (to me) is ["Teach Yourself Scheme in Fixnum Days"]("http://tinyurl.com/pys4") What I've been told about SCIP, though, it that it helps newbies learn to think like programmers.

---

### Post by jimi_hendrix on 2009-02-13
> **igneousquill said:**
> I don't remember seeing anything like that.  One tutorial that looks fairly straightforward (to me) is ["Teach Yourself Scheme in Fixnum Days"]("http://tinyurl.com/pys4") What I've been told about SCIP, though, it that it helps newbies learn to think like programmers.

ya thats what i use for a quick reference...its pretty good

SCIP is great if you get past the MIT speak

the one i was talking about was written by MIT but for high school classes

---

### Post by CptPicard on 2009-02-13
I am not sure if DrScheme has been mentioned here -- it's PLT Scheme with a nice "IDE". Good for learning.

It's too bad mit-scheme is broken on Ubuntu... it is really the most representative and useful implementation IMO. Scheme is not just a learning-thing, it can be meaningfully used for a lot of things. There is even a type-hinted native-code compiler (bigloo).

Personally I have always found Scheme to be the most elegant lisp because it just really just cuts straight to the minimum while maintaining the maximum of what is possible to be expressed in a programming language. Of course CL is more "practical" but that also comes at a cost in language-design sense...

And it is **SICP**, not SCIP...

---

### Post by SteelDragon on 2009-02-13
> **jimi_hendrix said:**
> i lost the link but there was another tutorial like SCIP, but with easier language, it was an ebook with a blue cover...

Sounds like "How to Design Programs" to me.

[http://www.htdp.org](http://www.htdp.org)

---

### Post by jimi_hendrix on 2009-02-13
yes, i recommend that book (i didnt finish it but i read a good amount)

---

### Post by maximinus_uk on 2009-02-14
> **CptPicard said:**
> Personally I have always found Scheme to be the most elegant lisp because it just really just cuts straight to the minimum while maintaining the maximum of what is possible to be expressed in a programming language. Of course CL is more "practical" but that also comes at a cost in language-design sense...

I always think of Scheme as 'the mathmaticians lisp' and Common Lisp as the 'engineers Lisp'. The former is very minimalist and the latter throws in the kitchen sink - it's all there if you need it!

Personally I prefer the latter (OK, hygenic macros and reentrant continuations are pretty cool, but CL has bonuses in other areas)

---

### Post by CptPicard on 2009-02-14
Pretty good characterization... and it would be wrong to say that I have a "preference" in that sense that one dominates the other. CL is the more practical one, but there is a lot to be said for the elegance of Scheme... it is such a wonderful example of how you can retain the important conceptual things while cutting away a lot. And especially because it has continuations, it really contains pretty much all other programming languages as special cases...

---

### Post by nvteighen on 2009-02-14
MIT/GNU Scheme is broken in Ubuntu since 8.04. The issue is that in 8.04 the error was easily solvable by modifying a config file and now the issue is a huge dependency conflict.

MzScheme, one of the PLT Schemes, is maybe the second-best you can get. The issue is that it uses some non-R5RS compliant functions for very simple stuff, for example, instead of the standard "display" function, you use "print" for outputting to screen, while MIT/GNU is one of the most complying implementations (but the one with the least amount of useful extensions).

---

### Post by Mr.Macdonald on 2009-02-14
> scheme isnt ment for development...its ment for learning and exploring ideas and opening the mind

This is very wrong, Scheme is a language as is anything else. I use it as one would Python. I prefer Scheme to languages such as C++ and Java.

My latest Scheme project is a terminal based Connect 4. It comes with a prompt and displays the board.

---

### Post by Mr.Macdonald on 2009-02-14
EDIT: Not My Post

---

### Post by jimi_hendrix on 2009-02-14
> **Mr.Macdonald said:**
> This is very wrong, Scheme is a language as is anything else. I use it as one would Python. I prefer Scheme to languages such as C++ and Java.

My latest Scheme project is a terminal based Connect 4. It comes with a prompt and displays the board.

ok...i am generalizing, name 5 major apps written in scheme

---

### Post by igneousquill on 2009-02-14
> **SteelDragon said:**
> Sounds like "How to Design Programs" to me.

[http://www.htdp.org](http://www.htdp.org)

Thanks for the link.  I'm bookmarking it.

---

### Post by igneousquill on 2009-02-17
Apparently I never updated here on how things worked out.  I have guile up and running and am able to follow along just fine with SICP.  Thanks again for the help, everyone.

---

### Post by Sorivenul on 2009-02-17
> **igneousquill said:**
> Apparently I never updated here on how things worked out.  I have guile up and running and am able to follow along just fine with SICP.  Thanks again for the help, everyone.
Glad to hear it. Good luck!

---

### Post by pgatrick on 2009-02-17
> **igneousquill said:**
> That's the gist of what the developers where I work told me.  Since mit-scheme apparently won't work on Ubuntu, how about a variety that will and a good tutorial to go along with it?

Thanks.

Have you tried drscheme? It's been a while, but it installed fine when I last used ubuntu, and goes along with the sicp course.

Guess I should have read the rest of this thread, oh well.

---

### Post by keymoo on 2009-11-21
mit-scheme seems to work fine with koala

```
apt-get install mit-scheme
```

---

