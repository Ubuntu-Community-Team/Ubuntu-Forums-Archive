---
title: "&quot;scripting&quot; with python"
date: 2011-01-03
forum: Programming Talk
---

### Post by skullmunky on 2011-01-03
I'm not sure what the exact term is for what I'm trying to do; 'scripting' seems to be closest, by which I mean something different from 'programming'.

I'm working on something like a game editor, and I want to be able to add arbitrary bits of python code as event handlers to game objects, via a GUI editor or just within data structures describing the game scene.  I'm thinking of things like Director's Lingo/Javascript, Flash's ActionScript, Unity3D's Javascript and C#, or Second Life's LLScript, for example.

I think what I'm trying to do is dynamically add code to objects at runtime. 

basic examples of how this would be used:

- a door which can only open if you have the key
- a gate which opens if you flip a lever in another room
- a trapdoor hidden under a rug

I see 3 possibilities so far:

1) use new.function() and new.instancemethod() to bind methods onto the object
2) create a signal system, where the object has a dict of signals and code strings
3) make everything actually a subclass, but disguise that fact in the editor GUI

what's the most pythonic?

---

### Post by dv3500ea on 2011-01-04
I would just use the event system supplied by the 'gobject' module. Simply subclass your object classes from gobject.GObject and you have a simple event system.

eg.

```


import gobject

class A(gobject.GObject):
    __gsignals__ = {
        'fire' : (gobject.SIGNAL_RUN_LAST, gobject.TYPE_NONE,
            [gobject.TYPE_PYOBJECT]
        )
    }
    def __init__(self, val):
        super(A, self).__init__()
        self.val = val
    def fire(self):
        #this fires the 'fire' event.
        #Any methods connected to this will be called
        self.emit('fire', self.val)

def print_func(obj, val):
    print(val)

a = A('BOO!')
a.connect('fire', print_func) #connect method print_func to fire event
a.fire()


```

---

### Post by skullmunky on 2011-01-05
Thanks, I'll give that a try.  That's right, no need to reinvent the wheel! 

Now, the thing I need to do is have that function be generated from a string.  I'd want to be able to make a data file sort of like this:

```

<object id="Gold Door">
  <model file="data/door.obj"/>
  <animlist>
    <anim id="open" file="data/door_open.anim"/>
  </animlist>
  <script language="python_obviously">
    def onClick(self):
      if player.hasItem("Gold Key"):
        self.playAnimation("open")
      else:
        textoutput("You don't have a key to open this door")
  </script>
</object>

```

In this scenario this is a 3D engine we're playing with, there's collision detection on the door model, and the open animation moves it out of the way so you can walk past it; there's also a theoretical text notification system and global player object ... anyway that should get the idea across, I hope. 

there's also theoretically an event manager which handles the mouse interaction stuff and sends the click event.

---

