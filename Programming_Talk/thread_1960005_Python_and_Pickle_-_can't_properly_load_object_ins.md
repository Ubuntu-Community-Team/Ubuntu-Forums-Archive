---
title: "Python and Pickle - can't properly load object instance"
date: 2012-04-16
forum: Programming Talk
---

### Post by Pharnavaziani on 2012-04-16
Hi,

I'm working on a simple text (for the moment) RPG with Python 2.7 under Oneiric.  I've got a directory tree and a number of disparate parts working, but I'm having difficulty integrating them.  I recently built a 'player creation' program which:

[LIST]
[*] defines a character as an object,
[*]creates an instance with stats
[*] creates a save file for the character
[*]pickles the instance and saves to the aforementioned file
[/LIST]
All of this works fine.  In a second program, *cbt.py*, I attempt to read and unpickle the save file.  It's a short program (for now), so it's posted below:


```

#!/usr/bin/env python

import random
import pickle
import player # defines the 'PC' class

loadChar = open('save/pc/player_character.creature', 'r+') # save/pc/<CHARACTER NAME>
# The save/pc tree branches off from this one.

pc = pickle.load(loadChar)

print pc.name


```Running this program gives the following error message: 


```

Traceback (most recent call last):
  File "cbt.py", line 19, in <module>
    pc = pickle.load(loadChar)
  File "/usr/lib/python2.7/pickle.py", line 1378, in load
    return Unpickler(file).load()
  File "/usr/lib/python2.7/pickle.py", line 858, in load
    dispatch[key](self)
  File "/usr/lib/python2.7/pickle.py", line 1090, in load_global
    klass = self.find_class(module, name)
  File "/usr/lib/python2.7/pickle.py", line 1126, in find_class
    klass = getattr(mod, name)
AttributeError: 'module' object has no attribute 'PC'

```I'm at a loss for what's wrong and Google searches haven't turned anything up.  Both player.py and cbt.py are in the right directories, but for some reason cbt.py can't unpickle player_character.creature. I should mention that I'm fairly new at this, so apologies in advance if I've missed something obvious.  Thoughts/suggestions?

---

### Post by nvteighen on 2012-04-17
Hm... my bet is that you're dumping the character module or class instead of dumping an *instance* of it. That's why it's failing: because you can't get the attribute name of something that is not an instance!

However, there might be cases in which loading/dumping a class is what you need. What is it exactly that you're trying to achieve? Some kind of plugin system?

---

### Post by Pharnavaziani on 2012-04-17
Thanks for replying!  I was getting worried....

I'm in a school course - introduction to programming games with Python and Pygame - and the final is to create your own game.  My partner and I decided to try a very small, survival RPG with a turn-based combat minigame (a la Final Fantasy, Pokemon, etc.,).  The 'Player' file originally create a character, which the player stats out, and saves that character through Pickle to another file.  This 'Combat' file seeks to use that saved data in the combat minigame.  I considered having save files just be CSV or SQLite databases - I'm a little more comfortable with those - but thought that having the actual object rebuilt in the minigame might be helpful.  I'm beginning to rethink that....

If you have any suggestions on how I can fix this with Pickle, I'm all ears.  Otherwise, it's back to the drawing board with a database.

---

### Post by nvteighen on 2012-04-18
OK. Then it makes sense to do this in Pickle.

My bet is that you're dumping the object incorrectly. Could you send us the code you're using to do it? Or some reduced example? The idea is to call pickle.dump() on the object instance... but it might happen that you are doing that accidentally on something else, e.g. the whole class itself. I see no problem in the code loading the object.

---

### Post by Pharnavaziani on 2012-04-18
> **nvteighen said:**
> OK. Then it makes sense to do this in Pickle.

My bet is that you're dumping the object incorrectly. Could you send us the code you're using to do it? Or some reduced example? 

Sure, here's most of the Character Generator script.  At the moment, it just lets you put in whatever stats you want, and puts them into an instance of the object.

