---
title: "best version of scheme for self study of SICP in ubuntu"
date: 2009-12-29
forum: Programming Talk
---

### Post by badperson on 2009-12-29
Hi,
One of my new year's resolutions is to start working thru the SICP book, and I was doing some googling and saw a post reccomending (pretty emphatically) 
[http://www.gamedev.net/reference/articles/article1966.asp]("http://www.gamedev.net/reference/articles/article1966.asp")
against using Common Lisp. 

Has anyone else worked thru that book using ubuntu? I'd like to use it with emacs and would be interested to hear what setups people reccomend or have used. 
bp

---

### Post by CptPicard on 2009-12-29
Emacs and MIT/GNU Scheme *or* DrScheme (which is a PLT Scheme) for a fun and easy environment to play in... for SICP's purposes, both are good.

---

### Post by nvteighen on 2009-12-29
MIT/GNU Scheme. It's what they use in SICP and so you are guarranteed to not having to deal with implementation annoyances, as the SICP course will rely on non-standard Scheme stuff like cons-stream, for example, which is built-in MIT/GNU but available in PLT Scheme only as an extension you have to import manually (as "stream-cons").

On the other hand, PLT Scheme (i.e. DrScheme and MzScheme) is the best for real production as it 1) is updated to the last standard (which MIT/GNU is not and this new standard has incorporated lots of useful stuff) 2) contains lots of useful stuff for deploying code (a compiler capable of generating executable images, module-like importing, a Foreign Function Interface... MIT/GNU lacks all of this). The main drawback for PLT is lack of out-of-box Emacs support... though it seems there are ways to integrate it.

The other Scheme implementations are to be forgotten (at least the Free Software ones...).

So, I recommend you to use MIT/GNU Scheme for following SICP and then switching into PLT Scheme afterwards.

---

### Post by Axos on 2009-12-29
Holy cow. I used that book in college roughly 40 billion years ago. I just grabbed my copy off my bookshelf. Mine was printed in 1985. It's one of the few textbooks I didn't sell back to the book store.

Wow, maybe I'll download Scheme and work through the book again after all these years. Thanks for the memories!

---

### Post by badperson on 2009-12-29
I think I'll use the mit/gnu scheme then...is that in the repositories? (I'm away from my ubuntu machine)

I think if I were ever to write any production code, I would use Common Lisp...but my interest in SICP is really in upping my overall programming chops. 
thanks for the responses. 
bp

---

### Post by Axos on 2009-12-30
> **badperson said:**
> I think I'll use the mit/gnu scheme then...is that in the repositories?

On my 64-bit system I see only mit-scheme-doc but on my 32-bit system I see mit-scheme, mit-scheme-dbg, and mit-scheme-doc. I'm guessing that means there isn't a 64-bit version in the repository (well, at least not the default repositories). If you are using 32-bit Ubuntu, you are good to go. I'll have to look into building it from the portable C source.

---

### Post by CptPicard on 2009-12-30
> **badperson said:**
> 
I think if I were ever to write any production code, I would use Common Lisp...

Probably... but Scheme really has all the ideas already, and a very clear, minimalized design. One of the good things about knowing Scheme too is that at some point you are bound to want to write your own internal interpreter or something close to that (remarkably many problems can be cast as symbolic-manipulation-engine-writing: as soon as you start having evaluatable data structures inside your code, you're *very* close to having an interpreter) and then, understanding the functioning of "a Scheme" is very helpful.

@Axos, SICP is such a classic... some of us resident Lispers here try to introduce people to it as much as we can... ;)

---

### Post by badperson on 2009-12-30
I have 64 bit...so that's kind of a drag. I'll have to look around for a 64 bit version or figure out a way to use DrScheme if necessary. 

found this post...

