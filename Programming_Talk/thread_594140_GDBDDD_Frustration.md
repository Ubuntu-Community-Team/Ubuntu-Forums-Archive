---
title: "GDB/DDD Frustration"
date: 2007-10-27
forum: Programming Talk
---

### Post by Carl Hamlin on 2007-10-27
I am frustrated to *tears* with GDB/DDD.

Most of my work involves writing large amounts of assembly language, and I've been relying on the GDB/DDD combo to help me with the instances where the code doesn't do what I think it should.

However - it's *extremely* frustrating to use and I have found a number of times now that it's simply more cost effective for me to go back and rewrite my program from scratch than it is to puzzle out how to get the damned thing debugged using GDB and DDD.

First it doesn't want to run the program. Three or four tries into it, the program finally loads, but when I go to run it, GDB gets the arguments wrong. Then it hangs up trying to disassemble. And God help you if you're *relying* on debugging information.

Do any of you know of a debugging utility that makes more sense? I'm even willing to pay for the damned thing just to get away from GDB/DDD.

Anyone?

---

### Post by pmasiar on 2007-10-29
I am just curious what kind of job is it, if it is not secret: plain C is not good enough and it has to be ASM? I thought this kind of jobs went extinct in mid-90. :-)

---

### Post by Carl Hamlin on 2007-10-29
I'm an independent contractor with a background in embedded logic.

You're quite right; most of this work has dried up recently, but the US military still uses systems where my skillset is not quite obsolete, as well as many academic institutions.

---

### Post by NathanB on 2007-10-31
If you ever used DEBUG from the DOS days and you enjoyed it, here is something of a Linux clone:

[http://modest-proposals.com/Furball.htm](http://modest-proposals.com/Furball.htm)

Nathan.

---

### Post by j_g on 2007-10-31
Is the problem with GDB itself (ie, the debugger), or its frontend (ie, DDD)? If the latter, you should try Nemiver (if you're running a Gnome desktop) or Kdbg (if running KDE). Frankly, I found DDD to be rather buggy and unpredictable, so I use Nemiver.

---

### Post by Carl Hamlin on 2007-10-31
Nathan:

Something like DEBUG would be *perfect*! Thank you so much; I'll try that out right away!

j_g:

Never heard of Nemiver, but I'll be happy to give it a shot if I can find it. Thanks!

---

### Post by j_g on 2007-10-31
Nemiver is in the Ubuntu repository. Just run Synaptic, click on the Search button, and enter "Nemiver".

---

### Post by NathanB on 2007-11-03
> **Carl Hamlin said:**
> Nathan:

Something like DEBUG would be *perfect*! Thank you so much; I'll try that out right away!



I wouldn't wish GDB on my worst enemy!  :)  The GNU folk were "weird" in that they designed both (G)AS and GDB as backends and not intended to be used by a 'real' human.  IMHO, even the GUI frontends for GDB are horrible compared to what's available for that other OS (IDApro and OllyDbg).  I haven't tried it yet, but Evan's Debugger looks decent:

[http://freshmeat.net/projects/edebugger/](http://freshmeat.net/projects/edebugger/)

---

