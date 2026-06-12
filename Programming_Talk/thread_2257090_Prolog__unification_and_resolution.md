---
title: "Prolog  unification and resolution"
date: 2014-12-16
forum: Programming Talk
---

### Post by skyUK on 2014-12-16
Hi all.
help pls. 
it is impossible to write a program.
2 months spent no result.
I'm new in the prologue.
----------------------------
you need to write a program to prove the truth, on the basis of unification and resolution.

[ATTACH]258649[/ATTACH]
predatory fish and not.
--------------------------
Here is the code of the program that I have tried to write, but does not work.
I need to know whether yavlyaetsya shark predatory fish


domains
 kind, q, z, y, yy = symbol
 
predicates
fish(kind)
eat_fish  (q)
not_eat_fish (z)
predatory(y)
not_predatory(yy)


clauses


predatory(X) :- fish(X), eat_fish(X).
not_predatory(X) :- fish(X), not_eat_fish(X).


fish(bersh).
fish(piranha).
fish(shark).




fish(common_bream).


eat_fish(bersh).
eat_fish(piranya).
eat_fish(acula).


not_eat_fish(common_bream).


goal
predatory (shark).

 UML diagram, painted look file  1121.zip



Please help:(:(   use visual prolog 5.2[ATTACH]258651[/ATTACH][ATTACH]258651[/ATTACH]

---

### Post by slickymaster on 2014-12-17
I'm closing this thread because while we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you.

---