[http://www.mail-archive.com/mit-scheme-devel@gnu.org/msg00527.html]("http://www.mail-archive.com/mit-scheme-devel@gnu.org/msg00527.html")

which indicates a new 64 bit release is in the works. 

You're saying DrScheme doesn't work in emacs? I'll read up on that, 
thanks. 
bp

---

### Post by nvteighen on 2009-12-30
> **badperson said:**
> 
You're saying DrScheme doesn't work in emacs? I'll read up on that, 
thanks. 
bp

DrScheme is something close to an IDE for PLT Scheme. It's not only an IDE, but that way you might get an idea.

PLT's MzScheme (the text-based interpreter for PLT Scheme) doesn't work with Emacs... at least in a clean way. You can of course set the Scheme interpreter to be MzScheme and get an instance of it running in Emacs, but you don't get any handy shortcuts to load files and debugging and such, like you get for MIT/GNU.

---

### Post by Axos on 2009-12-30
I had no problem building Scheme from the portable C source on my 64-bit system. Maybe there is some arcane thing which doesn't work but it works fine with the examples I've tried from the book.

Here are the instructions:

[http://www.gnu.org/software/mit-scheme/liarc-build.html](http://www.gnu.org/software/mit-scheme/liarc-build.html)

After the build completes, if you want to run it in place rather than installing it:

export MITSCHEME_LIBRARY_PATH=/foo/src/lib
/foo/src/microcode/scheme

...where "foo" stands for the entire path to the root of the build tree.

---

### Post by elibarzilay on 2009-12-30
> **nvteighen said:**
> PLT's MzScheme (the text-based interpreter for PLT Scheme) doesn't work with Emacs...

This is completely wrong.

---

### Post by elibarzilay on 2009-12-30
> **nvteighen said:**
> MIT/GNU Scheme. It's what they use in SICP and so you are guarranteed to not having to deal with implementation annoyances, as the SICP course will rely on non-standard Scheme stuff like cons-stream, for example, which is built-in MIT/GNU but available in PLT Scheme only as an extension you have to import manually (as "stream-cons").

Wrong.  SICP has parts that are not compatible with any Scheme implementation, including MIT Scheme.  In case anyone wants to go through SICP with PLT, there is a package at [http://www.neilvandyke.org/sicp-plt/](http://www.neilvandyke.org/sicp-plt/) that gives you everything you need -- even the picture language.__

---

### Post by nvteighen on 2009-12-31
> **elibarzilay said:**
> This is completely wrong.

Quoted that way, of course. But if you read the whole sentence, I said: "PLT's MzScheme (the text-based interpreter for PLT Scheme) doesn't work with Emacs... at least in a clean way. You can of course set the Scheme interpreter to be MzScheme and get an instance of it running in Emacs, but you don't get any handy shortcuts to load files and debugging and such, like you get for MIT/GNU."

There are packages like Quack that seek to integrate PLT Scheme into Emacs, but are quite a hassle and I'm not sure how scheme-mode actually responds to MzScheme loading systems, for example (-i, -f, and module-wise). 

> **elibarzilay said:**
> Wrong.  SICP has parts that are not compatible with any Scheme implementation, including MIT Scheme.  In case anyone wants to go through SICP with PLT, there is a package at [http://www.neilvandyke.org/sicp-plt/](http://www.neilvandyke.org/sicp-plt/) that gives you everything you need -- even the picture language.__

If you refer to those parts where "wishful thinking" is used, where the student is told that you've got "something that makes x", then well... yes... but there the idea is another one, either you implement it or just look at it as a theorical example (the best is option #1). But the language used in SICP is MIT(/GNU) Scheme, which is fully compatible with the course.

I wasn't aware of that PLT package, though. But it's a bit awkward to use a package for SICP. I'll take a look at it.

---

### Post by nvteighen on 2009-12-31
Errata: I found Quack in Debian's repositories (emacs-goodies-el package) and have to recognize I was mistaken about PLT Scheme integration with Emacs. Quack is an enhanced Scheme mode that not only makes PLT Scheme integrate better but all other implementations as well.

So, I've learned something new :)

---

### Post by elibarzilay on 2009-12-31
> **nvteighen said:**
> Quoted that way, of course. But if you read the whole sentence, I said: "PLT's MzScheme (the text-based interpreter for PLT Scheme) doesn't work with Emacs... at least in a clean way. You can of course set the Scheme interpreter to be MzScheme and get an instance of it running in Emacs, but you don't get any handy shortcuts to load files and debugging and such, like you get for MIT/GNU."

I've seen that, and it's still false -- even without quack.  MzScheme is a plain Scheme REPL, very similar to many others.  One difficulty that people complain about is the fact that MzScheme uses modules extensively -- but (a) this is true for many other implementations too; (b) there are solutions that allow you to deal with modules just fine.  The bottom line is that as far as stuff that is built-into Emacs, using MzScheme is just as easy as any other random implementation.

> **nvteighen said:**
> There are packages like Quack that seek to integrate PLT Scheme into Emacs, but are quite a hassle and I'm not sure how scheme-mode actually responds to MzScheme loading systems, for example (-i, -f, and module-wise).

Using -i is the default; -f is the (almost) same as running mzscheme and then using the load function; and for modules you can use `enter!' to go inside some module.  Also, see [http://barzilay.org/misc/interactive.ss](http://barzilay.org/misc/interactive.ss) for a package that gets you additional REPL tools.

> **nvteighen said:**
> If you refer to those parts where "wishful thinking" is used, where the student is told that you've got "something that makes x", then well... yes... but there the idea is another one, either you implement it or just look at it as a theorical example (the best is option #1).

If you're saying that there's some advantage in implementing it yourself then you can of course do that with any scheme with graphical capabilities.  But this thing *did* run in the past, and was used as part of the course.

> **nvteighen said:**
> But the language used in SICP is MIT(/GNU) Scheme, which is fully compatible with the course.

If you're talking about the MIT course, then JFYI, before it got killed for other reasons, it used PLT.  Have a look here: [http://sicp.ai.mit.edu/Spring-2007/SchemeImplementations/](http://sicp.ai.mit.edu/Spring-2007/SchemeImplementations/) and [http://sicp.ai.mit.edu/Spring-2007/generalinfo_st07.htm](http://sicp.ai.mit.edu/Spring-2007/generalinfo_st07.htm)

> **nvteighen said:**
> I wasn't aware of that PLT package, though. But it's a bit awkward to use a package for SICP. I'll take a look at it.

And the above links are from before this package existed.  With it, PLT has the most supported SICP-working environment.

---

### Post by nvteighen on 2009-12-31
> **elibarzilay said:**
> 
If you're talking about the MIT course, then JFYI, before it got killed for other reasons, it used PLT.  Have a look here: [http://sicp.ai.mit.edu/Spring-2007/SchemeImplementations/](http://sicp.ai.mit.edu/Spring-2007/SchemeImplementations/) and [http://sicp.ai.mit.edu/Spring-2007/generalinfo_st07.htm](http://sicp.ai.mit.edu/Spring-2007/generalinfo_st07.htm)

I was actually thinking in the SICP video lectures and I'm not sure why. Somehow I forgot about the the actual course :P But looking at the dates, I guess the SICP book (2nd edition being of 1996) didn't change to PLT.

Anyway, it seems I was wrong... :P Thanks for all the information!

Btw, am I mistaken in thinking you are the guy who wrote Swindle? If you are, I want to thank you for the great job you've done. Swindle has been a much nicer solution for my FreeTruco project (look at my sig, but don't expect spectacular code) than MIT/GNU SOS... well, actually the whole migration from MIT/GNU to PLT has been an improvement.

---

### Post by elibarzilay on 2009-12-31
> **nvteighen said:**
> I was actually thinking in the SICP video lectures and I'm not sure why. Somehow I forgot about the the actual course :P But looking at the dates, I guess the SICP book (2nd edition being of 1996) didn't change to PLT.

IIRC, the book doesn't mention any specific implementation...  (And when I took the course, we did it in SCM...)

> **nvteighen said:**
> 
Btw, am I mistaken in thinking you are the guy who wrote Swindle? If you are, I want to thank you for the great job you've done. Swindle has been a much nicer solution for my FreeTruco project (look at my sig, but don't expect spectacular code) than MIT/GNU SOS... well, actually the whole migration from MIT/GNU to PLT has been an improvement.

Yes, I wrote Swindle -- it's nice to know that it is still useful!

---

### Post by badperson on 2010-01-05
> **Axos said:**
> I had no problem building Scheme from the portable C source on my 64-bit system. Maybe there is some arcane thing which doesn't work but it works fine with the examples I've tried from the book.

Here are the instructions:

[http://www.gnu.org/software/mit-scheme/liarc-build.html](http://www.gnu.org/software/mit-scheme/liarc-build.html)

After the build completes, if you want to run it in place rather than installing it:

export MITSCHEME_LIBRARY_PATH=/foo/src/lib
/foo/src/microcode/scheme

...where "foo" stands for the entire path to the root of the build tree.

I followed these instructions and was able to install mit-scheme on my 64-bit amd setup. So, I should be good to go. Thanks so much for this link!
bp

---

### Post by element8 on 2010-06-27
just wanted to add this worked for me also, took about an hour to build, to run just type scheme in the terminal at the prompt after installing, > (quit) exits

thanks for the link!

---

