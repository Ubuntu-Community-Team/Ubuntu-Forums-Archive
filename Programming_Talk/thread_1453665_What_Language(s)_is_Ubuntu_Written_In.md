---
title: "What Language(s) is Ubuntu Written In?"
date: 2010-04-13
forum: Programming Talk
---

### Post by asddf on 2010-04-13
Is Ubuntu pure Assembly or is there also some C++ in there?

Thanks

---

### Post by nmaster on 2010-04-13
gnome is written in C: [http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)
linux is written in C: [http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)

different higher level applications are written in different languages.

---

### Post by Simian Man on 2010-04-13
First off "Ubuntu" is just an amalgamation of software written by tons of different people/groups in tons of different languages.

There is *very little* assembly used anywhere because Linux works on lots of different architectures.  There is a lot of C used, but you can really find software written in just about any language.

---

### Post by skierkyles on 2010-04-13
Well, thousands of packages/applications make up the Ubuntu operating system. So it is not written in only 1 language.


But a few of the languages used in the standard install would be: C, C++(maby Im not sure), C#, and Python.

There are surely a few more that are slipping my memory.

---

### Post by shawnhcorey on 2010-04-13
Actually, Linux is written in Tiny C.  It is a simplified version of C which leaves out things not needed in Linux, like floating point numbers and printf.  On a virgin system, you write the Tiny C compiler in assembler, use it to compile Linux, boot Linux on the system, use it to compile the C compiler written in Tiny C, compile in the real C compiler using the Tiny C compiler, use that to compile the rest of the GNU utilities, then start loading and compiling applications.

---

### Post by grayrainbow on 2010-04-13
It was mention already but to summarize...
Standard Linux distro:
Linux - C
XOrg - C
Gnome/KDE - C/C++
gcc - C
GNU utils - C
drivers - C
...
And a LOT of config files and shell/other scripts(that's EXTREAMLY importand!)

---

### Post by phrostbyte on 2010-04-13
Gives you a general idea of the popularity of certain languages in FOSS as a whole:

[http://www.ohloh.net/languages?query=&sort=code](http://www.ohloh.net/languages?query=&sort=code)

---

