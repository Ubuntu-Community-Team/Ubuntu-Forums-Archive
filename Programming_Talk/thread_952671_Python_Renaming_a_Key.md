---
title: "Python: Renaming a Key"
date: 2008-10-19
forum: Programming Talk
---

### Post by jesuisbenjamin on 2008-10-19
hello forum,

I am new to Python (to programming) but find it really interesting.

I am now looking at dictionaries. Having created a dictionary with 40 keys, the values of which are another dictionary, i am trying to figure out how to rename a key without changing its values.

How could i do that?

Thanks for your help :)

---

### Post by pp. on 2008-10-19
I don't think you do that at all.

---

### Post by nvteighen on 2008-10-19
Well, you could create a function that does that. 

It should:
1. Create a new pair.
2. Delete the old one.

And if you know about Python's object system, you could even create a new custom dictionary type inheriting the old one and just changing what you want.

---

### Post by WW on 2008-10-19
> **nvteighen said:**
> 
It should:
1. Create a new pair.
2. Delete the old one.

E.g., if x is the dictionary,
```

x[newkey] = x[oldkey]
del x[oldkey]

```

---

### Post by jesuisbenjamin on 2008-10-19
yes this rocks, thanks :)

Also when i ran functions with *def*, i figured out my results were flushed at the end, so i replaced *return* by *global* *x* (where x is the name of the variable calculated in *def*) and then the value of *x* survives...

Did i do the right thing? Is this the best thing to do?

Cheers

---

### Post by Canis familiaris on 2008-10-19
> **jesuisbenjamin said:**
> yes this rocks, thanks :)

Also when i ran functions with *def*, i figured out my results were flushed at the end, so i replaced *return* by *global* *x* (where x is the name of the variable calculated in *def*) and then the value of *x* survives...

Did i do the right thing? Is this the best thing to do?

Cheers

No it isn't the best way. Could you show the complete code?

---

### Post by jesuisbenjamin on 2008-10-19
Here you go:

```
#This function creates 3 dictionaries:
# 'xy' with the coordinates of regions set at x = 0 and y = 0
# 'info' includes 'xy'and other info about the region
# 'region' includes 48 regions with from 0 to 47, with 'info' set as their respective value.

def make():
    xy = {'x': 0, 'y': 0}

    info = {'xy': xy, 'terrain': 'sea', 'landlord': 'no one', 'governor': 'no one',
            'fort': False, 'general': 'no one', 'army': 0, 'wonder': False}

    region = {}
    a = 0
    while len(region) < 48:
        region[a] = info
        a = a + 1
    global xy, info, region


#This function will print the menu:
def menu():
    option = 3
    if option != 0:
        print "Menu"
        print "1. New Game"
        print "0. Quit"
        print
        option = input("Please chose an option: ")
        if option == 1:
           make()
        else:
            print "Thank you, good bye!"
    return


menu()
```


What i need is to keep the keys and values of xy, info, and region going after the function ends... which is not the case when using return, then i get xy = {}

PS thanks for the tip, it should be clearer now...

---

### Post by WW on 2008-10-19
It would help if you wrapped your code in **[****code****]** and **[****/code****]** tags.  That will preserve your indentation.

---

### Post by BackwardsDown on 2008-10-19
```

#This function creates 3 dictionaries:
# 'xy' with the coordinates of regions set at x = 0 and y = 0
# 'info' includes 'xy'and other info about the region
# 'region' includes 48 regions with from 0 to 47, with 'info' set as their respective value.

def make():
	xy = {'x': 0, 'y': 0}

	info = {'xy': xy, 'terrain': 'sea', 'landlord': 'no one', 'governor': 'no one',
	'fort': False, 'general': 'no one', 'army': 0, 'wonder': False}

	region = {}
	a = 0
	while len(region) < 48:
		region[a] = info
		a = a + 1
	return xy, info, region

#Next regions should be getting proper coordinates:

#This function will print the menu:
def menu():
	option = 3
	if option != 0:
		print "Menu"
		print "1. New Game"
		print "0. Quit"
		print option = input("Please chose an option: ")
	if option == 1:
		xy,info,region = make()
	else:
		print "Thank you, good bye!"
	return
```

