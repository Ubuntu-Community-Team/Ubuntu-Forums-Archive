---
title: "Proper use of Classes in Python"
date: 2013-12-16
forum: Programming Talk
---

### Post by blackout2 on 2013-12-16
I have this (pseudo)code, take a look at it.
```

class Scenes(object):


    def room1(self):
        print "You are standing in a deserted cave."
        print "Enter the next room?"
        user_input = raw_input("Y/N\n")
        if user_input == "Y":
            scenes.room2()
        elif user_input == "N":
            exit()
        else: 
            print "That's odd."
    def room2(self):
        print "You are standing outside of a cave."
        print "Enter next room?"
        user_input = raw_input("Y/N\n")
        if user_input == "Y":
            scenes.room3()
        elif user_input == "N":
            exit()
        else:
            print "That's odd."
    def room3(self):
        print "You are standing in a well."
        print "Do you want to go back(B), or go forwards(F)?"
        user_input = raw_input("B/F\n")
        if user_input == "B":
            scenes.room2()
        elif user_input == "F":
            scenes.room4()






scenes = Scenes()
scenes.room1()

```


I want to make 2 classes, one that holds different rooms, and one class that calls the next room. Right here, I have it set up, in a way, that is too straight forward. I want to make a second class, that will read in the current room, and then call the next room in Scenes(). I came very close, but I couldn't make the second class read in the first class(Scenes) self. You see, I had it so that self.scene in Scenes(), would hold a variable named scene, and as you progressed to the next room, it would set self.scene to be "room2", and then the second class would read self.scene, and decide what room is next. However, it couldn't read Scenes() self.scene object. So....I'm at a loss. I want to make this code, work with 2 classes, and I ask myself, is it worth the time, when I could just do it with the above code?
Hope you can help, thanks.

I almost forgot, this is the code I use for 2 classes, and it only runs the first room, over and over again. My guess is that when I set self.scene = "room2", it's somehow not doing it right.

```

scene = "room1"
class Scenes(object):
    def __init__(self, scene):
        self.scene = scene
    def room1(self):
        print "You are standing in a deserted cave."
        print "Enter the next room?"
        user_input = raw_input("Y/N\n")
        if user_input == "Y":
            scene = "room2"
            determine.determine()
        elif user_input == "N":
            exit()
        else: 
            print "That's odd."
    def room2(self):
        print "You are standing outside of a cave."
        print "Enter next room?"
        user_input = raw_input("Y/N\n")
        if user_input == "Y":
            scenes.room3()
        elif user_input == "N":
            exit()
        else:
            print "That's odd."
    def room3(self):
        print "You are standing in a well."
        print "Do you want to go back(B), or go forwards(F)?"
        user_input = raw_input("B/F\n")
        if user_input == "B":
            scenes.room2()
        elif user_input == "F":
            scenes.room4()


class next(object):
    def __init__(self, scene):
        self.scene = scene
    def determine(self):
        if self.scene == "room1":
            scenes.room1()
        elif self.scene == "room2":
            scenes.room2()
    
determine = next(scene)
scenes = Scenes(scene)
determine.determine()

```


[RESOLVED](By me)




After a lot of fiddling, my pseudo code was getting stringier and stringier, bigger and bigger, and more and more complicated. I decided to just scrap it, and redo it entirely...Well, it worked on the first try after that, and I'm happy the way it turned out. Thanks for your help...
Thank you ofnuts, for your very well structured reply.

---

### Post by Irihapeti on 2013-12-16
*Thread moved to **Programming Talk**.*

---

### Post by ofnuts on 2013-12-17
I think you pout too much concern in the rooms. Each room doesn't really know its environment and if you change your map, you wiil have to change every interconnected room... It's Ok to have room classes (but they could all derive from a common basic room) for room specific "behavior" (dragon, loot, or even unlocking some passages) but navigating between rooms should be left to some top-level "controller" function (that can ask the current room what passages are open, for instance).

---

### Post by blackout2 on 2013-12-18
I've come very, very close to getting what I need. The problem is, I'm not sure how to get the "Controller" class I use to run an "unknown" class.
For example:
```

class first_room(object):
	
	def start():
		print "This is the first room."
		print "The next room is the second room"
		return "room_2"
class room_2(object):
	
	def start():
		print "This is the second room."
		print "The End."
		return "the_end"
class Controller(object):
	rooms = {"first_room": first_room.start(), "room_2": room_2.start()}
	def __init__(self):
		self.next_room = #I need to set self.next_room to be the "return" of the first room.
		#I can change the value of self.next_room when I contine through the game in Run()
		#I will use the return of each room, to search through a dict, until I find the right
		#class, then have Run(), run whatever class that is.
	def Run(self):
		#But, I don't know how to do that.
control = Controller()
control.Run()

```