```

import pickle

# This file defines and generates the character initially!

class PC(object):
    def __init__(self, name, hp, physical, mental, status):
        self.name = name
        self.hp = hp
        self.physical = physical
        self.mental = mental
        self.status = status

def character_creation():
    nom = raw_input("Enter a player name: ")
    hip = raw_input("how many hit points? ")
    hip = int(hip)
    body = raw_input("How strong and fit: ")
    body = int(body)
    mind = raw_input("How clever and wise: ")
    mind = int(mind)
    return nom,hip,body,mind


nom, hip, body, mind = character_creation()

Nom = PC(nom, hip, body, mind, 'healthy')

inproperNoun = Nom.name.lower()


savNom = "save/pc/"+inproperNoun+".creature"
print savNom   # for debugging.  I've confirmed the file it's printing to is correct, and that it's actually printing there.

savChar = open(savNom, 'w')
pickle.dump(Nom, savChar)

```> 
The idea is to call pickle.dump() on the object instance... but it might  happen that you are doing that accidentally on something else, e.g. the  whole class itself. I see no problem in the code loading the object.You said earlier that Pickle made sense for this.  If we can't find a solution, do you think it'd be worth it to use a CSV file or SQLite database instead?  I'm a little more practised at using those kinds of methods, though the actual operation is uglier and less elegant.

---

### Post by Tony Flury on 2012-04-19
you need to close the file after doing the pickle.dump - although that shouldn't be the issue since the program exits immediately after the pickle.dump.

Also you need to make sure that your player module does actually define the PC class with exactly the same attributes that the dump program uses - I notice that your dump program does not import the player module, so effectively it is dumping a similar (but maybe slightly different) class of object.

---

### Post by Pharnavaziani on 2012-04-19
I found a minor error in my original program, which fixed the first error message and made the program load the object instance!

But I have a new problem:  I have to hard-code the general object into the combat minigame.  When I just use 'import player' and run the o program, I get the following error message:

```

Traceback (most recent call last):
  File "cbt.py", line 19, in <module>
    pc = pickle.load(loadChar)
  File "/usr/lib/python2.7/pickle.py", line 1378, in load
    return Unpickler(file).load()
  File "/usr/lib/python2.7/pickle.py", line 858, in load
    dispatch[key](self)
  File "/usr/lib/python2.7/pickle.py", line 1090, in load_global
    klass = self.find_class(module, name)
  File "/usr/lib/python2.7/pickle.py", line 1126, in find_class
    klass = getattr(mod, name)
AttributeError: 'module' object has no attribute 'PC'

```

But creating the object in cbt.py fixes this.  I'd prefer to just load out of a single file, is there a different way I should be trying to load out of player.py?

---

### Post by Tony Flury on 2012-04-20
Can you post your revised code - it is not clear what you mean.

---

### Post by Pharnavaziani on 2012-04-20
> **Tony Flury said:**
> Can you post your revised code - it is not clear what you mean.

The code below works fine now:

```

#!/usr/bin/env python

import pickle

class PC(object):
    def __init__(self, name, hp, physical, mental, status):
        self.name = name
        self.hp = hp
        self.physical = physical
        self.mental = mental
        self.status = status


loadChar = open('save/pc/matt.creature', 'r+')

pc = pickle.load(loadChar)

print pc.name
print pc.hp

```

But this code does not:

```

#!/usr/bin/env python

import pickle
import player

loadChar = open('save/pc/matt.creature', 'r+')

pc = pickle.load(loadChar)

print pc.name
print pc.hp

```

In the end, I'd like to just be able to import my object, rather than manually add it to every new script.

---

### Post by Tony Flury on 2012-04-20
When you save your pickle file - do you create the object from a PC object created via the player module - I think pickle object use the fully qualified name (of sorts) so to pickle the two instances will be different (even if they have all the same attributes).

I would expect your save code to look something like this : 

```

#!/usr/bin/env python

import pickle
import player

pc = player.PC(name="Matt",  hp=100, physical=30, mental=40, status="alive")

SaveChar = open('save/pc/matt.creature', 'w')

pickle.dump(pc, SaveChar)

SaveChar.close()


```

---

### Post by Pharnavaziani on 2012-04-20
> **Tony Flury said:**
> When you save your pickle file - do you create the object from a PC object created via the player module

No, 'player.py' is just the name of my own Python file which has the class in it. I've had to include it locally in other files, too....that's what I want to be able to do here.



 >  think pickle object use the fully qualified name (of sorts) so to pickle the two instances will be different (even if they have all the same attributes).

I would expect your save code to look something like this : 