You have to catch the return values of a function when you execute it. You should use as less globals as possible, preferably none, because globals will create spagetti code very fast.
Hope this helps.

---

### Post by mssever on 2008-10-19
You can return multiple values if you want. ```
def test():
    x = 1
    y = 2
    return x, y

val1, val2 = test()
```

---

### Post by jesuisbenjamin on 2008-10-19
OOOOKAY :O

This is sooo classy, i love programming i think :)

Thanks guys.

---

### Post by jesuisbenjamin on 2008-10-19
:-k
Err wait a minute...
This is not working:
```
>>> print region
{}
>>> print info
{}
```

Though i changed:
```
global xy, info, region
```
into:
```
return xy, info, region
```

and:
```
if option == 1:
      make()
```
into:
```
if option == 1:
      xy, info, region = make()
```

Did i miss something?
Is this because* xy, info, region = make()* is within *def menu() *?

---

### Post by eragon100 on 2008-10-19
I am still learning python (programming) myself and have only just learned about making my own functions, program scopes etc, so I can't really help you. I wonder tough: what kind of game are you writing?

---

### Post by BackwardsDown on 2008-10-19
> Did i miss something?
Is this because xy, info, region = make() is within def menu() ?

Yes. Variables are only accessable if they are within their function (unless if they are global, but those are evil). So I suggest rewriting it to:

> 
#This function will print the menu:
def menu():
	option = 3
	if option != 0:
		print "Menu"
		print "1. New Game"
		print "0. Quit"
		print option = input("Please chose an option: ")
	if option == 1:
		xy,info,region = make()
	else:
		print "Thank you, good bye!"
	return xy,info,region


---

### Post by jesuisbenjamin on 2008-10-19
Got it and i should add ```
xy,info,region = menu()
``` at the very end too. 
[LIST]
[*]So this means i need to extract all data i need to carry around by adding it in the line above and after *return* at the end of menu()...?
[*]No space between comma and the next variable?
[*]What's the evil spaghetti about?
[/LIST]

*eragon100: it's an attempt to put into a program a diplomatic game which i have made on board so far, it's trying to stand apart from what's already been made by making the game simple but also leaving no space for randomness and giving a lot of space to actual diplomatics and games of power between players. My bro is professional in the 3D technology, so when i get together the basics he will do the 3D interface. But apparently i still have progress to make, i started to learn Python 2 days ago :)*

---

### Post by eragon100 on 2008-10-19
> **jesuisbenjamin said:**
> Got it and i should add ```
xy,info,region = menu()
``` at the very end too. 
[LIST]
[*]So this means i need to extract all data i need to carry around by adding it in the line above and after *return* at the end of menu()...?
[*]No space between comma and the next variable?
[*]What's the evil spaghetti about?
[/LIST]

*eragon100: it's an attempt to put into a program a diplomatic game which i have made on board so far, it's trying to stand apart from what's already been made by making the game simple but also leaving no space for randomness and giving a lot of space to actual diplomatics and games of power between players. My bro is professional in the 3D technology, so when i get together the basics he will do the 3D interface. But apparently i still have progress to make, i started to learn Python 2 days ago :)*

Have you ever tried diplomacy? It's the sort of game you're describing :wink: (and RISK offcourse)

---

### Post by BackwardsDown on 2008-10-19
> 
[*]So this means i need to extract all data i need to carry around by adding it in the line above and after *return* at the end of menu()...?

Correct.

> 
[*]No space between comma and the next variable?

That does not matter.

> 
What's the evil spaghetti about?

On very small projects (< 1k lines of code). You can use tricks like globals and goto-statements but on bigger projects it will ultimately lead to [spaghetti code]("http://en.wikipedia.org/wiki/Spaghetti_code"). It means that you cant easily see where variables are created, what they mean, if the variable name maybe is already taken, etc. If you make every variable global, bigger projects will have thousands of variable, you will lose the overall picture, and have spagetti code.