My question, how do I set self.next_scene to be the return of a function, and how do I run a function from a dict.

---

### Post by blackout2 on 2013-12-18
Okay, I am nearly there, I just have one problem now, and it's very simple.
```

room = None
class first_room(object):
	
	def start(self):
		global room
		print "This is the first room."
		print "The next room is the second room"
		room = "room_2"
		return "room_2"
class room_2(object):
	
	def start(self):
		global room
		print "This is the second room."
		print "The End."
		room = "the_end"
		return "the_end"
class Controller(object):
	
	rooms = {"first_room": first_room(), "room_2": room_2()}
	def __init__(self, room):
		global next_room
		self.next_room = first_room()
		self.room = room
	def Run(self):
		global next_room
		if Controller.rooms[self.room] == self.next_room.start():
			Controller.rooms[self.room]


control = Controller(room)
control.Run()

```

My problem is that 'room' isn't set to "room_2", or whatever, before control.Run(), uses it. How can I make first_room(), set room, without actually instantiating it? Or is there a better way?

---

### Post by ofnuts on 2013-12-18
Because you really need a map of you rooms, ie, some structure that says how the rooms are placed next to each other. In the simple cases this is just a 2-dimensional array. Room1 doesn't know that Room2 is on its west and Room2 doesn't know that Room1 is on its east, only the controller, using the map structure, knows... When the player leaves a room, some player position indicator changes depending on the exit taken and the controller finds the next room, and start the interaction of the player with it. This way you can change the map without changing the rooms. 

Something like:
```

class Player(object):
    def __init_(self):
        self.x=1 # we start in room11
        self.y=1
  
    # Plenty of attributes here to manage health/kharma/loot/tools
  
    def move(self,direction):
        '''As defined this method assumes that the rooms at the
        edges of the map don't allow exiting in the void'''
        if direction=='N':
            self.y=self.y-1
        elif direction=='S':
            self.y=self.y+1
        elif direction=='E':
            self.x=self.x+1
        elif direction=='W':
            self.x=self.x-1
        else:
            crashElegantly();

class Room(object):
    '''Base class for all the room classes'''
    
    def __init__(self,name)
        self.name=name
        self.initialized=False;
    
    @abstractmethod
    def visitedBy(player):
        ''' The method that defines the player/room interaction
        At the end the play has a new position, because during
        the interaction Player::move(direction) is called. Each
        room class defines its own'''
        if not self.initialized: # lazy initialization
            self.initialize()
        # proceed with visit

class SimpleRoom(Room):
    '''real room implementation'''
    
    def visitedBy(player):
        '''the visit of this kind of room by the player'''

class DragonNest(Room):
    '''real room implementation, with a more complicated interaction due to dragon'''
    
    def visitedBy(player):
        '''the visit of this kind of room by the player'''
        
        
room00=SimpleRoom('room00')
room01=SimpleRoom('room01')
room02=SimpleRoom('room02')
    
rooms_map=[[room00, room01, room02],[room10, room11, room12],[room20, room21, room22]]


class Game(object):
    '''the whole game'''
    def __init___(self):
        self.player=Player()

    def run(self):
        while player.notDeadYet: # never ending game
            rooms_map[self.player.x][self.player.y].visitedBy(player)


```

Of course, the array above instantiates all the rooms when it's created, but that can be a minimal instantiation that does nearly nothing, the real initialization of the room being done when it's used for the first time (ie, the activate() method of the room checks a flag to see if the room has already been initialized).

One can also discuss at length if the player visits the room or the room receives the player. Finding the right answer for your design is the hard part of object oriented programming.

---

### Post by blackout2 on 2013-12-18
I didn't see your post when I edited my original post.  Thank you for your help, although some of that is beyond the scope of my current knowledge.
All I had to do, is make a class that will run my rooms, and the rest will(hopefully) come with the rest of the game. Right now, I'm re-making a text-adventure game I made a couple weeks ago, that was entirely functions. I will definitely be looking at your code, and implementing that idea into the game. But for right now, this skeleton works fine, to the extent that I need it.

Thank you.

```

#!/usr/bin/python




run_room = "Start"


def Start():
	global run_room
	run_room = "End"
	print "Hello, welcome to the game, I hope you enjoy it."
def End():
	global run_room
	run_room = "Exit_Game"
	print "Good job."


def Exit():
	print "Well done, good job., and The End"
	exit()
class Control(object):
	rooms = {"Start": Start(), "End": End(), "Exit_Game": Exit()}
	def __init__(self, run_room):
		self.run_room = run_room
	def RunCurrentRoom(self):
		if self.run_room == Control.rooms[run_room]:
			Control.rooms[run_room]
				
control = Control(run_room)
control.RunCurrentRoom()

```

---

