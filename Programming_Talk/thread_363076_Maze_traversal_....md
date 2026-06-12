---
title: "Maze traversal ..."
date: 2007-02-16
forum: Programming Talk
---

### Post by laxmanb on 2007-02-16
I need a algorithm to traverse a maze for a contest... the problem i'm having is that you can only change a function that returns whether to go left, right or straight...  i'm getting very frustrated trying to do this... You also have to avoid two ghosts...

here's my problem in it's entirety...
[http://www.dcetech.com/events/troika/bots_predefined.php](http://www.dcetech.com/events/troika/bots_predefined.php)

Your ideas on solving the problem are important... please do share them!! (It is a contest but i just need some ideas... )

---

### Post by Choad on 2007-02-16
google the a* path finding algorithm

---

### Post by laxmanb on 2007-02-16
Oh... i've tried using A* ... it's just hard to implement with this problem (the entire problem has been linked...) bcoz you have to build your matrice on the fly...

---

### Post by Wybiral on 2007-02-16
If you can read the maze, get the starting position and the ending position, then A* can be used. It's one of the most commonly used algorithms for this type of problem.

---

### Post by yaaarrrgg on 2007-02-16
If you don't know the start and end, the simplest thing would be to always turn left, when the opportunity presents itself, and of course to avoid monsters.  

To get better results, might experiment with a probablitic left turn (say 2/4 turn lefts, 1/4 turn righ, 1/4 straight), or fact in the number of left/right turns taken and passed.  Aside from actually running some experiments with actual algorithms, it's hard to say what the best would be.

---

### Post by hod139 on 2007-02-16
Try the  [D* lite]("http://portal.acm.org/citation.cfm?id=777092.777167&coll=portal&dl=ACM&CFID=15151515&CFTOKEN=6184618") algorithm.


**Edit:**  Wow, no responses in 2 hours to 3 responses at almost the same time.

---

