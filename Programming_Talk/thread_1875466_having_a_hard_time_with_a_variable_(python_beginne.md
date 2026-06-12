---
title: "having a hard time with a variable (python beginner)"
date: 2011-11-04
forum: Programming Talk
---

### Post by texasboy2084 on 2011-11-04
I am making a small text game to test what I have learned from tutorials. Here is part of the code:

```
#!/usr/bin/python

import time, sys


enemy_health = 50


battle = raw_input("your walking throught the forest and come across a dwarf. What do you do?\n1 Fight\n2 Run\n")
if battle == "1":
    print "Prepare to fight!\n"
    time.sleep(1)
    print "You strike the dwarf, it has ",enemy_health -10,"hp left\n"
    hit_1 = raw_input("Hit it again? y/n\n")
    if hit_1 == "y":
        time.sleep(1)
        print "the dwarf evaded your attack he still has ",enemy_health,"left."
else:
    print "You ran from battle."
```


I don't know how to make the enemy health stay at 40. I thought it would change because of what I did, but it seems I was wrong. And I am completely stuck now.

Also to make an enemy hit the hero for a different amount each time would i have to import random and get the damage in a range?


Thanks for the hand :)

---

### Post by crdlb on 2011-11-04
For the first part, you are not changing the value of enemy_health, only printing the result of "enemy_health - 10". On the line before that, put ```
enemy_health -= 10
``` which is a shortcut for ```
enemy_health = enemy_health - 10
```

For the second part, your plan sounds good, for example:
```
damage = random.randint(5, 15)
```

You probably will also want to wrap the whole thing in a "while True:" loop and "break" when the battle is over.

---

### Post by texasboy2084 on 2011-11-05
Thanks for the help :), everything is going smooth now.



edit: 

everything was running smooth, until I tested this morning.  I used alot of resources last night and learn a lot, most of it from these forums.  I included random loot drops, ability  to buy and sell stuff, and even a few quests its shaping up nicely (for a noob lol). 

I guess I am not fully understanding the if statement. Because even if the "if" is false it sill takes away damage from the enemy.


```



enemy_attack = random.choice(fight_1)

fight_1 = "You strike the enemy\n","the enemy evades, but trips and hits it head on a rock\n","the enemy evaded your attack\n"

damage = random.randint(0,20)

hero_damage = random.randint(40,50)






battle = raw_input("your walking throught the forest and come across a enemy. What do you do?\n1 Fight\n2 Run\n")

    if battle == "1":
        print "Prepare to fight!\n"
        time.sleep(1)
        print enemy_attack

        if enemy_attack == "You strike the enemy\n" or "the enemy evades, but trips and hits it head on a rock\n":
            enemy_health -= hero_damage
            print "the enemy now has",enemy_health,"hp left\n"

        else:
             enemy_attack == "the enemy evaded your attack\n"
             print  "the enemy has",enemy_health,"hp left\n"

        if enemy_health <= 0:
            print "you have won"
            sys.exit() 
```

In my main code everything is wrapped in a while loop, how to I make it do enemy_health -= hero_damage, only if it is true? If I take that one part out everything works like a charm.


Also this file is large, other than organisation there benefits to splitting a file in multiple files?

---

### Post by simeon87 on 2011-11-05
You should not write something like:

```
if var == "string1" or "string2":
```

Python will compare var to "string1" (which won't be equal) so then it'll check "string2". That is a string and it's not empty so the if-statement will be True. That's why it always executes the code after the if-statement. You probably want to write:

```
if var in ["string1", "string2"]:
```

which will indeed check if var is equal to either "string1" or "string2".

---

### Post by gsmanners on 2011-11-05
I have a strong feeling this might be necessary:

[http://ubuntuforums.org/showpost.php?p=1984319](http://ubuntuforums.org/showpost.php?p=1984319)

---

### Post by nvteighen on 2011-11-06
What do you mean with this:

```

        else:
             enemy_attack == "the enemy evaded your attack\n" # (*)
             print  "the enemy has",enemy_health,"hp left\n"

```

The line marked by (*) just compares *enemy_attack* to the string, it doesn't assign that string to *enemy_attack*... but when it compares it, it will just return either True or False, but no if block or any conditional is there to actually check it and decide something based on that result.

I guess what you wanted to do is to add a second condition that has to be checked if the previous one failed. That's what we call an "else if". However, in Python you do that using the *elif* keyword:

```

        elif enemy_attack == "the enemy evaded your attack\n":
             print  "the enemy has",enemy_health,"hp left\n"

```

---

