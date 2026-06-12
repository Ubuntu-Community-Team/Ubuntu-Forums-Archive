---
title: "Prolog Multiple Return Expression"
date: 2009-01-16
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-01-16
I am trying to write a merge "function" (quotes). that can take two lists and return all the possible combinations of each other

I want results like this
```
merge([1, 2], [3, 4], X)
X = [1, 2, 3, 4]
X = [1, 2, 4, 3]
X = [1, 3, 4, 2]
...
...
```

I wrote this to start but only the first gets evaluated, as it should. but how do I get more results??

```
merge([H0], [H1|T1], [H0, H1|T1]).
merge([H0], [H1|T1], [H1, H0|T1]).
```

---

### Post by pp. on 2009-01-16
After Prolog has written the first solution, you request another solution by typing a semicolon, I believe. Prolog then writes the next solution or 'no' if there are no more solutions.

---

### Post by Q8harpoon on 2009-01-17
i spent some time tring to help you . i hope this is important :D

this code give you what you need but there is a small problem.
there is many rows come back again many times . 

i hope this could help you 

```

delete(X,[X|T],T).
delete(X,[Y|T],[Y|T1]):-
	delete(X,T,T1).

conc([],L,L).
conc([H1|T1] , L2 , [H1|T3]):-
	conc(T1,L2,T3).

merge1([],_,[]).
merge1(_,[],[]).
merge1(L1,Z):-
	member(H1,L1),
	delete(H1,L1,L4),
	delete(H1,Z,L4).

merge(L1,L2,Z):-
	conc(L1,L2,L3),
	member(X,L3),
	delete(X,L3,Y),
	merge1(Y,L),
	conc([X],L,Z).
```

---

