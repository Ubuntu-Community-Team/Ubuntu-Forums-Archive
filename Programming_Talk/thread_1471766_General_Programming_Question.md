---
title: "General Programming Question"
date: 2010-05-03
forum: Programming Talk
---

### Post by xaegis on 2010-05-03
I am a beginning Programmer using Python and am having trouble wrapping my head around WHY I would create a class. Procedural programming I get, but object orientation I would like a little help with.

Say I was creating a GURPS character and I wanted to store his stats.
```

#!/usr/bin/env python3



#name
name = raw_input ("What is your characters name?")
#stats
str = raw_input ("What is your characters Strength score?")
int = raw_input ("What is your characters Intelegence score?")
dex = raw_input ("What is your characters Dexterity score?")
heal = raw_input ("What is your characters Health score?")

#print your character
print "Name:",name
print "Strength:	 ",str
print "Intelegence:	 ",int
print "Dexterity:	 ",dex
print "Health:		 ",heal

```

Easy peasy! But how, and more importantly WHY would I do this as an object?

```

class GurpChar(object):
	"""this class is the player character"""
	def __init__(self,name =None,str=None,dex=None,heal=None,int=None):
		self.name = name
		self.str = str
		self.dex = dex
		self.heal = heal
		self.int = int
		return self.name


```

I just cant wrap my mind around it. I've been searching the internet for a dialog about why one would use Objects and Classes and Functions,and cannot seem to find one which is understandable. Is it is just "the norm"?

Thanks for your input,
:)

---

### Post by wmcbrine on 2010-05-03
You have to imagine a much more complicated program than the one you posted. Already, in your first example, you have five global variables. (BTW, "str" and "int" have meaning in Python, and although they're technically not reserved, you should avoid using them for your own variables.) Now suppose you have two characters, each with the same five attributes... or ten characters... or a hundred.

Not that this alone would necessarily justify the use of a class. In some languages, it would -- there'd be no other sensible way to deal with it. In Python, you might consider a dict instead.

You might get a feel for how classes are used just by studying some existing code.

---

### Post by Portmanteaufu on 2010-05-03
The reason for using classes becomes obvious when you start dealing with larger collections of an object. Imagine that you are going to make a game that has players as you describe, but there can be 100 players on the screen at any time.

Being able to talk about "this character does this" or "this character attacked that character" becomes far, far easier to mentally manage with objects:

```

# p1's weapon damage is calculated, p2's armor is calculated, p2's health decreases as necessary
p1.attack(p2) 

# p1's "hp" field has been restored to 100!
p1.drink_potion() 

# p1's "gold" field has increased behind the scenes!
p1.sell("rusty shortsword") 

```

You get to write lines of code that are only a hop, skip and a jump from the way you're already naturally thinking about what needs to happen.

The alternative (making variables and arrays to keep track of all possible statistics) would be a terrible mess to keep track of. (It can be done, obviously -- consider all the games written in plain ol' C. It's just a pain.)

---

### Post by trent.josephsen on 2010-05-03
> **Portmanteaufu said:**
> The alternative (making variables and arrays to keep track of all possible statistics) would be a terrible mess to keep track of. (It can be done, obviously -- consider all the games written in plain ol' C. It's just a pain.)

Look at NetHack's source.  It uses the techniques you've described as benefits of using classes, and is written in mostly pre-ANSI C if I recall correctly.

---

### Post by Portmanteaufu on 2010-05-03
> **trent.josephsen said:**
> Look at NetHack's source.  It uses the techniques you've described as benefits of using classes, and is written in mostly pre-ANSI C if I recall correctly.

Ahh, really? That shouldn't surprise me, I suppose. I guess there're structs all over the place, eh? Good ol' struct! :)

I didn't mean to imply that it wasn't possible to write clean, organized functions / structures in C -- it's just that C++ adds so many features to simplify the process.

---

### Post by trent.josephsen on 2010-05-03
Agreed, although personally I'm not a big fan of C++ from what I've seen of it.  My main point was that the things most people associate with "object-oriented design" (e.g. data abstraction, user-defined types, etc.) are in fact much older.  The main thing that OOP brought into the mix was dynamic binding, and even that existed before, although in a much less usable state.

Good design transcends the limitations of individual languages.

---

### Post by vek on 2010-05-03
You can do most of what you can do in c++ using your OWN virtual function tables, with structs and so forth, but there's a huge difference between a system that was designed with OOP in mind and one that was done with ANSI-C in mind and then converted into something OOP.

Object Oriented programming starts to shine when you're working on collections of objects with similar traits, and that inherit from a hierarchy, implement interfaces, are iterable due to those interfaces, etc.

Putting everything into a container like in the above example is not an example of OOP, merely one aspect of it (encapsulation).  The power of object oriented programming comes into play more in statements like:
```

for each thing in collection:
   thing.think()

```

where each "thing" is a child of some base class that has an overridable think function, but could be doing a wildly different thing.  As oppsed to the more non-oop way of doing things:
```

function globalThinkFunction(typeOfThing):
  if (typeOfThing == thingTypeHuman):
    globalThinkHuman(..)
  else if (typeOfthing == ...)
   ..

```

And so on... or the ever popular method, where a function pointer is set to the appropriate method first, where you have an array of type-of-things-to-functions-they-call, or you store a function pointer in each struct that is its think function but at that point, you're just basically doing the same thing except clumsily and non-standardly and probably making memory bugs.


This functionality can be achieved in C using function pointers, virtual function table, etc, but then you're just essentially implementing C++ in C anyway... and probably making mistakes that the C++ folks have had decades to encounter and fix.

---

### Post by xaegis on 2010-05-03
Wow, Great stuff everyone. Thanks!
I'm going to explore some more code and see what I can see.

Thanks again.:)

---

