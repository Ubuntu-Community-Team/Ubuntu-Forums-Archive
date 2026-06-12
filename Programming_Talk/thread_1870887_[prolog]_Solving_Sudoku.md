---
title: "[prolog] Solving Sudoku"
date: 2011-10-28
forum: Programming Talk
---

### Post by ufis on 2011-10-28
For some time now (on and off) I have been coding a Sudoku solver in java. Right now it solves about 70% of all sudoku's I feed into it. I am busy implementing some of the more difficult techniques for solving sudoku.

Then a couple of days ago I was introduced to Prolog when someone showed it to me as a way to solve [Einstein's puzzle]("http://en.wikipedia.org/wiki/Zebra_Puzzle").

Now my question is: Could prolog be used to solve sudoku? Even if it is not the ideal language to use. Is coding a sudoku solver in prolog advisable as an exercise to learn prolog, or should I find some other problem to solve to use as learning prolog?

The aim is to learn prolog rather than implement a complete sudoku solver.

---

### Post by gsmanners on 2011-10-28
If it is possible to solve Sudoku with logic, then of course Prolog could. It lets you store and manipulate data. That's all you really need. It's just a question of what logic you use.

Whether it's good for learning, I don't know. Probably not. It would force you to learn it a lot more thoroughly than I did, though. :D

---

### Post by ofnuts on 2011-10-28
> **ufis said:**
> For some time now (on and off) I have been coding a Sudoku solver in java. Right now it solves about 70% of all sudoku's I feed into it. I am busy implementing some of the more difficult techniques for solving sudoku.

Then a couple of days ago I was introduced to Prolog when someone showed it to me as a way to solve [Einstein's puzzle]("http://en.wikipedia.org/wiki/Zebra_Puzzle").

Now my question is: Could prolog be used to solve sudoku? Even if it is not the ideal language to use. Is coding a sudoku solver in prolog advisable as an exercise to learn prolog, or should I find some other problem to solve to use as learning prolog?

The aim is to learn prolog rather than implement a complete sudoku solver.
It's not a bad problem to solve in Prolog (somehow a sudoku looks a bit like the ["eight queens puzzle"]("http://en.wikipedia.org/wiki/Eight_queens_puzzle") that is a great Prolog classic) but you have to "think Prolog", otherwise you'll just code a procedural solver in Prolog and that won't be a pretty sight.

---

