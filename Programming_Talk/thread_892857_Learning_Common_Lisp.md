---
title: "Learning Common Lisp"
date: 2008-08-17
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-08-17
I decided that I wanted to venture a bit into this 'mysterious' language. I've read the sticky (many times, in fact), and LaRoza's wiki helped a lot, but neither of those resources really had what I was looking for. After being linked to [Practical Common Lisp]("http://www.gigamonkeys.com/book/"), I came to the (hopefully) misconception that in order to hack Lisp, you must use emacs+slime as your editor. The book explained no other way, and I refuse to touch the monstrosity that calls itself 'emacs'.

What I want to know is if their is a more common way to hack lisp (gedit, geany), and how I compile/interpret it's code. Also, any further links on learning the language would be much appreciated. :)

---

### Post by Kadrus on 2008-08-17
I explained it here a couple of weeks ago,read my posts on how to use Lisp with Gedit,and I posted how to run Lisp code.
[http://ubuntuforums.org/showthread.php?p=5469679](http://ubuntuforums.org/showthread.php?p=5469679)
EDIT:
> Also, any further links on learning the language would be much appreciated.
Read the [Common Lisp Wiki]("http://www.cliki.net/index")as it links you to a lot of resources.

---

### Post by Alasdair on 2008-08-17
Why do you refuse to use Emacs? It's the best thing there is for lisp coding, at least try it for a while - you might end up liking it!

---

### Post by CptPicard on 2008-08-17
Coding "within the environment" is half the impressiveness of Lisp so yes you most certainly don't want to use a normal editor for this.

I have found the cusp plugin for Eclipse to be promising if you absolutely don't want Emacs, but... come on... :) Emacs rules.

---

### Post by badperson on 2008-08-17
> **CptPicard said:**
> Coding "within the environment" is half the impressiveness of Lisp so yes you most certainly don't want to use a normal editor for this.

I have found the cusp plugin for Eclipse to be promising if you absolutely don't want Emacs, but... come on... :) Emacs rules.

I'm just getting my feet wet with emacs, and the more I use it, the more I like it. I kind of like the old school vibe of it anyway, and your project of learning lisp sounds cool, I'd like to do that someday as well. 

there are some good tutorials for emacs, and once you learn the basic commands, it's pretty intuitive. 

good luck. 
bp

---

### Post by CptPicard on 2008-08-17
The reason why Emacs is such a lisper's editor is that ... actually, the application itself is an Emacs-Lisp application running on top of an Emacs-Lisp interpreter. If you know lisp, you can customize the editor.

---

### Post by squarepegg on 2009-12-01
(I don't understand why people feel limited to using programming environments.  It is entirely valid to learn and code in Lisp, or any other language, without one.)

That said..  Sinkingships7, it makes total sense that you would like to use an environment while learning Lisp.  It can be very helpful.  And I completely understand your frustration with Emacs.  I don't like it either.  

You can go with language non-specific CRiSP/Brief, which is recursively written, much like (but since before) Emacs, and is much much more powerfuly so.  (CRiSP is nearly an exact copy of Brief, which modern forms of Emacs and Vi try to emulate in the recursive sense.  Add in the mega-useful macros, and you'll never look back.  Promise.)  Or, if you want something Lisp-specific, you can go with CLISP.  (However, if you are doing some heavy-duty computation, I would go with CMUCL.)

Happy Lisping...

---

### Post by CptPicard on 2009-12-01
> **squarepegg said:**
> (I don't understand why people feel limited to using programming environments.  It is entirely valid to learn and code in Lisp, or any other language, without one.)

Lisp is a language that is very much intended to be programmed by writing code against a "live image". I have actually seen some people try write Lisp "offline" like they would write, say, C, and let me tell you, those are the people who choose willfully to be limited.

Implementations' raw REPLs are not really meant to be used directly, either. So... you want an editor with good integration to your Lisp implementation. And, yes, Emacs+SLIME is pretty much the best one, so it makes a lot of sense to use it.

In Lisp, more so than in any other language, it is far less valid to try to get around using a proper environment for your programming, unless you want to avoid the language's basic philosophy and/or are a masocist :)

> 
That said..  Sinkingships7, it makes total sense that you would like to use an environment while learning Lisp.

I am not sure what you suggest he uses, if not some kind of "environment" that allows for working with the system?

> 
You can go with language non-specific CRiSP/Brief, which is recursively written, much like (but since before) Emacs, and is much much more powerfuly so.

What does "recursively written" mean? Interesting that I've never actually heard of this editor...

> Or, if you want something Lisp-specific, you can go with CLISP.

CLISP is a Lisp implementation. He wants to learn Common Lisp. CLISP is not an editor...

> 
  (However, if you are doing some heavy-duty computation, I would go with CMUCL.)

The only implementation worth considering these days is SBCL. Its compiler is very good, too.

(EDIT: Oh yeah, this thread was remarkably old...)

---

### Post by squarepegg on 2009-12-01
> **CptPicard said:**
> 
What does "recursively written" mean?

it means it's written in itself.  very powerful.


> **CptPicard said:**
>  Interesting that I've never actually heard of this editor...


don't feel too bad.  most folks haven't.  you probably will soon enough though.


> **CptPicard said:**
>  (EDIT: Oh yeah, this thread was remarkably old...)

yep. sure is.

---

### Post by squarepegg on 2009-12-01
> **CptPicard said:**
> CLISP is a Lisp implementation. He wants to learn Common Lisp. CLISP is not an editor...

CLISP is an environment for the Common Lisp implementation.  It can be used alone or in-concert with other editors.

---

### Post by squarepegg on 2009-12-01
> **CptPicard said:**
> Lisp is a language that is very much intended to be programmed by writing code against a "live image". 

Lisp was originally intended as a notation and was largely based on lambda.  It, therefore, grew into something very useful for logical programming.  Which is why, yes, current implementations of Lisp are usually best utilized in an environment.  

However, Lisp definitely wan't always, or even usually, coded in a standard environment and does not have to be.  It certainly doesn't have to be coded in Emacs to be fully appreciated.

---

### Post by CptPicard on 2009-12-01
> **squarepegg said:**
> it means it's written in itself.  very powerful.

Interesting. Never heard of the term being used in that fashion. I guess you mean it is some sort of internal language engine in terms of which the editor is written, as in Emacs.

> 
don't feel too bad.  most folks haven't.  you probably will soon enough though.

Well, if I have not ever heard of it in my 10+ years of Linux-based hacking, it certainly has its work cut out, but I'm wishing it luck :)


> **squarepegg said:**
> CLISP is an environment for the Common Lisp implementation. It can be used alone or in-concert with other editors.

I believe there is some confusion between concepts here. CLISP is a Common Lisp implementation. Lisp, in itself, is a kind of self-contained "environment" by design (the currently running Lisp image). I am not aware that CLISP in itself would come with anything else than very basic editing support, which in itself is very inadequate for any kind of proper programming work, therefore, one pretty much needs a "proper" editor.

And when you need that, you'd much prefer it to integrate well to your Lisp runtime...

> **squarepegg said:**
> Lisp was originally intended as a notation and was largely based on lambda. 

... *calculus*.

Yes, it was a pencil-and-paper language originally. You can also write C without a compiler, but mostly you don't. I do believe we're talking about real-life programming no? :)

> It, therefore, grew into something very useful for logical programming.

Lisp is more of a general-purpose language with functional-programming concepts added. "Logic programming" refers more to Prolog-style declarative languages.

> Which is why, yes, current implementations of Lisp are usually best utilized in an environment.

I don't understand the reasoning. Implementations of Lisp have pretty much since the beginning been interactive, which is one of the language's important features usage-wise. It has nothing to do with lambda calculus, but it just how implementations behave.

I suspect you mean the interactive Lisp image of the Lisp system by "environment"... yes, you can technically code Lisp by using the traditional edit-run-cycle by reloading the entire Lisp mechanism for each run, but why on Earth would anyone voluntarily do that unless they are a bit clueless as to what the possibilities of Lisp are in this regard?

> 
However, Lisp definitely wan't always, or even usually, coded in a standard environment and does not have to be.

See above. I am also not making any claims regarding a "standard" environment.

> 
  It certainly doesn't have to be coded in Emacs to be fully appreciated.

No, it does not have to be Emacs, but the combination of Emacs and SLIME is currently very good, if not the best. Another option is Eclipse with the cusp plugin.

But, if one is going to abandon the live-editing nature of Lisp, then one certainly is not appreciating Lisp fully.

---

### Post by squarepegg on 2009-12-01
> **CptPicard said:**
> I guess you mean it is some sort of internal language engine in terms of which the editor is written, as in Emacs.

Emacs was designed to emulate that, and many other, aspect(s) of Brief, yes.  In an earlier post, you referred to that feature of Emacs, saying that is one of many reasons you use it.  I am on some downtime here and there this afternoon and was looking through some unsolved threads.  I saw your post and thought I'd be helpful and point out its much more powerful predecessor, in case people might find that information useful.


> **CptPicard said:**
> Well, if I have not ever heard of it in my 10+ years of Linux-based hacking, it certainly has its work cut out, but I'm wishing it luck 

It sounds like you and I are experienced hackers who "grew up" in different programming cultures, with different ways of describing things.  My Unix-like experience reaches back about twenty years, and my programming about thirty.  So maybe I am just a tired old dinosaur using outdated metaphors.  

In any case, that old editor to which I refer is a lost gem.  It seems that you haven't heard of it because you haven't been around long enough to have used it.  It was resurrected by a for-profit company pretty recently.  People (especially Linux-users) are starting to rediscover it.  It's really too bad it's not an open project.

---

### Post by squarepegg on 2009-12-01
> **CptPicard said:**
> Lisp is more of a general-purpose language with functional-programming concepts added. "Logic programming" refers more to Prolog-style declarative languages.

Logic programming is a paradigm, not a language.  But, yes, logic programming generally calls to mind Prolog, since that became a favored language at one point.

---

### Post by nvteighen on 2009-12-01
Nice discussion. :)

I think all languages deserve a sane environment to work with. The thing is that Lisp environments (Emacs+SLIME for Common Lisp, DrScheme for Scheme... or something I've heard about called Quack, that seems to be a SLIME for Scheme if I'm not wrongly informed) are really powerful and help you to have your work done in a very suitable way for Lisp.

Usual IDEs, instead, seem to be stuck on a weird level... They're useful, but they always bring the issue (refer to these forums) of hiding relevant aspects to the user... In the end, if you use an IDE you should also be prepared to manually fix the automated tasks. Also, the tasks that are automated are actually fairly basic ones: compilation/execution, reasonable debugging tools, autocompletion, object inspection, GUI building... which are all tasks meant to aid the coding process but externally to the language. SLIME, true to the Lisp traditions, does all that from the language itself... it somehow doesn't get in the way, it just changes the way you work...

I'm not sure if I'm being clear and scientifical as usually I am, but I've got the intuition that working with those Lisp-based environments is really different to other IDEs (even IDEs meant for dynamic languages like Python... Emacs+python-mode.el+ipython isn't the same as Emacs+SLIME)

---

### Post by sam191 on 2009-12-01
> **CptPicard said:**
> The reason why Emacs is such a lisper's editor is that ... actually, the application itself is an Emacs-Lisp application running on top of an Emacs-Lisp interpreter. If you know lisp, you can customize the editor.

I know of one particular lisper who uses Vi ;)

