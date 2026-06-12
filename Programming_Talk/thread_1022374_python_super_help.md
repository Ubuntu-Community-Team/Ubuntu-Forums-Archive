---
title: "python super help"
date: 2008-12-26
forum: Programming Talk
---

### Post by king vash on 2008-12-26
I am writing a poker simulator in python. I have an object called "table" which contains all the relevant information about the table (number of players, buy in, small blind, big blind, each player's money, each player's cards...). Because I allow up to 8 players at a table I think I want a super class.

right now I would do this
```
table.player1cards
table.player1money
table.player2cards
table.player2money
```

I want to be able to do this
```
table.player1.cards
table.player1.money
table.player2.cards
table.player2.money
```

and I would like it to work with a varied number of players. 
I would also like to be able to generate "player1" on the fly ie
```
for playerNumber in range(1,numberOfPlayers):
    table."Player%s"%(playerNumber).cards = randomcard() 
```

---

### Post by jbrackett on 2008-12-26
I may be missing something, but you probably want your table to contain a list of player objects which themselves contain a list of card objects.

So to get the player you want you would just do something like

```

for player in table.getPlayers():
   #do whatever you need


```

Edit:
an example of something to do that last code snippet you have
```

for player in table.getPlayers():
  player.addCard(Deck.getNextCard())

```
not perfect but maybe enough to get the idea

---

### Post by pp. on 2008-12-26
Actually, what you need is not Python help but OO Design help. 

Suggestion: try and describe the whole evening of a poker session. You will find terms such as players, decks, cards, hands, rounds, and so on. For starters, presume that there will be an class for every noun in your description. Some classes might "degenerate" into simple collections, others might begome trivial attributes of other objects, and still other classes might surface while you're refining your concept or "architecture".

---

### Post by iQuizzle on 2008-12-26
it sounds like all you need to do is have a 'table' class and a 'player' class. then just make instances of players in the table

```

class player(object):
  cards = None
  money = None

class Table(object):

  def newPlayer(self,name):
    self.__setattr__(name,player())

  def rmPlayer(self,name):
    self.__delattr__(name,player())


```

that should do what you want.

ex:
table = Table()
table.newPlayer('player1')
table.player1.money = 1000

---

### Post by meanburrito920 on 2008-12-26
> **iQuizzle said:**
> it sounds like all you need to do is have a 'table' class and a 'player' class. then just make instances of players in the table

```

class player(object):
  cards = None
  money = None

class table(object):
  def __init__(self):
    player1 = player()
    player2 = player()
    

```

that should do what you want

Exactly. But I would suggest using lists to contain players so you can dynamically change how many players there are, etc. 

```

class player(object):
  cards = []
  money = 0

  ...

class table(object):
  def __init__(self):
    self.players = []
    
   ...

```

---

### Post by nvteighen on 2008-12-27
I'm also developing a card game simulator (though not in Python and neither is it Poker) and also advise (as pp.) you to carefully observe what elements interact with eachother in a session.

Card games are a great way to learn OOP, as it fits it perfectly: objects are clearly distinguishable and their actions are quite simple.

Good luck!

---

