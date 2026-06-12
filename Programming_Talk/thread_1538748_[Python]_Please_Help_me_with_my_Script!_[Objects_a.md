---
title: "[Python] Please Help me with my Script! [Objects and Loops]"
date: 2010-07-25
forum: Programming Talk
---

### Post by nicoobe on 2010-07-25
Hello everybody, my problem is the following:
     Imagine I am making a script to manage a Hotel and the first time the script runs I want to ask the user how many rooms do his Hotel have and after that create one object per room.

It will be something like this:
```

class room(self)
     def __init__(self):
          print "Created!"

NumberR = ("How many rooms does it have your Hotel? ")
Counter = 1

while Counter <= NumberR:
     "Room",Counter = room()
     Counter = Counter + 1


```
As you must see it doesnt works! Please Help

How would you do it?

---

### Post by StephenF on 2010-07-25
> **nicoobe said:**
> Hello everybody, my problem is the following:
     Imagine I am making a script to manage a Hotel and the first time the script runs I want to ask the user how many rooms do his Hotel have and after that create one object per room.

..8<..

As you must see it doesnt works! Please Help
First of all I would wrap code in [noparse]```
code goes here
```[/noparse] tags to preserve indentation. Hit the quote button to see how I composed the following...

```

class Room(object):
    def __init__(self):
        print "Created!"

n_rooms = int(raw_input("How many rooms does your hotel have? "))

rooms = [Room() for x in xrange(n_rooms)]

```
Edit: I hope this isn't going to be a "Please turn my pseudocode into Python" thread.

---

### Post by nicoobe on 2010-07-25
Thanks you very much StephenF. Would you be so nice to explain me how it works the following extract of the code.
```
rooms = [Room() for x in xrange(n_rooms)]
```

As I could see this makes a list, but in what moment does it declare the objects? 
Thanks you again :)

---

### Post by Can+~ on 2010-07-25
> **nicoobe said:**
> As I could see this makes a list, but in what moment does it declare the objects? 
Thanks you again :)

Here:

```
rooms = [**Room()** for x in xrange(n_rooms)]
```

This is a list comprehension, which goes like:

```
rooms = [**Action** for **Iterator** in **Iterable**]
```

It's the equivalent of doing:

[PHP]for x in xrange(n_rooms):
    rooms.append(Room())[/PHP]

---

