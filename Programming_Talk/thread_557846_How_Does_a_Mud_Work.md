---
title: "How Does a Mud Work?"
date: 2007-09-23
forum: Programming Talk
---

### Post by Noodels on 2007-09-23
I am interested in programming, muds and linux (what a nerd) and I've come to find that I am unable to get any mud engine to work on my computer since I got linux. So, even if I did get one working, in the end I would still want to build a really simple mud engine. In doing so I hope to be able to do far more stuff than on any other mud engine due to understanding how it works. I've just hit a few snags.

I'm leaning towards learning C++ and using that to build my mud engine, although I could use C or Python, what's everyone else's opinions?

A player walks into a room. He sees all the items in that room. How does that work?! As far as I know every object is a class, and each of those have an object.environment value or something similar, so the only theory I have is that the server looks at every single object and lists all the ones with the environment that the player has; it's a very inefficient theory.

Programming + Mud Clients = ???
How do I set up a program that another computer can just telnet up to? I can't find any sites that help me very much with this. Does anyone have a link? Is there a whole tutorial like the classic "Hello World!" program but for telnet, just give me the simplest possible code in the language you think is best that another computer can telnet up to and see "Hello World" and I'd be so so so happy...

How does an engine deal with different commands from different people? I'd just get confused! How does it know who to send what to and how to avoid mixing everything up?

Any sort of help would be great, is there a website? I've looked and I can't find one. There should be one...

---

### Post by Lord Illidan on 2007-09-23
try searching google :

programming mud tutorial.

