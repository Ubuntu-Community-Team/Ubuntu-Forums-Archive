---
title: "How to make a GUI in python?"
date: 2010-05-06
forum: Programming Talk
---

### Post by makuab on 2010-05-06
Im wondering how i can make a GUI for something like this

```

agility = input("what is your agility level? ")

```

and have a little box where they can enter a number and it calculates for them or something.

---

### Post by loell on 2010-05-06
you can have **zenity** or **pyzenity** for that.

---

### Post by makuab on 2010-05-06
> **loell said:**
> you can have **zenity** or **pyzenity** for that.
another question, how does python do order of operations, for example I want python to take strength multiply it by .10 add 3 and then add it back on to the original strength.
would this work? 

```

strength = strength + strength * .10 + 3 

```

or would that take strength, add it to strength, and then multiply it by .10 and add 3?

---

### Post by Nebelhom on 2010-05-06
As far as I know, python follows general mathematical rules:

e.g.

everything that is bracketed goes first, then it is multiplication and division before addition before substraction. but best wait till someone else seconds this... or tells you that I'm wrong ;)

But the general advice, if in doubt, put it in brackets. It would be a pain to debug 4 weeks later if there was a problem because of it.

You can always try it out. 2 + 2* 0.1 + 3 if it is 5.2 then I am right, if it is 3.4 python does it sequentially.

*EDIT: I just checked. it seems to be the way I said it*

As to the GUI thing, there are plenty of options. some are more elaborate than others. the ones I know are wxpython, pyQt, tkinter (but stay away from that).

Does that answer your question?

---

### Post by OgreProgrammer on 2010-05-06
I would recommend installing quickly. You'll find it in synaptic rather than the software center. 

Follow this tutorial and you will go along way to understanding how to efficiently make GUI code.

[http://www.jonobacon.org/2009/10/19/ubuntu-and-the-opportunistic-programmer/](http://www.jonobacon.org/2009/10/19/ubuntu-and-the-opportunistic-programmer/)

---

### Post by makuab on 2010-05-06
> **Nebelhom said:**
> As far as I know, python follows general mathematical rules:

e.g.

everything that is bracketed goes first, then it is multiplication and division before addition before substraction. but best wait till someone else seconds this... or tells you that I'm wrong ;)

But the general advice, if in doubt, put it in brackets. It would be a pain to debug 4 weeks later if there was a problem because of it.

You can always try it out. 2 + 2* 0.1 + 3 if it is 5.2 then I am right, if it is 3.4 python does it sequentially.

*EDIT: I just checked. it seems to be the way I said it*

As to the GUI thing, there are plenty of options. some are more elaborate than others. the ones I know are wxpython, pyQt, tkinter (but stay away from that).

Does that answer your question?

i have another thing, how do i skip a segment of code, for example if someone selects one option i dont want them to be able to select the one below it (this is not in the GUI, its in terminal)

---

### Post by Tony Flury on 2010-05-06
> **makuab said:**
> i have another thing, how do i skip a segment of code, for example if someone selects one option i dont want them to be able to select the one below it (this is not in the GUI, its in terminal)


use if statements
```

if option == 1:
    ..... do stuff
else
    ..... do other stuff

```

---

### Post by KdotJ on 2010-05-06
Not to start a war here, but I just want opinions...

What Gui framework do guys recommend for python?
 
wxPython or PyQT?

What are the pros and cons for each? Is it more worth it to learn QT if I plan to learn C++ later on?
All help appreciated

---

### Post by nvteighen on 2010-05-06
> **makuab said:**
> Im wondering how i can make a GUI for something like this

```

agility = input("what is your agility level? ")

```

and have a little box where they can enter a number and it calculates for them or something.

Well, it's difficult without knowing how functions work, because everything related to GUIs is usually stated in "object oriented programming" (i.e. programming designing your code around objects that do stuff... those actions are called "methods", but are just functions associated to an object).

I'd kindly suggest you to forget about GUIs for a while, otherwise you'll frustrate yourself unnecessarily and won't enjoy learning the art of programming :)

---

### Post by dkfalcone on 2010-05-15
Hope this is not too little too late, but I am also looking for fairly basic info on Python with a GUI bent. Haven't found just what fits me yet. But you might take a look at 
[http://www.awaretek.com/tutorials.html](http://www.awaretek.com/tutorials.html)
Lots of stuff to look through. 
You might also take a look at "Python in a Nutshell" at your local book store.
And, if you are not in a hurry, and want to have a bit of fun learning about such concepts as conditional branches, you might try loading GvRng. It's a game that requires you learn programing concepts. Kind of fun. 
Good luck.

p.s. Python has sort of two parts. The first part, Python proper, is a line by line language that you do in a termanal; no GUI. Once you learn that you add GUI tool kits "on top"  that make GUI possible for new users like us.

---

