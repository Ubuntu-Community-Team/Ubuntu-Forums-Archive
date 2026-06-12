---
title: "Learning LISP"
date: 2009-06-28
forum: Programming Talk
---

### Post by JordyD on 2009-06-28
So I want to learn LISP. Unfortunately, I can't find any tools to do so. Not that there is a lack of them, in fact, my problem is that there are so many. I don't know what to use, mainly because I don't know what they are. I do a search for 'lisp' in the package manager and I see CMU, clisp, slime. I don't know the difference between any of them, and whenever I try to install one, it decides that I need EMACS installed as well. That's my second issue. Do I really need EMACS? I prefer Vim/GVim, and have become accustomed to it.

Any advice?

---

### Post by Modred on 2009-06-28
I've been a vim user for something approaching four years, and it's my default editor for almost everything, from plain text to C++ to Rails projects.  However, there are two things that I absolutely could not imagine without Emacs: LaTeX and LISP.  SLIME is a customized environment for developing LISP code, and it simply blows everything I've found for vim out of the water. (Although, if anyone has something similarly mature for vim, please share.)  Executing code in an editor buffer is so much more convenient than using the shell provided by your LISP implementation (most of them are horrible), and that's only the beginning of what SLIME does for you.  So yes, it's worth having Emacs+SLIME if you want to make the most of your time.

As for LISP implementations, there are dozens out there, but the ones I've stuck to most are GNU clisp and SBCL.  CMUCL would also be a good choice.  In general, most implementations will give you the complete standard language, and would be suitable for learning.  You'll start to find differences when moving into areas like GUI development, multithreading, and object orientation.

If you haven't found a good learning reference, I'd suggest [Practical Common Lisp](http://www.gigamonkeys.com/book/) ([http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/)), since it's a pretty good learning tool and available for no charge, to boot.

---

### Post by JordyD on 2009-06-28
> **Modred said:**
> I've been a vim user for something approaching four years, and it's my default editor for almost everything, from plain text to C++ to Rails projects.  However, there are two things that I absolutely could not imagine without Emacs: LaTeX and LISP.  SLIME is a customized environment for developing LISP code, and it simply blows everything I've found for vim out of the water. (Although, if anyone has something similarly mature for vim, please share.)  Executing code in an editor buffer is so much more convenient than using the shell provided by your LISP implementation (most of them are horrible), and that's only the beginning of what SLIME does for you.  So yes, it's worth having Emacs+SLIME if you want to make the most of your time.

As for LISP implementations, there are dozens out there, but the ones I've stuck to most are GNU clisp and SBCL.  CMUCL would also be a good choice.  In general, most implementations will give you the complete standard language, and would be suitable for learning.  You'll start to find differences when moving into areas like GUI development, multithreading, and object orientation.

If you haven't found a good learning reference, I'd suggest [Practical Common Lisp](http://www.gigamonkeys.com/book/) ([http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/)), since it's a pretty good learning tool and available for no charge, to boot.

Thanks! This helps. Thanks for the link, also. I hadn't looked for a tutorial yet since I hadn't installed any compilers yet, so it definitely helps.

I guess I'll be installing EMACS then. I have some basic knowledge in it, but I've always prefered the terser and less modifier-dependant vim commands. Eh, maybe after a while I'll like it.

I've also installed SLIME, but does it come with a LISP compiler? I believe LISP can be compiled, no? Should I be installing clisp or SBCL if I want to compile?

Thanks for the help.

---

### Post by CptPicard on 2009-06-29
> **JordyD said:**
> I have some basic knowledge in it, but I've always prefered the terser and less modifier-dependant vim commands. Eh, maybe after a while I'll like it.

The point is the "live editing" features with an extended REPL it gives you... coding Lisp is different from coding other languages where you edit source, pass it through compiler, execute, debug... in Lisp you work on stuff one function at a time, adding to what you have as you go along. You need a kind of "IDE" for proper working with the Lisp environment.

> 
I've also installed SLIME, but does it come with a LISP compiler?

SLIME is an Emacs extension. You need a Lisp system in addition of course... SBCL being my favourite.

> 
 I believe LISP can be compiled, no?

Yes, it can. The Lisp compiler is essentially just a provided function (and a major part) of a Lisp system, and what this does is that it takes the source of a Lisp function and turns that into native code that can then be run instead of interpreting the Lisp code. The latter can always still be done though. The native code then, in turn, calls among other things back into the Lisp system's runtime support code...

This results in interesting things you can do at runtime -- you can generate code on the fly and either interpret it or if you expect to run the code a lot, you can compile the dynamically generated code at runtime for subsequent speed...

> Should I be installing clisp or SBCL if I want to compile?

Definitely SBCL, its compiler is actually very good.

---

### Post by soltanis on 2009-06-29
I suggest SBCL. It's the best Common Lisp implementation I've seen, and supports the widest range of useful asdf packages. Oh and it comes with asdf installed.

btw SBCL compiles all code that you pass through it then executes it as machine code (including the code input in the basic REPL). But it doesn't compile in the same sense of producing a standalone executable file like you'd think with languages like C. Instead, you produce a lisp "core", basically a dump of the memory image with the entire state of the lisp interpreter (which can be loaded separately or I believe can also be made stand-alone), using the (save-lisp-and-die) function.

It's a pretty baller language. Good choice, man.

---

### Post by JordyD on 2009-06-29
Thank you. I've installed SBCL as well. And thanks to CptPicard for clearing some things up for me.

Although I don't know what 'baller' means, I imagine it's a good thing. :D

---

### Post by JordyD on 2009-06-29
Eh, I have a problem. This tutorial says that SLIME should be showing me the syntax of defun after I type in "(defun", but it's not. Plus it says when I type "(defun hello-world ()" and then enter, it should auto-indent. But again, it's not. I have SBCL installed, do I need to do something to get SLIME to detect it?

Again, thank you.

EDIT: When I type C-c C-c, it says, "Searching for program: no such file or directory, lisp"

EDIT: Never mind, I found the fix through Google.

---

### Post by Illuminatus- on 2010-11-11
> **Modred said:**
> However, there are two things that I absolutely could not imagine without Emacs: LaTeX and LISP.  

Not true for latex!! try to search for 'vim-latex' suite in synaptic.
Once u install it add the following lines to your ~/.vimrc

```
map <C-l> :w<CR>\ll<CR>\lv<CR>
map <C-k> :w<CR>:!pdflatex %<CR>:!evince *.pdf<CR>
```
This maps Ctrl-l to save and launch a dvi version of your tex file
Ctrl-k does the same thing but for a pdf version.

Hope it helps :)

---

### Post by mo.reina on 2010-11-11
i would suggest looking into [How to Design Programs]("http://www.htdp.org") and [SICP]("http://mitpress.mit.edu/sicp/") for learning resources.

HTDP uses the PLT implementation of lisp called Racket (formerly known as PLT Scheme), and Racket comes with an IDE of sorts called DrRacket (formerly known as DrScheme).

Someone on #racket over at freenode also suggested [Teach Yourself Scheme in Fixnum Days]("http://www.ccs.neu.edu/home/dorai/t-y-scheme/t-y-scheme.html") after going through SICP, they basically suggested the following progression:

HTDP
SICP
Teach Yourself Scheme in Fixnum Days

I actually started on SICP first, but have since put it on hold while I work through HTDP.  SICP requires some math background, probably wouldn't have been such a big deal if you do it right after High School or while you're in Uni.  I haven't touched some of the math concepts mentioned in SICP in years, so I've had to do some extensive googling.

---

