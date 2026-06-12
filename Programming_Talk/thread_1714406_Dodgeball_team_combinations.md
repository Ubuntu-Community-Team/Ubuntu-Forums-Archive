---
title: "Dodgeball team combinations"
date: 2011-03-25
forum: Programming Talk
---

### Post by drewsus on 2011-03-25
Hello all!
So, I was curious if anyone could point me to or help me out with a program to generate a list of possible combinations for a dodgeball team. 
I want to give everyone equal play time for 20 games. 
We have 4 girls and 8 guys and each line needs to have 2 girls and 4 guys (technically it is a min of 2 girls and 2 guys and any combination for the remaining 2 spots). 
It would be best if it could work with any number of people as we don't always get a full turn out. 
Thanks in advance for anything.
Drew

---

### Post by andrew1992 on 2011-03-25
Probably the easiest way to start going about this problem is to assume a set of rules for one team such that when you find a valid team, you know that the other team is valid as well.  For example, you have only 4 girls and need a minimum of 2 of each gender, so as you said each team would have to consist of 2 girls and four guys.  When you find a valid team, whatever players are left make up another valid team.  I would organize this by having an array of all the girls that show up, and another array for all the guys that show up.  Since the absolute minimum is 2/gender for each team, you need a minimum of 4/gender to show up or else you can't play. Otherwise, you can start finding combinations.  For a valid team, you will have several positions,

_  _  _  _  _  _  
g  g  b  b  b  b

and fill these positions in a systematic way, keeping track of combinations.

---

### Post by drewsus on 2011-03-26
The min of 4/gender is not true because if just 2 girls show up then they are just playing every time. 
Furthermore, we only fit in about 20 games per session, but if we have the entire team show up, thats 420 possible unique teams with 2 girls and 6 boys. How would I narrow that down to 20 teams equalising the amount of floor time for each player?

---

### Post by Zugzwang on 2011-03-26
Here is one generic way to do what you want: try to formalize your requirements to a valid solution into an [Integer linear programming]("http://en.wikipedia.org/wiki/Linear_programming") problem. If you succeed in doing so, you can use "lpsolve" from the repositories as backend, and write some kind of script that produces an ILP from your requirements.

In principle, "lpsolve" will only generate *one* possible solution to your problem (i.e., one valid matching). However, there might be a way to tell "lpsolve" to give you a list of all of them.

You might also want to have a look at "constraint programming", which is a research direction for finding generic solutions to problems like the one you have at hand. The guys working on that have so-called solvers which might also do the trick.

---

### Post by tgm4883 on 2011-03-26
Hmm, so you need some way to

A) Select which players showed up
B) Generate a schedule in that all users play the same amount of games (20)
C) Ensure balanced teams (X females on each a team)
D) Balance the game load for a player (Although it probably won't be an issue, I could see a schedule where someone didn't play the first 5 games then played the last 15, which probably isn't desired)

---

### Post by tingg on 2011-03-26
How about maintaining 2 queues? One for males, one for females. For each game, pop as many as you need for each side per game, and then add them back to the end of the queue.

This will work for any number of males/females, ensure that they're rotated, and ensure that they're balanced. Just make sure to pop in alternation for each team, per gender, etc. You could generate on a per game basis, or put the whole thing in a loop till you generate 20 games' worth of dodgeball teams.

---

