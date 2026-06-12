---
title: "looking for a language with a simple syntax."
date: 2008-12-07
forum: Programming Talk
---

### Post by ThaDoctor99 on 2008-12-07
I am looking for something with a simple syntax, and not to many features free software, easy to learn and perhaps doing some extension work, does anybody in here know of such a language.


Greetings Denmark.

---

### Post by nvteighen on 2008-12-07
> **ThaDoctor99 said:**
> I am looking for something with a simple syntax, and not to many features free software, easy to learn and perhaps doing some extension work, does anybody in here know of such a language.


Greetings Denmark.
Scheme (a Lisp dialect).

You won't ever get easier syntax (except other Lisp dialects), it has almost no features (at least in "purist" implementations like MIT/GNU Scheme), the best implementations are Free Software and IIRC, it's used as extension language at the GIMP (via GNU Guile implementation).

EDIT: Yes, GIMP uses Scheme. It's called TinyScheme, used for Script-Fu scripting. (the other being Python-Fu)

---

### Post by Martin Witte on 2008-12-07
This thread is mentioned in the [stickies]("http://ubuntuforums.org/showthread.php?t=528134") of this forum

---

### Post by ThaDoctor99 on 2008-12-08
yeah well scheme could be a great one there- not as complicated as lisp, but as sofisticated either.
I kind of like perl, but that is not the most simple language to write or read in.
I might just try scheme

---

### Post by crazyfuturamanoob on 2008-12-08
Python. It's very easy.

---

### Post by nvteighen on 2008-12-08
> **ThaDoctor99 said:**
> yeah well scheme could be a great one there- not as complicated as lisp, but as sofisticated either.
I kind of like perl, but that is not the most simple language to write or read in.
I might just try scheme
Scheme is Lisp. :) (Did you mean "Common Lisp"?)

Perl is not that difficult if you have some programming experience... yes, it looks scary and you can do some really weird stuff with it ([like this]("http://99-bottles-of-beer.net/language-perl-737.html")... read the comments)... but forget that: it's a nice language and such experiments are just experiments. If interested look at [www.perl.org](www.perl.org)

---

### Post by cmay on 2008-12-08
> **ThaDoctor99 said:**
> 

Greetings Denmark.
<off topic>
hi. nice to see a Danish ubuntu user.  :)........ .  merry xmas. 
</off topic>

---

### Post by StOoZ on 2008-12-08
C++:guitar:

---

### Post by jworr on 2008-12-08
Python has simple and easy to learn syntax.  I highly recommend it.

---

### Post by mentallaxative on 2008-12-08
Lua has a fairly simple syntax, has only one complex data structure (tables), and is quite sparing on features. However, if you want to learn something with a little more reach, popularity and power, Python is good.

---

### Post by Asteroid Al on 2008-12-08
> **ThaDoctor99 said:**
> I am looking for something with a simple syntax, and not to many features free software, easy to learn and perhaps doing some extension work, does anybody in here know of such a language.


Perl is free, easy to learn and use, and (like any other language) you can use as many or as few features as you wish. It has the added benefit of having many user-written libraries.

What do you plan on programming? That might influence your decision.

---

### Post by fiddler616 on 2008-12-08
I'll confess, I don't know Perl...but I've read about it, and this is the first time in my entire life people-who-aren't-Slavik are saying positive things about it. Especially since a "simple syntax" is required.

