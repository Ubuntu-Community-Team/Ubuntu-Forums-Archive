---
title: "I'm brand new to coding and need some help."
date: 2010-02-19
forum: Programming Talk
---

### Post by rcayea on 2010-02-19
Hi everyone,

As my title says, I am an ultra-complete newb at this programming thing. I love hockey and wanted to make a simple, and obviously, beginner program so that when my friends type in a "response" as in a certain amount of goals, my team, the Bruins would always get one more and win. I keep getting the following error and was wondering if you could look at my code below and see if you can eyeball any tips for me. Thanks-a-bunch!

Randy 

Error/program running:
>>> ================================ RESTART ================================
>>> 
```

```Since we in this house love the Boston Bruins
We accept no other result than a win
How many goals do you think your team will score against the Bruins: 4```

```

Traceback (most recent call last):
  File "/home/rcayea/Python Progamming/bruinsalwayswin.py", line 4, in <module>
    bruins_goals =int(response+1)
TypeError: cannot concatenate 'str' and 'int' objects
>>> 



print "Since we in this house love the Boston Bruins"
print "We accept no other result than a win"
response = raw_input("How many goals do you think your team will score against the Bruins: ")
bruins_goals =int(response+1)
print response, "That's it?"
print "Sorry the Bruins scored one more goal than that and won!"
print bruins_goals, "Bruins Goals"

---

### Post by love to learn on 2010-02-20
Im a bit out of touch with python,however i am able to give you a few pointers for you to think about so long.
Your 'response variable holds a string input,so this line:
bruins_goals =int(response+1) 
should be something more like bruins_goals =int(response)+1 if typecasting is the way to convert strings to ints.
But wouldnt typecasting a string to an int just give you the ascii code for the character?
in c you would use something like atoi(response).
bruins_goals must also be an int  although if i remember correctly,python doesnt care.

Just thinking aloud here  lol  if it doesnt spark any clues,well at least i bumped your request for help to the top of the queue which helps too ;)

good luck

---

### Post by rcayea on 2010-02-20
Thanks for thinking aloud. It never hurts. 

I will give your tips some thought and tries. 

Randy

---

### Post by rcayea on 2010-02-20
OH SO EXCELLENT! 

Thank you! you were correct about the (response)+1

Randy

---

### Post by Penguin Guy on 2010-02-20
If your new to programming, you should take a look at [the Python tutorial]("http://docs.python.org/tutorial/index.html"). I'm halfway through and am finding it a lot more fun and easy-to-follow than other tutorials. Anyway, good luck learning Python.

[PHP]
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    print "-- This parrot wouldn't", action,
    print "if you put", voltage, "volts through it."
    print "-- Lovely plumage, the", type
    print "-- It's", state, "!"
[/PHP]

---

### Post by bunburya on 2010-02-20
I may also weight in and point out that I am having a good time with Dive Into Python ([http://www.diveintopythyhon.org](http://www.diveintopythyhon.org) or [http://www.diveintopython3.org](http://www.diveintopython3.org) if you're using python3.x). Strangely enough the tutorial describes itself as being for experienced programmers but I am completely new to programming yourself, and half way through I find it quite manageable.

---

### Post by donkyhotay on 2010-02-20
Python is my programming language of choice but I've dabbled in others. Most of my learning has been done by going through the source code of other projects, modifying them, and then seeing the results. I've found this to be very useful since you can get results immediately (whether it breaks or changes as you planned) and you're not just looking at the equivalent of "hello world" level of programs or recreating exactly what the tutorial wants, which can be a little boring. It's how I do almost all my coding, starting with another piece of code and modifying it into what I want, my biggest project I've done actually started by me taking an incomplete FOSS RTS engine and then modifying it into an [open source version of Moonbase Commander](code.google.com/p/tether) (which if you've ever played you'll know is radically different from an RTS).

---

### Post by rcayea on 2010-02-20
I am using/learning from a book called *Hello World!* Computer Programming for kids and other Beginners. 

I searched and searched for a book that would assume I am a complete beginner and would explain every single word. I am quite the literal person so I find this book to be a great learning tool. 

Thanks again,
Randy

---

### Post by love to learn on 2010-02-21
Well im glad if i could help. 
Now u just have to find a way to make your prog results come true.  something like:

```

sudo make --my_code_influence_game_results

```

perhaps???  ;)

Good luck

---

