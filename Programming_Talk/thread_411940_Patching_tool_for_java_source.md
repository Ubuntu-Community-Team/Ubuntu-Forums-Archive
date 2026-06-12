---
title: "Patching tool for java source"
date: 2007-04-17
forum: Programming Talk
---

### Post by Ramses de Norre on 2007-04-17
Does anyone know of a relatively simple, cross-platform tool for making and applying patches to java source files?
I'm asking because I'm in the middle of developing a fast growing software system together with someone and transferring the files over by mail starts getting annoying and inefficient.
Also, if I make changes to a source file and make a patch for it and at the same moment my teammate makes his own changes too and patches it, can we both apply the other one's patch and have both the same double-updated source file? Or is there another tool to achieve this? 
(btw, I know about svn but I hope there is something simpler that doesn't need a server that's always online)

---

### Post by MadMan2k on 2007-04-17
[http://en.wikipedia.org/wiki/Revision_control](http://en.wikipedia.org/wiki/Revision_control)

---

### Post by amohanty on 2007-04-18
> Does anyone know of a relatively simple, cross-platform tool for making and applying patches to java source files?
I'm asking because I'm in the middle of developing a fast growing software system together with someone and transferring the files over by mail starts getting annoying and inefficient.

**patch -p0 < patchfile** will work with cygwin on windows or gnuwin32.sf.net tools and linux.

> Also, if I make changes to a source file and make a patch for it and at the same moment my teammate makes his own changes too and patches it, can we both apply the other one's patch and have both the same double-updated source file? Or is there another tool to achieve this?
(btw, I know about svn but I hope there is something simpler that doesn't need a server that's always online)

As MadMan2k suggested there are lots of revision control system out there. However for most of them the bottleneck is merging the source. So for example if user U1 has a copy of file A and modifies it most source control systems will be able to merge the code in. However if user U1 and user U2 both have file A and U1 commits it first U2 will have to manually merge in the changes. Parallel merges are only implemented in high end version control systems if at all or bit-keeper :) So you may still be stuck with the merge issue even if you use patch or svn or cvs

ALso if you cannot afford to maintain a server online, try hunting for free svn or cvs hosts, there are quite a few of them out there.

HTH
AM

---

### Post by Ramses de Norre on 2007-04-18
Then how do bigger teams handle this problem? I can imagine that in for instance open source programming where several people work on the same source from totally different locations, you don't always know when another teammate is working on the code?
Are they restricted to modify only the piece of code they got responsibility over?

Sorry for my dumb questions but I'm working on my first project in a team (it's for college), and I don't have many possibilities to try stuff out because the deadline for the project is really coming near...

---

### Post by amohanty on 2007-04-18
Some use hosted facilities like bitkeeper [http://www.bkbits.net/](http://www.bkbits.net/)
I know clear case does parallel merges or some form of it.
There's a plugin for subversion that lets you do parallel merges. 

AM

---

### Post by Ramses de Norre on 2007-04-21
Thanks for the inputs, I'm reading up on svn now.

---

