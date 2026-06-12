---
title: "text adventure rpg in python (having some truble)"
date: 2011-09-30
forum: Programming Talk
---

### Post by yoanar on 2011-09-30
so i'm making this rpg in python, and i have a problem with my attack function
it looks like i dont indent but it's just something weird that happened when i posted

>  
from gasp import *

lvl = 1
health = 1000
exp = 0
immortality = 'no'  

def attack():
    global lvl
    global exp
    global health
    enemy = random_between(100, 125)
    handling = raw_input()
    if handling == 'attack':
        while enemy > 0:
            if lvl == 1:
                lost = random_between(35, 40)
                hit = random_between(5, 10)
                enemy = enemy - hit 
                health = health - lost
                if clas == 'mage':
                    print 'you cast a spell at the enemy, the enemy loses', hit,  'lives, you lost', lost, 'lives'
                if clas == 'knight':
                    print 'you swing your sword at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'marksman':
                    print 'you shoot an arrow at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
            if lvl == 2:
                lost = random_between(30, 35)
                hit = random_between(10, 15)
                enemy = enemy - hit
                health = health - lost
                if clas == 'mage':
                    print 'you cast a spell at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'knight':
                    print 'you swing your sword at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'marksman':
                    print 'you shoot an arrow at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
            if lvl == 3:
                lost = random_between(25, 30)
                hit = random_between(15, 20)
                enemy = enemy - hit
                health = health - lost
                if clas == 'mage':
                    print 'you cast a spell at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'knight':
                    print 'you swing your sword at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'marksman':
                    print 'you shoot an arrow at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
            if lvl == 4:
                lost = random_between(20, 25)
                hit = random_between(20, 25)
                enemy = enemy - hit
                health = health - lost
                if clas == 'mage':
                    print 'you cast a spell at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'knight':
                    print 'you swing your sword at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'marksman':
                    print 'you shoot an arrow at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
            if lvl == 5:
                lost = random_between(15, 20)
                hit = random_between(25, 30)
                enemy = enemy - hit
                health = health - lost
                if clas == 'mage':
                    print 'you cast a spell at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'knight':
                    print 'you swing your sword at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'marksman':
                    print 'you shoot an arrow at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
            if lvl == 6:
                lost = random_between(10, 15)
                hit = random_between(30, 35)
                enemy = enemy - hit
                health = health - lost
                if clas == 'mage':
                    print 'you cast a spell at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if go == 'go left':
                    print 'you cast a spell at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'knight':
                    print 'you swing your sword at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'marksman':
                    print 'you shoot an arrow at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
            if lvl == 7:
                lost = random_between(10, 13)
                hit = random_between(35, 40)
                enemy = enemy - hit
                health = health - lost
                if clas == 'mage':
                    print 'you cast a spell at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'knight':
                    print 'you swing your sword at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'marksman':
                    print 'you shoot an arrow at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
            if lvl == 8:
                lost = random_between(10, 12)
                hit = random_between(40, 45)
                enemy = enemy - hit
                health = health - lost
                if clas == 'mage':
                    print 'you cast a spell at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'knight':
                    print 'you swing your sword at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'marksman':
                    print 'you shoot an arrow at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
            if lvl == 9:
                lost = random_between(8, 10)
                hit = random_between(45, 50)
                enemy = enemy - hit
                health = health - lost
                if clas == 'mage':
                    print 'you cast a spell at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'knight':
                    print 'you swing your sword at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'marksman':
                    print 'you shoot an arrow at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
            if lvl == 10:
                lost = random_between(6, 8)
                hit = random_between(50, 55)
                enemy = enemy - hit
                if clas == 'mage':
                    print 'you cast a spell at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'knight':
                    print 'you swing your sword at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
                if clas == 'marksman':
                    print 'you shoot an arrow at the enemy, the enemy loses', hit, 'lives, you lost', lost, 'lives'
        if enemy < 0:
            print 'you defeated the monster'
            exp = exp + 2
            exp()
        
        if health < 0:
            if immortality == 'yes':
                pass
            if immortality == 'no':
                print 'you have died,'
                happen = random_between(1, 5)
                if happen == 1:
                    while 1 == 1:
                        print 'and a mad-man ate your remains because he thaught it was candy'
                if happen == 2:
                    while 1 == 1:
                        print 'and you were found by archeologists in the year 2 million, they used you as a proof for the theory of evoulution'
                if happen == 3:
                    while 1 == 1:
                        print 'and a new religion was founded on you, their saviors name is', name, 'Christ'
                if happen == 4:
                    while 1 == 1:
                        print 'and fungus has started to grow out of your brain'
                if happen == 5:
                    while 1 == 1:
                        print 'and the monster that killed you ate you and got sick then later it died'    


here is the exp() function that is called after "enemy = 0"

> 
def exp():
    global exp 
    global lvl
    if exp == 10:
        print 'CONGRATULATIONS, you have ascended to lvl 2!'
        lvl = 2
    if exp == 20:
        print 'CONGRATULATIONS, you have ascended to lvl 3!'
        lvl = 3
    if exp == 30: 
        print 'CONGRATULATIONS, you have ascended to lvl 4!'
        lvl = 4
    if exp == 40: 
        print 'CONGRATULATIONS, you have ascended to lvl 5!'
        lvl = 5
    if exp == 50:
        print 'CONGRATULATIONS, you have ascended to lvl 6!'
        lvl = 6
    if exp == 60:
        print 'CONGRATULATIONS, you have ascended to lvl 7!' 
        lvl = 7
    if exp == 70:
        print 'CONGRATULATIONS, you have ascended to lvl 8!'
        lvl = 8
    if exp == 80:
        print 'CONGRATULATIONS, you have ascended to lvl 9!'
        lvl = 9
    if exp == 90:
        print 'CONGRATULATIONS, you have reached the maximum level of 10!'
        lvl = 10
i keep getting the error:
"""
  File "DUNGEONER.py", line 507, in <module>
    attack()
  File "DUNGEONER.py", line 296, in attack
    exp = exp + 2
TypeError: unsupported operand type(s) for +: 'function' and 'int'
"""

hope somebody can help

---

### Post by karlson on 2011-09-30
> **yoanar said:**
> so i'm making this rpg in python, and i have a problem with my attack function
it looks like i dont indent but it's just something weird that happened when i posted

here is the exp() function that is called after "enemy = 0"

i keep getting the error:
"""
  File "DUNGEONER.py", line 507, in <module>
    attack()
  File "DUNGEONER.py", line 296, in attack
    exp = exp + 2
TypeError: unsupported operand type(s) for +: 'function' and 'int'
"""

hope somebody can help

I'll say it once and I'll say it again read what the compiler/interpreter tells you and use descriptive names.
```

exp = exp + 2

```

In your code exp is both a function exp() and a variable in addition to that exp is a function defined in math module which I don't know if you are importing but could also present a problem.

The interpreter in this case took the exp to be a function so when you try to add an integer to a function exp it naturally gave you an error.

use long names like: 
```

experience = 0

```
and 
```

get_experience()

```

This way you avoid problems like this...

---

### Post by cgroza on 2011-09-30
@OP, use CODE tags, they keep indentation right, which is crucial for python code.

---

### Post by yoanar on 2011-10-01
ty, btw is nesting if statements a bad way to make something like this (the levels)

---

