---
title: "Arena.py issues"
date: 2009-12-03
forum: Programming Talk
---

### Post by karimruan on 2009-12-03
I am writing a game for ubuntu (in python). It is a console game. I am having two problems.

When during battles the code is supposed to print the updated HP and enemy HP to the console. It prints, but never changes, it always stays to points below the max HP for the enemy. I really think the battle code needs redone, so any help with that would be nice. I used the battle code from Adventure.py from the forums.

Second, when in the function prompt1() if you 'look', 'take gold' and then 'look' again, it takes you back to the Troll battle ( level4() ). Not sure why. Anyways, thanks a bunch for the help.

here is the code for the battles:

[code = Python]

def level4():
    os.system("clear")
    global gold
    charhealth = 20
    trollhealth = 20

    print "You are faced with a Troll."
    print
    print \
          """

        []++++++[]
        |  TROLL |
        []++++++[]

YOUR HEALTH            TROLL HEALTH
===========            ==========
20 HP                   20 HP

"""

    while (charhealth > 0) and (trollhealth > 0):
        
# Player attacks
        chardmg = random.randrange(5) + 1
        print "You attack the troll with your sword..."
        print "You attack the troll for", chardmg, "damage!"

        trollhealth -= chardmg
        print "HP: ", charhealth
        print "TROLL HP: ", trollhealth
        raw_input()
# TROLL attacks
        trolldmg = random.randrange(5) + 1
        print "The TROLL attacks you for", trolldmg, "damage!"
        charhealth -= trolldmg
        print "HP: ", charhealth
        print "TROLL HP: ", trollhealth
        raw_input()

        if charhealth < 0:
            print "\nThe TROLL destroyed you!"
            print 'You have lost.'
            gameover()
        else:
            print "You killed the TROLL!"
            gold_earn = random.randrange(8, 16)
            print "You earned ", gold_earn, "Gold!\n"
            gold += gold_earn
            
            raw_input()
            
            dungeon1()
[/code]

I am also attaching the entire source to help with the problem with the look, take gold, look again problem.

---

### Post by karimruan on 2009-12-03
for some reason I can't get the python syntax to show up on my post. Sorry for the inconvenience!

---

### Post by openuniverse on 2009-12-03
.

---

### Post by karimruan on 2009-12-03
Thanks, it looks pretty much like it is supposed to. Any idea what is going wrong?

---

### Post by openuniverse on 2009-12-04
.

---

### Post by nvteighen on 2009-12-04
> **karimruan said:**
> I am writing a game for ubuntu (in python). It is a console game. I am having two problems.

When during battles the code is supposed to print the updated HP and enemy HP to the console. It prints, but never changes, it always stays to points below the max HP for the enemy. I really think the battle code needs redone, so any help with that would be nice. I used the battle code from Adventure.py from the forums.


This is because you aren't printing the whole thing again. You're just print the attack result and nothing else...

What you really need, not only for this, but for the whole game, is to learn how to use ncurses ([http://docs.python.org/library/curses.html](http://docs.python.org/library/curses.html)). That library allows you to do quite interesting things with your terminal, like updating specific text areas and such.

> 
Second, when in the function prompt1() if you 'look', 'take gold' and then 'look' again, it takes you back to the Troll battle ( level4() ). Not sure why. Anyways, thanks a bunch for the help.


Your problem is that you try to pass from one function the other by calling it in the function where you are... So, the picture is that when you get into, say, level3, you are still running level2 and level1.

Do this: Create a function in which all levels are called sequentially, something like:
```

def game():
    level1()
    level2()
    level3()
    # ...

```

Inside each function, whenever you need to return to the "toplevel", use the return statement... If you can also return a useful value, do it.

Also, try using either a dictionary or, better, a class for your player, so that you can inspect the player's attributes and get rid of all your globals.

P.S: Why are you importing pygame?

---

