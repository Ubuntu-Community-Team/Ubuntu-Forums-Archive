---
title: "Turned to the dark side..."
date: 2013-02-06
forum: Programming Talk
---

### Post by Mikeb85 on 2013-02-06
Or maybe the light side...

Been playing around with SBCL Common Lisp, Emacs and Slime, and I must say, it's been alot of fun.  I've read much about the virtues of Lisp and Emacs and while I'm not sure about the Kool-Aid, it is a pretty nice setup all around. 

Took me a little bit of time to set everything up and get things working, but after I realized where I went wrong (Quicklisp is my friend!), it's actually remarkably easy to set up.  

Anyone else hack on Common Lisp?  I'm not sure if it's particularly practical yet, but since I'm not a developer and never plan to be, I can waste time trying to build a personal project with it.  There are some really cool things people have put on Github, HH-Web is what I'm playing with, looks promising (though I'm not sure how it will stack up to things like Rails).

---

### Post by CptPicard on 2013-02-07
Glad you've seen the light, at least to some degree. ;)

SBCL in particular is a pretty awesome piece of software. With it, the distinction between interpreter and compiler doesn't really exist and you can just choose at which level of abstraction you want to operate on, and do that on live code, no less.

My own Lisp interests revolve around Clojure these days, but Common Lisp is certainly nice as well.

I would suggest though that you do not evaluate Lisp too much based on actual practicality in the real world (as in, versus Rails in web development); the lessons to be learned are deeper and more general in nature.

---

### Post by ofnuts on 2013-02-07
> **CptPicard said:**
> 
I would suggest though that you do not evaluate Lisp too much based on actual practicality in the real world [...] the lessons to be learned are deeper and more general in nature.
Hmm. So that means:

[LIST=1]
[*]Lisp isn't a language for practical programming
[*]It teaches you things nevertheless
[/LIST]
Drawing the necessary conclusions, either:

[LIST=1]
[*]The things Lisp teaches have no practical use, then why bother?
[*]They have a practical use, which implies they can be applied with a language more practical than Lisp, then why not use that one instead to learn things?
[/LIST]

---

### Post by CptPicard on 2013-02-07
> 
Lisp isn't a language for practical programming

This is because of practical reasons you'll have with most platforms that are not broadly used, plus maybe some Lisp-specific ones -- but I guess running in a self-contained Lisp image is rather comparable to the situation of needing a JVM for Java. With the difference that with Lisp you can actually mess with the code inside rather freely.

Sometimes I wonder what the world would be like if we were using Lisp machines instead of the kinds of architectures that took off (for very *pragmatic* reasons -- speed being the most important one).


> 
The things Lisp teaches have no practical use, then why bother?

Latin is not particularly useful in day to day life, why bother learning it if you're interested in languages?

Just knowing that Lisp is a Turing-complete language really is sufficient to me even if there was never a single GUI widget set binding written for it. And the situation isn't even that bad.

> They have a practical use, which implies they can be applied with a language more practical than Lisp, then why not use that one instead to learn things?


Because Lisp throws away all extra syntactic crud and such and is a very minimal language while still being very abstract. With the other languages you're bound to their way of doing and seeing things.

It's very telling that if you're interested in writing interpreters or compilers, doing a small Lisp implementation first is an educational good start.

---

### Post by Mikeb85 on 2013-02-07
> **CptPicard said:**
> Glad you've seen the light, at least to some degree. ;)

SBCL in particular is a pretty awesome piece of software. With it, the distinction between interpreter and compiler doesn't really exist and you can just choose at which level of abstraction you want to operate on, and do that on live code, no less.

My own Lisp interests revolve around Clojure these days, but Common Lisp is certainly nice as well.

I did play around with Clojure some too, it's nice, Leiningen is an awesome tool, if I fail at Common Lisp I'll probably do something in Clojure...

> **CptPicard said:**
> 
I would suggest though that you do not evaluate Lisp too much based on actual practicality in the real world (as in, versus Rails in web development); the lessons to be learned are deeper and more general in nature.

Well, in my particular situation (hacking on things in my spare time, mostly for fun) it doesn't have to be too practical.  Just practical enough to build something that works.  I'm not working with others, don't ever plan to (I'm taking Finance in University - don't plan on pursuing a job in software), just building a few random things for my own needs. 

One thing that I have found, is that even though there's less Lisp libraries and stuff in the wild than other languages, is that there's some incredibly ingenious Lisp stuff out there.  And people are doing some really cool things, generating code in other languages with Lisp, embedding Lisp, and of course then you have Clojure and Shen, which are both very cool.

---

### Post by CptPicard on 2013-02-07
> **Mikeb85 said:**
> is that there's some incredibly ingenious Lisp stuff out there.

Yeah, and that there are also some incredibly talented people working with Lisp -- and interestingly these are the guys who have a really insightful, big-picture kind of view of pretty much everything. How to conceptualize about the problem and how to do it "right" are their strong point. Personally I like playing with Lisp because it lets you get to the "idea" of what you're building so easily.

---

### Post by tgalati4 on 2013-02-07
Having taken 4 years of Latin in high school, I have yet to find anyone who speaks it today.  But I'm comfortable with the jargon in the law and medical communities that use Latin-based ideoms.  I dabbled with Lisp in the 80's.  It's interesting that it is still around (like X-Windows, now xorg).  It's really a foundation and framework that anyone serious in computer science should spend some time with.  

If you spent 4 years studying music in school, you may feel that is not useful, but the benefits will continue throughout your entire life.  Lisp is similar.  Not immediately useful, but the benefits last a lifetime.

---

### Post by ofnuts on 2013-02-07
> **tgalati4 said:**
> Having taken 4 years of Latin in high school, I have yet to find anyone who speaks it today.  But I'm comfortable with the jargon in the law and medical communities that use Latin-based ideoms.  I dabbled with Lisp in the 80's.  It's interesting that it is still around (like X-Windows, now xorg).  It's really a foundation and framework that anyone serious in computer science should spend some time with.  

If you spent 4 years studying music in school, you may feel that is not useful, but the benefits will continue throughout your entire life.  Lisp is similar.  Not immediately useful, but the benefits last a lifetime.My questions isn't about the music, but about the instrument you learn it on. If you can learn music with either a guitar or a theremin, which one would you pick?

---

### Post by tgalati4 on 2013-02-07
Playing a theremin would require more skill, but you can make more money playing guitar. :guitar:

---

### Post by Mikeb85 on 2013-02-07
Another thing I want to add is that I'm by any definition of the word, new to programming.  Never did CS, never took any courses, the extent of my programming experience is a little Visual Basic when I was 10 years old, and messing around with Ruby, OCaml, Clojure and Lisp in the last year.  

I must say though, I really like the simplicity of Lisp.  It really is simple, though with CL there's obviously alot of legacy functions built in which require learning.  But the lack of syntax, the ease of grouping together ideas and functions, and the flexibility is very appealing, especially as a newbie.

---

### Post by Odexios on 2013-02-07
> **ofnuts said:**
> My questions isn't about the music, but about the instrument you learn it on. If you can learn music with either a guitar or a theremin, which one would you pick?
Both, if I love music and not just playing a specific instrument. 

Especially if I'm a guitar player, learning the theremin will teach me a new way to approach music, and learning a new way to play is always a great advantage.

---