In fact, if it wasn't for him, I probably wouldn't even know about Lisp.

---

### Post by Arndt on 2009-12-02
> **squarepegg said:**
> Emacs was designed to emulate that, and many other, aspect(s) of Brief, yes.  In an earlier post, you referred to that feature of Emacs, saying that is one of many reasons you use it.  I am on some downtime here and there this afternoon and was looking through some unsolved threads.  I saw your post and thought I'd be helpful and point out its much more powerful predecessor, in case people might find that information useful.



Are you talking about TECO Emacs or elisp (GNU) Emacs here?

I have heard Brief mentioned, but never seen it.

---

### Post by Sinkingships7 on 2009-12-02
Wow. Feels weird to have my old thread brought back up a year later.

Emacs really is the best editor to go about learning CL with, but if I remember correctly, I didn't follow through with it too much. I believe I ended up learning Scheme via DrScheme and SICP. If you're after the experience, knowledge, and "enlightenment" that LISP brings, instead of the practical use part, I suggest you go this route as well.

("You" in this post refers to some future reader who finds this thread while searching for answers.)

---

### Post by CptPicard on 2009-12-02
> **squarepegg said:**
> In any case, that old editor to which I refer is a lost gem.  It seems that you haven't heard of it because you haven't been around long enough to have used it.  It was resurrected by a for-profit company pretty recently.  People (especially Linux-users) are starting to rediscover it.  It's really too bad it's not an open project.

