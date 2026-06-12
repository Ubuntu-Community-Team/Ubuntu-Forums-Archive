---
title: "python n00b"
date: 2010-03-17
forum: Programming Talk
---

### Post by HarrisonNapper on 2010-03-17
Ok, let me preface this by saying this is NOT homework. No comp sci teacher would give out homework to write something that is the same as an instantiation (I hope). Test was a globally defined dictionary and was declared as "test = {'browser': None, 'os': None, 'jre': None}"

```

>>> class Master:
    def __init__(self, testUser):
        self.testUser = testUser
    def objToInst(self, d):
        dres = {}
        for k in d.keys():
            dres[k] = []
            i = int(raw_input("How many %s? " % (str(k))))
            for j in range(i):
                a = str(raw_input("Enter %s %s: " % (str(k), str(j))))
                dres[k].append(a)
        return dres.copy()
    testUser = {'browser': None, 'os': None, 'jre': None}

    
>>> j = Master.objToInst(test)
Traceback (most recent call last):
  File "<pyshell#27>", line 1, in <module>
    j = Master.objToInst(test)
TypeError: unbound method objToInst() must be called with Master instance as first argument (got dict instance instead)

>>> j = Master.objToInst(Master.testUser)
Traceback (most recent call last):
  File "<pyshell#35>", line 1, in <module>
    j = Master.objToInst(Master.testUser)
TypeError: unbound method objToInst() must be called with Master instance as first argument (got dict instance instead)

```EDIT: And since I realize that I don't understand classes (obviously) and RTFM is indeed in my signature, rest assured that I'm looking in to this as we speak. So far, google has yielded others not a) taking self as an argument, which I did and b) circular importing, which I did not do. Thanks so much to anyone who takes the time to look at this. Much appreciated. Hopefully, my skillz will improve and I can give back to this section of the forums. (also sorry for tl;dr)

---

### Post by n0dix on 2010-03-17
Try with this:
j = Master(Master.testUser)
k = j.objToInst(j)

Only guessing, i don't have much experience with python :(

---

### Post by km0r3 on 2010-03-17
> **HarrisonNapper said:**
> Ok, let me preface this by saying this is NOT homework. No comp sci teacher would give out homework to write something that is the same as an instantiation (I hope). Test was a globally defined dictionary and was declared as "test = {'browser': None, 'os': None, 'jre': None}"

```

>>> class Master:
    def __init__(self, testUser):
        self.testUser = testUser
    def objToInst(self, d):
        dres = {}
        for k in d.keys():
            dres[k] = []
            i = int(raw_input("How many %s? " % (str(k))))
            for j in range(i):
                a = str(raw_input("Enter %s %s: " % (str(k), str(j))))
                dres[k].append(a)
        return dres.copy()
    testUser = {'browser': None, 'os': None, 'jre': None}

    
>>> j = Master.objToInst(test)
Traceback (most recent call last):
  File "<pyshell#27>", line 1, in <module>
    j = Master.objToInst(test)
TypeError: unbound method objToInst() must be called with Master instance as first argument (got dict instance instead)

>>> j = Master.objToInst(Master.testUser)
Traceback (most recent call last):
  File "<pyshell#35>", line 1, in <module>
    j = Master.objToInst(Master.testUser)
TypeError: unbound method objToInst() must be called with Master instance as first argument (got dict instance instead)

```EDIT: And since I realize that I don't understand classes (obviously) and RTFM is indeed in my signature, rest assured that I'm looking in to this as we speak. So far, google has yielded others not a) taking self as an argument, which I did and b) circular importing, which I did not do. Thanks so much to anyone who takes the time to look at this. Much appreciated. Hopefully, my skillz will improve and I can give back to this section of the forums. (also sorry for tl;dr)

You haven't instantiated the class `Master`. Achieve this by:
```
j = Master('Test User') # Requires one argument, because that's defined in the __init__ constructor
```Now I don't know what you want to do with this line:
> ```
j = Master.objToInst(Master.testUser)
```Please explain; you cannot access a variable like you're doing there.

I wrote this a little up so it makes some more sense to me:
```

class Master:
    def __init__(self, testUser):
        self.testUser = testUser
    def objToInst(self, d=None): # These are
        if not d:                # the modified
            d = self.testUser    # lines
        dres = {}
        for k in d.keys():
            dres[k] = []
            i = int(raw_input("How many %s? " % (str(k))))
            for j in range(i):
                a = str(raw_input("Enter %s %s: " % (str(k), str(j))))
                dres[k].append(a)
        return dres.copy()
    testUser = {'browser': None, 'os': None, 'jre': None}

user = "invalid"    
j = Master(user) # *Initializing* class requires instantiating class.
j.objToInst() # Now you don't need to pass a value for `d`, by default.
```

I hope you understand now. If not please ask.

