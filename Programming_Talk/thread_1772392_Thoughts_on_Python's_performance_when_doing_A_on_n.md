---
title: "Thoughts on Python's performance when doing A* on n-puzzle"
date: 2011-05-31
forum: Programming Talk
---

### Post by skytreader on 2011-05-31
Hi. So, I've coded an n-puzzle solver through A* search using Python3. I also made it such that my program can generate random solvable instances of n-puzzle. Testing my program, however, I see that it takes too long when solving my randomly generated puzzles. My computer (laptop) overheats to the point of auto-shutdown.

There are two possibilities I can think of here:
[LIST=1]
[*]I got something wrong in my code that's why it takes too long. Or,
[*]Python isn't a very good choice for algorithms like this.
[/LIST]

To test, I hard-coded some puzzles (n=15) for it to solve and it solves perfectly (so I'm crossing my fingers that I can rule-out #1). It has solved puzzles up to a Manhattan Distance of 11 (haven't hard-coded anything further than that yet). The randomly generated puzzles that take ages to solve have size n=15 with Manhattan Distances ranging around 30, give or take.

Also, I've just cleaned the internals of my laptop so we can safely rule out dust bunnies here.

So, is this Python's problem? Do you think I may get better performance if I code it in Java?

---

### Post by TwoEars on 2011-05-31
Well, while you say that you've ruled out your algorithms, it could still be down to them. For example, there are various optimizations you may not be aware of. Chances are is that it's down to your algorithm. Of course, it would be faster in a different language such as C.

Now, there are several things you could do with your current code.
These are the two I suggest -
1) Re-implement the vital performance function in C, and include it using Cython/ctypes.
Or
2) Use a different implementation of Python. I suggest Pypy.

---

### Post by Vaphell on 2011-05-31
> So, is this Python's problem?
imho yes

> Do you think I may get better performance if I code it in Java?
yes
check out this page
[http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)
while individual tests don't tell the whole truth you can see that Python3 is consistently approx 30-40x slower than the fastest languages

---

### Post by DangerOnTheRanger on 2011-05-31
Slowdown due to language performance is *negligible *compared to algorithm speed.
A better algorithm will result in a significant speedup in your program, compared to implementing your A* solver in a faster language.

So, I'd recommend looking for a better algorithm, instead of re-implementing your app in another programming language.

P.S: If push comes to shove, try Cython. It compiles Python code to *straight C*. Psyco (a JIT compiler for Python) is another alternative.

---

### Post by Some Penguin on 2011-06-01
> 
To test, I hard-coded some puzzles (n=15) for it to solve and it solves perfectly (so I'm crossing my fingers that I can rule-out #1


Perfectly, as in you have produced a trace log tracking exactly every iteration that it's done and it's actually performing A*, or "perfect" only in that it gives a valid solution (which might be achieved even if, say, your algorithm is inefficiently duplicating computation)?

---

### Post by MadCow108 on 2011-06-01
if the program also runs in python 2.7 you can try out pypy.
pypy JIT compiles your python code (somewhat similar to what java does) making it considerably faster, but its still in development.
[http://pypy.org/](http://pypy.org/)

---

### Post by skytreader on 2011-06-07
> **Some Penguin said:**
> Perfectly, as in you have produced a trace log tracking exactly every iteration that it's done and it's actually performing A*, or "perfect" only in that it gives a valid solution (which might be achieved even if, say, your algorithm is inefficiently duplicating computation)?

First off, sorry for the late reply as I've been overwhelmed by other (not-so-personal) projects. Anyway, thanks for the feedback.

In reply to Some Penguin's question, I believe that, yes, it is performing A*[1].

And the way I understand it is

1) Make all the (four) possible moves on the puzzle.
2) Put them in a priority queue based on the value of the heuristic function on the resulting configuration. Lower value for the heuristic == higher priority in the queue[2].
3) Pop the configuration with the highest priority (i.e., lowest value for heuristic).
4) Continue doing this until either the queue is empty (no solution[3]) or you've reached the solved state.

> (which might be achieved even if, say, your algorithm is inefficiently duplicating computation)?

Before doing step 2 above, I check that the configuration I will enqueue is not yet enqueued. If that is what you mean by this, then I already have it covered.

[1] I'm self-studying AI techniques (like A*) so it might be prudent to take this to mean "A* works the way I understand it".

[2] My heuristic is (depth of search tree so far) + (Manhattan distance).

[3] I have code to check that the configuration is solvable in the first place, so I don't expect this to happen. I use the method from [http://www.cs.bham.ac.uk/~mdr/teaching/modules04/java2/TilesSolvability.html](http://www.cs.bham.ac.uk/~mdr/teaching/modules04/java2/TilesSolvability.html)

---

