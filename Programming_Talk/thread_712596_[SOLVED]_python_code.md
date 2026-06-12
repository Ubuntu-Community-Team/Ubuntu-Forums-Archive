---
title: "[SOLVED] python code"
date: 2008-03-01
forum: Programming Talk
---

### Post by bschleusner on 2008-03-01
ok, I have some source to check the sanity of values being put into my function. The problem is that I don't like the way it looks, it seems to bulky for what I want done. Is there a simpler way to write this?

Python code:
```

    if speed < 80:
        speed = 80
    if speed > 370:
        speed = 370
    if amplitude > 200:
        amplitude = 200
    if amplitude < 0:
        amplitude = 0
    if pitch > 99:
        pitch = 99
    if pitch < 0:
        pitch = 0
```

I know, I'm picky about my code.... :D

---

### Post by kaens on 2008-03-01
You could define a function to check it like so:
```

def bounds_check(x, min, max):
    if x < min:
       return min
    if x > max:
       return max
    return x

pitch = bounds_check(pitch, 0, 99)
...

```

There's really a bunch of ways, this way could use some improvement as well.

Edit: if this is only needed in one function, you can define the function within the function that it's needed in.....

---

### Post by dmsynck on 2008-03-01
Since there is no "switch/case" statement in Python, you can either code it the way you have it currently or use an if ... elif ... else ladder. I am a Python newbie myself, so I am not going to pretend I know everything about the langauge, so this is the only suggestion I can make at this time. Hope this helps in some way.

---

### Post by bschleusner on 2008-03-01
> if this is only needed in one function, you can define the function within the function that it's needed in.....

How would I do that?

---

### Post by kaens on 2008-03-01
> **bschleusner said:**
> How would I do that?

You don't need anything special, just define the function how you normally would, but at the correct indentation level inside the function it's being defined in. The inner function will only be visible inside the outer function.


For example:
```

def do_stuff(item_one, item_two):
    def increment_item(item):
        return item + 1

    print item_one, item_two
    item_one = increment_item(item_one)
    print item_one, item_two


>>>do_stuff(1, 2)
1 2
2 2

```

There's a better example [here.]("http://www.diveintopython.org/object_oriented_framework/all_together.html")

---

