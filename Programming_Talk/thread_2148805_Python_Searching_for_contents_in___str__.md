---
title: "Python: Searching for contents in __str__"
date: 2013-05-26
forum: Programming Talk
---

### Post by izziere on 2013-05-26
I am trying to create a specialist dominos programme, where the __str__ method of each hand is populated by dominos such as "1|6\t3|6\t6|6"

To start I need to find the hand with "6|6" and wrote the following code (extract):

```
while not starter:
        for i in range(6, -1, -1):
            double = str(i) + "|" + str(i)
            for player in self.players:
                if double in player:
                    starter = True
```

the code "print(player)" prints the string correctly, but the line "if double in player" returns the error "TypeError: argument of type 'Player_Hand' is not iterable"

What am I doing wrong?  Sorry for the noob question...

---

### Post by Tony Flury on 2013-05-26
Is there a reason you are storing the hand in a single string ? A much better way (I would have thought) would be to have a list of the dominoes.

Even though the _str_ attribute of your Player_Hand returns a string, when you write a for loop on a custom type, it doesn't use the str attribute to create that loop. It looks at the whole type definition and looks for the appropriate iteration methods on the type : 

 [http://docs.python.org/release/2.6.8/tutorial/classes.html#iterators](http://docs.python.org/release/2.6.8/tutorial/classes.html#iterators)

the other way of doing this - if you insist on using a string representation, is to do : 
```

if double in str(player):

```

But learning iterators and using the power of python would be much better IMHO.

---

### Post by epicoder on 2013-05-26
Try this:
```
if double in str(player):
```
or, you could just use __str__ directly:
```
if double in player.__str__():
```
Both methods work, but I belive the former is the conventional method. You could also be wild and implement an iterator in your Player_Hand class:
```

class Player_Hand():
        ...
        def __iter__(self): return iter(str(self))
```

---

### Post by izziere on 2013-05-27
Thanks both - that's really helpful.  I was using the string because I am ripping off the Blackjack programme in Python Programming for the Absolute Beginner and the string is the method used to store the cards in the hand in that example.  Essentially I am trying to learn by making mistakes.  The good news is that I am clearly learning a lot, judging by the number of mistakes!

---

### Post by alan9800 on 2013-05-27
> **izziere said:**
> Essentially I am trying to learn by making mistakes.  The good news is that I am clearly learning a lot, judging by the number of mistakes!Solving mistakes is the best way for gaining experience :D (in programming or even about the life).
Regarding to your first loop, it could be rewritten as follows```
for i in range(7):
    double = "|".join([str(i),str(i)])
```by using the join method.

---

