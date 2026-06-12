---
title: "An array of classes in Python not working?"
date: 2008-11-20
forum: Programming Talk
---

### Post by FoxHound22 on 2008-11-20
Hi, I am trying to make an array of my class "bullet"

```

class bullet:
    x = 0
    y = 0
    (etc)
    pass

```

Whenever I run:
```

b[50] = bullet[50]

```

I get the error 'classobj' object is unscriptable.
If I run:
```

b[50] = bullet

```
I get the error name 'b' not defined.

Help please! I've searched for "array of class" and haven't found anything except for a few references to "dictionaries". Thanks in advance!

---

### Post by cdekter on 2008-11-20
What you are attempting is not valid Python syntax. Python does not have the concept of arrays (in general terms), but rather has lists. You could create a list of 50 bullet instances by doing:

```
b = []
for x in range(50):
   b.append(bullet())

```

I don't know if this is what you were actually trying to achieve - it kind of looks like you were trying to allocate an array of size 50 with type bullet. This concept does not exist in Python, since it is not a strongly typed language. You cannot declare the type of a variable statically.

Read some Python tutorials - links available in the stickies at the top of this forum - if you want to know more.

---

### Post by wmcbrine on 2008-11-20
I'd put it this way:

```
b = [bullet() for x in range(50)]
```

However, this is IMHO still not very pythonic. I'd want to look at the larger problem to see if there might be a better way to handle it.

---

### Post by Tony Flury on 2008-11-20
A dictionary is one way to do what you want. The thing about dictionaries is that they have have a unique key (like the index in an array but keys can be strings as well as integers).

it really depends what you are trying to do - will you always have exactly 50 instances ? or will the number of instances vary during your program execution ?

if the key (index) is important to you - then build a dictionary,

For example : to build a dictionary with 50 elements : 

```

b = {}
for i in range(50)
    b[i] = bullet()

```

you can now access each of these by using b[<index>]

you don't have to have 50 elements in the dictionary either - you could have b[1] and b[50] but nothing in between. However if you use a key which does not exist in the dictionary then you will get a KeyError.

If the key is irrelevant - i.e. you are just using it to access the next instance - then a list is better for you

```

b = []
for i in range(50]
    b.append(bullet())

```

a list can be access two ways - 

by index : 
b[20] will get the 21st element (counting starts from zero) if it exists - if not the programm will generate an error.

you can also access the list by using an iterator : 
```

for _this_bullet in b:
    _this_bullet.move_me()

```
this will loop through every entry in the b list, and execute the move_me method on every instance in the list.

---

### Post by nvteighen on 2008-11-20
> **wmcbrine said:**
> I'd put it this way:

```
b = [bullet() for x in range(50)]
```

However, this is IMHO still not very pythonic. I'd want to look at the larger problem to see if there might be a better way to handle it.

It isn't Pythonic, but it's a nice idea.

---

### Post by raf_kig on 2008-11-20
How is list comprehension not Pythonic? :-)

It's one of Python's features i really love.

Sorry for not contributing anything useful. :-)

Regards

raf

---

### Post by slavik on 2008-11-20
> **FoxHound22 said:**
> Hi, I am trying to make an array of my class "bullet"

```

class bullet:
    x = 0
    y = 0
    (etc)
    pass

```

Whenever I run:
```

b[50] = bullet[50]

```

I get the error 'classobj' object is unscriptable.
If I run:
```

b[50] = bullet

```
I get the error name 'b' not defined.

Help please! I've searched for "array of class" and haven't found anything except for a few references to "dictionaries". Thanks in advance!
Why do you want an array/list of limited size? just append onto it when needed.

---

### Post by wmcbrine on 2008-11-21
> **raf_kig said:**
> How is list comprehension not Pythonic? :-)List comprehension is pythonic; it's the fixed-size list of n objects that I'm questioning.

---

### Post by nvteighen on 2008-11-21
> **wmcbrine said:**
> List comprehension is pythonic; it's the fixed-size list of n objects that I'm questioning.
Well, that depends on the code, I guess. Of course, it's much nicer to have this determined as a function parameter, but if you don't need it and just want a fixed size, doing it that way may result being redundant.

