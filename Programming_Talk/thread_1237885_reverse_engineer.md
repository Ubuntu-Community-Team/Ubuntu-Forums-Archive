---
title: "reverse engineer"
date: 2009-08-11
forum: Programming Talk
---

### Post by Cardale on 2009-08-11
Are there any programs for reverse engineering in ubuntu or linux I can use? Resource hackers? Memory sniffers?

---

### Post by tgalati4 on 2009-08-11
man hexdump
apt-cache search hex

---

### Post by NathanB on 2009-08-11
Number One:  The subject is illegal in some countries, so we shouldn't talk about it here if we want to avoid a TOS violation.

Number Two:  In the F/OSS world, one shouldn't have a need for this activity because the 'source' is usually available.

That said, check out these:

[http://freshmeat.net/projects/edebugger](http://freshmeat.net/projects/edebugger)

[http://modest-proposals.com/Furball.htm](http://modest-proposals.com/Furball.htm)

---

### Post by NathanB on 2009-08-11
There is also things like this:

[http://www.porcupine.org/forensics/tct.html](http://www.porcupine.org/forensics/tct.html)

so, keep searching for interesting and educational tools:

[http://www.linux.org/apps/](http://www.linux.org/apps/)

[http://sourceforge.net/](http://sourceforge.net/)

[http://en.wikipedia.org/wiki/Assembly_language](http://en.wikipedia.org/wiki/Assembly_language)

It never hurts to understand how it all fits together.

---

### Post by Cyanidepoison on 2009-08-11
IDA works well in Crossover on OS X, so I'd imagine it works pretty well in Wine.

---

### Post by oomar on 2009-08-11
among having reverse engineering tools, Backtrack is a great tool for any type of computer auditing. I suggest you to check it out. if anything look at the list of programs.

---

### Post by slavik on 2009-08-12
for java, get the jdk.

sun java comes with: jmap, jstack, jstat - very powerful tools.
bea jrockit comes with: jrcmd (replaces all the above), jra, jrcmd
not sure what ibm has for their jdk.

look up jad for compiled java code ;)

regular processes:
dtrace (linux), strace (solaris)

---

