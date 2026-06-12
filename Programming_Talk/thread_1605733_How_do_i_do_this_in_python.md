---
title: "How do i do this in python"
date: 2010-10-25
forum: Programming Talk
---

### Post by CaptainMark on 2010-10-25
im sure this is quite simple but i cant find it in my book, (im still learning)
so im making a class for an object say Sheep and the sheep has an attribute, name, if i make multiple sheep how do i go through them and list their names, im assuming something like 
for i in sheep:
print(i.name)

---

### Post by schauerlich on 2010-10-25
Put your sheep in a list, and then go through that list in a for loop:

```
class Sheep:
    def __init__(self, name):
        self.name = name


def main():
    a_few_sheep = [Sheep("little"), Sheep("bo"), Sheep("peep")]

    for sheep in a_few_sheep:
        print(sheep.name)

main()
```

---

### Post by CaptainMark on 2010-10-25
and if the sheep were already created and i wanted to list them later on in the program, is there a way to do it listing all the sheep pre instantiated, plus some ones the user is prompted to create and print all the names automatically without having to type all the names again, in the real program there may be many many objects/sheep

---

### Post by schauerlich on 2010-10-25
Computers are very dumb. They can only do exactly what they're told to do. If you want a bunch of things to be printed, you need to tell it which ones you want it to print, and it's on you to keep track of those things. Why not add all of the sheep to some list as you create them, and then later you can print them all at once?

```
class Sheep:
    def __init__(self, name):
        self.name = name


def main():
    my_sheep = []
    little = Sheep("little")
    my_sheep.append(little)
    my_sheep.append(Sheep("bo"))

    some_name = input("What do you want to name your sheep? ")
    my_sheep.append(Sheep(some_name))

    for sheep in my_sheep:
        print(sheep.name)

main()

```
```
schauerlich@inara:~$ python3.0 sheep.py

What do you want to name your sheep? peep
little
bo
peep
schauerlich@inara:~$
```

---

### Post by CaptainMark on 2010-10-25
thank you, this will suffice for this project, im surprised theres not a class method or something that can run a particular method against each instance of a class seperatley

---

### Post by schauerlich on 2010-10-25
> **CaptainMark said:**
> thank you, this will suffice for this project, im surprised theres not a class method or something that can run a particular method against each instance of a class seperatley

Behold:

```
class Sheep:
    sheep = []

    def each(func):
        for sheep in Sheep.sheep:
            func(sheep)

    def __init__(self, name):
        self.name = name
        Sheep.sheep.append(self)

    def __repr__(self):
        return self.name


def main():
    little = Sheep("little")
    bo = Sheep("bo")
    peep = Sheep("peep")
    Sheep("forever alone") # notice I never explicitly store this anywhere...

    Sheep.each(print)

main()

```

I make a class variable Sheep.sheep, and every time I make a new sheep, I append it to that list. Magic!

Now, there's a big drawback to this, which is that you keep track of EVERY sheep that gets made, ever, even the temporary ones (such as "forever alone"). You could take care of this with a destructor, but it's much easier to just make a list explicitly in your code that uses the Sheep class so that everyone knows where it's coming from.

---

### Post by mo.reina on 2010-10-25
the closest you can probably get to is return a list of instance addresses, though i don't think there's a way to return the namespace...

```
>>> import gc
>>> class test(object):
...   def __init__(self):
...     pass
... 
>>> a = test()
>>> b = test()
>>> for obj in gc.get_objects():
...   if isinstance(obj, test):
...     print obj
... 
<__main__.test object at 0x7fd56eacc1d0>
<__main__.test object at 0x7fd56eacc250>
>>> 

```

---

### Post by StephenF on 2010-10-26
> **schauerlich said:**
> Now, there's a big drawback to this, which is that you keep track of EVERY sheep that gets made, ever, even the temporary ones (such as "forever alone"). You could take care of this with a destructor...
But it's much easier to take care of this with [weak references]("http://docs.python.org/library/weakref.html#weak-reference-objects"). They allow you to keep a list in one place of all the instances that are created and have instances out there in the wider program. This means of course you would have to have assigned each sheep to at least a temporary local variable.

---

