---
title: "[SOLVED] [Python] Having trouble with this one."
date: 2008-09-20
forum: Programming Talk
---

### Post by dodle on 2008-09-20
I'll try to explain the best I can what I am trying to do.  I'm having a really hard time figuring this out.  Let's say there is a room:[PHP]def room():
  action = raw_input('What would you like to do?')[/PHP]

In this room, there are four objects.  A lamp, a flashlight, keys, and pogo stick.  Let's say that I have a bag around my shoulders.  I want to "take" each object and add it to my bag using a command.

Something like:[PHP]command lamp # lamp is added to bag
command flashlight # flashlight is added to bag
command keys # keys are added to bag
command pogo stick # pogo stick added to bag[/PHP]

Have I confused everyone?  I've got functions down pretty well, but if this requires classes I'm in deep doo-doo.  Classes are still out of my reach.:(

---

### Post by gomputor on 2008-09-20
If i understand what you want to do, then the answer maybe simple.

Suppose you have a bag and you want to add things inside, so it must be a list, and declare it like
[PHP]my_bag = [] # an empty list[/PHP]

Now suppose in your **def** room you want the user to type something
like 'take apple' so you can add it in your bag, you can do something like:

[PHP]
def room():
    # split the input into arguments, the first one (action[0]), is the command
    # and the second one (action[1]), the thing you want to take
    action = raw_input('What would you like to do?').split()
    if action[0] == 'take':
        # add the thing in your bag
        my_bag.append(action[1])
[/PHP]

Was it helpfull?

---

### Post by dodle on 2008-09-20
Yes, I think that is exactly what I want to do.  Thank you.  I'm going to play around with it to make sure, then I'll mark this thread as solved.

Edit: Oh!  I have a question about split().  This divides my input in two parts right?  Can the input be divided into more than two?

---

### Post by gomputor on 2008-09-20
> **dodle said:**
> Oh!  I have a question about split().  This divides my input in two parts right?  Can the input be divided into more than two?

It can be divided into as many parts as you want. If you don't specify any delimiter for the split() method, then it separates the string according to the space between the words or chars inside that string. Split always returns a list, so for example:
[PHP]>> my_string = 'Hello my dear friend'.split()

>> my_string

['Hello', 'my', 'dear', 'friend'][/PHP]
Then you reference to them with my_string[0], my_string[1], my_string[2], my_string[3]... an so on. Got it? :)
And always read the docs.
[http://docs.python.org/lib/string-methods.html]("http://docs.python.org/lib/string-methods.html") scroll down to see the split() method

---

### Post by dodle on 2008-09-20
Thanks again, got it!

---

### Post by dodle on 2008-09-24
I unmarked this thread as solved because I am having a new problem with this.

[PHP]bag = []
loop = "go"
while loop == "go":
    command = raw_input('What would you like to do').split()
    if command[0] == "take":
        if command[1] == "item":
            bag.append['item']
            print "You got the item."
            loop = "stop"
        else:
            print "take what?"[/PHP]
If I type "take item", everything works fine.  If I type "take blahblah", works fine.  But if I just type "take", I get the following error:```
IndexError:  list index out of range
```
I guess this is because it is looking for a second word.  How can I fix this?

---

### Post by ghostdog74 on 2008-09-24
check for length of the list. make sure its 2 items. I am sure you know how to check for length.

---

### Post by gomputor on 2008-09-24
> **dodle said:**
> [PHP]bag = []
loop = "go"
while loop == "go":
    command = raw_input('What would you like to do').split()
    if command[0] == "take":
        if command[1] == "item":
            bag.append['item']
            print "You got the item."
            loop = "stop"
        else:
            print "take what?"[/PHP]
If I type "take item", everything works fine.  If I type "take blahblah", works fine.  But if I just type "take", I get the following error:```
IndexError:  list index out of range
```
I guess this is because it is looking for a second word.  How can I fix this?

Frankly I can't understand how you came up with this. :) It's full of errors.
First you don't need the [COLOR="Blue"]if command[1] == "item":[/COLOR]
You want to take something, an item, not something that is called "item".
Second, you don't append to a list with [COLOR="Blue"].append[][/COLOR]. You do it with [COLOR="Blue"].append(my_thing_to_append)[/COLOR]. () instead of [].
Read carefully the tutorial that comes with the Python documentation. Read about lists, loops, and the split() command. Read carefully and experiment. It's the only way.

Check the following. Play with it and try to figure out what it does. It's not the best way to write it, but it's a simple one to understand. Read, experiment and think! :)
[PHP]bag = []

