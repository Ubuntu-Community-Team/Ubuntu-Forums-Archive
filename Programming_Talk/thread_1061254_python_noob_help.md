---
title: "python noob help"
date: 2009-02-05
forum: Programming Talk
---

### Post by gregnoir200 on 2009-02-05
Hello there :)

Im quite new to python and I am getting to grips with it at a steady pace, although currently I am experiencing an issue. Basically Just for a learning exercise I decided to start constructing a basic rock paper scissors game. Now as far as I have got I have done a basic choice of rock paper scissors and a basic AI system ("ais"). So just at the point I am in this project of mine is that it should effectively work. But unfortunately it just returns as "none" all the time. I'm not entirely sure what I'm doing wrong here but help would be very much appreciated :).

Source code is posted below;

import random
import time

loop = 1
rock = "r"
paper = "p"
scissors = "s"
choice = ""
overchoice = ""
ais = ""
aim = ""
aih = ""

#Menu system
def menu():
    loop2 = 1
    choice = ""
    overchoice = ""
    while loop2 == 1:
        print "| Press r for ROCK!"
        print "| - - - - - - - - - - - "
        print "| Press p for PAPER!"
        print "| - - - - - - - - - - - "
        print "| Press s for SCISSORS!"
        print "'-----------------------"
        print ""
        choice = raw_input("Enter your choice here:").lower()
        if choice == "r":
            overchoice = 1
            return overchoice
            loop2 = 0
        elif choice == "p":
            overchoice = 2
            return overchoice
            loop2 = 0
        elif choice == "s":
            overchoice = 3
            return overchoice
            loop2 = 0
        else:
            print ""
            print "Sorry, that wasnt a valid choice please re-enter your choice."
            print ""

#Judge system
def judge(player, ai):
    winner = ""
    if player == 1 & ai == 2:
        winner = "ai"
        return winner
    elif player == 2 & ai == 1:
        winner = "player"
        return winner
    elif player == 1 & ai == 3:
        winner = "player"
        return winner
    elif player == 3 & ai == 1:
        winner = "ai"
        return winner
    elif player == 1 & ai == 1:
        winner = "none"
        return winner
    elif player == 2 & ai == 2:
        winner = "none"
        return winner
    elif player == 2 & ai == 3:
        winner = "ai"
        return winner
    elif player == 3 & ai == 2:
        winner = "player"
        return winner
    elif player == 3 & ai == 3:
        winner = "none"
        return winner

    
#Basic AI system
#Generates random choice
def basic_ai():
    ai = random.randrange(1,4)
    return ai

#Main system
while loop == 1:
    player = menu()
    player = int()
    ais = basic_ai()
    ais = int()
    judge(player, ais)
    print judge(player, ais)



Any more details needed just ask but thank you all very much for your time :)

Many regards and respects 

Gregnoir200

---

### Post by Tony Flury on 2009-02-05
a useful debugging tip is to add in extra print statements so you can display the value of key variables while your program runs.

also - when you post code in these forums - you can use the code tags to preserve the indents (which as you know are key in python).

to use the tags - press the # button in the toolbar as you enter your post - and insert the code inside the tags.

---

### Post by sjbaugh on 2009-02-05
I think you may have your comparisons wrong.
instead of:
```
if player == 1 & ai == 2:
```
etc
Try
```
if (player == 1) and (ai == 2):
```
etc

I haven't checked all your logic but I think this is what you may mean.

Best of luck,

Steve

---

### Post by Tony Flury on 2009-02-05
A couple of things show up immediately : 

```

player=int()

```

What is that intended to do ? It actually sets your variables to zero - which you probably don't want.

Also in your if conditions ... you are using "&" - i think you mean to use "and". & is a bit wise operator - a very different beast in most cases.

---

### Post by dandaman0061 on 2009-02-05
Alright... I have a couple of rhetorical questions w/ suggestions...

One thing is that you can get rid of your loop & loop2 variables in favor of 'while True:' loops.  In your menu() function, setting the loop2 variable to 0 after the return call doesn't ever happen, so you can remove those lines.  Once you call return, you break completely out of any loop and the function as well.

Why are you storing the player's and ai's choices as integers which you have to lookup when you store AND compare?  There might be benefits for optimizations, but for python code I'd just store the strings to help keep it straight.

```

choice = raw_input("Enter your choice here:").lower()
    if choice == "r":
        return 'Rock'
    elif choice == "p":
        return 'Paper'
    elif choice == "s":
        return 'Scissors'

```

Just don't forget to change your 'judge()' code as well to match this logic.  Which brings me to another suggestion:  Instead of having a bunch of statements like:
```

if (player == 1) and (ai == 2):

```
I find that it is easier to keep track of the logic when you nest the statements. e.g.
```

if player == 1:
    if ai == 1:
        winner = "None"
    elif ai == 2:
        winner = ...
elif player == 2:
    if ai == 1:
        winner = ...
    elif ai == 2:
        ...
...

```

