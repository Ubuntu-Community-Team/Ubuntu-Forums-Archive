---
title: "Beginning Programming Theory"
date: 2005-04-20
forum: Programming Talk
---

### Post by darthsabbath on 2005-04-20
Hi,

I'm looking into learning programming, and as you may have gathered, I have a question. ;-) 

No, it's not how to program or what language to learn.  I can learn a program's syntax, and I know that Python is pretty much the king of the noobs (from what little I've seen, Python = awesome).

My question, or rather, my request, is for some good resources on programming theory, for a beginner, such as algorithms, design, APIs, etc.  I've found numerous tutorials on "how to program," but they always seem to fall short on the theory end of things.  

One example I've found is Greg Perry's [Teach Yourself Beginning Programming in 24 Hours](http://www.amazon.com/exec/obidos/tg/detail/-/0672323079/qid=1114039903/sr=8-1/ref=sr_8_xs_ap_i1_xgl14/103-3044130-7942206?v=glance&s=books&n=507846).  It's mostly Windows related programming, but goes into several different languages, as well as some basic programming theory. 

However, it's very commercial in that it looks at programming from a strictly business standpoint.  

I hope I've been specific enough in this request, but if I need to elaborate, please let me know.

By the way, in reponse to a question I've seen on other "beginner" posts, what I want to with with programming is just learn as much as possible, from web programming to app design to scripting.  I'd like to start with a solid foundation that I can use to branch off in any direction I want. 

Yes, I ask for a lot. ;-)

Thanks,
Phil

---

### Post by DirtDawg on 2005-04-20
There's a great book called [How to think like a Computer scientist](http://www.ibiblio.org/obp/thinkCSpy/) , available both from the website(free) or in paper form. It's geared toward beginners and uses mostly Python for its examples. I highly recommend it.

---

### Post by jdonnell on 2005-04-20
There are many different tangets that "cs theory" can go it. 

Here are some good places to start:

The Mythical Man-Month
[Thinking in Java](http://64.78.49.204/)
[Thinking in Python](http://mindview.net/Books/TIPython) 
[URL=http://www.faqs.org/docs/artu/]The Art of Unix Programming
[/URL]

---

### Post by toojays on 2005-04-21
[The Structure and Interpretation of Computer Programs](http://mitpress.mit.edu/sicp/) (SICP) absolutely blew me away when I first read it. I recommend it to anyone who wants to be a good programmer.

[How to Design Programs](http://www.htdp.org/2003-09-26/) (HtDP) is also supposed to be quite good; it claims to cover most of the concepts from SICP, but with a more modern teaching style. I haven't read this one myself.

[The Art of Computer Programming](http://www.amazon.com/exec/obidos/tg/detail/-/0201485419/002-4335188-8481660?v=glance) (TAoCP) is the ultimate reference for someone who wants to learn the theory behind computer programming. I am glad to have this on my bookshelf, but it's pretty hard going.

I have to share with you my favourite quote about TAoCP: "It's always a pleasure when a problem is hard enough that you have to get the Knuths off the shelf. I find that merely opening one has a very useful terrorizing effect on computers." - Jonathan Laventhol

"The Mythical Man Month" is definitely worth reading, but it is much more about the practice of software engineering than it is about the theory of programming.

"How to Think Like a Computer Scientist" is also quite good, but it doesn't go as deep as SICP.

---

### Post by darthsabbath on 2005-04-21
Thanks for all the help!

I'll definitely look into some of these.  One question, though:  are these texts written for novices, or for experienced programmers?  

I will definitely check into some of them though.

Thank you once again!

Phil

---

### Post by darthsabbath on 2005-04-21
Hi, all,

While reviewing these books from MIT, I noticed they were done in Scheme.  Has anyone here done any work with this language?  From what I understand, it's a derivative of LISP, which I'm interested in for it's (claimed) elegance. 

Just curious on what others thoughts of Scheme are.

Phil

---

### Post by Tinwood on 2005-04-22
I think that a lot of people think that Scheme is basically a simplified Lisp, and I would generally agree. I learnt Scheme using the SICP book, and I'm now learning Lisp using Paul Graham's 'On Lisp' (which is really heavy going in my opinion, but that's just because the subject is **hard**!!).

I guess the things that stand out for me are:


[list=1]
[*]Lisp has more, bigger and standard libraries for everything.  Scheme is *smaller* (has a much smaller core language).
[*]Lisp has separate namespaces for variables and functions. e.g. (defun and (setq produce different namespaces. This has caught me out a few times!
[*]Scheme has continuations (i.e. call/cc). Continuations are amazingly powerful and amazingly hard to understand (until you do and then they are easy, although the syntax looks a little odd). They are similar (yet oh so different) to the *yield* statement in Python.
[/list]A (poor) example of the differences (in namespaces are):

[list]
[*]Lisp
[/list]```

(defun make-adder (x) (lambda (y) (+ x y)))
(setq add2 (make-adder 2))
(funcall add2 3)
=> 5

``` 

[list]
[*]Scheme
[/list]```

(define (make-adder x) (lambda (y) (+ x y)))
(define add2 (make-adder 2))
(add2 3)
=> 5

```

Here Lisp has to have the *funcall* to call the function that is pointed to by *add2*. Note that I'm sure that there is a very elegant way to re-implement my very simple example using Macros so that it would look like the Scheme (which I think is more elegant). In Lisp *add2* can be both a function and a variable, whereas in Scheme there can only be one thing called *add2*.

Personally, I really like both languages, but I do most of my stuff in Perl and Python!

Just my $0.02

Cheers
Alex.

---

### Post by darthsabbath on 2005-04-22
From the reading I've done, quite a few people (ESR, for instance) highly recommend learning LISP to REALLY learn how to program.

Again, I'm a newbie, and only know a little BASIC and Pascal, but I want to learn programming  to as deep a level as possible.

Would you recommend learning LISP and/or Scheme before, say Python or one of the C family?  Or save that for more advanced learning?

I guess what I'm curious about is, if I dove into LISP or Scheme now, what would I learn in comparision to say Python or C?  I do notice the Scheme books are used for MIT's beginner programming classes, so surely they know something about it. ;-)

Phil

---

### Post by toojays on 2005-04-24
I think you're really at the stage now where you have to stop procrastinating and just jump in somewhere. Whether you start with LISP, Scheme or Python, you can always pick up another one later.

If you want to learn programming to as deep a level as possible, you should aim be confident enough to use any of those languages.

If I could go back in time 10 years and teach myself programming, I would do it in this order:

1) Emacs Lisp
2) Scheme
3) Python
4) C
5) An assembly language
6) C (revisit this with new eyes after doing ASM)

---

### Post by jdonnell on 2005-04-24
[QUOTE=darthsabbath]
I guess what I'm curious about is, if I dove into LISP or Scheme now, what would I learn in comparision to say Python or C?  [/QUOTE]

I think you should think of something you'd like to create and create it. Which language you use first isn't as important, but I'd suggest python. The hardest and most important part of programming isn't using the language but developing the abstract structure of the code. This you can only learn through experience so just jump in and have fun :)

---

### Post by Urusai on 2005-04-25
All you need to know about CS:
1) All systems are incomplete (Godel), and
2) Not everything is computable (Turing).
Conclusion:  LALR(1) grammars are sufficient to write games, who cares.

---

### Post by darthsabbath on 2005-04-25
Thanks for all your help.

I think I'm going to give Python a go and probably Scheme on the side. 

This has been very enlightening... thanks!

Phil

---

### Post by Stormy Eyes on 2005-04-25
If you intend to do this for a living, **darthsabbath**, then here's a bit of practical advice: always get the requirements *in writing* and preferably signed. People tend to change their minds when it comes to features, and it helps to be able to hit people upside the head with the specification.

---

