---
title: "having trouble with raw_input command python"
date: 2012-01-09
forum: Programming Talk
---

### Post by ilikelinuxitisthebest on 2012-01-09
Hey guys. I'm trying to make a VERY simple program that opens a pygame window. the problem is i want the size of the window to be specified by the user via raw_input. I cant seem to find a way to do that. Forgive me for being a noob.

---

### Post by CoffeeRain on 2012-01-09
The raw_input() command takes the input as a string. This may be your problem. I don't have pygame experience, but I would assume that the size is taken as a tuple. Try this... I haven't tested this code though.

```

height=raw_input('What would you like for the height? ')
width=raw_input('What would you like for the width? ')

size=width, height # Make the tuple out of the variables

screen = pygame.display.set_mode(size) # I'm pretty sure this is way to set the screen

...

```

---

### Post by KdotJ on 2012-01-09
I too have zero experience with PyGame, but I'm sure you could just cast them to an int upon entry:

```
width = int(raw_input('Enter the width:'))
```

This may not be the best way to do it, however (I'm not very clued up on casting safety in python)

---

### Post by cgroza on 2012-01-09
> **KdotJ said:**
> I too have zero experience with PyGame, but I'm sure you could just cast them to an int upon entry:

```
width = int(raw_input('Enter the width:'))
```This may not be the best way to do it, however (I'm not very clued up on casting safety in python)
Python is not statically typed so there is no casting. What are you doing there is creating an int from a string using a built-in function.

For more about the function and how to detect errors:
[http://docs.python.org/library/functions.html#int](http://docs.python.org/library/functions.html#int)

---

### Post by KdotJ on 2012-01-09
> **cgroza said:**
> Python is not statically typed so there is no casting. What are you doing there is creating an int from a string using a built-in function.

[http://docs.python.org/library/functions.html#int](http://docs.python.org/library/functions.html#int)

Indeed lol, hence it doesn't use typical casting syntax but rather constructor/function syntax. My mistake, it's been a while since I pythoned...

---

### Post by ilikelinuxitisthebest on 2012-01-09
still haven't gotten a solid answer.

---

### Post by JDShu on 2012-01-09
> **ilikelinuxitisthebest said:**
> still haven't gotten a solid answer.

KdotJ's answer works. What else do you want?

---

### Post by CoffeeRain on 2012-01-10
For a better answer, maybe you could post your code, or at least what you have so far. Then you might also post your error message if you have one.

---