In other news, +1 Python [Edit: Never mind], -1 C++, +? Scheme (I don't know enough about it to make an educated decision).
Why I edited out Python: As beautiful as the syntax is, and as great as it is to use, I don't think it qualifies as a "small language"
Edit: <off-topic>Whoa...new icons...I'm not sure I'm a fan...huh.</off-topic>

---

### Post by jimi_hendrix on 2008-12-08
BF or Ook!

---

### Post by mssever on 2008-12-08
> **jimi_hendrix said:**
> BF or Ook!
jimi_hendrix makes an important point, whether or not it was intentional. There are a number of esoteric languages that have very simple syntaxes. Brainf*** and Whitespace are two such examples. But doing useful stuff in those languages isn't quite so simple. The point is, that there's much more to selecting a language than syntax.

---

### Post by ThaDoctor99 on 2008-12-09
I am not looking for anything with a fancy syntax nothing python or perl ruby or any of those big languages, I am perhaps looking for a simple functional language.
Which simply has few functions and nothing to fancy there either something free software and rather simple in the source of it...

---

### Post by fiddler616 on 2008-12-09
> **ThaDoctor99 said:**
> I am not looking for anything with a fancy syntax nothing python or perl ruby or any of those big languages, I am perhaps looking for a simple functional language.
Which simply has few functions and nothing to fancy there either something free software and rather simple in the source of it...
As mssever touched on, you need to make a decision.
Do you want a language with an *easy* syntax? If so, Python is probably the way to go. Hello World! in it is merely:
[php]print "Hello World!"[/php]which is about as easy as it gets. And because of it's adherence to dynamic whitespace, and reasonable naming (for example "not" instead of "!") the rest of it is only slightly more complex.

Or do you want a *simple* syntax? If so, go for BF, ///, or pretty much any esoteric language. However, keep in mind that Brainf*** has its name for a reason.

---

### Post by fiddler616 on 2008-12-09
> **ThaDoctor99 said:**
> Which simply has few functions and nothing to fancy there either something free software and rather simple in the source of it...
Sorry, missed this point.
Just because a language *has* a large standard library doesn't mean you have to use it.
Also, you could make a lot of annoying arguments: such as saying "oh, for statements are worthless--why not just use while?"
(Since my area of expertise is Python, I'll use it as an example again.)
Compare:
[PHP]
for i in range(1, 10):
    print "Hello"[/PHP]
and
[PHP]
counter = 0
while counter < 10:
    counter += 1
    print "Hello"[/PHP]
The second is simpler--it minimizes the need to learn for. However, learning for is acutually a great timesaver. And if it *really* bugs you, you can just ignore it--just because it's there doesn't mean you have to use it.

---

### Post by mssever on 2008-12-09
> **ThaDoctor99 said:**
> I am not looking for anything with a fancy syntax nothing python or perl ruby or any of those big languages, I am perhaps looking for a simple functional language.
Which simply has few functions and nothing to fancy there either something free software and rather simple in the source of it...
It would help if you'd tell us what you're trying to accomplish (and why you don't want Python). The languages that come closest to the criteria you've stated are many of the esoteric languages (though I'm assuming that you don't really want one of those), Scheme, Smalltalk, or perhaps Haskell.

But honestly, there's so much more to a language than syntax. If you're trying to learn programming (I have to make assumptions until you explain why you're looking for such a language), choosing a language with straightforward semantics--such as Python or Ruby--will benefit you more than choosing based on syntax. There was a time when I thought that syntax was a crucial difference between languages, but I no longer think that. Other factors, such as semantics and library coverage, make a much bigger difference in the long run.

---

### Post by moberry on 2008-12-09
I would recommend python. Namely, because it has a very simple syntax at its basic level. It also has the characteristics and functionality of a modern object oriented programming language. The transition from Python to another main stream language would be easy because of the shared concepts.

I would not recommend something like Lisp or Scheme myself because those languages are simply not popular enough in modern programming to warrant it.

---

### Post by pmasiar on 2008-12-09
> **fiddler616 said:**
> I'll confess, I don't know Perl...but I've read about it, and this is the first time in my entire life people-who-aren't-Slavik are saying positive things about it. Especially since a "simple syntax" is required.

I am not sure if I get your point. Perl's syntax is anything, but not simple. There is difference between list and arrays when processed in scalar context - and whole concept of scalar vs non-scalar context: give me a break!

> Why I edited out Python: As beautiful as the syntax is, and as great as it is to use, I don't think it qualifies as a "small language"


Interesting: what **does** qualify as small then? Only something with no library and few basic constructs, like Turing machine? :twisted:

---

### Post by fiddler616 on 2008-12-09
> **pmasiar said:**
> I am not sure if I get your point. Perl's syntax is anything, but not simple. There is difference between list and arrays when processed in scalar context - and whole concept of scalar vs non-scalar context: give me a break!

Quite possibly I fail at communicating. I was expressing surprise that Perl was getting positive light thrown on it--since I've heard a LOT of bad things about it.

---

### Post by hessiess on 2008-12-09
<joke>
Whitespace, only uses space, tab and enter ;)
</joke>

More seriously: C, simpler than its often made out to be.

---

### Post by nvteighen on 2008-12-09
> **hessiess said:**
> <joke>
Whitespace, only uses space, tab and enter ;)
</joke>

More seriously: C, simpler than its often made out to be.
Careful: C is simple in design, but not in use.

Also keep in mind that OP wants a language to do extension development... I guess an interpreted language would suit that better.

---

### Post by mssever on 2008-12-09
> **nvteighen said:**
> Also keep in mind that OP wants a language to do extension development... I guess an interpreted language would suit that better.
Thanks for clearing that up. The sentence where the OP mentioned extensions is quite convoluted, and I didn't see that he/she appears to be considering extension development until I re-read the original post in response to your post.

If you and I are understanding things correctly, then that vastly changes the requirements for such a language. First, the system to be extended probably needs to embed an interpreter for the language. Then, the language should ideally be quite accessible and widely-known. I question whether Scheme meets those criteria. It sounds to me like an ideal task for Python, except the OP has already rejected Python.

I know that Lua is often used to script other programs, and Tcl might also work nicely. I don't know either language myself.

---

### Post by slavik on 2008-12-10
WoW plugins are written in Lua.
Pidgin plugins get the choise of Perl or Tcl.
GIMP works with Scheme and Python
Emacs is big on LISP

as for lists vs. arrays in Perl ... the're the same. I also like the difference between context (Perl6 adds explicit list and hash contexts which is awesome)

---

### Post by fiddler616 on 2008-12-10
Dia and Vim both let you use Python. (Not that Dia is the most commonly-used program in the world, but...)

---

### Post by nvteighen on 2008-12-10
> **mssever said:**
> Thanks for clearing that up. The sentence where the OP mentioned extensions is quite convoluted, and I didn't see that he/she appears to be considering extension development until I re-read the original post in response to your post.

Well, I play with some advantage, as I've been here since the beginning of the thread. :)

> (...) I question whether Scheme meets those criteria. It sounds to me like an ideal task for Python, except the OP has already rejected Python.

Well, Scheme may be an interesting way and also an intellectual challenge for OP. Of course, an extension Scheme is not the pure Scheme you get from the standalone implementations (read MIT/GNU Scheme, MIT Scheme48, PLT Scheme, etc.), but a spiced-up one capable of interfacing with the application's plugin API.

---

### Post by fiddler616 on 2008-12-17
Er, what happened, OP?

---

