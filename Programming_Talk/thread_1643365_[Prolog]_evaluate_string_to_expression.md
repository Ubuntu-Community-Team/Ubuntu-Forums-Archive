---
title: "[Prolog] evaluate string to expression"
date: 2010-12-11
forum: Programming Talk
---

### Post by agnes on 2010-12-11
Prolog newbie here. I don't know if Prolog's actually popular at any place, but I have a simple question.

Is it possible in Prolog to have a function **evaluatefun** like
```
fun(Cm, Meters, Result) :-
	Result is Cm * Meters.

evaluatefun( (fun(arg1, arg2, Result)), 50, 10) :- ...
```

Where **(fun(arg1, arg2, Result)** (put as first parameter to **evaluatefun**) is actually passed as a string/constant - and then **fun** (the function itself) is evaluated with parameters 50 and 10 as first two parameters.

So **(fun(arg1, arg2, Result)** is a string/constant put as first parameter to **evaluatefun**, but the idea is to evaluate/call/run the passed string/constant ánd parameters, as the related existing function with parameters.

---

### Post by debsankha on 2010-12-11
**call** predicate is what you are asking for.
```

call(fun,10,2,Res).

```
will do the job.

---

### Post by agnes on 2010-12-12
Thanks, I have it working now with

```
costfun(Cm, Meters, Result) :-
	Result is Cm * Meters.

evaluatefun([Fun,[X, Y, Result]], A, B) :-
	call(Fun,A,B,Result).
```

```
?- evaluatefun([costfun,[Arg1,Arg2,Result]], 50, 10).
Result = 500.
```
 Although, now Fun does have to be passed as **[Fun,[X, Y, Result]]** instead of **(Fun,(X, Y, Result))**.

---

