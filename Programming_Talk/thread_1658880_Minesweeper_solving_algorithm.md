---
title: "Minesweeper solving algorithm"
date: 2011-01-03
forum: Programming Talk
---

### Post by n~kf)}BW% on 2011-01-03
Hello!

I'm interested in algorithms for solving non-trivial minesweeper field configurations such as:
(? marks an uncovered field)
```

Row 0 = |1|1|1|1|*|1| | | | |
Row 1 = |1|*|2|2|1|1| | | | |
Row 2 = |1|2|*|1| | | | | | |
Row 3 = | |1|1|1| | | | | | |
Row 4 = | | | | | | | |1|1|1|
Row 5 = | | | | | | | |2|*|2|
Row 6 = | | | |1|1|1| |2|*|2|
Row 7 = |1|1|1|2|*|1| |1|1|1|
Row 8 = |?|?|?|?|2|2|1|1| | |
Row 9 = |2|?|2|?|1|1|*|1| | |

```

There are several popular approaches to solve this: CSP (using constraints), subsets, brute-forcing all possible combinations, calculating possibilities...

What would you implement and why? Which is most reliable and rational? And if you understand CSP solving, please share some lines of the algorithm! :)

Thanks!!

---

### Post by trent.josephsen on 2011-01-03
For this particular problem?  Easy:  brute force.  You've only got 6 covered squares that can each be either a mine (1) or not (0); your solutions are therefore 0x0 through 0x3F -- only 64 possibilities.  If you add just the one constraint that there are 3 mines in the covered area, you can trivially narrow it down to just 10 without even looking at the accessory information provided by the numbers.

The ideal solution depends on the problem.  Brute force may work for small problems with only one possible solution (like this one), but it won't give you partial solutions (assuming they exist) without some extra magic.  It's impossible[1] to find the ideal solution for every problem, so which solution you settle on will be based on (a) an educated guess based on what you know of the algorithms and the problems, and (b) benchmarking the code to determine real-life performance.

[1] I wrote this without thinking it through, but upon reflection I think the problem of finding the ideal solution to some (solvable) problem reduces to the halting problem or an equivalent.  There's probably a theorem or something out there that says what I want to say better...

In any case, I'd probably implement the brute-force solution first.  There are three good reasons to do this:
1. To get a better understanding of the problems a solver algorithm is likely to encounter;
2. To understand and categorize the techniques humans use and the logic behind them; and
3. To get the framework and mundane details (input, output, notation, data structures, etc.) out of the way early so you can focus on solutions.

---

### Post by n~kf)}BW% on 2011-01-03
Thanks for your opinion!! :)

I found an article which explains solving minesweeper by testing all combinations and there is also a program written in LISP, which i cannot fully understand...

Could someone please try to explain this code part by part? Thanks...:)

Blog: [http://www.stephenlombardi.com/blog/?p=11]("http://www.stephenlombardi.com/blog/?p=11")

Program: [http://stephenlombardi.com/minesweeper/minesweeper.lisp]("http://stephenlombardi.com/minesweeper/minesweeper.lisp")

---

### Post by Some Penguin on 2011-01-03
Hm, this is a fairly classic homework problem about constraint propagation.

---

### Post by trent.josephsen on 2011-01-03
> **Some Penguin said:**
> Hm, this is a fairly classic homework problem about constraint propagation.
Possibly, but the OP has shown preliminary research and has not asked us to do any work for him.  I think it's perfectly reasonable to ask for an explanation of the Lisp source, and within the forum guidelines to provide one.

I would be happy to do so myself, but unfortunately I don't understand Lisp.

---

### Post by AlphaLexman on 2011-01-03
I have played minesweeper many times, and it seems to me that EVERY time logic cannot truly determine between two squares, (usually in a corner) I ALWAYS hit the mine. Not 50% of the time as I would think! I seem to believe there is a 'cheat' on the computer side!

---

### Post by n~kf)}BW% on 2011-01-03
> **Some Penguin said:**
> Hm, this is a fairly classic homework problem about constraint propagation.

I'm not doing this for a homework. (I'm still in high-school and we don't get such homeworks unfortunately.) It is interesting that there are not many specific solver programs on the Internet, yet you say it's a common assignment.

> **AlphaLexman said:**
> I have played minesweeper many times, and it seems to me that EVERY time logic cannot truly determine between two squares, (usually in a corner) I ALWAYS hit the mine. Not 50% of the time as I would think! I seem to believe there is a 'cheat' on the computer side!

You can calculate probability of hitting a mine in every situation. There is no such conspiracy behind minesweeper ;)

I understand the basics of CSP, but implementing it in a program is way more difficult than understanding it, so I'm asking for some points/hints...

If you would like to read more about this, here are some papers describing the problem:

[http://www.clear.rice.edu/comp440/handouts/pa3.pdf]("http://www.clear.rice.edu/comp440/handouts/pa3.pdf")
[http://www.cs.us.es/cursos/ia1-2007/trabajos/trabajo-2/minesweeper-toronto.pdf]("http://www.cs.us.es/cursos/ia1-2007/trabajos/trabajo-2/minesweeper-toronto.pdf")

---

### Post by cyberslayer on 2011-01-03
> **slovenia said:**
> I understand the basics of CSP, but implementing it in a program is way more difficult than understanding it, so I'm asking for some points/hints...


An easy way to do it would be to reduce the CSP to a SAT instance and run the input through a SAT solver; although solving SAT is NP-complete, there are SAT solvers which are fast for instances that typically arise in practice.  Since minesweeper is also NP-complete, you can't really do any better in the worst case anyway.

You would probably also get better performance than a custom CSP algorithm since there are SAT solvers which have very finely tuned heuristics.  It would also be a good example of a CSP to SAT reduction.

---

### Post by n~kf)}BW% on 2011-03-06
How can i use the python-constraint ([http://labix.org/python-constraint](http://labix.org/python-constraint)) module to compare minesweeper constraints? Can somebody please help me translate this Ruby program to Python? Thanks...

[http://gecoder.rubyforge.org/examples/minesweeper.html](http://gecoder.rubyforge.org/examples/minesweeper.html)

---

