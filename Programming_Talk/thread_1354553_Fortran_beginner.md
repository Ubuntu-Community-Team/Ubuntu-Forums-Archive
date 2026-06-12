---
title: "Fortran beginner"
date: 2009-12-14
forum: Programming Talk
---

### Post by Mezog on 2009-12-14
Hey everyone I was just want to know if FORTRAN would be a good first language to start with and if so where to start?

I also have another question about what is the most popular version of FORTRAN?

---

### Post by resander on 2009-12-14
It depends, if you are into numerical analysis with matrices, eigenvalue problems, differential equations etc FORTRAN is probably the best choice. If not, pick C or Python.

---

### Post by Jonwenger on 2009-12-14
It depends on whether you want to start learning programming from scratch, mathematical and history based, or if you want to use a programming language that is more recent (python, c+, Java).

Here is a link to an explanation of FORTRAN:
[http://www.engin.umd.umich.edu/CIS/course.des/cis400/fortran/fortran.html]("http://www.engin.umd.umich.edu/CIS/course.des/cis400/fortran/fortran.html")

A recent version is FORTRAN 2003.

---

### Post by NewbuntuUser777 on 2009-12-14
No.  Learn python.

Then learn C+ or java.

Then learn scheme or fortran.

---

### Post by ibuclaw on 2009-12-14
Moved to PT.

---

### Post by keplerspeed on 2009-12-14
Fortan (95) was the first language I learnt, since it was the first language they taught us at Uni.

Python would be a much easier language to learn first, for example a print statement in python:
[php]print "Spam please"[/php]
However with Fortran:
[php]write (*,*) 'No Spam please'[/php]
Both Fortan and Python would be worth learning if you intend on doing any type of numerical analysis. Fortran will be faster than python by a long shot, however, as you can see above, Python is a very intuitive language.

---

### Post by TheStatsMan on 2009-12-14
Fortran works very well with Python. It is a good combination for numerical analysis. I would normally recommend to learn Python first and then learn Fortran when you need speed. Combining the languages could not be easier. The advantage of Fortran as an extension language over C/C++ is the simplicity of both the language and the ease at which it can be combined with Python. It is also easier to write efficient code when working with arrays.

---

### Post by kitten16 on 2009-12-14
Personally, I'd rather start with a language like Fortran 90/95/2003 (older than that doesn't optimize the use of computers today) and then learn Python, because (1) I think a less intuitive language forces good programming practices (ie. proper documentation, considering program efficiency in design, etc.) and (2) because I'm sentimental and like old things :P.

Although, I find that Fortran is rather intuitive as it is, especially since the later versions have made array manipulation much easier.  

Just a note, the most basic print statement in Fortran is actually

[PHP]print *, "Insert text here."[/PHP]

The latest is, indeed, Fortran 2003, but unless you're moving towards parallel computing, you can settle for Fortran 90/95.

The down side of Fortran and strength of Python in my opinion is imaging.  I'm currently using gnuplot and DISLIN for plotting, though you can use Python, as well.

---

### Post by jimi_hendrix on 2009-12-14
If your in to math/engineering (its big use), fortran might work well, otherwise learn something a little more widely used (C/Python/Ruby/other)

---

