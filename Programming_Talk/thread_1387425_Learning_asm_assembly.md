---
title: "Learning asm assembly"
date: 2010-01-21
forum: Programming Talk
---

### Post by davidboy on 2010-01-21
Could someone point me to a good e-book or tutorial on learning asm assembly?  Thanks!

---

### Post by rCXer on 2010-01-21
[This](http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/www.artofasm.com/index.html) is one of my favorites.  [Here's](http://www.drpaulcarter.com/pcasm/index.php) another one.

---

### Post by caelestis2 on 2010-01-21
Perhaps ask the people over at the MASM forum, or look around for a tutorial over there. Quite a large userbase

I couldn't find suitable material for FASM so I gave up, especially on linux. Hope you don't give up
:(

---

### Post by Can+~ on 2010-01-22
I always suggest MIPS assembly due to the simple emulator.

[http://ubuntuforums.org/showpost.php?p=7944864&postcount=3](http://ubuntuforums.org/showpost.php?p=7944864&postcount=3)

---

### Post by Some Penguin on 2010-01-22
Yes.  Choice of architecture should probably be decided early.

RISC architectures like MIPS are arguably simpler to learn than CISC ones like IA32.  MIPS in particular has frequently been used at the university level for this reason.

If you're feeling particularly masochistic,  I suggest looking at the IA64 architecture.  I looked at a bit some time ago, and my impression was that it provided copious work opportunities for compiler authors.

---

### Post by caelestis2 on 2010-01-22
Wow, I just found some good material!

[http://savannah.nongnu.org/projects/pgubook/](http://savannah.nongnu.org/projects/pgubook/)

Just go to the download area. It uses GAS, the GNU assembler and is just what I wanted.

(You might want to use intel syntax though, because GAS uses AT&T which sucks. Type .intel_syntax noprefix at the top of your files)

---

### Post by rCXer on 2010-01-23
> **caelestis2 said:**
> Perhaps ask the people over at the MASM forum, or look around for a tutorial over there. Quite a large userbase

I couldn't find suitable material for FASM so I gave up, especially on linux. Hope you don't give up
:(

Hey, I use fasm all the time in ubuntu :p Unfortunately there are very no (few?) fasm tutorials for linux.  Did you try asking for help at the [fasm forum](http://board.flatassembler.net/index.php)?

---

### Post by NathanB on 2010-01-23
> **rCXer said:**
> Hey, I use fasm all the time in ubuntu :p Unfortunately there are very no (few?) fasm tutorials for linux.  Did you try asking for help at the [fasm forum](http://board.flatassembler.net/index.php)?

Really good point that you make.

Also, he could easily learn the L'unix-specific information via simply following the plentiful NASM-oriented material:  [http://asm.sourceforge.net/](http://asm.sourceforge.net/)

Since FASM syntax is very similar to NASM, any novice should be able to easily convert the example code to something digestible by FASM simply by referring to the friendly FASM manual.

---

### Post by Wistful on 2010-01-23
Assembly Language Step-by-Step: Programming with Linux (October 2009) :
[http://www.amazon.com/Assembly-Language-Step-Step-Programming/dp/0470497025/ref=dp_ob_title_bk](http://www.amazon.com/Assembly-Language-Step-Step-Programming/dp/0470497025/ref=dp_ob_title_bk)
Book's site : [http://www.duntemann.com/assembly.htm](http://www.duntemann.com/assembly.htm)
(this book is different from others in that will teach you not only HOW-to but also MORE IMPORTANT - WHY -, the first 3-4 chapters will teach you every aspect you must know before you go into the HOW things; It assumes that you are new to programming and assembly language is your first language) Quote: "Assembly programmers are the only programmers who can truly claim to be the masters, and that's a truth worth meditating on"

or The Art of Assembly Language, 2nd Edition which will be released in February 2010 -> [http://nostarch.com/assembly2.htm](http://nostarch.com/assembly2.htm)

or Guide to Assembly Language Programming in Linux : [http://www.amazon.com/Guide-Assembly-Language-Programming-Linux/dp/0387258973/ref=pd_sim_b_1](http://www.amazon.com/Guide-Assembly-Language-Programming-Linux/dp/0387258973/ref=pd_sim_b_1)

or Professional Assembly Language (Programmer to Programmer) [http://www.amazon.com/Professional-Assembly-Language-Programmer/dp/0764579010/ref=pd_sim_b_3](http://www.amazon.com/Professional-Assembly-Language-Programmer/dp/0764579010/ref=pd_sim_b_3)

or [http://www.google.com/search?q=x86+assembly&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=x86+assembly&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by mmix on 2010-01-24
[http://en.wikipedia.org/wiki/Assembly_language](http://en.wikipedia.org/wiki/Assembly_language)

&

AMD CPU manual

[http://developer.amd.com/documentation/guides/Pages/default.aspx](http://developer.amd.com/documentation/guides/Pages/default.aspx)


Please keep this in mind.
To understand primitive language, try to understand smallest part.

---

