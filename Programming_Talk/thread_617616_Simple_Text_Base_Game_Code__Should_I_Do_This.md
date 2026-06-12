---
title: "Simple Text Base Game Code : Should I Do This?"
date: 2007-11-19
forum: Programming Talk
---

### Post by Noodels on 2007-11-19
I've been working on this code a while, not much but I've put a little bit together in an attempt to create my own single player text based game. And I'm wondering, if anyone would care to download that quick code and look at primarily the sud.py, player.py and comms.py paying attention to the player input.

The player has a dictionary of commands, when a key for that command is typed in it brings up the relating function. I'm in the process of trying to upgrade to a better command system than what I had left commented, where every command is an elif function. You can see that one is still unchanged, the one to move. That one currently works, but from the go function in the comms module. So far the command in the dictionary only relates to the room it points to, and not the ability to go to that room. If you removed the current elif function that deals with the exits, the program would cease to work.

My question is this, is it worth going to the trouble of making the room exits actual commands or not, and put the go function in the comms module back to a simpler form, or find some way to put all the possible commands in one place? (Quit command stays where it is, I dunno how to make it work from anywhere else.)

Any pointers or advice would also be helpful, this is my first time doing this sort of thing. Be nice. :)

P.S. There are a few bugs for the look command, but I've dealt with that since then so it's fine now. Just saying so no-one points it out.

---

### Post by smartbei on 2007-11-19
Well, this is somewhat of an odd way of doing it :).

Firstly, I am by no means an accomplished OOP programmer in python (or really in any language for that matter, but in others more than python), but it seems like you chose an odd way to accomplish what you were trying to do. I guess I would do it this way:

The player is a class with the abilities: move, look around, peek into nearby rooms, etc. Each one of those could be a method of the player class. The player has several attributes: current place (coordinates on the map), current health, max health, power, etc.

Then there is a class that is a map. This is initialized with the size of the playing field, and it holds a matrix (could be represented as a list of lists) of rooms in the map. This class has methods like: in_room (returns what is in a room), move_possible (returns whether the requested move is possible (i.e. not blocked by a wall), etc.

A room is a class that has atributes: in_room (a list of items), exits/walls, etc. And for methods it has various helper functions.

Items are a class that can hold, as attributes, abilities of the item, its health, whether it can be destroyed, whatever. it has a method do_effect or something of the sort so that it can be called easily by iterating through the items in each room (which is something the helper function in the room could do), etc.

A monster class could inherit from item, and add a delay until attack, whether it can be charmed, etc.

Then, game would proceed by calling map.player.<action>() (or map.players[i].<action>()) using some sort of cover function which could be implemented as a simple dictionary with the keys being the possible actions, and the values being functions of the player class. Note that this dictionary does not change - If the player want's to walk into the wall, only the room should be able to tell him that there is a wall there.

Well, I hope you understood what I meant here - sorry about the length. You got me interested though, so I think I will write my own implementation :).

Lastly, you may want to think about using something like ncurses for the tui (text user interface :D).

---

### Post by Martin Witte on 2007-11-19
some random comments:
- keep your code together in one module, as you only have 100 lines or so in total. if it gets difficult to manage you always can split
- in comms.py methods look and glance do more or less the same, I suggest to remove one of these
- use default arguments, your code will look more clean.
- python supports boolean values, so you can write 'loop = True'  instead of 'loop = 1', and then 'while loop'  instead of 'while loop == 1'

my shot looks then like:
def go(guy,direction):
 #Seriously. Fugged.
 print "You walk",direction
 #Makes note of where we're going.
 where = guy.commands[direction]
 #Player can no longer go to one of the rooms that this room leads
 #to, as he is going somewhere else.
 for value in guy.environment.exits.keys():
  del guy.commands[value]
 #Heave ho! Now he's where he wants to be.
 guy.environment = where
 #Checks his surroundings for baddies!
 look(guy)
 #Enables the guy to walk to the rooms leading off this one.
 for key,value in guy.environment.exits.iteritems():
  guy.commands[key] = value
 #That's it, cool huh?

def look(guy):
 if guy.blind:
  print "You cannot see because you are blind!"
 else:
  print guy.environment.description,
  print guy.environment.longdesc,
  contents = guy.environment.contents
  for content in contents:
   if contents.index(content) <= 0:
    word = str(content) + "."
   else:
    word = str(content) + ","
   print word
  print " "
  print "Exits:",guy.environment.exits.keys()

class room:
 def __init__(self, desc = "There is a room.", exits = {}, ldesc =  "No long description has been set."):
  self.exits = exits
  self.description = desc
  self.contents = []
  self.longdesc = ldesc

void = room("Well now you're fuckered..")
room1 = room("In a clearing in the forest.")
start = room("This is the starting room.", {'north' : room1})

room2 = room("On a small path in the forest.", {'west': room1})
room1.exits['east'] = room2

class item:
 def __init__(self,name,getable=0):
  self.name = name
  self.environment = void
  void.contents.append(self)
  self.getable = getable

 def move(self,where):
  del self.environment.contents[self.environment.contents.index(self)]
  self.environment = where
  self.environment.contents.append(self)

 def __str__(self):
     return self.name

totempole = item("a totem pole")
totempole.move(room1)

totempole = item("an evil totem pole")
totempole.move(room1)

class player:
 def __init__(self,name):
  self.name = name
  self.maxhealth = 100
  self.health = self.maxhealth
  self.environment = start
  self.blind = False
  self.contents = ["a sandwich"]
  self.commands = {"look":look, "north":room1}

guy = player("Berin")

#The running of the game starts here.
loop = True
while loop:
 print guy.health,"/",guy.maxhealth," >"
 command = raw_input()

 if command == "quit":
  loop = False
  print "Goodbye and thankyou for playing."
 #elif command == "glance":
 # comms.glance(guy)
 #elif command == "look":
 # comms.look(guy)
 elif guy.environment.exits.has_key(command):
  go(guy,command)
 elif guy.commands.has_key(command):
  guy.commands[command](guy)
 else:
  print "I do not understand."

---

### Post by smartbei on 2007-11-19
Please use code tags :).

Ok, I have mine mostly implemented, but not quite read yet. I ended up using simple tuples for the items as they are simpler that way, but that may change. One way to process the effect of each item is to define a method for each possible efect in the item class, and then have each item modify the attributes to make the method do something, or have no effect. So each item would have the methods:
```

def hurt(self, current_health):
    return current_health - self.health_effect

```
And ditto for various other options - heal, add coins, etc. Aftere ach move the program would go through the list calling all the methods on each item, and if there is no effect it just doesn't do anything.

I won't post my program now - I want to perfect it a bit first.

---

### Post by Noodels on 2007-11-20
Okay thanks, it's my first time doing this and since I started I've had loads of new ideas for ways of doing it, some of that stuff I didn't understand so it'll be a while before I get it right.

By the way, even though python supports booleans and I didn't find this out till recently, it will treat any integer that is not zero as true, just thought you might like to know.

---

