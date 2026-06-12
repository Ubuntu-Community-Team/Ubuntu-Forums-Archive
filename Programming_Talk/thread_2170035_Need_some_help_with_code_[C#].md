---
title: "Need some help with code [C#]"
date: 2013-08-24
forum: Programming Talk
---

### Post by Ninja&gt;Master on 2013-08-24
Hi,
I am making a Tic Tac Toe game (you probably know what Tic Tac Toe is). Its fully complete however there is a bug/problem. It is that the CPU move isn't actually good. Its based on randomness (Random()). It first generates a random number then checks whether the field is empty or not and then places a mark there. This isn't actually good because you can win easily almost all the time. Also, there is a bug when you put a mark somewhere sometimes the CPU can remove your mark and put a mark there. I need help to improve the CPU's move function.

The source code: [Download]("http://db.tt/Rj2v1y6g") (Dropbox link)

There is a source file in it (among many) called 'Form1.cs' in it there is a function 'cpu_move()' which you may need to look into mainly as it handles the CPU's move.

(Also I wouldn't want to use LINQ because I am making it .NET 2.0 compatible)

Thanks in advance.

---

### Post by ofnuts on 2013-08-24
OK, so you have done the trivial part and now you want help with the only part of significant value?

Look here: [http://en.wikipedia.org/wiki/Tic-tac-toe](http://en.wikipedia.org/wiki/Tic-tac-toe)

---

### Post by r-senior on 2013-08-24
You can make an unbeatable computer opponent by following the strategy listed on Wikipedia:

[https://en.wikipedia.org/wiki/Tic-tac-toe#Strategy](https://en.wikipedia.org/wiki/Tic-tac-toe#Strategy)

You can work toward that in stages. For example, you must already have a function that checks if it's a winning game. If you iterate over your free squares looking for somewhere that you can place your mark to win, you have implemented step 1. You can use the same function to block the human opponent, which implements step 2. And so on.

How you do the predictive part is up to you. Maybe have a board that you can undo your trial moves. Or keep a board running in parallel for your calculations.

I haven't looked at your code.

---

