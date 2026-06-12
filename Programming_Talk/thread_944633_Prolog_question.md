---
title: "Prolog question"
date: 2008-10-11
forum: Programming Talk
---

### Post by babacan on 2008-10-11
Hey lads,
I have recently started learning prolog yet the syntax is pretty weird after common programming languages.

I am trying to achieve this very easy problem:

Assume I have 3 different kinds fruits such as:
```

apple(one).
orange(two).
cherry(three).

```
now I want to make such a function that checks if the input order is apple,orange,cherry. If so gives true but it something like orange,apple,cherry it should give false.

one,two,three should give true
two,three,one should give false
I tried this but doesnt seem to work :S
```

checkorder(X,Y,Z) =- apple(X),orange(Y),cherry(third).
```

OR this one didnt work aswell:

```
checkorder(X,Y,Z) =- apple(X) and orange(Y) and cherry(Z).
```

---

### Post by pp. on 2008-10-11
You are looking for a solution which is much too complicated.

Lacking more specifics about the problem, I would solve that as

```
proper_order([apple,orange,cherry]).
```
or, perhaps
```
proper_order(apple,orange,cherry).
```
depending on how you can get hold of your 'input'.

---

### Post by babacan on 2008-10-11
hello again,
Thanks for the input, It partially solves but not as whole.
I have tried ```
proper_order(apple,orange,cherry).
```

I want a function that consumes 3 inputs lets say X Y Z , checks it the object type of the input is in the order of : X as apple object, secondly Y as orange  and thirdly Z  as a cherry object.

Imagine I have made 5 "objects:

apple(appleone).
apple(appletwo).
orange(orangeone).
cherry(cherryone).
cherry(cherrytwo).

If I somehow do a such operation: proper_order(appletwo,orangeone,cherryone). -> should give me true but
proper_order(cherryone,cherrytwo,appleone). -> should be false

I am really newbie at prolog and thats why it is pretty hard for me to explain .

Regards

---

### Post by pp. on 2008-10-11
It's really quite difficult to tell where exactly your understanding of Prolog fails. I would rather suggest that you get hold of a good tutorial and follow its examples step by careful step.

However, your problem - as I understand it - could be solved by something like:

```
apple(appleone).
apple(appletwo).
orange(orangeone).
cherry(cherryone).
cherry(cherrytwo).

proper_order(A,B,C):- apple(A),orange(B),cherry(C).

```

you would invoke (call) your program by entering
```
proper_order(appletwo,orangeone,cherryone).
```
which would succeed (return 'true')
or 
```
proper_order(cherrytwo,orangeone,gaga).
```
Which would fail (return 'false') for several reasons.

---

### Post by pmasiar on 2008-10-11
> **babacan said:**
> Hey lads,
I have recently started learning prolog yet the syntax is pretty weird after common programming languages.

Syntax is very simple, semantics is very different - this is **exactly** why I recommend it. 8-)

Your example has no internal logic in it, that's why it does not make sense to you. Instead, as suggested above, follow some tutorial. 

Trivial use of Prolog would be to investigate family relationships, and you can ask meaningful questions about them. Try that instead.

---

### Post by CptPicard on 2008-10-11
> **pmasiar said:**
> 
Trivial use of Prolog would be to investigate family relationships, and you can ask meaningful questions about them. Try that instead.

Brings back to mind vivid memories of my professor's family-tree Prolog example, and during class I showed him that he was ignoring the brother-sister marriages that were also produced by the model... heh heh. Big win :)

---

### Post by hondacodonbk on 2009-02-19
hey,now I alse learn program with prolog,but I don`t how to install prolog (or prologEditor) in ubuntu,please help me
thank

---

### Post by sujoy on 2009-02-19
there is swi-prolog and gprolog that i know of.

---

### Post by hondacodonbk on 2009-02-19
yes,thank you,I installed it.but I don`t how to run a program ? I have a simple code:
```

giaithua(0,1).
giathua(N,KQ):- N1 is N - 1,giaithua(N1,KQ1),Kq is KQ1 * N.

```
So,how do you run it ?
thank for your help ! ^_^

---

### Post by hondacodonbk on 2009-02-23
ok,I runed it ! It is very easy ^_^

---