while 1:
    command = raw_input('What would you like to do?: ').split()
    if command[0] == 'exit':
        print 'Bye bye!'        
        break

    if len(command) > 1:
        item = command[1]
        if command[0] == 'take':
            bag.append(item)
            print 'You got ', item
        else:
            print 'Sorry but I don\'t understand your command'
    else:
        print command[0], ' what?'

[/PHP]

EDIT:* while 1:*  means loop for ever until some contition is met (in this case if you type 'exit'.)
And we assume that you type something and not just hit the ENTER key.

---

### Post by dodle on 2008-09-24
Okay, I didn't do it exactly how you told me to gomputor, I'll have to practice it some more.  But, I was able to do what I wanted to with your advice.

> **gomputor said:**
> 
Second, you don't append to a list with [COLOR="Blue"].append[][/COLOR]. You do it with [COLOR="Blue"].append(my_thing_to_append)[/COLOR]. () instead of [].

I did notice that in my original script when the program wouldn't run because of it :D.  But I forgot to correct it in my post.  Thanks again for your help.

Edit:  You'd probably laugh at all the unnecessary stuff if I showed you my original script:D.

---

### Post by gomputor on 2008-09-24
> **dodle said:**
> Edit:  You'd probably laugh at all the unnecessary stuff if I showed you my original script:D.

I bet you'd propably laugh more if I showed you my first attempts at programming! Not that now you can't, but ok... you can laugh less :)

---

### Post by skullmunky on 2008-09-25
Hi, it sounds like you solved your problem already.  But this just reminded me of an example I happened to have lying around that does exactly this, plus a few more things.  Enjoy it, look at it for a while, and then you'll quickly get motivated to learn classes and file I/O.  :)

