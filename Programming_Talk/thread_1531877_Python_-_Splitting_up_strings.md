---
title: "Python - Splitting up strings"
date: 2010-07-15
forum: Programming Talk
---

### Post by skaarr on 2010-07-15
Teaching myself python and I've tried my best to solve figure this out but I can't see how it's done.

Using pygame

```
pygame.mouse.get_pos()
```

I get the mouse position on the pygame 'screen'. 
This returns a pair of coordinates eg. (254, 43)

What I want to do is separate these two coordinates and but I can't figure out how I would do it using the basic string manipulation methods (especially as the values can be 1, 2 or 3 digits, meaning that the position of the data changes).

Any help much appreciated.

---

### Post by robots.jpg on 2010-07-15
I don't know much about pygame, but I'm assuming the value returned by that function is a tuple, not a string (check the documentation). If that's correct, you can just assign each element to a separate variable like this:
```

  mouse_x, mouse_y = pygame.mouse.get_pos()
  
```
 
Edit - But to answer your question, this is one way to split a string like that:
```

pos = '(254,43)'
x, y = pos[1:-1].split(',')

```

---

### Post by skaarr on 2010-07-15
You're right it is a tuple. Thanks for the help, code does what I want it to now :)
Thanks for the string method as well.

---

### Post by Can+~ on 2010-07-15
Also, tuples can be split in the arguments of a function, for instance:

[PHP]mytuple = (9, 2)

# Function that multiplies two arguments
def multiply(first, second):
    
    return first*second

# Break down tuple when calling
print multiply(*mytuple)[/PHP]

With that in mind, you can create a function that accepts an X and Y coordinate, and break the position on call:

[PHP]dosomething("SomeArgument", *pygame.mouse.get_pos(), "Other argument")[/PHP]

Where the function "dosomething" prototype is something along the lines of:

[PHP]dosomething(somestring, x, y, otherstring)[/PHP]

---