One last suggestion, again in the judge() function.  I would set the winner variable like you have, but you can remove all of the 'return winner' functions and consolidate them into one call at the bottom. (Notice I also changed the comparison to check the actual string) e.g.

```

def judge(player, ai):
    winner = None
    if player == 'Rock':
        if ai == 'Rock':
            winner = "none"
        elif ai == 'Paper':
            winner = "ai"
        elif ai == 'Scissors':
            winner = "player"
    elif player == 'Paper':
        if ai == 'Rock':
            winner = "player"
        elif ai == 'Paper':
            winner = "none"
        elif ai == 'Scissors':
            winner = "ai"
    elif player == 'Scissors':
        if ai == 'Rock':
            winner = "ai"
        elif ai == 'Paper':
            winner = "player"
        elif ai == 'Scissors':
            winner = "none"

    return winner

```

---

### Post by gregnoir200 on 2009-02-05
ok thanks for the tip Tony Flury :)
Il repost the code as soon as i can :)
Ah right, i didnt know it did that :S i thought it made it into an integer, i was worried it was trying to compare a string to an integer and thats why it was misbehaving :S (feel rather silly, but at least im learning :) ).

Also thank you sjbaugh :) thats very useful thank you very much :)
I hope that helps solve it, i will test asap and get back to you all :)

dandaman0061 you are also a star, thank you very much for the excellent advice, it all makes sense. I can definatly see the inefficiency of my code in comparison to yours. Thank you very much for donating this time to helping.

Thanks to you all, you have been very helpful :D

Enjoy your evenings :)

Gregnoir200

---

### Post by Tony Flury on 2009-02-06
Actually - thinking about it - there is a way you can do all of the judging and your validation without using chains of if statements.

```

import random
import time

choices = ["r","p","s"]
beatenby = {"r":["p"], "p":["s"], "s":["r"]}

#Menu system
def menu():
    valid = False
    while (not valid):
        print "| Press r for ROCK!"
        print "| - - - - - - - - - - - "
        print "| Press p for PAPER!"
        print "| - - - - - - - - - - - "
        print "| Press s for SCISSORS!"
        print "'-----------------------"
        print ""
        choice = raw_input("Enter your choice here:").lower()
        if not (choice in choices):
            print ""
            print "Sorry, that wasnt a valid choice please re-enter your choice."
            print ""
        else:
            valid = True
    return choice

#Judge system
def judge(player, ai):
    winner = ""
    print "ai chose",ai
    if (player in beatenby[ai]):
        return "player"
    elif (ai in beatenby[player]):
        return "ai"
    else:
        return "draw"

#Basic AI system
#Generates random choice
def basic_ai():
    return choices[random.randrange(0,3)]

#Main system
while True:
    player = menu()
    ais = basic_ai()
    print judge(player, ais)

```

This code uses a list (choices) to validate the input from the player (and convert the ai's choice).

It then uses a dictionary (beatenby) to encapsulate all the rules for the game. In each entry in this dictionary the value lists all of those options which can beat the key.
```

beatenby = {"r":["p"], "p":["s"], "s":["r"]}

```
basically means p beats r, s beats p, and r beats s.

as you can see from the code, working out if someone is a winner is simply a case of working out if your choice is in the list of values that can beat your opponents choice.

Dictionaries and lists are massively powerful in python - I would recommmend you get used to using them.

---

### Post by Bachstelze on 2009-02-06
> [font="monospace"]if not (choice in choices):[/font]

[font="monospace"]if choice not in choices:[/font] is better IMGO (more intuitive, and avoids the need for parentheses).

---

### Post by Tony Flury on 2009-02-06
HymnToLife : you are right that you don't need to parenthesis in this case -  I wasn't aware that you could do "not in" - thanks for that.

---

### Post by gregnoir200 on 2009-02-07
wow thank you all for your time :D

My script now works :D

Although using dictionaries and lists in that way are slightly beyond me at the moment :) but I have bookmarked the page so I can revise it in the future. 

I cant thank you enough for your help. This has to be the best community I have ever seen :)

I owe you all, so if there is anything I can do for any of you feel free to pm me and il do my best :)

---

### Post by nvteighen on 2009-02-07
> **gregnoir200 said:**
> 
I owe you all, so if there is anything I can do for any of you feel free to pm me and il do my best :)

Keep learning! That's all we want from you ;)

---

### Post by Tony Flury on 2009-02-08
> **nvteighen said:**
> Keep learning! That's all we want from you ;)

+1 to that.

to gregnoir200 - don't forget - you can play around with python in the command line - just type python in your normal terminal.

you can do almost anything in the interpreter - it is a really good learning tool.

Make sure you work through the Python tutorial : [http://docs.python.org/tutorial/index.html](http://docs.python.org/tutorial/index.html)

It is brilliant written - and you can learn so much through it - so long as you give yourself a chance to play and experiment - you can't damage anything.

---

