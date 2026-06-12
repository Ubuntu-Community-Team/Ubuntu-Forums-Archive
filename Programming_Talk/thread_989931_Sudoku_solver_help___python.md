---
title: "Sudoku solver help   python"
date: 2008-11-22
forum: Programming Talk
---

### Post by Bodsda on 2008-11-22
Hi, I commute every day to work on the train and play sudoku puzzles to pass the time. But recently I haven't been able to complete any puzzles cause there getting harder. I want to write a program that first asks me to input the default numbers in sequence from left to right for each row.

That bit is simple but i have no idea how to do the rest -- i think i may need to have alot of lists, one for each row and one for each column.

Can anyone give some advice?

Thanks Bodsda

---

### Post by fiddler616 on 2008-11-22
IMHO, you might do better with an 81-unit long dictionary. Have the keys be the numerical position, and the values be the number that's in there.

---

### Post by Bodsda on 2008-11-22
ok, but then how would i use an 81-unit dictionary to solve sudoku? that only helps hold the values.

---

### Post by unutbu on 2008-11-22
Peter Norvig has written a sudoku solver in python.
Interestingly, it only took ~100 lines of code (including comments):
[http://norvig.com/sudoku.html](http://norvig.com/sudoku.html)

---

### Post by fiddler616 on 2008-11-22
It'd be kind of interesting if we turned it into another sysres/PycTacToe--host it on Launchpad and open it up to any Forumer who's interested...Just a thought.

---

### Post by Bodsda on 2008-11-22
That would be a good plan actually -- first though il have to get my head around that code and understand it :)

---

### Post by nvteighen on 2008-11-22
> **fiddler616 said:**
> It'd be kind of interesting if we turned it into another sysres/PycTacToe--host it on Launchpad and open it up to any Forumer who's interested...Just a thought.
Why not? But don't look at me! I'd be glad to contribute, but it'd be really interesting that someone else takes care of this.

---

### Post by fiddler616 on 2008-11-22
> **Bodsda said:**
> That would be a good plan actually -- first though il have to get my head around that code and understand it :)
Why do we have to clone Norvig's? We can do some algorithm-making ourselves...
Would you be willing to be the big cheese of it on Launchpad?

---

### Post by Mr.Macdonald on 2008-11-22
This is AI, Python is great for that because its very easy to use while so powerful.

you need to setup a board as a 2 dimesional array, 9*9

Fist you need to have an easy sudoku board, and go square by square (as a computer would, and try and solve it. Then do it again and again with different board until you start to solve soduku like a computer. step by step.

In Python you will want a class for the sudoku board. make functions like:
[INDENT]
getRowNeeded - gets needed in a row
getSSqrNeeded - gets needed in a small square
getColumnNeeded - gets needed in a column
placeAble - checks if you can place this value here (x, y, val) and if so then it does
[/INDENT]

First make you program work perfectly for easy boards, then try on medium. It will probably fail, then see what went wrong and fix that.

Make as many functions as possible (only if it is a commonly repeated task), test them and then make more. don't worry about speed, just get it to work.

I would suggest doing this alone, it will make you better, and it shouldn't be too hard. In  about 12 hours, I made a connect4 algorithm that is unbeatable (by my skill). It was fun and challenging, and above is the exact way that I made it. This will be very good for you!

---

