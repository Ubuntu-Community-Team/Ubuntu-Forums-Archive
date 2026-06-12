---
title: "Prolog question"
date: 2012-04-01
forum: Programming Talk
---

### Post by casperdino on 2012-04-01
Hopefully some one can give me a hint about a query in Prolog.

I got a database as follows:
```

male(john).
male(steve).
male(peter).
male(bart).
male(jeff).

female(anne).
female(lisa).

born(john, 1944).
born(anne, 1944).
born(lisa, 1973).
born(steve, 1966).
born(peter, 1975).
born(bart, 2005).
born(jeff, 2007).

father(john, steve).
father(john, lisa).
father(john, peter).
father(steve, bart).
father(steve, jeff).

mother(anne, lisa).
```And some rules:

```
parent(X, Y) :- father(X, Y).
parent(X, Y) :- mother(X, Y).

sibling(X, Y) :- parent(C, X), parent(C, Y), \+ X=Y.

brother(X, Y) :- sibling(X, Y),  male(X).

** is_oldest_brother(X) :- ???**

```I need help with *is_oldest_brother(X)* ...

I'd like to query is_oldest_brother(steve) => True and is_oldest_brother(jeff) => False

/Casper

---

### Post by schauerlich on 2012-04-01
Hint: you could start by writing a predicate that succeeds only when the first person is older than the second. So:

```
?- older(lisa, steve).
false.

?- older(steve, lisa).
true ;
false.

?- older(steve, X).
X = lisa ;
X = peter ;
X = bart ;
X = jeff ;
false.

```

---

### Post by casperdino on 2012-04-02
I even managed to write one to find the oldest:

```
oldest([X], X).
oldest([B1, B2 | L], M) :- born(B1, A1), born(B2, A2), (A1 > A2), oldest([B2 | L], M).
oldest([B1, B2 | L], M) :- born(B1, A1), born(B2, A2),  (A2 >= A1), oldest([B1 | L], M).
```Maybe  could implement the rest of is_oldest_brother(X) as:

[LIST=1]
[*]check if X is male
[*]find all X's brothers
[*]remove any duplicates
[*]append X
[*]get the oldest brother
[*]compare it with X
[/LIST]

---

