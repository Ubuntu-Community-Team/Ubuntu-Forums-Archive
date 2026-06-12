---
title: "Python Problem"
date: 2007-05-27
forum: Programming Talk
---

### Post by Loft on 2007-05-27
I'm pretty much new to Python (although have fairly limited experience with Java) and I'm just messing around for now, learning the language.  I'm writing a tournament system to get to grips with Pythons class and object system and am stuck. 

I have two classes, a Player class and a Tournament class.  The Player class defines two attributes, the player's name and whether or not the player is still in the tournament (using a string of either 'yes' or 'no' at the moment).

The Tournament class asks for the number of players, a player name and whether the player is in or not, then creates a Player object using these.  These are then put in the list.

Populating the list is fine, I get to put how many players I want, their name and whether they are still in the tournament, but I then want to print the names and their staus out to screen and get an error.

Below is the source code.

```
class Player:
    def __init__(self, name, playerIn = 'yes'):
        self.name = name
        self.playerIn = playerIn
    def playerName(self):
        print self.name, self.playerIn

class Tournament:

    def playerCreation(self):

        playerList = []
        for i in range (int(raw_input("Enter the number of players: "))):
            playerName = raw_input("Enter name of player: ")
            stillIn = raw_input("Is the player still in? Yes or No: ")
            obj = Player(playerName, stillIn)
            playerList.append(obj)
        return playerList

p = Tournament()
players = p.playerCreation()
for item in players:
    print playerName, stillIn
```

And below is the output.

```
Enter the number of players: 2
Enter name of player: john
Is the player still in? Yes or No: yes
Enter name of player: luke
Is the player still in? Yes or No: no
Traceback (most recent call last):
  File "tourn", line 23, in <module>
    print playerName, stillIn
NameError: name 'playerName' is not defined

```

I'm not sure where I'm going wrong, can anyone help please?  Thanks in advance.

---

### Post by Game_Ender on 2007-05-27
```

p = Tournament()
players = p.playerCreation()
for item in players:
    # --> Where do 'playerName' and 'stillIn' come from?
    print playerName, stillIn

```

What do you type do you think 'item' is?

---

### Post by ankursethi on 2007-05-27
This will work :
```

class Player:
    def __init__(self, name, playerIn = 'yes'):
        self.name = name
        self.playerIn = playerIn
    def playerName(self):
        print self.name, self.playerIn

class Tournament:

    def playerCreation(self):

        playerList = []
        for i in range (int(raw_input("Enter the number of players: "))):
            playerName = raw_input("Enter name of player: ")
            stillIn = raw_input("Is the player still in? Yes or No: ")
            obj = Player(playerName, stillIn)
            playerList.append(obj)
        return playerList

p = Tournament()
players = p.playerCreation()
for item in players:
    print item.name, item.playerIn

```

Just notice the changes I made.

---

