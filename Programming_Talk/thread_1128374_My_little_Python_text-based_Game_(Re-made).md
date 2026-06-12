---
title: "My little Python text-based Game (Re-made)"
date: 2009-04-17
forum: Programming Talk
---

### Post by Swenghk on 2009-04-17
This is the second version of a python game I made, I know
its ridiculously simple for the amount of code, but it took me 2 days to make!

---

### Post by M4rotku on 2009-04-17
> joey@joey-laptop:~/Desktop$ ./Adventure.py 
Traceback (most recent call last):
  File "./Adventure.py", line 8, in <module>
    import pygame
ImportError: No module named pygame


It sounds like you might want to include the module.  I don't know if you wanted us to test the game or not, but I just tried to play it.  If you were just looking for us to look over the code, then ignore this post. ;)

---

### Post by Swenghk on 2009-04-17
Oh crap! I was testing something with PyGame and I forgot to remove that, I'm incredibly sorry! And this game is meant to be played in a terminal by the way...

Um...How do post a new attached file?

---

### Post by tcoffeep on 2009-04-17
Choose an option: 5
Really quit? y
Thanks for playing!
Really quit? y
Thanks for playing!
Really quit? das
Really quit? QUIT
Really quit? fsa
Really quit? fioasjhfas
Really quit? yes
Really quit? yes
Really quit? y
Thanks for playing!
Really quit? y
Thanks for playing!
Really quit? y
Thanks for playing!
Really quit? 


it doesn't want to let me quit D:

---

### Post by amingv on 2009-04-17
I kinda like it. I do not consider myself a very good programmer at all, but i feel there's some things I could suggest:

1. Don't repeat yourself: make a variable (or a list) with the quest items and comment them well, then compare the items in the inventory against the variable and not the string every time.

2. Don't put unnecessary options in the menus, that is, walking into walls (at least that's my preference, they get you out of the story), unless there's a switch or something when you inspect the wall.

3. I can't see the point of creating a "stats" variable and then a "charhealth" variable in the rat's battle, or am I missing something?

4.Selling in the store is tiring, make a menu with your inventory items, I'd also make a sell/buy function that takes the item as an argument and compares it to a "prices" dictionary and a "nosale" list, and modifies the inventory/gold accordingly to make it look less verbose.

5. There's some bugs that I'll let you find the solution for:
   a. The quitmenu() function never ends
   b. There's an error in the battle loop in ratbattle() (the rat can fight with 0HP).

I'll be waiting for the forest storyarc, so keep working :)

