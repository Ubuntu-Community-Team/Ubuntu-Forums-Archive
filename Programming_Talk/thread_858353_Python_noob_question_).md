---
title: "Python noob question :)"
date: 2008-07-13
forum: Programming Talk
---

### Post by bramming on 2008-07-13
Hey. Today i decided to try some real programming after spending a lot of my time in JASS (some language to make triggers for warcraft 3 maps :) )
Well i really like Python and i made a little basic program, which asks you a lot of questions and do calculations based on those. But my problem is, at the start i would like to ask the user how many people are going to be in the "test". i do so the following way:

antal_ppl = float(raw_input("Number of ppl participating in this test: "))
print
antal_ppl_counter = antal_ppl
while antal_ppl_counter != 0
(indent here)	personnr(antal_ppl_counter) = raw_input("Name of person number", antal_ppl_counter,":")
(indent here)	antal_ppl_counter = antal_ppl_counter - 1


so what i want it to do, is to ask how many people are going to participate, and then ask for the name of each person and store all the names in variables. i wonder how i should store them in variables. i would like to do it so, that every name is stored in "personnr(the number of the person here), so if i say 5 people will participate, i store the 5 names in the variables personnr1, personnr2, personnr3, personnr4, personnr5. Whatever i do it displays an syntax error. Any help will be much appreciated :)

EDIT: I have been searching, but i probably missed it. Isnt there a way to do "for each integer from 1 to X do the following:" in Python? must be :D would make it all so much easier.

---

### Post by TreeFinger on 2008-07-13
for future purposes, when posting code on the forums surround your code in "["code"]" code here "["/code"]"

excluding quotations


read about lists for storing your user names

---

### Post by LaRoza on 2008-07-13
> **bramming said:**
> 
EDIT: I have been searching, but i probably missed it. Isnt there a way to do "for each integer from 1 to X do the following:" in Python? must be :D would make it all so much easier.

Please see the sticky on how to post code on the forum.

```

>>> for i in xrange(10):
...     print i
... 
0
1
2
3
4
5
6
7
8
9
>>> 

```

---

### Post by days_of_ruin on 2008-07-13
> **bramming said:**
> Hey. Today i decided to try some real programming after spending a lot of my time in JASS (some language to make triggers for warcraft 3 maps :) )
Well i really like Python and i made a little basic program, which asks you a lot of questions and do calculations based on those. But my problem is, at the start i would like to ask the user how many people are going to be in the "test". i do so the following way:

antal_ppl = float(raw_input("Number of ppl participating in this test: "))
print
antal_ppl_counter = antal_ppl
while antal_ppl_counter != 0
(indent here)	personnr(antal_ppl_counter) = raw_input("Name of person number", antal_ppl_counter,":")
(indent here)	antal_ppl_counter = antal_ppl_counter - 1


so what i want it to do, is to ask how many people are going to participate, and then ask for the name of each person and store all the names in variables. i wonder how i should store them in variables. i would like to do it so, that every name is stored in "personnr(the number of the person here), so if i say 5 people will participate, i store the 5 names in the variables personnr1, personnr2, personnr3, personnr4, personnr5. Whatever i do it displays an syntax error. Any help will be much appreciated :)

EDIT: I have been searching, but i probably missed it. Isnt there a way to do "for each integer from 1 to X do the following:" in Python? must be :D would make it all so much easier.

Just use a dictionary.
```
player_names = {}
for num in xrange(number_of_players):
    player_names["player"+num] = int(raw_input("what is player number "+num+":"))

```
Then you can access a players name by
```
player1 = player_names['player1']
```

---

### Post by imdano on 2008-07-13
You should read through the [Python tutorial](http://docs.python.org/tut/tut.html).  The first 5 chapters in particular.

---

### Post by bramming on 2008-07-13
Thanks for all the help :) Think i will get it right now. if i dont get it right in an hour or two i'll post again :P but thanks a lot :)

---

### Post by pmasiar on 2008-07-13
See wiki in my sig - selected best links for Python learners

---

### Post by bramming on 2008-07-13
thanks.

I also got it right by using dictionaries :D

---

### Post by Sukarn on 2008-07-13
> **LaRoza said:**
> ```

>>> for i in xrange(10):
...     print i
... 
0
1
2
3
4
5
6
7
8
9
>>> 

```

Maybe this doesn't belong in this thread, and I might be hi-jacking a thread, but would it be a bad or slower idea to use **range (*firstnumber*,*lastnumber+1*)** instead of **xrange(*lastnumber+1*)**?

---

### Post by Phenax on 2008-07-13
> **Sukarn said:**
> Maybe this doesn't belong in this thread, and I might be hi-jacking a thread, but would it be a bad or slower idea to use **range (*firstnumber*,*lastnumber+1*)** instead of **xrange(*lastnumber+1*)**?

range(1, lastnumber+1)
is equivalent to
range(0, lastnumber)
which is equivalent to
xrange(lastnumber)

There is no need to do +1. If you want to iterate ten times, just use 10. It will go from 0 to 9 (which results in ten iterations). Just putting that out there.

There is no real speed difference, so don't worry about it.

---

### Post by LaRoza on 2008-07-13
> **Phenax said:**
> 
There is no real speed difference, so don't worry about it.

[http://mail.python.org/pipermail/python-list/2007-December/468667.html](http://mail.python.org/pipermail/python-list/2007-December/468667.html)

---

