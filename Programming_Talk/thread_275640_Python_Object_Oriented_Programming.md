---
title: "Python: Object Oriented Programming"
date: 2006-10-11
forum: Programming Talk
---

### Post by walesmd on 2006-10-11
I have a file ("data/map1.map") that is a cPickle dump an object Template(). This object has a num_layers field.

Now let's say I have the following code, with DisplayMap.enter() as my entry point into my program (note - not complete code, just a portion of it:
```

import cPickle as pickle

class DisplayMap(Scene):
    def enter(self):
        tiles = Tilemap('data/map1.map')
        tiles.display()

class Tilemap:
    def __init__(self, filename):
        f = file(filename)
        self = pickle.load(f)
        print "\nTest #1:", self.num_layers

    def display(self):
        print "\nTest #2:", self.num_layers

```

Why is it that Test #1 (found in Tilemap.__init__) responds correctly but test #2 (found in Tilemap.display) returns a AttributeError: Tilemap instance has no attribute 'num_layers'

Is it because self is referring to something else, and not the tilemap instance of Tilemap()? What would it be referring to?

---

### Post by walesmd on 2006-10-11
I'm thinking because it's not going to be as simple for me to populate the object in-code with the object from file, am I going to have to cycle through all of the fields of the object in file (which has a lot more than just num_layers) to populate my new object in code?

Is there some magical code snippet that will replicate an object for me?

---

### Post by dabear on 2006-10-11
yeah, .load() only gives one object at a time. You would need to run a while loop until you get an EOFError (that mean there are no more pickled objects left). This is what we have generators for :D

That way, you could do just a for apickledobj in pickledfile('filename') to get all objects in unpickled form.

---

### Post by walesmd on 2006-10-11
I've only been using Python for a week - so I'm not quite following along with you.

I think I forgot to mention that the pickle dump is of an entire class. :o

I did manage to get it to work, I changed my Tilemap.__init__ function to the following:
```

def __init__(self, filename):
    f = file(filename)
    mapfile = pickle.load(f)
    self.num_layers = mapfile.num_layers
    self.layers = mapfile.layers
    self.imagemap = mapfile.imagemap

```

I can then use the self. objects as I expected.

Now I am attempting to get my dummy "map generator" to only save certain data out of the class and not the various functions it uses (which won't be present in it's final version).

---