I found this : [http://www.gamedev.net/reference/programming/features/mudpie1/](http://www.gamedev.net/reference/programming/features/mudpie1/)

but it's windows..

this : [http://www.geocities.com/buildersclan/Articles/article7.html](http://www.geocities.com/buildersclan/Articles/article7.html)

and this : [http://www.gignews.com/morrow1.htm](http://www.gignews.com/morrow1.htm)

---

### Post by Noodels on 2007-09-23
> **Lord Illidan said:**
> try searching google :

programming mud tutorial.

I found this : [http://www.gamedev.net/reference/programming/features/mudpie1/](http://www.gamedev.net/reference/programming/features/mudpie1/)

but it's windows..

this : [http://www.geocities.com/buildersclan/Articles/article7.html](http://www.geocities.com/buildersclan/Articles/article7.html)

and this : [http://www.gignews.com/morrow1.htm](http://www.gignews.com/morrow1.htm)

Wow, Google must have some sort of vendetta against me, these links are great.

---

### Post by pmasiar on 2007-09-23
> **Noodels said:**
> I am interested in programming, ... want to build a really simple mud engine. In doing so I hope to be able to do far more stuff than on any other mud engine due to understanding how it works. 

Games are good start. But multi-user games are hard, to learn programming start with single-user games.

> I'm leaning towards learning C++ and using that to build my mud engine, although I could use C or Python, 

C++ is overkill. In Python, you will be 10 times as productive (or more), and when you find bottleneck (after you **measured** it, and tried to change algorithm, and it did not helped) you can rewrite those 5% of code in C. Python has framework for writing multi-user games, called twisted. It includes IRC and web server :-) Look it up.

> A player walks into a room. He sees all the items in that room. How does that work?! As far as I know every object is a class, 

What level is your experience with OOP? Don't force OOP if plain old database would be enough. ORM would auto-generate object definitions, setters and getters for you. Python's SQLObject or SQLAlchemy are excellent.

MUD is pretty large program, you need to learn smaller programs first. Links in wiki from my sig will get you started. Try pythonchallenge.

Then, join some existing project to learn how things are done. **After that** you can either add your favorite features to that project, or fork, or start new project. But you would have experience about what works and why, from real working code.

Good luck, and have fun!

---

### Post by Noodels on 2007-09-23
> **pmasiar said:**
> Games are good start. But multi-user games are hard, to learn programming start with single-user games.



C++ is overkill. In Python, you will be 10 times as productive (or more), and when you find bottleneck (after you **measured** it, and tried to change algorithm, and it did not helped) you can rewrite those 5% of code in C. Python has framework for writing multi-user games, called twisted. It includes IRC and web server :-) Look it up.



What level is your experience with OOP? Don't force OOP if plain old database would be enough. ORM would auto-generate object definitions, setters and getters for you. Python's SQLObject or SQLAlchemy are excellent.

MUD is pretty large program, you need to learn smaller programs first. Links in wiki from my sig will get you started. Try pythonchallenge.

Then, join some existing project to learn how things are done. **After that** you can either add your favorite features to that project, or fork, or start new project. But you would have experience about what works and why, from real working code.

Good luck, and have fun!

I've been doing my own easy stuff in python and it's all very good, I like python, open source is brilliant. However, I am concerned about cpu. I don't have an amazing computer, (I hope to get a better one in a year) and since python compiles as it goes, I am thinking it uses more cpu and you said yourself that a mud is a fairly big program. So I was thinking of starting off using a code that is a little less demanding on my "high spec" (That's what it was advertised as) computer.

OOP? What is OOP? I'm just skimming over free tutorials again and again until I remember them and I feel like I can speak that language, or at least part of that language, naturally. Then I look at real programs and try and think how they work. (Am I right about the player.environment thing by the way?)

A single player game, GOOD IDEA! I was going to do that a while ago but I think I got... Carried away? I'm going to look at doing that right now.

P.S. Is there a way to see the source code for a really simple mud client? I just want to know what's going on between the client and the server.

---

### Post by Noodels on 2007-09-23
How do I make an if statement return true if a string called command matches any of the keys in a dictonary? I am trying to implement moving.

EDIT : Never mind that, I got it, used the exit key to dictate the viable commands rather than have verbs east, north, west, south and god knows what.

---

### Post by Lord Illidan on 2007-09-23
> **Noodels said:**
> I've been doing my own easy stuff in python and it's all very good, I like python, open source is brilliant. However, I am concerned about cpu. I don't have an amazing computer, (I hope to get a better one in a year) and since python compiles as it goes, I am thinking it uses more cpu and you said yourself that a mud is a fairly big program. So I was thinking of starting off using a code that is a little less demanding on my "high spec" (That's what it was advertised as) computer.

OOP? What is OOP? I'm just skimming over free tutorials again and again until I remember them and I feel like I can speak that language, or at least part of that language, naturally. Then I look at real programs and try and think how they work. (Am I right about the player.environment thing by the way?)

A single player game, GOOD IDEA! I was going to do that a while ago but I think I got... Carried away? I'm going to look at doing that right now.

P.S. Is there a way to see the source code for a really simple mud client? I just want to know what's going on between the client and the server.

There are a lot of opensource muds out there, check them out. I haven't played any mud, though.

However, since it is text-based, I have a feeling that python is going to be as good as C in this environment. I mean, let's say the difference is 1 second slower. In a graphical client like WoW, this difference can lose up 25 fps, for example...but in a text based client, you might not even notice it. Not to mention the time you'll save implementing it.

---

### Post by Noodels on 2007-09-23
> **Lord Illidan said:**
> There are a lot of opensource muds out there, check them out. I haven't played any mud, though.

I was asking about a mud client, I want to know what the server sends to the computer, because I know other stuff is being sent because sometimes my client goes funny and decides to show some of it. (Might just be the colour thing though)

> **Lord Illidan said:**
> However, since it is text-based, I have a feeling that python is going to be as good as C in this environment. I mean, let's say the difference is 1 second slower. In a graphical client like WoW, this difference can lose up 25 fps, for example...but in a text based client, you might not even notice it. Not to mention the time you'll save implementing it.

That is a good point, but I am thinking about when you have lots and lots and lots of players and items in the mud at once, an ordinary processor may begin to struggle.

Anyway, I am still having the snag where I don't know how to see all the items in a room. I have a new theory, the room could have a list of items that it contains, and that list is displayed when the player looks. Small problem though, why would the source codes for muds have a player.environment value when this theory is available? I'm confused!

---

### Post by Tuna-Fish on 2007-09-23
> **Noodels said:**
> 
Anyway, I am still having the snag where I don't know how to see all the items in a room. I have a new theory, the room could have a list of items that it contains, and that list is displayed when the player looks. Small problem though, why would the source codes for muds have a player.environment value when this theory is available? I'm confused!

I think you need both, or then you need a special membership object between them. You need to be able to both list all items in the current location, and to be able to find where an item x is currently.

A tip: never ever ever change the item.environment (or whatever you want to call it) directly from code outside the class. Implement a Item.move(where) function that looks up where the item is currently, removes it from there, and then changes both the item.environment to point to the new place and adds the item to the list of items at that place.

---

### Post by Noodels on 2007-09-23
> **Tuna-Fish said:**
> I think you need both, or then you need a special membership object between them. You need to be able to both list all items in the current location, and to be able to find where an item x is currently.

A tip: never ever ever change the item.environment (or whatever you want to call it) directly from code outside the class. Implement a Item.move(where) function that looks up where the item is currently, removes it from there, and then changes both the item.environment to point to the new place and adds the item to the list of items at that place.

Okay thanks, and I will, changing the two manually is rather tedious. I also need add functions for rooms and items due to having to make them in little bits. Any idea how I'd make a library of rooms and things? Currently I'm keeping the whole thing in a file called matrix.py which is beginning to look awful at just 20 lines or so.

---

### Post by Noodels on 2007-09-23
There's a couple of things in python I can't but need to do right now and I've no idea what to do without them.

1) If I had a class and I wanted to make an object from it, how can I name that object from a string. Like so..

```
mystring = objectname
mystring = myclass(values)
```

If I put that into python it would just call the object mystring.

2) When I print it automatically starts a new line, this isn't very good for listing items in rooms, how do I print without starting a new line?

