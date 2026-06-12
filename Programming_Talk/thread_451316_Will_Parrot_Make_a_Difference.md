---
title: "Will Parrot Make a Difference?"
date: 2007-05-22
forum: Programming Talk
---

### Post by ankursethi on 2007-05-22
Parrot has been under development since forever. Let us for one moment presume that it actually comes out, then will compiling my Python/Perl programs to Parrot bytecode give me any significant speed boost? If anybody here has tried out Parrot then please answer.

Currently C# on Mono seems to be faster than Python. Will Parrot bring the execution time at par with Mono? BTW, can you compile to bytecode now or are you still forced to use that intermediate language?

GM

---

### Post by pmasiar on 2007-05-22
> **ankursethi said:**
> Parrot has been under development since forever. Let us for one moment presume that it actually comes out, then will compiling my Python/Perl programs to Parrot bytecode give me any significant speed boost?

Perl (formerly known as "ducttape of the internet") committed mortal sin: full rewrite. Mozilla almost died on that, perl might be less lucky - because it is not needed anymore. We have Python and Ruby which serve the same niche. Many former perlmonks are now snake charmers and see no reason to come back - I know I am not coming :-)

Python has own "kernel", PyPy: Python in (compilable subset of) Python, financed by EU. Parrot is hobby project  of Perl6 guys, who work in own free time. IMNSHO Python community does NOT count on Parrot at all - Python 3000 is coming 2008, on Google's time, and it is NOT full rewrite :-)

> Currently C# on Mono seems to be faster than Python. Will Parrot bring the execution time at par with Mono? 

Python has Pyrex and couple other compilers. Or even simpler, just recode 5% of bottleneck code as C library.

Or use PyPy subset - compilable, with minor restriction on syntax. Why you would want to use Mono?

---

### Post by ankursethi on 2007-05-23
Dang! It's really annoying when they break backwards compatibility (both Python 3 and Perl 6 are doing).

I know both Python and Perl and like them both. Python is for regular use but Perl is just something you **have** to know. It's a really eccentric but useful language.

Okay, will Python 3000 do something about speed?

---

### Post by pmasiar on 2007-05-23
> **ankursethi said:**
> It's really annoying when they break backwards compatibility (both Python 3 and Perl 6 are doing).

IMHO Python is breaking it in the smart way: 
- converting program solving 90% issues made available
- you can add many features from "future" versions by "from __future__ import xxx" trick, when and as is convenient for you.
- Py3K changes are not radical changes like perl6 - maybe that's why they are able to finish them in planned timeframe :-)

> but Perl is just something you **have** to know. It's a really eccentric but useful language.

Perl is special for me as first language I tried with dynamic "duck" typing. But I would not advise anyone to learn it now, unless project require it. It is too quirky, too excentric, too unforgiving for occasional user. Requires real devotion. For casual users in same application niche, better alternatives are Python or Ruby (minus Perl libraries of course - but they are matter of time).

Okay, will Python 3000 do something about speed?[/QUOTE]

Yes. Scientific calculations is big use case (has special python cenference), and speed was focus of couple sprints and projects with outside financing. Developers say that having PyPy (Python in Python) allows then experiment with more efficient implementations on big scale, instaed of making little optimizing changes here and there.

---

### Post by ankursethi on 2007-05-23
Actually I use 2 Python apps frequently - Deluge and Scribes. Both of them seem a bit on the slower side. Not really slow, but slow enough compared to other applications of the same size. On the other hand, Tomboy seems reasonably fast. That's why I asked about Parrot - whether apps compiled to Parrot bytecode running under the VM will be faster.

Anyway, for now I'm not concerned about speed. Let me do a few small projects first and then when I move on to bigger ones which require speed, I'll write them partly in C, as you said.

Thanks.

---

