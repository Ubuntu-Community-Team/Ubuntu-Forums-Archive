---
title: "How to edit scheme programs?"
date: 2009-11-23
forum: Programming Talk
---

### Post by keymoo on 2009-11-23
Hi there,

I'm attempting to read through [Structure and Interpretation of Computer Programs]("http://mitpress.mit.edu/sicp/full-text/book/book.html"), and to work through it I've downloaded the videos and the mit-scheme version of Scheme from the ubuntu repositories in 9.10 x86. All is well.

However, I am typing in programs into the interpreter, but if i make a mistake I have to type the whole thing in again. I'm wondering how you have set up your own mit-scheme on ubuntu, and wondered what the best way to is to tackle the problem. I will get around to reading the [85 page scheme manual]("http://www.gnu.org/software/mit-scheme/documentation/mit-scheme-user.pdf") shortly.

For example I typed in an implementation of Ackermann's function, but made a mistake, I don't want to have to keep typing it in every time I make a mistake.
```
1 ]=> (define (A x y)
        (cond ((= y 0) 0)
                ((= x 0) (* 2 y))
                ((= y 1) 2)
                (else (A (-x 1)
                        (A x (- y 1))))))
```
My mistake is on the else line, I need a space between the - and the x.

Thanks for any pointers!
keymoo

---

### Post by CptPicard on 2009-11-23
Yeah, don't use the raw repl, it's not meant for that. :)

Google for tutorials how to use use mit-scheme from Emacs, or alternatively look at the DrScheme implementation... it's a nice small "IDE" meant for learning.

---

### Post by baizon on 2009-11-23
> **CptPicard said:**
> Yeah, don't use the raw repl, it's not meant for that. :)

Google for tutorials how to use use mit-scheme from Emacs, or alternatively look at the DrScheme implementation... it's a nice small "IDE" meant for learning.

I recommend DrScheme. It's a nice IDE for Scheme.
Link: [http://www.plt-scheme.org/]("http://www.plt-scheme.org/")

---

### Post by grayrainbow on 2009-11-23
+1 for DrScheme, best one IMO, if you exclude some proprietary IDEs. But it's kinda heavy(the IDE, not the interpreter). Last time I use gnu/mit scheme it hangs all the times in bigger programs, guess it's just not standard Scheme implementation.

---

### Post by nvteighen on 2009-11-23
> **grayrainbow said:**
> +1 for DrScheme, best one IMO, if you exclude some proprietary IDEs. But it's kinda heavy(the IDE, not the interpreter). Last time I use gnu/mit scheme it hangs all the times in bigger programs, guess it's just not standard Scheme implementation.

Well... historically speaking, MIT/GNU Scheme is the direct offspring of the original MIT Scheme implementation. Anyway, you better use an editor (Emacs has great out-of-the-box support for MIT/GNU) or an IDE.

It's a question hard to answer. If you're following SICP, you must use MIT/GNU Scheme as trying to do **cons-stream** in PLT Scheme (DrScheme, MzScheme, etc.) will yield an error. And curiously, who's right is PLT, as "cons-stream" is not standard Scheme (it's one of the SRFI "Scheme Requests for Implementation"... specifically, SRFI 41).

Scheme is a mess. Its standard is too small (on purpose) and this leads to the fact that lots of the code you write will be plagued by non-standard extensions... just because you'll need them. The PLT designers have stated that "Scheme is more an idea than a programming language" and that might be really true. So, no matter which implementation you use, you'll always end up writing non-portable code; for portability, Common Lisp is always a better choice.

This is the reason why you should stick to MIT/GNU if you're following SICP. You'll avoid having to translate stuff and lose time learning implementation-specific stuff and so you'll be able to focus on the concepts. In the end, if you learn the ideas that SICP teaches you, you'll be able to easily jump from one implementation to the another or implement the stuff by yourself.

People here know from my posts I am a huge fan of MIT/GNU. Well, it's the best implementation for learning Scheme, IMO. But PLT Scheme is far superior if you plan to use Scheme for a real project. Another drawback of MIT/GNU is that it didn't finished the transition from Scheme's standard R4RS into R5RS... and the current standard is R6RS since 2007. PLT already supports R6RS. You may not be able to appreciate the changes, but the macro system has been greatly improved from R4RS to current R6RS.

Other implementations are far too small (in the sense of support and presence in the Schemer community)... though MIT Scheme48 is an interesting candidate for a "third competitor".

---

### Post by keymoo on 2009-11-23
Thanks for the replies!

I never intend to produce anything serious in scheme - I only want to use it to improve my programming skills. My main languages are SQL and C#, but I'm also interested in looking at python.

So, the only reason I'm learning scheme is just to follow the book and do the exercises - so I guess I should use MIT/GNU scheme for this purpose. The only drawback is that I know vi a little bit but have never fired up emacs before in my life. :rolleyes:

Hmmm, do I have to learn emacs, to learn scheme, to read the book? Seems like a lot of effort. Any easier ways, shortcuts, further hints/tips? :)