---

### Post by Tuna-Fish on 2007-09-23
> **Noodels said:**
> Okay thanks, and I will, changing the two manually is rather tedious.

By the way, this is one form of encapsulation, and is considered one of the main principles of OO programming. And, actually, if you walk into a CS classroom teaching about OO, very likely the professor will outright ban you from manipulating or fetching any attribute manually, using setters and getters instead, for example:
```

Instead of:
main:
a.age = 13
print a.age

do:
class:
def set_age(self,age):
    self.age = age
def get_age(self):
    return self.age
main:
a.set_age(13)
print a.get_age()


```

At first it looks awful. Why would you ever want to do that? It's a lot more to type and it even looks ugly. But what if you, a year later and with 10.000 lines of code depending on your class, you finally realize that storing age as a plain number is f*#"&* stupid, as updating those ages gets hairy fast. If you used attributes manually, you are pretty much SOL, but if you used setters and getters, all you need to do is change the class to:

```

def set_age (self, age):
    self.birthday = (datetime.date.today()-datetime.timedelta(365*age))
def get_age(self):
    return ((datetime.date.today()-self.birthday).days/365)

```

and update the data, and all the old code still keeps working.
This is actually a very horrible way to do it, but I just couldn't be bothered to do it properly, and hopefully you get the point: it is easy to **change**.

> I also need add functions for rooms and items due to having to make them in little bits. Any idea how I'd make a library of rooms and things? Currently I'm keeping the whole thing in a file called matrix.py which is beginning to look awful at just 20 lines or so.

Just split it to many files, put all the files in the same dir and use 
```
import room 
#(for room.py)

``` Only place function and class definitions in these files, any code in the main gets executed when you import.

> **Noodels said:**
> There's a couple of things in python I can't but need to do right now and I've no idea what to do without them.

1) If I had a class and I wanted to make an object from it, how can I name that object from a string. Like so..

```
mystring = objectname
mystring = myclass(values)
```

If I put that into python it would just call the object mystring.

I don't think you really want to do that. it can be done, but there are really few reasons you'd ever want to do that. Just put all the objects into the proper lists, and don't give them a name in your namespace. Like:

```

temp = myclass(values)
level["darkroom"].stuffhere.append(temp) 

```
> 
2) When I print it automatically starts a new line, this isn't very good for listing items in rooms, how do I print without starting a new line?
```

print "hey, without a line break",
print "this truly is so",

```
note the ',' in the end. yes, it's bad notation.

---