```

# a short text adventure in python
# designed to demonstrate a few programming concepts:
#
# lists
# associative lists
# functions
# using loops and lists together
 
# a list is a variable that contain multiple items.  the items in the list are contained in square brackets.

inventory=[]

############# Room Descriptions ##############
# roomDescriptions is a list of texts, one for each place in the game (room).
# room 0 is the clearing, room 1 is the path, room 2 is the riverbank, etc.
# currentRoom keeps track of where you are; you can use this variable to 
# get the current description out of the list.

currentRoom = 0

roomDescriptions=[
"""Clearing
You are standing in a clearing in the middle of the forest.  A path leads to the east and to the west.""",
"""Forest
You are on a path in the forest.  You can hear water off to the east.""",
"""Riverbank
You are standing on the west bank of a river.  It's pretty wide, and the water is flowing too rapidly to cross here.  A path goes north along the riverbank.""",
"""Riverbank
There is an old oak tree here.""",
"""Forest
To the east is a clearing.  To the west, the woods get darker and more forbidding; a traveler could easily get lost in there.""",
"""Deep forest
You are in a deep part of the forest.  Very little sunlight makes it through the thick canopy of the trees.  It's hard to see which way you came from.""",
"""Small clearing
You find your way into a small clearing in the heart of the forest.""",
"""East Riverbank
You are on the other side of the river, and out of the forest."""
]

############## paths from one room to another ########
# each room has a list of other rooms it connects to.
# for example, room 0 connects to room 1 and room 4
# the links are labeled by direction

# this type of list, using text rather than numbers, is 
# called an "associative list" or "dictionary"

# it uses { } instead of [ ] to differentiate it from 
# a normal list.

# the words used to label the items (like "east") are
# called "keys"

# these lists are then combined into a master list of 
# all the connections, called "moves".

# create an empty list to begin with
moves=[0]*10

moves[0]={"east":1,"west":4}
moves[1]={"west":0,"east":2}
moves[2]={"north":3,"west":1}
moves[3]={"south":2}
moves[4]={"east":0,"west":5}
moves[5]={"east":5,"west":5,"north":5,"south":5}
moves[6]={"north":5}
moves[7]={}

################ items in different rooms ############
# each room can have a list of items
# combining them together gives another list of lists,
# for all the items.

items=[["stick"],["compass"],[],[],["mushroom"],[],["rope"],[]]

################# descriptions of objects ############
# this is an associative list, so you can look up the 
# description of an object from its name

itemDescriptions={
"stick":"It's a stick, about 3 feet long.",
"compass":"A handy little magnetic compass",
"mushroom":"It's white with red spots.  Looks tasty.",
"rope":"A long, sturdy coil of rope."}

################ functions to do things ##############

# def creates a function
# you can pass in a variable to a function

# look at things, or at places
# if noun is empty, then assume the player wants to 
# look at the room.  
# if there is a specific noun, like "mushroom", see if 
# it's in the inventory, or in the room

def look (noun):
	global currentRoom
	if (noun):
		if noun in inventory:
			print itemDescriptions[noun]
		elif noun in items[currentRoom]:
			print itemDescriptions[noun]
		else:
			print "There's no " + noun + " here."
	else:
		print ""
		print roomDescriptions[currentRoom]
		if len(items[currentRoom]) > 0:
			for i in items[currentRoom]:
				print "there is a " + i + " here"


################ function to go to another room #####

def go (direction):
	global currentRoom
	
# has_key is a method for dictionary lists, to tell you if 
# the list has an entry for that key or not
# so, this tells us if the room has a path in the direction
# we're trying to move in
	
	if moves[currentRoom].has_key(direction):
		currentRoom=moves[currentRoom][direction]
		look("")

	else:
		print "You can't go that way."
		

################# get an item ##################
# see if the item is in the room
# if it is, add it to my inventory,
# and remove it from the item list for the room
# so you can't get it twice

def get (noun):
# is that item here?
	if noun in items[currentRoom]:
		print "you got the " + noun
		inventory.append(noun)
		items[currentRoom].remove(noun)
	else:
		print "There is no " + noun + "here."
		
################# use an item ###############

def use (noun):
# do you have that in your inventory?
	if noun in inventory:
		if noun=="compass":
			useCompass ()
		elif noun=="rope":
			useRope()
		elif noun=="stick":
			useStick()
		else:
			print "I don't know what you'd use that for."
	else:
		print "You don't hava a " + noun + "."

########### special functions for items #########

def useCompass ():
	if currentRoom==5:
		print "Using the compass, you can now get your bearings."
# open up the path back to the east again
		moves[5]["east"] = 4
		moves[5]["south"]=6
	else:
		print "You're a good Boy Scout, but the compass doesn't tell you anything you didn't already know."
		
def useRope ():
	if currentRoom==3:
		print "You throw the rope over a branch of the oak tree, so you can swing across the river."
		moves[3]["east"]=7
		roomDescriptions[3]=roomDescriptions[3] + "There is a rope tied to a branch over the river."
		
def useStick ():
	print "You wave the stick around, pretending it's a sword.  Let's hope nobody's watching, you look pretty silly."
	
def eat (noun):
	if noun in inventory:
		if noun=="mushroom":
			print "You eat the mushroom, which tastes kind of funny.  Suddenly you find that you are much larger, and you feel like you could smash bricks.  Too bad that doesn't help you here in the forest."
		else:
			print "I don't think you want to eat that - you don't know where it's been."
	else:
		print "You don't have any " + noun + ".  Too bad, that sounds pretty tasty right now."
		
playing = 1

print "**** Afternoon in the Forest : A Short Text Adventure ********"
print ""


look ("")

while playing:
	
	playerinput=raw_input (">")
	
	words = playerinput.split(" ")
	
	action = words[0]
	
	if len(words)>1:
		noun=words[1]
	else:
		noun=""
		
	if action=="go":
		go(noun)
	elif action in ("east","west","north","south"):
		noun=action
		go(noun)
	elif action=="get" or action=="take":
		get(noun)
	elif action=="use":
		use(noun)
	elif action=="look":
		if noun == "at":
			noun=words[2]
		look (noun)
	elif action=="eat":
		eat (noun)
	elif action=="scream":
		print "in the woods, no-one can hear you scream."
	elif action=="jump":
		print "sorry, this is a no-jumping zone."
	elif action=="quit":
		playing=0
	else:
		print "You can't do that here."
	
print "Goodbye.  Thanks for playing"

```

---

### Post by dodle on 2008-09-26
Thanks skullmunky, this will be helpful.

---

### Post by dodle on 2008-10-02
Edit:  The answer to this problem was already given to me... in this same thread.  *blush*

---

