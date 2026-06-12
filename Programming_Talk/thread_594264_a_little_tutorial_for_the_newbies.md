---
title: "a little tutorial for the newbies"
date: 2007-10-27
forum: Programming Talk
---

### Post by bribaetz on 2007-10-27
[my python tutorial]("http://ubuntuforums.org/showthread.php?t=593887")
ok to all newbie programmers and i am not saying that i am not one
this tutorial is to help you get started.
[LIST=1]
[*]getting started
[*]choosing a language
[*]finding a good tutorial
[*]putting yourself in the community
[/LIST]
[SIZE="5"]getting started[/SIZE]
ok getting started it easy all you need is a compiler and a idea of what language  you want.
you might consider getting the geany ide it auto indents and has about 20 different language it can be an ide for and all you have to do is get a compiler.
 also you want to get to know Ubuntu and the terminal  there are plenty of tutorials for those around.
[SIZE="5"]picking a language [/SIZE]
you will want to find a good language 
here are some good ones for beginners[LIST]
[*]python
[*]ruby
[*]perl
[*]pascal (i know it is old but good anyway in my opinion)
[*]C++ (its not all that hard in my expieriance)
[/LIST]
these are all good
[SIZE="5"]finding a tutorial [/SIZE]
[tutorial for terminal]("http://ubuntuforums.org/showthread.php?p=990636") and just search around for a tutorial
[SIZE="5"]getting involved[/SIZE]
just put your self in to the community talk to others on ubuntu & linux forums.

---

### Post by LaRoza on 2007-10-27
This wiki is good for beginners, a lot of good resources and tutorials [http://learnpython.pbwiki.com/HowToStart](http://learnpython.pbwiki.com/HowToStart)

---

### Post by slavik on 2007-10-27
you put in C++ but not C?

---

### Post by bribaetz on 2007-10-28
im know a lot about c like its really  low level and hard for a first language.

---

### Post by LaRoza on 2007-10-28
[http://ubuntuforums.org/showthread.php?t=528483](http://ubuntuforums.org/showthread.php?t=528483)

The OP's opinion of C

---

### Post by CptPicard on 2007-10-28
> **bribaetz said:**
> i wrote this thread so new programmers would not end up where i did

Where did you end up? Why? What did you learn that you are applying here to make a better tutorial? :) Why are the other tutorials bad?

Anyway, welcome back man, I kinda missed you... kinda.. :)

---

### Post by Perfect Storm on 2007-10-28
Closed due to some complaints. Will be re-open when the investigation is done.

---

### Post by Perfect Storm on 2007-10-28
Re-open.

---

### Post by bribaetz on 2007-10-28
> **CptPicard said:**
> Where did you end up? Why? What did you learn that you are applying here to make a better tutorial? :) Why are the other tutorials bad?

Anyway, welcome back man, I kinda missed you... kinda.. :)

poser?? i never pretended to be what i am not i do know that pmaiser and lroza are better programmers much better thats no excuse for arrogance and. i ended up making enemies on this site rather than a larger knowledge of programming.being around them talking trash is a tad annoying all my intent ever was was to learn more and i can not apologize for that. i wrote this tutorial so anyone one who wants to learn a skill would not waist their time here trying to get help from people who are only interested in making them selves look better, and attacking anyone who tries to learn. when did i ever try to be a poser or do anything of the sort i apologize if i ever seemed like that all i am interested in doing is learning to program. and helping anyone who is interested in programming to the best of my skill. i know that i am at a lack of skills but does that give any one else the right to expose such things or even make a joke out of it?

---

### Post by bribaetz on 2007-10-28
yay my first functional program in python XD
can i ave opinions 
```
 loop = 0
choice = 0
while loop == 0:
 ##pycalc 
 ##setting a vairiable for the loop
 a = input("input a number:")
 sign = raw_input("input +, /, *, -:")
 b = input("input a number:")
 
 if sign == "+":
    choice = 1
 if sign == "-":
  choice = 2
 if sign == "*":
  choice = 3
 if sign == "/":
  choice = 4
 if sign == "e":
  choice = 5		
 if choice == 1:
  c = a + b
  print a, "+", b, "=", c 
 
 if choice == 2:
  c = a - b
  print a , "-", b, "=", c
 
 if choice == 3:
  c = a * b
  print a, "*", b, "=", c
  
 if choice == 4:
  c = a / b
  print	a, "/", b, "=", c
 if choice == 5:
    	loop = 0

```

---

### Post by bribaetz on 2007-10-28
is that really al everyone has for this thread

---

### Post by CptPicard on 2007-10-28
What is your point of using the "choice" variable? It's completely redundant. Just do the math already in the branch where you recognize the mathematical operation the user wants to perform by entering "+", "-", etc...

---

### Post by bribaetz on 2007-10-28
i guess i get what your saying i am  really inexperienced at this but none the less it works but not well i guess

---

### Post by CptPicard on 2007-10-28
I suggest you go back to reading tutorials before writing them ;)

---

### Post by bribaetz on 2007-10-28
your right i thought it might be able to help but it probably confused anyone who tried reading it caused by my confusion

---

### Post by ghostdog74 on 2007-10-28
> **bribaetz said:**
> yay my first functional program in python XD
can i ave opinions 
```
 loop = 0
......
 
 if sign == "+":
    choice = 1
 if sign == "-":
  choice = 2
 if sign == "*":
  choice = 3
 if sign == "/":
  choice = 4
 if sign == "e":
  choice = 5		
 if choice == 1:
  c = a + b
  print a, "+", b, "=", c 
 
 if choice == 2:
  c = a - b
  print a , "-", b, "=", c
 
 if choice == 3:
  c = a * b
  print a, "*", b, "=", c
  
 if choice == 4:
  c = a / b
  print	a, "/", b, "=", c
 if choice == 5:
    	loop = 0

```
you can use dictionaries for all these if/elses
```

signs = {  "+" : 4 , "-" : blah , blah ....}
choices = { }

```

you can use a while True (1) loop instead of specifying a loop flag. 

```

while 1:
   ... do stuff
   if choice in [ "q","Q"]; break # or exit
   ....


```

---

### Post by bribaetz on 2007-10-28
i haven't got that far yet

---