### Post by pmasiar on 2007-09-23
> **Noodels said:**
>  So I was thinking of starting off using a code that is a little less demanding on my "high spec" (That's what it was advertised as) computer.

Don't worry about speed first: if your code does NOT work right, even if fast, is useless.

You are looking into many months, possibly years of work before your game would be usable for others, so don't be carried away with speed now. 

BTW Python compiles sources into .pyc files (which is bytecode optimalized for fast run, of course because of dynamically typed languages it is not as tightly compiled with type info as statically typed languages like C or C++, but there are compilers which will infer this type info and compile more effective code at runtime. Confused? Summary: don't worry about speed, you can add speed later.

> OOP? What is OOP? 

Object-oriented programming. Before asking any  question you should search wikipedia: [http://en.wikipedia.org/wiki/Oop](http://en.wikipedia.org/wiki/Oop)

> P.S. Is there a way to see the source code for a really simple mud client? I just want to know what's going on between the client and the server.

Yes, get any open-source game and look at the code :-)

---

### Post by Noodels on 2007-09-24
Thanks, those last two posts look really helpful!

---

### Post by Noodels on 2007-09-24
> **Tuna-Fish said:**
> I don't think you really want to do that. it can be done, but there are really few reasons you'd ever want to do that. Just put all the objects into the proper lists, and don't give them a name in your namespace. Like:

```

temp = myclass(values)
level["darkroom"].stuffhere.append(temp) 

```


That's what I would do, but I wanted a function which would create a class object for me rather than having to decide what that class is called myself because sooner or later I'll probably end up calling a new thing the same as an old thing and then the old thing will disappear and I will get all confused and so on.

---

### Post by Tuna-Fish on 2007-09-24
> **Noodels said:**
> That's what I would do, but I wanted a function which would create a class object for me rather than having to decide what that class is called myself because sooner or later I'll probably end up calling a new thing the same as an old thing and then the old thing will disappear and I will get all confused and so on.

all right, this is going to get a bit complicated, but, I'll try to make it simple.

I'll first create a simplest possible class and make a couple of object instances of it:
```

>>> class h:
...    def ___init__(self, name):
...        self.name = name
...
>>> a = h('joe')
>>> b = h('jim')
>>> c = h('billy')

```
Now, let's store them all in a list:
```

l = [a,b,c]

```

now, let's just test everything is still all right:

```

>>> def pp(l):
...     for i in l:
...             print i.name
... 
>>> pp(l)
joe
jim
billy

```

yep, still works.

Now, what would you think would happen if I did a = h('margaret')?
Let's try:
```

>>> a = h('margaret')
>>> a.name
'margaret'
# now, what will have happened to poor joe?
>>> pp(l)
joe
jim
billy
# yep, still there, even if he doesn't have a name left anymore.

```

So what should you get from all this: when I do a = h('joe'), a isn't actually the name of the object, it's a reference to the object. The true name of an object can be seen for your own objects in python by just typing the reference name into the interpreter and pressing enter. (knowing the real name is not really useful usually)
```

>>> l[0]
<__main__.h instance at 0xb78434ec>
# that's joe.

>>> a
<__main__.h instance at 0xb784366c>
#and that's margaret.

```
Object exists and is useful as long as there is at least a single reference to it, if there's not even a single reference, there is no way of making new ones, and eventually the object will be deleted. Changing one reference to point somewhere else will not change any of the other references to the object: modifying "a" did not change "l[0]".

In most real code, you don't want to have named references to all your objects, heck, if you want to have a system where you can dynamically create items, having them would be a really bad idea. And another point of good OO design is to have as few references to stuff as possible, without sacrificing usability. So, players should have references to them in 2 lists: One list for objects at a location, and one list for actors. Items should only have reference in one list: the list of objects at some location, or the list of items carried by a player.

---

### Post by pmasiar on 2007-09-24
One more note. This kind of game has deep inside a database struggling to get out. It is table of players, table for inventory for each player, table of rooms, table of objects in each room, table of monsters/NPCs, table of where monsters can move, table with properties of each object and monster, etc.

Years ago I created a game creator, which used dBase tables to enter game info, then output game definition (using some adventure game toolkit) and compile it into a playable game.

---

### Post by CptPicard on 2007-09-24
On the other hand, pushing your data into a database is going to make things more complex and slower than they need be... MUDs are so simple that I bet you can do wonders with 4GB, and just serialize everything on disk when you need to persist your server's state. Of course, if RAM isn't enough, you're forced to use a database, certainly...

Another reason to use a database would be concurrency management, but I would probably start by coding my MUD as a single event processing loop that just handles events from players' queues one at a time, without multithreading or anything.

If you do look at databases, certainly check out PostgreSQL, it's got good custom datatype support and even GIS extensions and can do things like two-dimensional overlap queries etc in-database, which would be an interesting feature to have in a MUD :) You could ask for example "what objects are there within 100m reach of the character?"

I've always wondered what could be done with modern technology if MUDs were updated just a little, say, up to the point of creating a modern OSS Ultima Online... you could have a *humongous* virtual world. :)

---

### Post by Noodels on 2007-09-24
Now I can see that I can rename a class, which is pretty useful, I take it that a create item command can use the same name for a class, and that class can be accessed via the room it's in rather than by it's name. Good!

However, a library would be a nice thing to have. I'm not very experienced using these except for when I was playing with the Dead Souls Mud a little bit. For now all I want to do is this, import all the contents of a directory, can python do that?

---

### Post by LaRoza on 2007-09-24
> **Noodels said:**
> 
For now all I want to do is this, import all the contents of a directory, can python do that?
Like a package? 

[http://docs.python.org/tut/node8.html](http://docs.python.org/tut/node8.html) 

[http://www.network-theory.co.uk/docs/pytut/Packages.html](http://www.network-theory.co.uk/docs/pytut/Packages.html)

---

### Post by CptPicard on 2007-09-24
> **Noodels said:**
> Now I can see that I can rename a class, which is pretty useful, I take it that a create item command can use the same name for a class, and that class can be accessed via the room it's in rather than by it's name. Good!


Honestly, I have no clue what this design looks like based on this. :) Care to elaborate a little on what you're doing, as I'm curious... it seems like you're potentially doing things in a more complex fashion that is neccessary? Renaming classes? Accessing a class via a room instead of name? :)

I suspect you mean "object", and my hunch is you're using some kind of a factory method pattern...?

---

### Post by Noodels on 2007-09-24
No idea, but if someone gives me a link that's host files I'll gladly put it up there for you to see if you want. There's a lot to do yet.

---

### Post by aks44 on 2007-09-24
> **Noodels said:**
> if someone gives me a link that's host files I'll gladly put it up there for you to see if you want.

You can attach files to your forum posts. Just tgz all your files beforehand... :)

---

### Post by Wybiral on 2007-09-24
If it's 2d... Use Python.

If it's 3d, use Python... But write the rendering code in C.

Python is brilliant for games (particularly how easily generic objects can be created without dealing with large complex systems of inheritance).

---

### Post by Tuna-Fish on 2007-09-24
> **Wybiral said:**
> If it's 2d... Use Python.

If it's 3d, use Python... But write the rendering code in C.

Python is brilliant for games (particularly how easily generic objects can be created without dealing with large complex systems of inheritance).

By the way, it seems that lately the big commercial developers have figured this out too. I think the first was eve online, but of the last 3 games I've purchased, 2 use python. (Civ 4 and Oblivion)

---

### Post by Note360 on 2007-09-24
here is my idea. Each room is a class made up various arrays one is an array of say items another is an array of characters

---

### Post by Noodels on 2007-09-25
Here is it so far, please be nice, there's a lot to do on the code already have and to someone professional I expect it looks like a nightmare program.

---

### Post by Wybiral on 2007-09-25
It doesn't look bad, but for the sake of scalability you should definitely not be programming each action in. You should use a Python dictionary or something to store the key and it's corresponding function.

You'll probably want to do this with most of your components (rooms/items... You get the drift).

The reason is that... As you build on, having to code every detail in is going to cause massive code bloat and make it very difficult to manage. A game engines job is to handle all of those little details, then it will have an interface allowing for a simplified way of describing everything. This could be in the form of a level format or a simplified programming interface... But you shouldn't be hard-coding every action. It should be simple and quick to write levels, not a bunch of code.

---

### Post by Noodels on 2007-09-25
> **Wybiral said:**
> It doesn't look bad, but for the sake of scalability you should definitely not be programming each action in. You should use a Python dictionary or something to store the key and it's corresponding function.

You'll probably want to do this with most of your components (rooms/items... You get the drift).

The reason is that... As you build on, having to code every detail in is going to cause massive code bloat and make it very difficult to manage. A game engines job is to handle all of those little details, then it will have an interface allowing for a simplified way of describing everything. This could be in the form of a level format or a simplified programming interface... But you shouldn't be hard-coding every action. It should be simple and quick to write levels, not a bunch of code.

Dictionaries!! Of course! Why oh why didn't I think of that..? Thanks a lot. I also really want some easy way of storing each room in an individual file, possibly in a directory, I'm gradually making the room class more complicated, there's a lot I want to implement. When I had Dead Souls I rather enjoyed having a library with everything in it that I felt I could manage no matter how many files I added.

---

