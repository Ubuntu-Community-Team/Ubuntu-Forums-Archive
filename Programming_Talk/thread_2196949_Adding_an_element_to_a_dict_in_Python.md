---
title: "Adding an element to a dict in Python"
date: 2014-01-01
forum: Programming Talk
---

### Post by blackout2 on 2014-01-01
I have a dict, let's say that it's called ```
my_dict
```, and it's contents are as follows:```
{"Value1": Value1(), "Value2": Value2()}
```, and I want to add ```
"Value3", Value3()
``` to it. I could just do this: ```
my_dict.update({"Value3": Value3})
```. But, that's where I would run into a problem, you see, this needs to be OOP, so I won't actually know what "Value3" is, I can use a variable for the key, but when I try to use a variable for the content(Value3()), it won't take it in, because you can't put, let's call it```
my_variable
``` with a () at the end. This is the problem: ```
 my_dict[my_variable] = my_variable()
```, but the dict can't do that, because no "my_variable()" function or class exists.

How do I get Python to add a set of parentheses to the end of a variable?

---

### Post by Vaphell on 2014-01-01
so you want to magically translate a plain string to a valid object/method/function?
what do you need it for?

---

### Post by ofnuts on 2014-01-01
You don't need to:
```

>>> def foo(x): return x*x
... 
>>> foo(2)
4
>>> dict={}
>>> dict['function']=foo
>>> print dict
{'function': <function foo at 0x7fdfab4072a8>}
>>> dict['function'](3)
9

```

In other words, above the "thing" named "foo" in python is a function, and you can add it to a dictionary. The parentheses() are not part of its name...they are a "call function" operator, so to speak, that applies to the term on their left. This term can be the name of the function, or the result of a dictionary fetch, as above.

For simple expressions, you can even skip the function definition and use a lambda expression directly:
```

>>> dict['lambda']=lambda t:t**2
>>> dict['lambda'](4)
16

```

---

### Post by blackout2 on 2014-01-01
Really? Oh, well thanks ofnuts!
Now I have another question, what if I wanted to do this?
```

Operations.KeyNames[self.key_names] = Operations.Content[self.key_names]

```
But, it can't do that if whatever self.key_names is doesn't already exist in Operations.KeyNames. I hope you understand what I'm trying to do...

---

### Post by Vaphell on 2014-01-01
> **blackout2 said:**
> Really? Oh, well thanks ofnuts!
Now I have another question, what if I wanted to do this?
```

Operations.KeyNames[self.key_names] = Operations.Content[self.key_names]

```
But, it can't do that if whatever self.key_names is doesn't already exist in Operations.KeyNames. I hope you understand what I'm trying to do...

didn't you mean *doesn't already exist in Operation.Content*? You extract data from Content and put it in KeyNames.
simple if will solve it
```
if self.key_names in Operations.Content:
    Operations.KeyNames[self.key_names] = Operations.Content[self.key_names]
```
What should happen if it doesn't exist?



Could you describe the program you are writing/show relevant pieces of code? Because it looks like a relatively common beginner's mistake where you paint yourself into a corner with your vision and feel you absolutely need feature X or Y to solve your problem, but in reality the whole program structure is not sound and what you really need is stepping back and looking at things again from a different angle.

---

### Post by ofnuts on 2014-01-01
> **blackout2 said:**
> Really? Oh, well thanks ofnuts!
Now I have another question, what if I wanted to do this?
```

Operations.KeyNames[self.key_names] = Operations.Content[self.key_names]

```
But, it can't do that if whatever self.key_names is doesn't already exist in Operations.KeyNames. I hope you understand what I'm trying to do...
If "*[FONT=lucida console]Operations.KeyNames[/FONT]*" is a dictionary then the key "*[FONT=lucida console]self.key_names[/FONT]*" doesn't need to be in it and the operation above will add the key/value pair "*[FONT=lucida console]self.key_names/Operations.Content[self.key_names][/FONT]*" to the dictionary (otherwise it will just change the value indexed by "*[FONT=lucida console]self.key_names[/FONT]*").

---

### Post by blackout2 on 2014-01-01
> **Vaphell said:**
> didn't you mean *doesn't already exist in Operation.Content*? You extract data from Content and put it in KeyNames.
simple if will solve it
```
if self.key_names in Operations.Content:
    Operations.KeyNames[self.key_names] = Operations.Content[self.key_names]