The trick is to make your program as easily readable as possible. Because non-readable code is a programmers worst nightmare.

---

### Post by jesuisbenjamin on 2008-10-19
> Have you ever tried diplomacy? It's the sort of game you're describing :wink: (and RISK offcourse)

You bet i did :)

---

### Post by jesuisbenjamin on 2008-10-19
Thanks, the pictures of spaghetti and lasagna suddenly made the whole concept a lot clearer clearer :D

---

### Post by Can+~ on 2008-10-19
Programming draws a lot of principles from mathematics, where functions act as unchangeable blocks:

x -> f(x) -> y

Using globals breaks this isolated behaviour, and lets variables be changed anywhere in the code, later causing confusion and unexpected results.

The main point of Object Oriented Programming, is to have isolated blocks, each one with an specific task, and ideally, that can be used in sequence:

x -> f(x) -> g(f(x)) -> y

OOP also adds entities called classes and instances, and understands every variable as an instance of a superior class, where a string for example, is an instance of the class string, which holds it's own methods and values (the sequence of characters, the length, the strip/split/... methods, etc).

So far, you have created dictionaries, lists and tuples. Do you have any idea on how they work inside? You really don't need know how they work in the inside, you just call them, hand and retrieve data from them, this is the idea of OOP, you don't need deep knowledge to use them (but it helps), it's another level of abstraction, opposed to C where you need to know how a string works, otherwise you'll end up overflowing, causing a segfault, etc.

In short: Try to avoid globals, only use them when strictly needed (I can't picture an example though).

---

### Post by ratmandall on 2008-10-19
> **jesuisbenjamin said:**
> * i started to learn python 2 days ago :)*

raaaaaaaaaaaaaggggggggeeeeee

---

### Post by jesuisbenjamin on 2008-10-20
Hey Can+~,
Thanks for the details. I kind of have an idea of what you mean, but i guess time and mistakes will teach me the real stuff.
My field is not maths, but rather linguistics and history, and in those there is a lot of data flow and abstract stuff going on as well. :)

---

### Post by nvteighen on 2008-10-20
> **jesuisbenjamin said:**
> 
My field is not maths, but rather linguistics and history, and in those there is a lot of data flow and abstract stuff going on as well. :)

Tu quoque?

I'm studying Linguistics at University too. (well, actually Philology, but I'm going to specialize for Linguistics).

In programming, you could probably apply the idea that we actually only can talk about x if we have a name to refer to x; otherwise, you have the knowledge of x but are unable to do something with it. When you have some data in a program, you don't gain any control over it unless you name it (store into a named place, a variable)... otherwise, it gets outside your hands. Basically that was the problem you had: you generated data but didn't name it.

By giving names to some complex structure (i.e. more than one piece of data combined together), you create a new abstraction layer. For example, if you decide to create a structure formed by an integer and a string, combining them into a Python list or dictionary and then, you give a name to the function that creates new instances of that structures, and to some other functions that get or set the data stored inside... Voilà! you have implemented a new data type, and you gained control over that new data type because you gave name to the processes that create it and also those that allow you to profit from them.

Think about it!

---

### Post by jesuisbenjamin on 2008-10-20
It makes sense, and also not forgetting to define the function and its output as well.

*PS: my Latin is rusty, i do Sanskrit and more :)*

---

### Post by nvteighen on 2008-10-20
> **jesuisbenjamin said:**
> 
*PS: my Latin is rusty, i do Sanskrit and more :)*

I'm more the General Linguistics type... with some of Greek and Latin (my Greek is better than my Latin, though... I just don't like the latter...)

Nice to hear our beloved science is alive and healthy! :) (in Spain, where I'm studying, this kind of things are struggling to survive).

---

### Post by jesuisbenjamin on 2008-10-20
Haha,

we are studying in Leiden (Netherlands) and hardly are surviving, there are 8 teachers for 2 students in each year 
:-$

---

### Post by nvteighen on 2008-10-21
Our ratio is aprox. 1,046 teachers per student, which is a very good one... The issue is that we're too few students in total (43) and constantly decreasing.

---

