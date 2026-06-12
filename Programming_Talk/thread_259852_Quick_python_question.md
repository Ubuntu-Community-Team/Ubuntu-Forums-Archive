---
title: "Quick python question"
date: 2006-09-18
forum: Programming Talk
---

### Post by NoTiG on 2006-09-18
Hey i have a function

```
def distance(p1, p2):

    dx = p2.x - p1.x
    dy = p2.y - p1.y
    return dx, dy

```

it takes two points as arguments, and returns 2 numbers (the distance between the sides if you drew a triangle from the connect)

now if i want to take the hypotenuse like this:

```
def hypo(dx, dy):

    dsquared = dx**2 + dy**2
    print "side a is", dx
    print "side b is", dy
    print "hypo is", math.sqrt(dsquared)

```

How come i cannot acll the function like this:

```
hypo(distance(p1, p2))
```

instead of working it says that hypo expects two arguments.... but i returned two arguments in the distance function... shouldnt hypo(distance(p1, p2)) be read as hypo(dx, dy) by the runtime ?

---

### Post by msgyrd on 2006-09-18
I'm not all that fluent with Python, but this should work:

```

def distance(p1, p2):

    dx = p2.x - p1.x
    dy = p2.y - p1.y

    return dx, dy

def hypo(dx, dy):

    dsquared = dx**2 + dy**2
    print "side a is", dx
    print "side b is", dy
    print "hypo is", math.sqrt(dsquared)

a, b = distance(p1, p2)

hypo(a, b)

```

I'm more of a C++ programmer, but I think the reason what you were trying won't work is because when a function returns multiple values, it probably returns as an array of pointers (in your case, a 1x2 array), but when you embed a function inside another, you don't get comma seperated returns.  The error you were getting is probably because you're sending the function something like this 'hypo(array, null)'.

---

### Post by NoTiG on 2006-09-18
alright i realize that distance() returns dx, and dy as a single tuple... or an array like (dx, dy) ... so when i try to pass it to hypo which expects two single objects instead of the tuple with two objects... it errors.

Is there a way to pass it without having to assign more variables ? 

like i could do this

c = distance(p1, p2)
hypo(c[0], c[1])


but is there a way to pass directly to the hypo function? just curious i guess.

---

### Post by NoTiG on 2006-09-18
> **msgyrd said:**
> I'm not all that fluent with Python, but this should work:

```

def distance(p1, p2):

    dx = p2.x - p1.x
    dy = p2.y - p1.y

    return dx, dy

def hypo(dx, dy):

    dsquared = dx**2 + dy**2
    print "side a is", dx
    print "side b is", dy
    print "hypo is", math.sqrt(dsquared)

a, b = distance(p1, p2)

hypo(a, b)

```

I'm more of a C++ programmer, but I think the reason what you were trying won't work is because when a function returns multiple values, it probably returns as an array of pointers (in your case, a 1x2 array), but when you embed a function inside another, you don't get comma seperated returns.  The error you were getting is probably because you're sending the function something like this 'hypo(array, null)'.

your right :P . i was typing at the same time. Is there a way to return the function though as two single objects instead of an array ?

---

### Post by msgyrd on 2006-09-18
While memory efficiency is always something to strive for, I don't really see any problem with just using more variables.  If you wanted to eliminate variables or code length, you can always perform both of your functions inline as one function, but it limits your ability to use each function seperately.
```
def hypo(p1, p2):
    dsquared = (p2.x - p1.x)**2 + (p2.y - p1.y)**2
    print "side a is", (p2.x - p1.x)
    print "side b is", (p2.y - p1.y)
    print "hypo is", math.sqrt(dsquared)

hypo(a, b)

```
That does the same thing and only assigned 1 extra variable.

---

### Post by msgyrd on 2006-09-18
> **NoTiG said:**
> your right :P . i was typing at the same time. Is there a way to return the function though as two single objects instead of an array ?
Yeah, you can return multiple values from a single function without having to capture it's output into more variables.  Again, I don't know much python, but just have your first function return a tuple or array, and then your second function only accept 1 argument, your array.

Edit: Ok, didn't read what you said very carefully. My bad.  No, I don't think you can return two seperate objects like what you're asking, without getting overly complicated for your purpose.

---

### Post by llonesmiz on 2006-09-18
```
import math 

def distance(p1, p2):

    dx = p2.x - p1.x
    dy = p2.y - p1.y

    return dx, dy

def hypo(dx, dy):

    dsquared = dx**2 + dy**2
    print "side a is", dx
    print "side b is", dy
    print "hypo is", math.sqrt(dsquared)

#a, b = distance(p1, p2)

#hypo(a, b)
class point:
    def __init__(self):
        self.x=0
        self.y=0

p1=point()
p2=point()
p1.x=0
p1.y=0
p2.x=1
p2.y=1
hypo(*distance(p1,p2))
``` 
This works. The "point" class is lame, you'll need to use one better. Using "*" before a tuple in a function call converts the tuple to a succession of scalar arguments.

I hope this helps you. Sorry for my English.

---

### Post by NoTiG on 2006-09-18
> **llonesmiz said:**
> 

I hope this helps you. Sorry for my English.

Hey it worked... cool :P

---

### Post by ghostdog74 on 2006-09-18
> **NoTiG said:**
> 
How come i cannot acll the function like this:
```
hypo(distance(p1, p2))
```
?

you could do this :

```

def hypo(*args):
    ...
    print args

```

---

### Post by thumper on 2006-09-18
> **NoTiG said:**
> How come i cannot acll the function like this:

```
hypo(distance(p1, p2))
```


You need to call it like this:
```
hypo(*distance(p1, p2))
```

func(*args) means call func but expand the args to be positional parameters instead of a single argument.

you can also use a dict like **dict which expands to key word args.

---

