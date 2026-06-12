---
title: "AI for connect 4 in Scheme"
date: 2009-02-01
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-02-01
I am trying to write an AI for Connnect 4. I plan to use backtracking. But I don't know whether I should backtrack for every move or just until I have a path that lets me win.

If I try every move, then I will be able  to find the fasted way to win. But it might take too long. and be to processor intensive.

If I only try enough moves to ensure my win (all of the enemies moves and only the first few of mine). Then it will find it alot faster, but it will not be the smartest AI.

Another alternative, it to desend the tree of moves equally (desend all branches at same time), and quit when I find a way to win.


My concern is because I did this in Python along time ago and I tried backtracking all the possablities. This made it take an incredibly long time.

Please don't post code, just help with the concept. I want to learn!

---

### Post by mike_g on 2009-02-01
You might want to have a look at [alpha beta pruning](http://en.wikipedia.org/wiki/Alpha-beta_pruning) for optimising your search.

---