```
What should happen if it doesn't exist?



Could you describe the program you are writing/show relevant pieces of code? Because it looks like a relatively common beginner's mistake where you paint yourself into a corner with your vision and feel you absolutely need feature X or Y to solve your problem, but in reality the whole program structure is not sound and what you really need is stepping back and looking at things again from a different angle.


I really don't like giving other people my code, because that makes me feel like I'm not learning when you give me the solution.
However, I'll make an exception.
Please note, most of this code will be deleted, and fixed because it's just a rough draft, you only really need to focus on the "AddDragons" method.
Like I said, I will re-do the rest of the code with time, I just want your help with Adding a dragon from the list of dragons(DragonFunctions.dragons), to the list of "owned" dragons(OwnedDragons.owned_dragons).
I'm quite the beginner in Python, so I'm prepared for the harsh "advice" you'll be giving me. 
Thanks for the help.
```



class Coal():
    name = "Coal"
    HP = 100
    BA = 25
    SP = 30


class Hydros():
    name = "Hydros"
    HP = 100        
    BA = 20
    SP = 40
    
class Geon():
    
    name = "Geon"
    HP = 200        
    BA = 10
    SP = 15
    
class Hedger():
    
    name = "Hedger"
    HP = 50
    BA = 10
    SP = 10
    
run_room = "Start"
def Start():
    global run_room
    run_room = "Start"
    os.system("clear")
    print "Hello, and welcome to Dragon World!"
    print "In this game, you collect dragons, and battle against wild ones to level them up."
    print "You will be starting with 1 dragon, please pick which one you want.\n\n"
    print "Coal: A fiery dragon, with medium health, and medium attack.\n"
    print "HP: 100\n"
    print "BA: 25\n"
    print "SP: 30\n"
    print "\n"
    print "Hydros: A cool water dragon, with medium health, a lower attack, but a high special attack.\n"
    print "HP: 100\n"
    print "BA: 20\n"
    print "SP: 40\n"
    print "\n"
    print "Geon: A hard, stony dragon, with a very high health, and a low special and regular attack.\n"
    print "HP: 200\n"
    print "BA: 10\n"
    print "SP: 15\n"
    print "\n"
class Control(object):
    rooms = {"Start": Start()}
    def __init__(self, run_room):
        self.run_room = run_room
    def RunCurrentRoom(self):
        if self.run_room == Control.rooms[run_room]:
            Control.rooms[run_room]
    


class DragonFunctions(object):
    my_dragons = raw_input("> ")
    dragons = {"Coal": Coal(), "Geon": Geon(), "Hydros": Hydros()}
    def __init__(self):
        self.my_dragons = DragonFunctions.my_dragons
    def PrintDragons(self):    
        if self.my_dragons == DragonFunctions.dragons[self.my_dragons].name:
            print DragonFunctions.dragons[self.my_dragons].name, ":"
            print "HP: ",DragonFunctions.dragons[self.my_dragons].HP
            print "BA: ",DragonFunctions.dragons[self.my_dragons].BA
            print "SP: ",DragonFunctions.dragons[self.my_dragons].SP
        else:
            print "I don't understand that, sorry."


    def AddDragons(self):
        try:    
            self.my_dragons == OwnedDragons.owned_dragons[self.my_dragons] and self.my_dragons == OwnedDragons.owned_dragons_list[self.my_dragons]        
            print "You already own", self.my_dragons
        except:
            print OwnedDragons.owned_dragons
            OwnedDragons.owned_dragons_list.append(self.my_dragons)
            OwnedDragons.owned_dragons[self.my_dragons] = DragonFunctions.dragons[self.my_dragons]
            print "You now own", OwnedDragons.owned_dragons_list
class OwnedDragons(object):
    owned_dragons_list = ["Geon"]
    owned_dragons = {"Geon": Geon}
    def __init__(self):
        self.owned_dragons = OwnedDragons.owned_dragons


control = Control(run_room)
control.RunCurrentRoom()
DragonFunctions = DragonFunctions()
OwnedDragons = OwnedDragons()
DragonFunctions.AddDragons()

```

So far I can get the code to operate to a degree, I just can't figure out how to assign an *unknown* value to an *unknown* key in a dict.
By the way, I know that "my_dragons" is a horrible dict name, I will fix it eventually, on my own time.

Well thank you ofnuts, it seems that your solution *did* work, I just didn't realize that I was printing out my list, not the dict. Thank you for your help, it works like a charm now!

Problem solved, and yes, I know, my code is horrible :D

---

### Post by ofnuts on 2014-01-01
***"I know, my code is horrible :grin:"***

I totally agree with that... But since you figured that out yourself you have no excuse to not fix/clean it...  Cleaning up your code will make you ask yourself the right questions (at least, some of them).

---

### Post by Vaphell on 2014-01-01
i am not going to give you a bunch of code and say don't ask what it does, trust me, it works :-) I can give an example showcasing stuff, but it's up to you to absorb it and see what it can be used for.



Is there a reason you got separate class for each dragon? Imo you should have only 1 class, surprisingly enough called Dragon ;-), as it should be enough to describe all the common things your dragons share, and use it for all your majestic creatures.

If you need to specialize your dragons further you can use inheritance to add functionality, eg
```
class BlackDragon( Dragon ):
    <some black dragon stuff>
