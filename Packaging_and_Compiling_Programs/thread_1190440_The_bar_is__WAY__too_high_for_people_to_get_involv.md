---
title: "The bar is _WAY_ too high for people to get involved"
date: 2009-06-17
forum: Packaging and Compiling Programs
---

### Post by austin.lund on 2009-06-17
Probably the most liberating thing about FOSS is being able to have and utilise the source code.  Notice that there are two parts to this: a) *having* the source code, b) *utilising* the source code.

The current development model and packaging in Ubuntu (and Debian for that matter) does pretty good at part a) but woefully in part b).

Let me give an example. 

I would like to step through the execution of the program /bin/ls and possibly some of the libraries it calls.  (Seems like a pretty reasonable thing to do if you want to know how your system is working).  

What do I have to do now is:

* Figure out which package is responsible for my program and it's libraries (easy).
* Download and install debugging symbols for everything I want to debug (easy).
* Download and install the exact source with patches applied that was used to compile each of the components (fairly easy).
* Link the source code for each component into the debugger (hard).

Why should this last part be made so totally and utterly unworkable?  I can get a single file to appear, but as no directory information is present in the deugging symbols, I have to add literally hundreds of directories to the search path of the debugger!?!

The second part to this is the "GNU" philosophy.  Let's say I found a bug and it is a one line fix.  I go and report this to someone (probably a bug tracker) and I'm constantly told to as "check the latest git/svn" or whatever.  Basically the only way to do this would be to reroll the whole package and possibly break the entire test system.  

For a single line fix all of this combined (i.e. hard to step through meaningfully in debugger, difficult to check latest versions, in depth packaging knowledge essential) this is a lot of effort and I'm sure there are many people who would just give up. (i.e. the bar is too high).

So, how should the situation be?

a) It would be great if the debugging symbols and gdb worked together to figure out which source file is needed so you only need to point gdb to /usr/src and it can grab whatever file it needs.  

b) There should be a way of getting sources via a DVCS (or somehow getting the DVCS history) which adds the packaging as commits on top of the actual history which the upstream exports.  Gnome is now using git AFAIK.  It would be great if when you get the source code you could just pull down the latest from the gnome branch and rebase the packaging on top of it (or it somehow helps you with the packaging).  If I have a one line change, I can submit it up stream saying that I have tested with the current git and I can use the DVCS program to help me format the patch in exactly the right way.

Though there are clearly going to be other problems, these two things are I believe would alleviate many of the headaches that people who know how to program have to becoming contributors.  It would also give a closer relationship to upstreams, a comment that _always_ derivative distros such as ubuntu get bashed around the head with.  

Many bugs in launchpad are fixes which require < 10 lines of code.  I'll bet there are a lot of crashes which a single line changes.  It is these changes which can improve people's perceived "quality" of software and it would be a great shame to see the potential for people who could contribute these fixes not do so cause they don't want to spend time unnecessary learning how to create debian packages or adding paths to the debugger.

---

