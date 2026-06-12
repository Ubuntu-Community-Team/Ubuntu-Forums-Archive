---
title: "[Python] A Tic-tac-toe &quot;engine&quot;"
date: 2008-08-19
forum: Programming Talk
---

### Post by nvteighen on 2008-08-19
Hi,

Just for practice, I have written a tic-tac-toe class in Python I wanted to share with you. I think it's nice enough because it's class-based and allows some basic customization by passing arguments to the __init__() method (size of the board... so you can have a sort of "connect-four") and number of players (and the symbols the players want to use). Of course, I also wrote an interface to the class to show how to use it in a very simple text interface Tic-tac-toe... But it should be easy to port it to a GUI or ncurses... or at least I suppose so :p

Any comment to improve it will be appreciated. Thanks!

---

### Post by dwhitney67 on 2008-08-19
I'm not much of Python developer, but I wonder if the check() function you wrote could be simplified?

I've attached a TTT game that I got from the book "Object Oriented Programming with C++ and OSF/Motif" from Douglas Young.  From the title, you can deduce that the code is written in C++, but I'm sure the concepts are very similar to that of Python.

One thing the author did was to create/define a table that indicated all of the possible win scenarios; and there are only 8 of them (for a 3x3 board).  If you picture the board as being rotatable (sp?) then the number of win scenarios makes sense.

P.S.  The game "engine" is in the file Board.C.

---

### Post by nvteighen on 2008-08-19
Yes, but the point is that this code could be used for boards bigger than 3x3. What I wrote are general rules that will work for nxn.

Anyway, thanks. I'll give it a look!

---