Please look at some tutorials. It looks like you still don't understand the basics, but you'll get it soon. Believe me :) .

Hope I could help.

---

### Post by HarrisonNapper on 2010-03-17
> **km0r3 said:**
> You haven't instantiated the class `Master`. Achieve this by:
Now I don't know what you want to do with this line:
```
j = Master.objToInst(Master.testUser)
```
Please explain; you cannot access a variable like you're doing there.


Since objToInst returns a copy of dres, which is a dictionary created from they keys of dict d, but with values that are lists defined by user input, it should work like any other data structure. So that line sets j equal to the copy of dres by performing the method objToInst of the Master class on the attribute (variable afaik) testUser of the Master class. 

Really, my problems here (functionally; zing) were with the class and OOP since when I wrote up the function, it worked just fine. This function can be used in a lot of ways, but think of adding a new item to a game.

```

itemContainer = {'int': None, 'wis': None, 'dex': None, 'bonuses': None}
swordOfFubar = objToInst(itemContainer)

How many int? 1
Enter int 0: 12
How many wis? 1
Enter wis 0: 18
...  #1, 2, skip a few
How many bonuses? 3
Enter bonuses 0: fire shield
Enter bonuses 1: ray of truth
Enter bonuses 2: wearable

```

Obviously, a terrible implementation of item creation, but just an example of how it might be used.

> 
j = Master(user) # *Initializing* class requires instantiating class.
j.objToInst() # Now you don't need to pass a value for `d`, by default.[/CODE]

I hope you understand now. If not please ask.

Please look at some tutorials. It looks like you still don't understand the basics, but you'll get it soon. Believe me :) .

Hope I could help.

Ah, I had tried instantiating the class previously, but did not pass an argument. I'll try this when I wake up, but I already know it will work.

And I indeed do not grasp a lot of the basics, especially when it comes to OOP. I get the concepts, but not well enough to nail down an implementation. Is there a particular tutorial you recommend? I've been using Structure and Interpretation of Computer Programs (MIT OCW and Berkeley Webcast), Python for Beginners, and odds and ends found online. 

Honestly, most of my learning has just been writing little blocks of code and consulting the Python documentation when I'm stuck. Not the best way to learn, but with my attention span, certainly the most effective. If anyone knows of any projects where a beginner can contribute in some way, it would be most appreciated.

---

### Post by km0r3 on 2010-03-18
> 
```

itemContainer = {'int': None, 'wis': None, 'dex': None, 'bonuses': None}
swordOfFubar = objToInst(itemContainer)

```When writing a game, like in your case, saving all keys and values( The user's properties ) in a dictionary is probably not a good idea as the game eventually grows.
Maybe you should additionally define own variables for each property.

```

int = None
wis = None
...

```> 
```

How many int? 1
Enter int 0: 12
How many wis? 1
Enter wis 0: 18
...  #1, 2, skip a few
How many bonuses? 3
Enter bonuses 0: fire shield
Enter bonuses 1: ray of truth
Enter bonuses 2: wearable

```Obviously, a terrible implementation of item creation, but just an example of how it might be used.
OK, now I get it, though it varies a little from the original code you've posted.

> 
And I indeed do not grasp a lot of the basics, especially when it comes to OOP. I get the concepts, but not well enough to nail down an implementation. Is there a particular tutorial you recommend? I've been using Structure and Interpretation of Computer Programs (MIT OCW and Berkeley Webcast), Python for Beginners, and odds and ends found online. 
Don't worry, I'm no OO wizard either.

I recommend you reading these books/articles, which have helped me a lot:
* [Dive into Python]("http://diveintopython.org/")
  * [Dive into Python - Defining classes]("http://diveintopython.org/object_oriented_framework/defining_classes.html")
* [OOP - Voidspace]("http://www.voidspace.org.uk/python/articles/OOP.shtml")

You can cherry-pick the sections you'd like to read and the articles are relatively short. I admit that the Python Reference manual just cannot replace a good-written tutorial/book sometimes.

Not as important, but valuable, too:
* [Python Style Guide]("http://code.google.com/p/soc/wiki/PythonStyleGuide")

But still the best way is learning by Trial and Error, just like you're doing.

Have fun. :)

---

### Post by HarrisonNapper on 2010-03-21
> **km0r3 said:**
> 
I recommend you reading these books/articles, which have helped me a lot:
* [Dive into Python]("http://diveintopython.org/")
  * [Dive into Python - Defining classes]("http://diveintopython.org/object_oriented_framework/defining_classes.html")
* [OOP - Voidspace]("http://www.voidspace.org.uk/python/articles/OOP.shtml")


Thanks much for this. I've been to dive into python once before and I spent one afternoon trying to find it again with no luck. I have bookmark'd it now and have been through the first five chapters. Definitely one of the better I've seen, if not the best.

Thanks again. :)

---

