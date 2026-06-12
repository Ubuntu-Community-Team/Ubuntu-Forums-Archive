---
title: "Prolog question"
date: 2012-11-18
forum: Programming Talk
---

### Post by Ante2 on 2012-11-18
I need some help with a prolog question. Almost done with everything, just need help with a small pronlem.

Question is to make a cooking program. I have some ingredients at home, and some recipes. 
Database has the following information:

at_home([ingredient(rice,2), ingredient(water,10)]).

recipe(boiled_rice,[ingredient(rice,4),ingredient(salt,3),ingredient(water,5)]).
recipe(chicken,[ingredient(chicken,2),ingredient(salt,1),ingredient(pepper,1)]).
recipe(saltwater,[ingredient(salt,1),ingredient(water,3)]).
recipe(noodles, [ingredient(noodles,2)|I1]) :- recipe(saltwater,I1).

Question is:

Q1: Cook(X); should tell me what I can cook (from the recipes) from the ingredients I have at home.

Q2: Buy(X, L): should tell me the amount of ingregients I need to buy for dish X.

My solution: 

at_home([ingredient(rice,2), ingredient(water,10)]).

recipe(boiled_rice,[ingredient(rice,4),ingredient(salt,3),ingredient(water,5)]).
recipe(chicken,[ingredient(chicken,2),ingredient(salt,1),ingredient(pepper,1)]).
recipe(saltwater,[ingredient(salt,1),ingredient(water,3)]).
recipe(noodles, [ingredient(noodles,2)|I1]) :- recipe(saltwater,I1).

cook(X) :- at_home(YS), recipe(X,XS), check(XS,YS).

check([],_).
check([X|XS],YS) :- enough(X,YS), check(XS,YS).

enough(ingredient(V,T1),[ingredient(V,T2)|_]) :- T1 =< T2.
enough(I,[_|YS]) :- enough(I,YS).

buy(X, L) :- at_home(YS), recipe(X,XS), need(XS, YS, L).

need([], _, []).
need([X|XS], YS, L1) :- need(XS, YS, L), tobuy(X, YS, R), ( R = [], L1 = L, ! ; L1 = [R | L]).


tobuy(ingredient(V,T1), [], ingredient(V, T1)).

tobuy(ingredient(V, T1), [ingredient(V,T2)|_], R) :-
   !,    (T1>T2,    L is T1-T2,
   R = ingredient(V, L)
   ;
      R = [])
   .
tobuy(X, [ingredient(_,_)|TS], R) :- tobuy(X, TS, R).



Problem:

Q2 doesn’t work. It gives multiple answers for the same right. Example: 

3 ?- buy(X,L).
X = boiled_rice,
L = [ingredient(rice, 2), ingredient(salt, 3)] ;
X = boiled_rice,
L = [ingredient(salt, 3)] ;

If it requires more rice and salt to cook boiled_rice then it shouldn.t at the same time require only more salt. 

What have I done wrong?

---