```
In case you want to have other types of creatures too you may want to create an abstract Creature class (eg having hp,ba,sp) and derive the Dragon class(es) from it


Another issue i see is that at least some of your printed descriptions are not tied to the object they are related to (even though there seems to be a code that prints dragon info) and maintainability will suffer. Should any values change due to balance reasons or whatever, you would have to track and update manually in multiple places to maintain coherence. Good design would be based on a single set of master data and everything would query it when needed, so you never have to deal with contradictory duplicates.


Quick and dirty example

```

#!/usr/bin/env python

def walk( obj ):
    print '- {0} walks'.format( obj.name )
def fly( obj ):
    print '- {0} flies'.format( obj.name )
def breathe_fire( obj ):
    print '- {0} breathes fire'.format( obj.name )
def resist_magic( obj ):
    print '- {0} resists magic'.format( obj.name )
def stone_skin( obj ):
    print '- {0} has stone skin'.format( obj.name )
def fit_in_pokeball( obj ):
    print '- {0} fits in a poke ball'.format( obj.name )
def look_cute( obj ):
    print '- {0} looks cute'.format( obj.name )

class Creature:
    class_actions = [ walk ]
    def __init__( self, _name, _hp, _ba, _sp, _actions, _desc ):
        self.name = _name
        self.hp = _hp
        self.ba = _ba
        self.sp = _sp
        self.desc = _desc
        self.actions = self.class_actions[:]
        for a in _actions:
            self.actions.append(a)
    def info( self ):
        print '{0}: {1}\nHP: {2}\nBA: {3}\nSP: {4}'.format( self.name, self.desc, self.hp, self.ba, self.sp )
        for a in self.actions:
            a( self )

class Pokemon( Creature ):
    class_actions = [ walk, fit_in_pokeball ]

class Dragon( Creature ):
    class_actions = [ walk, fly, resist_magic ]

  

beasts = { 'Pikachu': Pokemon( 'Pikachu', 30, 20, 20, [ look_cute ],
                               'A cute, little pokemon of yellow color' ),
           'Coal':    Dragon( 'Coal', 100, 25, 30, [ breathe_fire ],
                              'A fiery dragon, with medium health, and medium attack' ),
           'Hydros':  Dragon( 'Hydros', 100, 20, 40, [],
                              'A cool water dragon, with medium health, a lower attack, but a high special attack' ),
           'Geon':    Dragon( 'Geon', 200, 10, 15, [ stone_skin ],
                              'A hard, stony dragon, with a very high health, and a low special and regular attack' ) }



if __name__ == '__main__':
    print 'Available beasts:'
    for name in beasts:
        beasts[name].info()

    

```


```

$ ./creatures.py 
Available beasts:
Coal: A fiery dragon, with medium health, and medium attack
HP: 100
BA: 25
SP: 30
- Coal walks
- Coal flies
- Coal resists magic
- Coal breathes fire
Pikachu: A cute, little pokemon of yellow color
HP: 30
BA: 20
SP: 20
- Pikachu walks
- Pikachu fits in a poke ball
- Pikachu looks cute
Hydros: A cool water dragon, with medium health, a lower attack, but a high special attack
HP: 100
BA: 20
SP: 40
- Hydros walks
- Hydros flies
- Hydros resists magic
Geon: A hard, stony dragon, with a very high health, and a low special and regular attack
HP: 200
BA: 10
SP: 15
- Geon walks
- Geon flies
- Geon resists magic
- Geon has stone skin

```


there is *None* keyword in python, that is used to describe emptiness

```
$ python
Python 2.7.4 (default, Apr 19 2013, 18:32:33) 
[GCC 4.7.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> x={ 1: None, None: 1 }
>>> for k in x:
...   if k is None:
...     print 'key is empty, value =', x[k]
...   elif x[k] is None:
...     print 'value is empty, key =', k
... 
value is empty, key = 1
key is empty, value = 1
```

---

### Post by blackout2 on 2014-01-01
Yep, you're absolutely correct and I'm planning on changing my code to be better, as I learn more about Python. So, I'll definitely use that kind of code in my own program. As you can probably tell, some of the code is taken from a different project(Control class), and I'm going to replace that, and add inheritance with my "dragons" after I get some things squared away(AddDragon was the last one).

---

