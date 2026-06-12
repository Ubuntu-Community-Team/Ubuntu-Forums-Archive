---
title: "While loops in Python...it's not looping, I think"
date: 2008-08-31
forum: Programming Talk
---

### Post by fiddler616 on 2008-08-31
Hello,
So I'm making a Python program which is too big to paste in here, but here's the skeleton:
```

while pos == 'cthree':
    #Do some stuff, including moving to the position C2 (ctwo) which has this line of code for it:
     pos = 'cthree'
while pos == 'ctwo':
    #Do some other stuff, including maybe moving back to C3, so I put:
    print "Returning to C3"
    pos = 'cthree'
    #So far, this is the physical end of the program

```
The thing is, I really thought that resetting pos to cthree would make the first 'while' be true again, which would move me back to that part of the program (what I really wanted to do was use GOTO...TI-BASIC habits die hard, but I know that's not allowed). However, when I run the program and go to the ctwo while loop, I see "Returning to C3" and then the program ends. How do I make it actually go back to C3?
Thanks in advance

---

### Post by Wybiral on 2008-08-31
Stop thinking in BASIC :) Python is not BASIC. It has nothing resembling GOTO. While follows normal program flow just like everything else (the condition has to be true when the flow reaches the while... Past that point, it's not going to be affected).

Read your program as you read a book... Why should it jump back up there?

---

### Post by nero1111 on 2008-08-31
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by fiddler616 on 2008-08-31
But BASIC is so easy! :)
OK, I guess that makes sense about program flow, though it just made me confused about what the difference is between while and if. Because i used to have ifs in there instead of whiles, and it worked--OK, rephrase: the output was exactly the same.
So how *would* I send it back there if I'm not allowed to use GOTO and while won't do the trick?

---

### Post by fiddler616 on 2008-08-31
Many thanks to whoever got rid of Nero1111's spam.
I'd just finished reporting as spam him in a different thread (he made the exact same post), and so I was timed-out of my "Report" button.

---

### Post by Wybiral on 2008-08-31
> **fiddler616 said:**
> So how *would* I send it back there if I'm not allowed to use GOTO and while won't do the trick?

Don't make a new loop for each state, make one loop that checks for all states. Here's a really simple example:

```

import time

tired = 0
danger = 0
state = 0
bears = 0
WALKING, SEE_BEAR, RUNNING, TIRED = range(4)

while True:

    if state == WALKING:
        print 'Walking...'
        tired = 0
        danger += 1
        if danger == 2:
            state = SEE_BEAR
        time.sleep(1)

    elif state == SEE_BEAR:
        print "I see a bear, run!"
        bears += 1
        if bears == 3:
            break
        state = RUNNING
        time.sleep(0.5)

    elif state == RUNNING:
        print "Running..."
        danger = 0
        tired += 1
        if tired == 4:
            state = TIRED
        time.sleep(0.25)

    elif state == TIRED:
        print "Too tired, must walk"
        state = WALKING
        time.sleep(1)

print "You've seen three bears in your trip, time to stop!"

```

But it's hard to tell what you need without seeing more (or you explaining what it's supposed to do).

---

### Post by cmay on 2008-08-31
> Many thanks to whoever got rid of Nero1111's spam.
I'd just finished reporting as spam him in a different thread (he made the exact same post), and so I was timed-out of my "Report" button.
i just open the report window to start type then it was gone.
that was fast. ??? not of my doing i think :)

---

### Post by fiddler616 on 2008-08-31
Nesting the entire thing inside a while statement seems...well it actually seems sort of messy for a big program...but maybe that's OK...huh...cool.
The program:
Is called STEXBAG for now (might change it) which stands for Stupid TEXt-BAsed Game. You know the type. "You're at the plains, and see mountains to the North, and a demolished building to the East. Press 8 to go North, or 6 to go East" (Numbers make sense on a numpad). So the end product's going to have 25 'regions' on the map, and the idea is that you're able to travel freely between them while retaining certain variables, such as nrg (Energy, walking is tiring), icepick (whether you have the icepick or not) etc.
You're thinking "Well, if you yourself admit that it's stupid, why are you making it?"--it's primarily so I learn Python better. I read the first 11 chapter in A Byte of Python by Swaroop (which I really liked, though I'm bracing myself for Object-Oriented Programming which is the next chapter),and I realized that even though it made sense when I read it, I couldn't just "think" in Python, and I should work on that. And making it a game means that it'll be worth slightly-more-than-nothing when it's done, instead of plain old nothing.
Wow...that was long. Sorry...
Thanks a lot for nurturing me through my first **two** "Help!" threads.

---

### Post by fiddler616 on 2008-08-31
> **cmay said:**
> i just open the report window to start type then it was gone.
that was fast. ??? not of my doing i think :)
This is why I love the Ubuntu community--at least two people can't report somebody because somebody else already has. Within minutes, too...

---

### Post by Wybiral on 2008-08-31
> **fiddler616 said:**
> Nesting the entire thing inside a while statement seems...well it actually seems sort of messy for a big program...but maybe that's OK...huh...cool.

No, you don't have to put everything in there, you can use functions or a class to make it easier, just use that for the state machine (which seems to be what you need).

```

while True:
    if state = 0:
        do_something0()
    elif state == 1:
        do_something1()
    elif state == 2:
        do_something2()

```