Yes, I suspected as much that it is some very old piece of software... I'm afraid non-open projects do not really have much of a future in the Linux world these days, especially when it comes to editors -- competition from the vi-emacs front (and all the rest) is heavy enough. While it is not readily available as a distribution package it will at least be a rather marginal choice for the OP's purposes...

And regarding prolog... yes logic programming is a paradigm, but Lisp is not a declarative predicate-satisfaction language ... :) although "a prolog" can be written in terms of Lisp of course.

---

### Post by nvteighen on 2009-12-02
> **CptPicard said:**
> 
And regarding prolog... yes logic programming is a paradigm, but Lisp is not a declarative predicate-satisfaction language ... :) although "a prolog" can be written in terms of Lisp of course.

As SICP videos show :)

---

### Post by terry_a_g on 2009-12-03
> **squarepegg said:**
> Emacs was designed to emulate that, and many other, aspect(s) of Brief, yes.
Considering Emacs was written before Brief, I doubt it was designed to emulate Brief.

---

### Post by nvteighen on 2009-12-03
> **terry_a_g said:**
> Considering Emacs was written before Brief, I doubt it was designed to emulate Brief.

That's right.

The whole Emacs story is a complicated one... If you refer to the "Emacs-concept" (a text editor which actually works and is implemented on top of an interpreter and its extended through that interpreter), then Brief is **posterior**. The first Steele-Stallmann Emacs was born in 1976, the one based off MIT TECO; GNU Emacs was born in 1986 because of the licensing issue with Gossling Emacs (the first UNIX Emacs) (See [http://en.wikipedia.org/wiki/Emacs](http://en.wikipedia.org/wiki/Emacs)).

Brief is just earlier to GNU Emacs, but not to Emacs.

---

