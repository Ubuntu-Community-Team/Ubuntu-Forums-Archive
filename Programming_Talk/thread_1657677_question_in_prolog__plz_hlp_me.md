---
title: "question in prolog ?? plz hlp me"
date: 2011-01-01
forum: Programming Talk
---

### Post by hazem_world on 2011-01-01
sum([],0). 
sum([H|T],S) :- sum(T,X),S is X+H. 
mean([],0). 
mean(L,M) :- sum(L,S),length(L,L1),M is S/L1. 
:-arithmetic_function(mean/1). 
--------------------------------------- 
when i try mean([1,2,3,4],X). 
it replies with 
X= 2.5 
Yes 
/////////////////////////////////////////// 
Now I wanna Use ?- X is mean ([1,2,3,4]. 
but it repies with Type error: ERROR: '.'/2: Type error: `[]' expected, found `[2, 3, 4]' ("x" must hold one character) 
---------- 
How Can use arithmetic-function with a list ?? 
plz any one help me :(

---