EDIT:
Oh! Almost forgot.
Don't declare the functions after you've used the (especially if you don't put any comments to them at usage-time), I believe it makes debugging so much harder than need be.
If you like you may even create a functions file and import it from the main source code.

---

### Post by Swenghk on 2009-04-18
> **amingv said:**
> 

4.Selling in the store is tiring, make a menu with your inventory items, I'd also make a sell/buy function that takes the item as an argument and compares it to a "prices" dictionary and a "nosale" list, and modifies the inventory/gold accordingly to make it look less verbose.
.

What do you mean by this? I have only been programming in Python for about a week, so I don't really completely understand dictionaries...if thats what you were referring to. Do you mean create a dictionary called prices:

```

prices{"item1": price1, "item2": price2}
```

and then compare the keys from the dictionry to what the player enters?

---

### Post by simeon87 on 2009-04-18
> **Swenghk said:**
> What do you mean by this? I have only been programming in Python for about a week, so I don't really completely understand dictionaries...if thats what you were referring to. Do you mean create a dictionary called prices:

```

prices{"item1": price1, "item2": price2}
```

and then compare the keys from the dictionry to what the player enters?

I think so yes. For example:

```

gold = 100
inventory = []
store = {"sword": 150, "blue potion": 25, "red potion": 75}

def purchase(store, item):
    global gold
    global inventory
    
    price = store[item]
    
    if gold >= price:
        gold -= price
        inventory.append(item)
    else:
        print "You can't purchase this."
    

purchase(store, "blue potion")
print gold
print inventory

```

gives:

```

75
['blue potion']

```

You may also want to look into objectoriented programming at some point as using globals becomes messy when the game becomes bigger.

---

### Post by Xender1 on 2009-04-18
how does one go about running it? when i double click it brings up an option to run in terminal but no terminal pops up and nothing happens. opening from the terminal gives me : 
```

~/Desktop$ python Adventure.py
Traceback (most recent call last):
  File "Adventure.py", line 8, in <module>
    import pygame
ImportError: No module named pygame

```

how do you fix that?

FIX: just deleted that include...

---

### Post by amingv on 2009-04-18
> **Swenghk said:**
> What do you mean by this? I have only been programming in Python for about a week, so I don't really completely understand dictionaries...if thats what you were referring to. Do you mean create a dictionary called prices:

```

prices{"item1": price1, "item2": price2}
```

and then compare the keys from the dictionry to what the player enters?

Yes, what I meant was pretty much what simeon87 said, plus a nosale list to keep the user from selling quest items. Like this:

```
gold = 100
inv = ["apple", "quest1", "ruby"]

def sell(item):
    global gold
    global inv
    nosale = ["quest1", "quest2", "quest3"]
    sell_prices = {"apple":15,\
                   "ruby":90, \
                   "old scale":25}
                      
    
    if item in nosale:
        print "That looks like an interesting item!\nHang on to it for a while."
    else:
            #you may tell the user the price and ask for confirmation before
            #the sale is final
            inv.remove(item)
            gold += sell_prices[item]
            
            print "Now you have:"
            for item in inv: print item, ', ',
            print gold, "gold\nThanks for your patronage!"

################################################################

#USAGE

################################################################

print "What do you want to sell?"

for n in range(len(inv)):
    print n+1, inv[n]

choice = int(raw_input())
#You may add something to handle non numeric input.
what = inv[choice-1]

sell(what)
```

But by no means limit yourself to that, exploit all possibilities! :)

EDIT:
Post data:
1. Come to think of it, you don't even need the nosale list: just check for items that are not in sell_prices (and which obviously are not meant to be sold), though I think the nosale list simplifies things.

---

### Post by tcoffeep on 2009-04-19
> **Xender1 said:**
> how does one go about running it? when i double click it brings up an option to run in terminal but no terminal pops up and nothing happens. opening from the terminal gives me : 
```

~/Desktop$ python Adventure.py
Traceback (most recent call last):
  File "Adventure.py", line 8, in <module>
    import pygame
ImportError: No module named pygame

```

how do you fix that?

FIX: just deleted that include...

i just 

sudo apt-get install python-pygame

and it worked.

---

### Post by s.fox on 2009-04-20
Hi,

I was playing with this yesterday and I like it. This has inspired me to attempt creating a game in python.  Thanks!

-Ash R

---

### Post by Bodsda on 2009-04-20
Just testing this out, and theres a few bugs, already mentioned was the problem with the quitmenu() function.

[php]
def quitmenu():
    while True:
        reallyq = raw_input("Really quit? ")

        if reallyq == "y":
            print "Thanks for playing!"
            quit

        elif reallyq == "n":
            print "Alright!"
            mainmenu()

        else:
            quitmenu()
[/php]

Firstly, theres the issue of, you never mention that the user type 'y' to quit, some may try 'yes' 'Y' 'Yes' etc, you could instead have a list of acceptable inputs and first convert the entry to lower case so that you wont have to worry about different cases. 

For converting to lower case you can use the lower() function, which can be wrapped around the raw_input like so.
```
import string
reallyq = string.lower(raw_input("Really Quit? "))
```
using this method even if i type in 'YeS' it will be converted to 'yes'

The next slight issue that I see is not so much a bug just a preference, in the else statement you call the quitmenu() function again, this is unnecessary as your using a loop, so instead you can just use 'pass' and the loop will reiterate

and finally, without actually giving you the answer to the quit bug, is 'quit' a valid statement? tip: try it in an interpreter

---

### Post by Swenghk on 2009-04-21
Thank you so much Bodsda! I figured out I must use "quit()", thanks for the help!

And Ash R, I would really like to see your game when your done with it, I think text-based games can be a lot of fun (unless your not making a text-based game, in that case, it would be really cool) And even though I'm working on C++ righht now, I think I might try to fix this game up this weekend and make it a bit longer.

---

