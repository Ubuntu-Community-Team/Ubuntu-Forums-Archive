---
title: "python: can i substitute an object name with a variable? (I'll explain the idea)"
date: 2010-09-21
forum: Programming Talk
---

### Post by daweefolk on 2010-09-21
I'm trying to streamline my code and I have an idea of what I can do.
I have a Room class, and as you navigate the rooms the x_and_y[] list is updated with your coordinates. 
When I created the rooms, I named them as such: the room at coordinate 1,1 is called room11. 1,2 is room12, so on and so forth. The Room class has a describe() function that simply prints the object's desc value (assigned when I create the object).
In my main game loop, I set it so if the user enters "d" the game performs the describe() function for the room the user is in. If the x_and_y[] is [1,2] the game runs ```
room12.describe()
```. I have an if statement like this for each of the 16 rooms. 
could I assign a variable with ```
currentroom="room"+str(x_and_y[0])+str(x_and_y[1])
``` and use it as a replacement for the object name? like after running that code use currentroom.describe()?
I hope I was clear enough with what I'm trying to do, and I hope I'm on the right track. Any help appreciated. TIA

---

### Post by jpkotta on 2010-09-22
Put the rooms in a container.  I'd use a dict.

```

rooms = dict()
rooms[1,1] = Room()
rooms[1,2] = Room()
...
x_and_y = (1,2)
rooms[x_and_y].describe()
rooms[1,1].describe()

```

Instead of a dict, you can make your own container.  Note if you use a dict, the key (the part in the square brackets) must be a tuple, not a list.  Lists are mutable, and thus not hashable.

---

### Post by daweefolk on 2010-09-22
> **jpkotta said:**
> Put the rooms in a container.  I'd use a dict.

```

rooms = dict()
rooms[1,1] = Room()
rooms[1,2] = Room()
...
x_and_y = (1,2)
rooms[x_and_y].describe()
rooms[1,1].describe()

```

Instead of a dict, you can make your own container.  Note if you use a dict, the key (the part in the square brackets) must be a tuple, not a list.  Lists are mutable, and thus not hashable.
awesome, thanks, I'll try that!
another question though:
if the key needs to be a tuple, and i need to later reference x_and_y, x_and_y needs to be a tuple as well right? if so, how would I update it as the user moves about the map?

EDIT: never mind. i changed rooms[x_and_y].describe() to 
rooms[tuple(x_and_y)].describe() and everything works

---