---

### Post by grayrainbow on 2009-11-23
@keymoo, it happen that I'm from people who like emacs and therefore on all machines I use, control and caps lock keys are swapped, just to be prepare if you want to use emacs. The really nice thing of emacs is, that instead of plugins you got elisp file, which you can edit or easyly create new when you become familiar with them ;) Otherwise, lot's of US universities teach Scheme for their first year, so lecture book from there could be helpfull, I also believe that there should be some video lecture on the subject in universitie sites, youtube or google video. Btw, I never find to be good idea to teach Scheme as first programming language. IMO one better know a bit of logic, data structures and simple Von Neumann architecture first(but seems you already got this).

@nvteighen, I think my biggest problem with GNU/MIT implementation are tail calls, when ever I try to do a lot of recursions, it simply didn't work, and tail calls are required by the standard as far as I remember.

---

### Post by nvteighen on 2009-11-23
> **keymoo said:**
> 
So, the only reason I'm learning scheme is just to follow the book and do the exercises - so I guess I should use MIT/GNU scheme for this purpose. The only drawback is that I know vi a little bit but have never fired up emacs before in my life. :rolleyes:

Hmmm, do I have to learn emacs, to learn scheme, to read the book? Seems like a lot of effort. Any easier ways, shortcuts, further hints/tips? :)

Hm... Learning Emacs would be a good idea because of the integration it has with MIT/GNU. Making Emacs work with PLT Scheme is quite a task. But if you prefer vi, well, use it... maybe you can find some way to plug MIT/GNU into it too... Or just use the **scheme --load myfile.scm** command.

> **grayrainbow said:**
> 
@nvteighen, I think my biggest problem with GNU/MIT implementation are tail calls, when ever I try to do a lot of recursions, it simply didn't work, and tail calls are required by the standard as far as I remember.

I've never had that issue... at least with big **reasonable** recursions (i.e., not taking the factorial of 56777777). What sometimes happens is that the GC intervenes too early to interrupt execution (aprox. at 34% memory usage).

---

### Post by grayrainbow on 2009-11-23
567...lot of 7... quite an interesting number you got :)
While factorial is very good for recursive example(especially couse it's most intuitive approach is not with tail call) it is indeed very bad for testing, too small and quite normally interpreter could got buggy with it. But I make more use of mutually recursive calls, and sometimes abuse with them(probably I should trow eye on Prolog).

---

### Post by CptPicard on 2009-11-23
I find it very hard indeed to believe that any decent Scheme implementation would have problems with tail call implementation. They are easily recognizable and simply optimizable into using just constant space... and them being the only "looping" construct and the one that makes the language thus Turing-complete (you need recursive structure, either with stack+loop or tail call -- or infinite space), pretty much nothing would work without tail calls working...

---

### Post by nvteighen on 2009-11-24
> **grayrainbow said:**
> 567...lot of 7... quite an interesting number you got :)
While factorial is very good for recursive example(especially couse it's most intuitive approach is not with tail call) it is indeed very bad for testing, too small and quite normally interpreter could got buggy with it. But I make more use of mutually recursive calls, and sometimes abuse with them(probably I should trow eye on Prolog).

(I did test the factorial of that number... MIT/GNU aborted immediately; PLT tried to solve it making my system swap that way that I had to interrupt it before I could know whether it worked or not)

I also use all kind of recursive stuff and haven't ever experienced any problem. Could you post an example so we can test it?

---

### Post by CptPicard on 2009-11-24
> **nvteighen said:**
> 
I've never had that issue... at least with big **reasonable** recursions (i.e., not taking the factorial of 56777777). What sometimes happens is that the GC intervenes too early to interrupt execution (aprox. at 34% memory usage).

Of course one has to understand that in cases like this the problem is not the size of the recursion (it still just turns into essentially a loop), but the size of the result, especially as Scheme has arbitrary length ints. :)

I've got the factorial running here in the background, at least not getting any memory problems or aborts.

---

### Post by grayrainbow on 2009-11-24
> **nvteighen said:**
> (I did test the factorial of that number... MIT/GNU aborted immediately; PLT tried to solve it making my system swap that way that I had to interrupt it before I could know whether it worked or not)

I also use all kind of recursive stuff and haven't ever experienced any problem. Could you post an example so we can test it?
Hmm, it may be the version, some improvements or some "improvements". I never look at the code of DrScheme, but I think behind the scene it does memoization on longer(complex) calculations, no matter that - it should respect the memory limit you set to it.

In some situations one of the things when you get pay daily for the code you write is, that when you do code at work, you don't own that code. Anyway, bots + physics and you may find yourself in trouble with recursion.

---

### Post by CptPicard on 2009-11-24
> **grayrainbow said:**
> Anyway, bots + physics and you may find yourself in trouble with recursion.

And you're sure those really are tail calls? It's easy to slip in an additional function call that is not the recursive one that occupies the value position...

There is also the possibility of the code just producing a lot of frames to be garbage-collected, but that's just your regular "garbage"...

---

