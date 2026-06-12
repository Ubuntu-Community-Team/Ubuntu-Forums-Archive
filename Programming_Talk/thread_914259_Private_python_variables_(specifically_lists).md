---
title: "Private python variables (specifically lists)"
date: 2008-09-08
forum: Programming Talk
---

### Post by jonthysell on 2008-09-08
I've been searching forever on this, but all I can find is references to mailing lists (instead of python list objects).

I have a class that needs to contain a collection of a specific type of object. Namely, a Graph object contains a list of Vertex objects, and a separate list of Edge objects.

An Edge object connects two Verticies, and so stores references to those two instances.

Verticies can belong to only one Graph, and Edges can only link Verticies within a single Graph.

Basically I want to allow access to the Graph's lists, without letting people append/remove objects directly, because if a Vertex is removed, then I need to remove all edges associated with it.

My current solution is to have two private lists __verticies and __edges within Graph, with functions to return iterators (for access), append and remove verticies, etc. It looks kludgey.

Basically, is there a way to fire a function when a list's append/remove is called, without sub-classing list? I need to prevent the adding of malformed Edges/Verticies, and remove the proper ones when necessary.

Or another approach? I'm open to the idea that I'm approaching the whole thing from the wrong perspective. Recovering Java programmer ;).

I'd like to have .verticies and .edges as just properties, but then I can only control the setting/getting not the whole list, not its functions.

---

### Post by pmasiar on 2008-09-09
In Python you usually trust callers not to mess with private attributes.

If you want magic getters/setters, you may want to look at property builtin [http://adam.gomaa.us/blog/the-python-property-builtin/](http://adam.gomaa.us/blog/the-python-property-builtin/) or a decorator.

---

### Post by Wybiral on 2008-09-09
If you just want to have an instance of a list without them being append/remove/set-able, you wouldn't have to subclass it. Just wrap it in some closure :)

```
[color=#008000]**class**[/color] [color=#0000FF]**ReadOnly**[/color]:
    [color=#008000]**def**[/color] [color=#0000FF]__init__[/color]([color=#008000]self[/color], obj):
        [color=#008000]self[/color][color=#666666].[/color]__len__ [color=#666666]=[/color] obj[color=#666666].[/color]__len__
        [color=#008000]self[/color][color=#666666].[/color]__iter__ [color=#666666]=[/color] obj[color=#666666].[/color]__iter__
        [color=#008000]self[/color][color=#666666].[/color]__getitem__ [color=#666666]=[/color] obj[color=#666666].[/color]__getitem__

obj [color=#666666]=[/color] [[color=#666666]1[/color], [color=#666666]2[/color], [color=#666666]3[/color], [color=#666666]4[/color]]
locked [color=#666666]=[/color] ReadOnly(obj)

[color=#008000]**print**[/color] locked[[color=#666666]0[/color]]
[color=#008000]**print**[/color] [color=#008000]len[/color](locked)
[color=#008000]**print**[/color] [x [color=#008000]**for**[/color] x [color=#AA22FF]**in**[/color] locked]

locked[[color=#666666]0[/color]] [color=#666666]=[/color] [color=#BA2121]"Test"[/color]

```

---

### Post by jonthysell on 2008-09-09
I'm just not sure which is more pythonic, since I want public access to the lists, but to perform cleanup operations when items are added/removed.

I've come up with a few solutions:

1. Keep it private, and have methods to access its iterator, and to add/remove items.
2. Keep it private, with add/remove methods, but have a get-only property that returns a [:] slice (so add/remove calls don't affect the internal list).
3. Subclass list, then override the add/remove methods.

Is any of them a standard paradigm in python?

---

### Post by Wybiral on 2008-09-09
Oh, you don't want to not-allow those operations, you just want to do extra stuff with them? In that case, just subclass list (conceptually, that's what you want).

---

### Post by jonthysell on 2008-09-09
I'm not sure what I want. ;)

I'm not sure which is more expected of a Python class that stores a collection of items and needs to maintain the validity of the items stored.

Is it more expected in the Python community to have public list attribute to which they may use append, remove, index, etc (in which I really give them a sub-class of list within which I intercept those methods) or do I simply have a private list and provide my own limited add/remove/iter functions within the class (which is what I'm doing now).

I'm trying to avoid being "too clever" about it, or apply a different language's idioms.

---

### Post by pmasiar on 2008-09-09
you are being too clever.

get list as private (_list), and provide methods. You don't have to subclass list if it does not make sense.

Do simplest thing which will work, release it, and ask for input.

---

