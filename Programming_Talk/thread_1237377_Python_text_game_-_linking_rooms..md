---
title: "Python text game - linking rooms."
date: 2009-08-11
forum: Programming Talk
---

### Post by BardSeed on 2009-08-11
I'm attempting to make a text-game to be run in IDLE. I've got the bare bones of my first room done, but I've realised that I don't know how to link rooms. I'd like the user to be able to pass back and forth between rooms.
As far as I can tell, classes will be needed, but I'm not very adept with them, having only been learning Python for less than a week. Here's what I have so far.

```
#Defining my functions.
#The menu function will add 1 to the index number of each entry
#and display them like this: "1) Item".
def menu(list, question):
    for entry in list:
        print 1 + list.index(entry),
        print ") " + entry
    return input(question)


#Lists for object in each area.
itemsA = ["beds", "drain", "open door"]


#Brief introduction
print """You awake in a room that is unfamiliar to you.
The harsh light stings your weary eyes. The walls and
floor appear to be composed of thick metal. Looking 
around, you see""", len(itemsA), """points of interest:"""
for entry in itemsA:
    print entry
print "Please enter the number that corresponds to your choice."
print " "

loop=1
choice = 1

while loop==1:
    choice = menu(itemsA, "What would you like to examine?")
    if choice == 1:
        print " "
        print "You see four beds; they seem to have been used recently."
        print " "
    elif choice == 2:
        print " "
        print "It looks as if it's been used as a toilet."
        print " "
    elif choice == 3:
        print " "
        print "The same sterile light as from this room emanates from the hallway."
        print " "
    else:
        print " "
        print "That is not an appropriate action."
        print " "
```

I'd like to offer the player the option to pass through the door when they examine it. So, it would be something like this(although this code doesn't work, it will explain my intentions):
```
elif choice == 3:
        print " "
        print "The same sterile light as from this room emanates from the hallway."
        input("Would you like to move into the hallway? (1 for yes, 2 for no)")
            if input == 1:
                Code for new room
        print " "
```
Any help or hints would be greatly appreciated.

---

### Post by Nevon on 2009-08-11
Using a procedural approach (running the code straight from top to bottom) is not recommended for something like this. I'd recommend that you learn how to properly use functions, and perhaps even have a look at object orientation before attempting something like this.

---

### Post by NathanB on 2009-08-11
Python has excellent list processing facilities.  Put them to good use by making a map of your game playing area.

[php]# key
# ---
# 1 hall    4 kitchen
# 2 cellar  5 armory
# 3 dungeon 6 treasury
#
# -------------
# | 6 | 2 | 3 |
# -------------
# | 5 | 1 | 4 |
# -------------

import sys

# room format:
#   Description,
#   Exits,
#   North, South, East, West
nullvoid = [
  'This is not a room -- your code is buggy!',
  'There are no exits.  Please fix the code!',
  0, 0, 0, 0 ]
hall = [
  'This is the main hall of the castle.',
  'Exits are North, East, and West',
  2, 0, 4, 5 ]
cellar = [
  'This is the grand cellar.',
  'Exits are South, East, and West',
  0, 1, 3, 6 ]
dungeon = [
  'You are in the creapy damp dungeon.',
  'There are no exits!!',
  0, 0, 0, 0 ]
kitchen = [
  'This is the mighty kitchen.',
  'Exits are North and West.',
  3, 0, 0, 1 ]
armory = [
  'This is the frightening armory.',
  'Exits are North and East.',
  6, 0, 1, 0 ]
treasury = [
  'This is the valuable treasury.',
  'You are welcome to stay here.',
  0, 0, 0, 0 ]
rooms = [ nullvoid, hall, cellar, dungeon,
  kitchen, armory, treasury ]
room = 1
currentroom = rooms[room]
playing = 1
print ' '
print currentroom[0]
print currentroom[1]
print ' '
print 'Please pick a direction: '
while playing == 1:
  direction = sys.stdin.readline()
  if (direction[0] == 'n') and (currentroom[2] <> 0):
    room = currentroom[2]
  if (direction[0] == 's') and (currentroom[3] <> 0):
    room = currentroom[3]
  if (direction[0] == 'e') and (currentroom[4] <> 0):
    room = currentroom[4]
  if (direction[0] == 'w') and (currentroom[5] <> 0):
    room = currentroom[5]
  currentroom = rooms[room]
  print ' '
  print currentroom[0]
  print currentroom[1]
  print ' '
  if room == 3:
    print 'You were eaten by the pet dragon.'
    print '    --- YOU LOOSE ---'
    print ' '
    print 'Please play again...'
    break
  if room == 6:
    print 'You have found the chest of gold!!'
    print '    --- YOU WIN ---'
    print ' '
    print 'Please play again...'
    break
  print 'Please pick a direction: '[/php]

Hope this helps!

---

