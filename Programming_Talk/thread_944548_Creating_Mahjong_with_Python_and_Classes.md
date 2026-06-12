---
title: "Creating Mahjong with Python and Classes"
date: 2008-10-11
forum: Programming Talk
---

### Post by luke77 on 2008-10-11
Hi guys,

I'm trying to create a simple Mahjong (card game) using Python. I am new to python and am having some problems. I'd appreciate any help. Here is my code so far; at this point I am just trying to create a proper, rational structure:

```
class  Tile:
    def __init__(self, name):
        self.name = name
    def __str__(self):
        return None
    def __cmp__(self, other):
        if self.getName == other.getName:
            return True
        else: return False
    
    def getSuit(self):
        self.suit=suit
    def getRank(self):
        self.rank=rank
    def getName(self):
        self.name=None
        
class SuitTile(Tile):
    def __init__(self, rank,suit):
        self.suit=suit
        self.rank=rank
    def getSuit(self,suit):
        return self.suit
    def getRank(self,rank):
        return self.rank
    def getName(self):
        return None
    #def __cmp__(self, other):
     #   self.getSuit other.getSuit
      #  self.getRank other.getRank

      
class HonorsTile(Tile):
    def __init__(self, name):
        self.name = name
    def getSuit(self):
        return None
    def getRank(self):
        return None
    def getName(self):
        return self.name

class Wall():
    
    def __init__(self):
        suits= ('Bamboo','Characters','Dots')
        winds=('North','South','East','West')
        dragons = ('White','Red', 'Brown')
        self.tiles= [SuitTile(rank, suit) for rank in range(1,18) for suit in suits]
        self.tiles+= [HonorsTile(wind) for wind in winds]
        self.tiles+= [HonorsTile(suit) for suit in suits]
        
    def __str__(self):
       return "%2d%s" % (self.tiles[0].rank, self.tiles[0].suit) 

class WholeDeck():
    """Create a deck of 4 Walls"""
    def __init__(self, decks=4):
        self.cards= []
        for i in range(decks):
            d= Wall()
            self.cards += d.cards
```


The Wall class creates a deck of Mahjohng cards as a list of self.tiles. At this point I'd just like to call all of the cards in the deck and print their rank and suit. I've created the __str__ function which prints the rank and suit for the first card (self.tiles[0].rank, self.tiles[0].suit), but this isn't helpful. It seems like I should just be able to replace the [0] with [x], and then take x as an argument to the __str__ function to print the card number specified by x. For instance, 
```

    def __str__(self,x):
       return "%d%s" % (self.tiles[x].rank, self.tiles[x].suit)
```

Then I could iterate through each card using a loop and print the entire list. But when I write the function like this and try to call a card:

```
c=Wall()
print c(1)

```

I get an error "Wall instance has no __call__ method". If I try printing just c(), I get an error saying that __str__ takes 2 arguments (1 given).

Can anyone help me out with this? How do I call a specific card?

Also, I'm not sure that this structure makes the most sense for the card game. I am storing all the cards in one list so I have to call self.tiles[cardnumber].(whatever) in order to access a specific card. It seems like it would be more straightforward if I could call self.tiles.cardnumber.(whatever) instead, but I'm not sure how I would set things up. 

Thanks very much for any advice.

---

### Post by gomputor on 2008-10-11
> **luke77 said:**
> ```
c=Wall()
print c(1)

```

I get an error "Wall instance has no __call__ method". If I try printing just c(), I get an error saying that __str__ takes 2 arguments (1 given).

c is an object, so you can't call it with the print statement. You must do:
**print c**

And I don't understand why you get the __str__ takes 2 arguments (1 given) error with the print c() statement. I get the __call__ method error with both your faulty tries. :confused:

---

### Post by luke77 on 2008-10-11
> **gomputor said:**
> c is an object, so you can't call it with the print statement. You must do:
**print c**

And I don't understand why you get the __str__ takes 2 arguments (1 given) error with the print c() statement. I get the __call__ method error with both your faulty tries. :confused:

That's what I'm asking. When I call:

```
print c
```

with the following Wall function
```
    def __str__(self):
       return "%2d%s" % (self.tiles[0].rank, self.tiles[0].suit)
```


it works correctly, and the output is 1bamboo. However, the only card it will call with this code is the first one in the list (tiles[0]), since it's hard coded in there. What I want to do, is to be able to call card number i. So, if I call card 12, the function would return the result of:

```
"%2d%s" % (self.tiles[12].rank, self.tiles[12].suit) 
```. With a normal function, I would just include i as an argument:

```
    def __str__(self,i):
       return "%2d%s" % (self.tiles[i].rank, self.tiles[i].suit)
```

But when I try this I get my error messages.

---

### Post by gomputor on 2008-10-11
But **__str__** , and also **__repr__** can't take any parameters other than **self**.
So to get your card you must write a normal method, like the one you wrote for __str__
```
def get_card(self, i):
    return "%d %s" % (self.tiles[i].rank, self.tiles[i].suit)
```

---

### Post by luke77 on 2008-10-11
Ah, I didn't realize __str__ doesn't take arguments other than self. Thanks!

---