### Post by sekinto on 2009-04-21
Some things in the interface could be worked on.

Example, instead of doing
```
choice1 = choice1.lower()
```
and checking for directions like "south" and "west".
It would be much better to do
```
choice 1 = choice1[0].lower()
```
and check for directions like "s" and "w".

That way the user can put in the full word or just one letter if they want, also if they screw up and misstype something they will still go somewhere. Text adventure games that are more linient when it comes to input are much more fun because you don't waste your time typing.

Also I know many people are suggesting a dictionary for items, but why not make an item class so you can create item objects and do many things with them (including assigning them a price). A dictionary or list would still be a good way to keep the item instances organized though.

---

### Post by Swenghk on 2009-04-21
I haven't learned OOP yet

---

### Post by amingv on 2009-04-21
> **Swenghk said:**
> I haven't learned OOP yet

Then forgive me for giving advise where it hasn't been asked, but I suggest you finish learning the basics of Python to an acceptable level before moving on to C++ (or any other language). I'm sure you'll learn it really fast after you finish python, but if you jump from language to language you'll understand neither.
I also stumbled between C++ and Python when I started, and I can tell you if I could do without that part of my life I would.

It's still your choice, though.

---

### Post by sekinto on 2009-04-21
Constructing a class is pretty simple.

```

# Makeing a class.

class MyClass:
    def __init__(self, arg1, arg2, optarg1=default):
        self.attr1 = arg1
        self.attr2 = arg2
        self.attr3 = optarg1
    def MyMethod1(self):
        <some code>
    def MyMethod2(self):
        <some code>

# Making an object with class.

MyObject = MyClass(arg1, arg2)

# Changing an attribute.

MyObject.attr2 = 9

# Calling a Method.

SomeValue = MyObject.MyMethod2()
``` 

Here is an example I made:

```
class rectangle:
    def __init__(self, width, height, measurement='cm', name='RandomRectangle', color=(0,0,0)):
        self.width = width
        self.height = height
        self.measurement = measurement
        self.name = name
        self.color = color
    def get_area(self):
        return self.width * self.height
    def print_info(self):
        print self.name
        print 'Dimensions: ' + str(self.width) + 'x' + str(self.height)\
            + self.measurement + ' (' + str(self.get_area())\
            + self.measurement + '^2)'
        print 'Color: ' + str(self.color)

rectangle_list = [rectangle(100,20),
    rectangle(50,20,name='Ye Ol Blue',color=(0,0,255)),
    rectangle(20,10,name='Inchy',measurement='in')]

for item in rectangle_list:
    print ''
    item.print_info()
```

That would output:

```

RandomRectangle
Dimensions: 100x20cm (2000cm^2)
Color: (0, 0, 0)

Ye Ol Blue
Dimensions: 50x20cm (1000cm^2)
Color: (0, 0, 255)

Inchy
Dimensions: 20x10in (200in^2)
Color: (0, 0, 0)
```

So basically the point of classes is to make repetitive things simpler. If you are going to be creating a bunch of objects with similar attributes and actions (methods) then it is a good idea to make a class for them so you can construct them all using that class.

---

### Post by Swenghk on 2009-04-24
> **amingv said:**
> Then forgive me for giving advise where it hasn't been asked, but I suggest you finish learning the basics of Python to an acceptable level before moving on to C++ (or any other language). I'm sure you'll learn it really fast after you finish python, but if you jump from language to language you'll understand neither.
I also stumbled between C++ and Python when I started, and I can tell you if I could do without that part of my life I would.

It's still your choice, though.

Thank you for your advise, and I am actually going to do that. I'm going to finish the last 5 or so Chapters of the Python book I was reading and then I'll move on, I still haven't covered Dictionaries, Functions, Software Objects, OOP, and Graphics

---

### Post by suchapity on 2009-08-09
> **Swenghk said:**
> This is the second version of a python game I made, I know
its ridiculously simple for the amount of code, but it took me 2 days to make!


Can I see the code as a .py I don't have the mac format's figured out but wanted to play with this code.

---

### Post by Bodsda on 2009-08-10
> **suchapity said:**
> Can I see the code as a .py I don't have the mac format's figured out but wanted to play with this code.

Just open it up in a text editor to view the code.

---