```

#!/usr/bin/env python

import pickle
import player

pc = player.PC(name="Matt",  hp=100, physical=30, mental=40, status="alive")

SaveChar = open('save/pc/matt.creature', 'w')

pickle.dump(pc, SaveChar)

SaveChar.close()


```
The idea for this script is it will eventually form a character creation back-end.  I've got the character creation part as sophisticated as it needs to be at this moment, now I need to hook that pickled instance - saved in a file - to the actual game files.

---

### Post by Tony Flury on 2012-04-21
> 
When you save your pickle file - do you create the object from a PC object created via the player module
No, 'player.py' is just the name of my own Python file which has the class in it. I've had to include it locally in other files, too....that's what I want to be able to do here.

since player.py is a file which you import - it is effectively a module.

> 
The idea for this script is it will eventually form a character creation back-end. I've got the character creation part as sophisticated as it needs to be at this moment, now I need to hook that pickled instance - saved in a file - to the actual game files.

Yes - I understand what you need. When you use pickle - every time you load or dump data you have to use the same object definition - i.e. if one programm tries to use a PC object as defined in player.py, then other programs also need to use the same definition - i.e. player.PC.


so your player.py should be like this : 

player.py
```

class PC(object):
    def __init__(self, name, hp, physical, mental, status):
        self.name = name
        self.hp = hp
        self.physical = physical
        self.mental = mental
        self.status = status

```

and then you can use it like this : 

save.py:
```

import player
import pickle

myPlayer = player.PC(name="Matt",  hp=100, physical=30, mental=40, status="alive")

SaveChar = open('save/pc/matt.creature', 'w')

pickle.dump(myPlayer, SaveChar)

SaveChar.close()

```

and read it like this :

load.py:
```

import player
import pickle

SaveChar = open('save/pc/matt.creature', 'r')

myPlayer = pickle.load(SaveChar)

SaveChar.close()
print myPlayer.name, myPlayer.hp

```

when you do the above (as I suggested) what happens ?

BTW - i have tested the above code : 

```

tony@laptop:~/Development/python/player$ python save.py
tony@laptop:~/Development/python/player$ ls save/pc/
matt.creature
tony@laptop:~/Development/python/player$ python load.py
Matt 100
tony@laptop:~/Development/python/player$ 

```
as you can see this correctly creates saves and then loads your object.

---

### Post by Pharnavaziani on 2012-04-25
> **Tony Flury said:**
> since player.py is a file which you import - it is effectively a module.


Yes - I understand what you need. When you use pickle - every time you load or dump data you have to use the same object definition - i.e. if one programm tries to use a PC object as defined in player.py, then other programs also need to use the same definition - i.e. player.PC.


so your player.py should be like this : 

player.py
```
Beyrl Bell
class PC(object):
    def __init__(self, name, hp, physical, mental, status):
        self.name = name
        self.hp = hp
        self.physical = physical
        self.mental = mental
        self.status = status

```and then you can use it like this : 

save.py:
```

import player
import pickle

myPlayer = player.PC(name="Matt",  hp=100, physical=30, mental=40, status="alive")

SaveChar = open('save/pc/matt.creature', 'w')

pickle.dump(myPlayer, SaveChar)

SaveChar.close()

```and read it like this :

load.py:
```

import player
import pickle

SaveChar = open('save/pc/matt.creature', 'r')

myPlayer = pickle.load(SaveChar)

SaveChar.close()
print myPlayer.name, myPlayer.hp

```when you do the above (as I suggested) what happens ?

BTW - i have tested the above code : 

```

tony@laptop:~/Development/python/player$ python save.py
tony@laptop:~/Development/python/player$ ls save/pc/
matt.creature
tony@laptop:~/Development/python/player$ python load.py
Matt 100
tony@laptop:~/Development/python/player$ 

```as you can see this correctly creates saves and then loads your object.

Thanks!  This, plus the line, *from player import * , *fixed my problem!  I have other issues, but they're not really relevant to pickle or this thread.

---

### Post by Tony Flury on 2012-04-25
Using :
```

from player import *

```
In my opinion it s not the best idea as your player module could define names which end up hiding other names which you need access too (i.e. it pollutes the global namespace)

It is far better to use : 
```

import player

```
and then using qualified names : 
```

e.g. :
player.PC

```

or use :
```

from player import PC

```
Which then means you can use "PC" instead of "player.PC"

---