And those functions or object methods could perform the action for that state.

---

### Post by Reiger on 2008-08-31
> **fiddler616 said:**
> Nesting the entire thing inside a while statement seems...well it actually seems sort of messy for a big program...but maybe that's OK...huh...cool.

Well to be frank your program 'feels' that way: 

Step 0: Initialize default Scenario;
Step 1: Player gets Scenario;
Step 2: Player acts;
Step 3: New Scenario is computed;
Step 4: Quit the program or continue at Step 1.

> 
You're thinking "Well, if you yourself admit that it's stupid, why are you making it?"

No. First thing I thought was stop writing TI BASIC! Only times I ever seriously considered gameplay like that was... well, on a TI84 Plus ... ;)

---

### Post by pmasiar on 2008-08-31
> **fiddler616 said:**
> Nesting the entire thing inside a while statement seems...messy for a big program

no, you define function doing the loop only. Rule of thumb: if your function has more than 50 lines, it's too long: refactor.

> retaining certain variables, such as nrg (Energy, walking is tiring),

don't be lazy typing, call it Energy.

> icepick (whether you have the icepick or not) 

use dictionary with object you carry

> it's primarily so I learn Python better. 

Go for Python challenge first. Check also wiki in my sig for simple training tasks (simpler than your adventure game, even if I created one for fun in less than 60 lines of Python :-) )

---

### Post by fiddler616 on 2008-08-31
@Wybiral: *exhales*, yeah...classes...on that...a big hole in my education. I can handle functions though. I guess I'll do that.
@Reiger:I'm assuming you meant 'this way'. That said, what are you trying to say? I think I'm missing something.
@Reiger again: TI-86s rock life! :) . I made an honest effort to research getkey (or its equivalent), but all I got was dead forums saying "What's the getkey equivalent in Python?". I'm also turning over not using numbers, but strings i. e.: Choice? north , but I'm trying to get the other gameplay mechanics working first. And it'll be tedious allowing for case variation (Oh!Just kidding, I can make a function! Haha!)(Sorry)

---

### Post by fiddler616 on 2008-08-31
> **pmasiar said:**
> no, you define function doing the loop only. Rule of thumb: if your function has more than 50 lines, it's too long: refactor.

> retaining certain variables, such as nrg (Energy, walking is tiring),

don't be lazy typing, call it Energy.

> icepick (whether you have the icepick or not) 

use dictionary with object you carry

> it's primarily so I learn Python better. 

Go for Python challenge first. Check also wiki in my sig for simple training tasks (simpler than your adventure game, even if I created one for fun in less than 60 lines of Python :-) )
I'm not being lazy typing, I'm trying to use three letter variables for everything that's not an item. Idiosyncratic, but at least pre-meditated.
Dictionaries: I've been thinking about using them for items in conjunction with a description of the item, but since I'm not doing descriptions (yet), what's the second slot for? Wouldn't a list work? Just ask if ___'s in the inventory list, if True: #pass | if False: #pass?

---

### Post by Wybiral on 2008-08-31
> **fiddler616 said:**
> (Oh!Just kidding, I can make a function! Haha!)(Sorry)

```

print "Hello World!".lower()
print "Hello World!".upper()
print "Hello World!".swapcase()

```

---

### Post by fiddler616 on 2008-08-31
> **Wybiral said:**
> ```

print "Hello World!".lower()
print "Hello World!".upper()
print "Hello World!".swapcase()

```
Thanks! So in practice it'd be:
```
dir = input("Where?").lower()
if dir = "north":
    #Do cool stuff
```

---

### Post by Wybiral on 2008-08-31
> **fiddler616 said:**
> Thanks! So in practice it'd be:
```
dir = input("Where?").lower()
if dir = "north":
    #Do cool stuff
```

I wouldn't use input, I would use raw_input. input evaluates what they type, raw_input just returns a string.

---

### Post by fiddler616 on 2008-08-31
Harrumph. I've been using int(raw_input()) (and raw_input for strings) throughout, but when it came time to write on here, I got all second-guessy about which one was which. Glad that's straightened up.

---

### Post by CptPicard on 2008-08-31
> **fiddler616 said:**
> But BASIC is so easy! :)

[Quote=Edsger Dijkstra]
The teaching of BASIC should be rated as a criminal offence: it mutilates the mind beyond recovery.[/quote]

[http://www.cs.utexas.edu/users/EWD/ewd02xx/EWD215.PDF](http://www.cs.utexas.edu/users/EWD/ewd02xx/EWD215.PDF)

---

### Post by Wybiral on 2008-08-31
The reason I advise against "input" is that it's not always what you expect. Suppose you want the user to enter "1+2" (not the result, but that expression), "input" will evaluate that and return 3 ... Not what you want at all. Or, enter this into an import prompt...

```

__import__("os").listdir("./")

```

It's basically a Python interpreter prompt, which is probably not what you want :)

---

### Post by fiddler616 on 2008-08-31
Yeah, I know that people who want to have a bit too much fun can do a lot from an input() if they know to look for it.
--
I'm debating whether this thread qualifies as solved...on the one hand, I haven't "solved" my program, but I've gotten buckets of useful stuff that I just haven't had time to implement yet.

---