---

### Post by FoxHound22 on 2008-11-21
> **wmcbrine said:**
> I'd put it this way:
```
b = [bullet() for x in range(50)]
```


> **Tony Flury said:**
> 
by index : 
b[20] will get the 21st element (counting starts from zero) if it exists - if not the programm will generate an error.


That works, thanks!

> 
you can also access the list by using an iterator : 
```

for _this_bullet in b:
    _this_bullet.move_me()

```
this will loop through every entry in the b list, and execute the move_me method on every instance in the list.

So it automatically tracks the bullet up through the list with "_this_"? It seems like there's much less to type in Python, which is great.

Is a method a function specific to a class?

[QUOTE=slavik]Why do you want an array/list of limited size? just append onto it when needed.[/QUOTE]

As far as the list size, I was thinking I would never have close to 50 bullets, and would create a "currentbullet" variable and as each new bullet is fired, it would be set with
currentbullet = currentbullet + 1
b[currentbullet].x = newbulletx
b[currentbullet].y = nefwbullety (etc...)
inside of a SetNewBullet function.

Now to have a look at functions :)

---

### Post by Tony Flury on 2008-11-21
you might want to read the python tutorial : 

[http://docs.python.org/tutorial](http://docs.python.org/tutorial)

Especially the sections about classes : [http://docs.python.org/tutorial/classes.html](http://docs.python.org/tutorial/classes.html)

and lists : [http://docs.python.org/tutorial/datastructures.html](http://docs.python.org/tutorial/datastructures.html)

in python you would not need to use a current_bullet variable at all - just create an empty list at the start of the program, and each time a bullet is fired - "append" a bullet object to the end of the list, and when a bullet hits an object or goes out of range - "remove" it from the list.

Essentially i would see your code having a bullet class - with methods that deal with being fired, moving, hitting something etc

Your code will probably have other classes as well - maybe be player classes, weapons etc - it will make your code much easier to write and to use and extend.

---

### Post by FoxHound22 on 2008-11-22
> **Tony Flury said:**
> you might want to read the python tutorial : 

[http://docs.python.org/tutorial](http://docs.python.org/tutorial)

Especially the sections about classes : [http://docs.python.org/tutorial/classes.html](http://docs.python.org/tutorial/classes.html)

and lists : [http://docs.python.org/tutorial/datastructures.html](http://docs.python.org/tutorial/datastructures.html)

in python you would not need to use a current_bullet variable at all - just create an empty list at the start of the program, and each time a bullet is fired - "append" a bullet object to the end of the list, and when a bullet hits an object or goes out of range - "remove" it from the list.

Essentially i would see your code having a bullet class - with methods that deal with being fired, moving, hitting something etc

Your code will probably have other classes as well - maybe be player classes, weapons etc - it will make your code much easier to write and to use and extend.

Letting the length of the list be changed automatically makes sense. 

After I append a bullet, how do I assign values to the latest object's attributes?

---

### Post by Greyed on 2008-11-22
> **FoxHound22 said:**
> After I append a bullet, how do I assign values to the latest object's attributes?

The latest?  

```

b[-1].attribute = value

```

Though I think we're engaging in a little of answering X when you mean to be asking Y.  IE, I'm fairly certain you know what you want to do and you're trying to solve that problem.  But instead of asking "how would I best do Y" you're asking "how do I make X work?"  X may not be the best way to achieve Y.

Maybe in your case a simple index is not the best method of tracking these objects.  In fact in most cases where I am tracking a homogeneous set of objects I build dicts since the semantics for creating, removing, altering and locating bear no relation to their position.  Unless you have some absolute need to maintain the order of these objects I have a suspicion you'll want to use a dict and devise some method of uniquely identifying those objects for later retrieval.

With the little information I can surmise from your posts might I suggest something using a tuple?  Tuples make great keys for dicts when you want a pair of separate but related data.  For example, X and Y coordinates on a map (10, 10) is different than (9, 10) for example.  The other would be (player, bullet)?

---

### Post by FoxHound22 on 2008-11-22
> **Greyed said:**
> The latest?  

```

b[-1].attribute = value

```

Though I think we're engaging in a little of answering X when you mean to be asking Y.  IE, I'm fairly certain you know what you want to do and you're trying to solve that problem.  But instead of asking "how would I best do Y" you're asking "how do I make X work?"  X may not be the best way to achieve Y.

Maybe in your case a simple index is not the best method of tracking these objects.  In fact in most cases where I am tracking a homogeneous set of objects I build dicts since the semantics for creating, removing, altering and locating bear no relation to their position.  Unless you have some absolute need to maintain the order of these objects I have a suspicion you'll want to use a dict and devise some method of uniquely identifying those objects for later retrieval.

With the little information I can surmise from your posts might I suggest something using a tuple?  Tuples make great keys for dicts when you want a pair of separate but related data.  For example, X and Y coordinates on a map (10, 10) is different than (9, 10) for example.  The other would be (player, bullet)?

Thanks for the reply. What I am trying to do is every tick (currently at 1/60th of a second using a timer:
-Draw an ASCII display as read from a file (mostly works, minor issue but will look into later)
-Go through all characters and draw their symbol at their co-ordinate
-Move each bullet according to its attributes (direction, speed etc)
-Draw the bullet at its new co-ordinates
-Check for input from the player and change the player's attributes accordingly (x+1, ammo-1 etc). If the player is firing, initialize new bullets. Draw the player at their co-ordinates.
-Go through all AIs and change their attributes/draw them accordingly (like the player).

Whenever the bullets move, I want them to check the "map" to see if they move over a wall (and if they do, erase the bullet). Then check to see if the bullet can hit a character (player or AI). 
It sounds like this could be accomplished with a method inside of the bullet class that checks the attributes of the current bullet and all available characters (player/AIs)?

Traditionally I've cycled through a series of arrays in the main loop and called functions to check other arrays (inside the MoveBullet function run through the entire Map array and entire Character array).

I'm not quite sure what I can do with Tuples - is the Tuple you're suggesting of (player,bullet) intended to run through a list of players and bullets?
Or would it be used in say, the MoveBullet function(method?) to better compare the attributes of bullets and attributes of the players/AIs? I'm not sure how this would work.

> use a dict and devise some method of uniquely identifying those objects for later retrieval
What would a better way to identify these objects be than a spot in a list like b[12]? 

Thanks for your help.

---

### Post by Greyed on 2008-11-22
> **FoxHound22 said:**
> I'm not quite sure what I can do with Tuples - is the Tuple you're suggesting of (player,bullet) intended to run through a list of players and bullets?
Or would it be used in say, the MoveBullet function(method?) to better compare the attributes of bullets and attributes of the players/AIs? I'm not sure how this would work.

They would be the keys for a dict.  Tuples are like a list in that they store discrete, separate pieces of data.  However they are immutable like a string and thus can be used as keys.  If I were doing what you described I would at least use it on the map.  Consider the following::

[php]
map = {} # Empty dict
for x in range(10):
    for y in range(10):
        map[(x, y)] = '.' # . = empty space
[/php]Nor much different than making a list of lists.  However, with a dict you can then do the following:

[php]
y = 8
for x in range(10,20):
    map[(x,y)] = '.'    
[/php]Now you have a corridor extending right side of the square but you didn't need to make a whole extra array to do it.  Movement then becomes simple as well since you just adjust the x,y position of the object you're looking at, feed it into a tuple and then:

[php]
if not (x,y) in map:
    print "illegal move"
[/php]But I digress.  It took me quite a while to grasp how neat tuples are as keys to dicts so whenever I get the chance to explain I go a tad overboard.  :)

> What would a better way to identify these objects be than a spot in a list like b[12]?TBH, this is really 6-of-one and half-dozen of the other.  I can see it both ways.  If it is important to track the results of ealier shots before later shots (IE, order matters) than I can see how a list would work just fine.  I presume for score tracking you would have a reference to the entity whom shot the bullet inside the bullet object?

On the other hand if order is not important then a dict would work.  It comes down to the semantics of adding and removing the data.  

List:
[php]
bullets = []
bullets.append(bullet) # add
for x in len(bullets): #check and remove
    if check_hit(buillet):
        del bullets[x]
[/php]Dict:
[php]
bullets = {}
key = index # single variable key
key = (index1, index2) # multivariable tuple key
bullets[key] = bullet # add
for bullet in bullets:
    if check_hit(bullets[bullet]):
        del bullets[bullet]
[/php]Functionally the same, just the order changes and the location of the data is slightly different.  The main advantage to the dict, esp with tuples for keys, is that you can put some of the important data as a key and extract only the portions of the dict that you need.  EG if you have (player, bullet_index) you can more easily extract all the bullets from one player by iterating over the keys of the dict vs. having to iterate every object in the list and extract the player ID from that object.  I *think* this will work but my list comprehension-fu is weak since I've never done them before.

[php]
for [x in bullets.keys() if x[0] = player]:
    do_something_here(x)
[/php]Hopefullt someone who knows list comprehensions better than I do will verify or correct that for me.

---

### Post by FoxHound22 on 2008-11-22
Well Python is making more sense now, I think. Two questions though:

In
```
bullets = {}
key = index # single variable key
key = (index1, index2) # multivariable tuple key
bullets[key] = bullet # add
for bullet in bullets:
    if check_hit(bullets[bullet]):
        del bullets[bullet]
```

Doesn't index and index1, index2 need to be defined earlier?
Also in
```
    for x in len(bullets): #check and remove
    if check_hit(bullet):
        del bullets[x]
```

I don't understand the check_hit(bullet) part. Is that calling a function with instance x of the bullet object? And is that function part of the bullet class or a standalone function? If it is, does that line not need the x because of the "For x in len(bullets)"?

---

### Post by Greyed on 2008-11-22
> **FoxHound22 said:**
> In
```
bullets = {}
key = index # single variable key
key = (index1, index2) # multivariable tuple key
bullets[key] = bullet # add
for bullet in bullets:
    if check_hit(bullets[bullet]):
        del bullets[bullet]
```Doesn't index and index1, index2 need to be defined earlier?

Yup.  Just throwing out examples with the presumption that any variables mentioned are initialized elsewhere.

> 
Also in
```
    for x in len(bullets): #check and remove
    if check_hit(bullet):
        del bullets[x]
```I don't understand the check_hit(bullet) part. Is that calling a function with instance x of the bullet object? Does that line not need the x because of the "For x in len(bullets)"?

Yup.  Should be:

[php]
if check)_hit(bullets[x]):
    del bullets[x]
[/php]

Yay for bugs in untested forum code examples!  :)

---

### Post by pmasiar on 2008-11-22
[quote=greyed]map[(x,y)] = '.'[/quote]

You don't have to use braces (): comma makes tuple, so "map[x,y] = '.'" is enough 8-) and it also looks righter 8-)

@FoxHound22: Please learn to trim. You don't have to quote half a page if you do not respond to any of it. Think about all those wasted electrons! ;-)

---

### Post by Greyed on 2008-11-22
> **pmasiar said:**
> You don't have to use braces (): comma makes tuple, so "map[x,y] = '.'" is enough 8-) and it also looks righter 8-)

Old Perl habits die hard.  When I realized Perl was unmaintainable unless one really regulated what one did I went extremely explicit on a great many things.  That went to including parens when they often were not needed.  It will serve me well when I move to Python 3 since I have, from day one, always used print('spam') instead of print 'spam'.  

But in this case, you're right, it does look neater that way.

---

### Post by slavik on 2008-11-23
in Perl6, comma is the list operator ;)

@list = 1,2,3,4,5;

---

### Post by nvteighen on 2008-11-23
> **slavik said:**
> in Perl6, comma is the list operator ;)

@list = 1,2,3,4,5;
Wasn't it already at Perl5?

---

### Post by FoxHound22 on 2008-11-29
Ok, so I used this before my main loop to test things out by creating a bullet:
```

b = []
b.append(bullet)

b[-1].x = 30
b[-1].y = 10
b[-1].speed = 4
b[-1].pause = 4
b[-1].dirt = 1
b[-1].angle = 0
b[-1].maxcycle = 5
b[-1].cycle = 5

```

And it all works fine down in the main loop where the bullet is moved (checking for players, obstacles and staying within the map boundries).

However, if I put this right after the above code:

```

b.append(bullet)
b[-1].x = 10
b[-1].y = 20
b[-1].speed = 4
b[-1].pause = 4
b[-1].dirt = 1
b[-1].angle = 0
b[-1].maxcycle = 5
b[-1].cycle = 5

```

Then when I run the code, I get a "Key Error 20" at this point:


```

    for k in range(0,len(b)):
        StillActive = 1
        if b[k].x > -1:
            if b[k].pause > 0:
                b[k].pause = b[k].pause - 1

            if b[k].pause == 0:
                b[k].pause = b[k].speed
                mapx = b[k].x
                mapy = b[k].y
                maploaded = str(map[mapy])[mapx:mapx+1]

```
That last line gives me the Key Error 20 if that second code block above is added in after the first. Anyone know why? (I'm just using maploaded to make it easier to read through)

---

### Post by slavik on 2008-11-29
> **nvteighen said:**
> Wasn't it already at Perl5?
in Perl5, you have to enclose it in parenthesis.

---

### Post by Tony Flury on 2008-11-30
Dragging the discusssion back to Python - which the OP was asking about ....

The error KeyError suggests that you have a dictionary where you are trying to use a key that does not exists.

A dictionary is initialised like this :

```

variable = {}

``` 

We would need to see all of your code, and the exact error message to tell you exactly what the problem is, but i would suggest that you look for something that you have initialised as a dictionary.

---

### Post by FoxHound22 on 2008-12-11
> **Tony Flury said:**
> 
The error KeyError suggests that you have a dictionary where you are trying to use a key that does not exists.

A dictionary is initialised like this :

```

variable = {}

``` 

We would need to see all of your code, and the exact error message to tell you exactly what the problem is, but i would suggest that you look for something that you have initialised as a dictionary.

I'm using 
```

b = []
b.append(bullet)

```

As I understand it, that makes a list where the first object is a bullet, right? And if I do b.append(bullet) again that will add a second bullet object to the list?
Then I could use b[0].attribute to access the first object's attributes and b[1].attribute to access the second object's attributes?

---

### Post by Tony Flury on 2008-12-12
Absolutely corrrect - if those entries in the list exist. Entries in a list are numbered from 0 upwards sequentially (a list of 3 items will always be 0,1 & 2) - and you try to use index -1 which will produce an error.

But you said you got a KeyError - which suggests to me that you are using a dictionary and not a list.

---

### Post by Greyed on 2008-12-12
> **Tony Flury said:**
> Absolutely corrrect - if those entries in the list exist. Entries in a list are numbered from 0 upwards sequentially (a list of 3 items will always be 0,1 & 2) - and you try to use index -1 which will produce an error.

No, Tony, I checked before offering the advice of -1 as a key.

```

>>> a = [1, 2, 3]
>>> a[-1]
3

```

Negative index numbers simply count from the right instead of the left.  So if someone wants to append an item then reference that item without knowing the index (ala a[len(a)-1]) using a[-1] is the correct way to go about it.  ;)

---

### Post by Tony Flury on 2008-12-14
ah right - relative indexes - a cool but potentially confusing feature.

Ok - but the fact that the code generate a KeyError still suggests to me that the OP is using a dictionary - not a list.

---

### Post by FoxHound22 on 2008-12-23
> **Tony Flury said:**
> 
Ok - but the fact that the code generate a KeyError still suggests to me that the OP is using a dictionary - not a list.

I looked over the code some more, and got it figured out! What I was trying to do was append a class directly into a list.. but Python didn't like that.

What I ended up doing was instancing the class, then appending the instance - which is probably what you guys have been saying all along :)

```

b = []

xv = bullet()
xv.x = 30
xv.y = 3
xv.speed = 4
xv.pause = 4
xv.dirt = 1
xv.angle = 0
xv.maxcycle = 5
xv.cycle = 5
b.append(xv)

```
Repeated, works perfectly. Thanks to everyone for your help! It's been a while since I looked at Python but this is encouraging me to get back into learning. Appreciate it, and Merry Christmas.

---

