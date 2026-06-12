---
title: "Scheme - Where to start?"
date: 2009-11-01
forum: Programming Talk
---

### Post by SunSpyda on 2009-11-01
I was considering taking a look at the Scheme language. I have lightly dabbled in functional languages over time, including CL, so I thought I would take a look at Scheme, since many comment on its 'purity' & minimalism.

As it stands, I don't think it will become my practical functional language (F# has taken this position due to the fact I know .NET quite well, & .NET is very widespread & isn't going away anytime soon), but I just want to use it as a 'pure', educational functional language.

I Googled & spotted 2 Scheme implementations, GNU/MIT Scheme & PLT-Scheme. Which one should I get? Whilst portability isn't completely paramount, running on XP & Linux is a must.

So, can anyone push me in the right direction. I don't want any IDE stuff. Just a CLI compiler/interpreter & Vim will do me fine :)

---

### Post by terry_a_g on 2009-11-01
Brian Harvey of UC Berkeley Intro to Programming class lectures are available on Youtube.
He teaches the class using Berkeley Scheme, which is a fork of STk Scheme, but I don't see why you couldn't use any Scheme for the majority of the lectures.  I did a few of them with Guile and it worked fine.  I want to say he uses joe for an editor in the lectures, so you should be able to follow along easily with vi.

[http://www.youtube.com/user/UCBerkeley#g/c/6879A8466C44A5D5](http://www.youtube.com/user/UCBerkeley#g/c/6879A8466C44A5D5)

---

### Post by jimi_hendrix on 2009-11-01
Sicp

---

### Post by terry_a_g on 2009-11-01
Sicp, or Structure and Interpretation of Computer Programs is the textbook used for the class I linked.  Brian Harvey is mentioned in the acknowledgements.

It's available for free online at [http://mitpress.mit.edu/sicp/](http://mitpress.mit.edu/sicp/)

---

### Post by grayrainbow on 2009-11-02
I personaly realy like PLT, no matter that it is realy huge, come with compiler and a lot of variaties, but it's the fastest implementation i tryed. Since you know lisp you already know much of Scheme, so it won't be much hard to do basicaly everything, I guess :)

P.S. F#...well I honestly don't look at that language, but...there was stuff like J#, managed DirectX that nobody support anymore, but I guess it's ok for scripting over .NET

---

### Post by CptPicard on 2009-11-02
About the editors... Emacs really is very good for Lisp stuff, as you get better REPL integration (in particular in SLIME with CL, dunno about Scheme-modes). Using a raw REPL with an editor is potentially painful :)

---

### Post by SunSpyda on 2009-11-02
Wow, that's strange. When I first posted this, it didn't come up (And no, I wasn't viewing a cached page), and it didn't turn up in my 'Created Threads' section in my CP. I assumed it had been vaporised by a error. Now I found it again :p

I have got a few ebooks on it, including Sicp, and am now looking for a compiler/interpreter. Is PLT to main one?

Is there some sort of Scheme standard, or just different implementations?

This functional stuff is great - I learn something new everything I use it! I work out ingenious solutions to problems when I'm using functional languages far more than OO/structured counterparts. I like the way it forces you to *engineer* a solution from early stages in the coding (Which is good, as I have a bad 'shoot-from-the-hip', no planning, cross bridges when I get to them approach, which isn't so great for programming).

---

### Post by terry_a_g on 2009-11-02
The wikipedia entry on Scheme has more info than you probably care to know, but I'll answer another one of your questions.  Scheme has an IEEE standard as well as a defacto standard, which is currently R6RS.

---

### Post by nvteighen on 2009-11-02
Uf... Welcome to the Jungle!!

Ok, **all** Scheme implementations are totally suboptimal. MIT/GNU Scheme and PLT are maybe the most decent ones, but the issue is that the Scheme standard is that minimalist that a lot of regularly used procedures are implementation-dependent. In the end, you end up writing "MIT/GNU" or "PLT" as if they were different programming languages.

I use MIT/GNU because of better Emacs integration and because it's somewhat more balanced... though it's also very common to find yourself downloading its source code to get "documentation" (actually, the code itself) in order to understand how undocumented features like packages work (and packages are standard in CL).

PLT has a Scheme->C->native compiler, but I've never been able to make that work. I always end up compiling native code into a Lisp image in MIT/GNU (though I'd like it worked like SBCL, which creates self-executable Common Lisp images...).

---

### Post by SunSpyda on 2009-11-02
OK, thanks for all the info :)

How many functions are present with MIT/GNU? Just basic I/O functions, or more?

Another question... What exactly is Clojure? A Scheme implementation for the JVM, or a different Lisp language all together?

EDIT - How does Scheme compare with CL for learning good functional programming? I did a bit of CL, but as I said, I actually started doing functional programming properly with MS's OCaml rip-off for .NET, F#.

---

### Post by terry_a_g on 2009-11-02
Clojure is another descendent of Lisp like Common Lisp and Scheme.  Clojure is pretty awesome.  It's written by a working programmer to solve real world problems, especially ones related to concurrency. It also has great Java interoperability so you can use classes that are written in Java as well as call Clojure code from Java.  The only thing I don't like is that it doesn't optimize tail recursion because the jvm doesn't support it, but you can work around it.  Rich has some great videos posted on [http://clojure.org](http://clojure.org), and what I've read of Stuart Halloway's book Programming Clojure has been pretty good.
```
(def frame (new javax.swing.JFrame))
(. frame setSize 320 200)
(. frame setVisible true)
```or
```
(def frame javax.swing.JFrame.) ;Same as above, just different syntax
(doto frame
   (.setSize 320 200)
   (.setTitle "Hello World!")
   (.setVisible true))
```

---

### Post by terry_a_g on 2009-11-02
Sorry my previous post got mangled.  There's also a version of Clojure for the CLR which may be handy for you.  I haven't tested that personally though.

---

### Post by grayrainbow on 2009-11-03
When it comes to Scheme IDE like support I am really a 'fan' of PLT, but as regular emacs looser(pardon user) I also have variant of [http://www.neilvandyke.org/quack/](http://www.neilvandyke.org/quack/) on all my machines.
Btw, Scheme standard is really "simple" and tiny and that's the right thing IMO(everything that's not in the Scheme standard usually involve calling C functions regardless of the language you use, or implying unnecessary restrictions to programmer). Keeping Scheme tiny is one of the reasons that many people use it for sending whole programs over the network in "real" time.

P.S. [http://schemers.org/](http://schemers.org/) for a lot of stuff :)

---

