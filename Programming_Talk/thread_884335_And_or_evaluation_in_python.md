---
title: "And or evaluation in python"
date: 2008-08-08
forum: Programming Talk
---

### Post by Xavieran on 2008-08-08
Hi all,

I am writing an implementation of the card game blackjack and am having some problems with a particularly complex if statement that needs to tell if there is a blackjack in the hand or not.

It looks like this:

[PHP]if (('Q' in self.ShowHand()) or ('K' in self.ShowHand())\
        or ('J' in self.ShowHand()) and 'Ace' in self.ShowHand())\
         and len(self.hand)==2:print 'Blackjack'[/PHP]

Basically I want it to print the word "Blackjack" if there is a blackjack in the hand.

Most of the time it seems to do this alright...
However, if there is a queen and another card in the deck it will also print blackjack (for reasons unknown to me)

Here is the full code to demonstrate what I mean:
[PHP]#Particularly cut down version,simply to demonstrate the
#Problems with the if and etc. statement

class Card():
    '''Base class that represents a playing card.
    self.string should be the string representation of the card,
eg. "Ace of Clubs"'''
    def __init__(self,string):
        if str(type(string)) != "<type 'str'>":raise CardError,'string must be\
 a string'
        self.string=string
    def __repr__(self):
        return self.string
        
class BlackjackCard(Card):
    '''

	The numbers are used to simplify things for the computer

	(no string manipulation etc.).

	Color: 0=black 1=red

	Suit: 0=clubs 1=spades 2=diamonds 3=hearts

	Type: 0=Ace (1 is 2,2 is 3,etc.) 10=Jack 11=Queen 12=King'''
	
    def __init__(self,color,suit,name,worth,string):
        Card.__init__(self,string)
        self.name=name
        self.suit=suit
        self.color=color
        self.worth=worth
        
class Player:
    def __init__(self,hand):
        self.hand=hand
        
    def ShowHand(self):
        '''Return a string of the cards in the deck'''

        return '\n'.join([card.string for card in self.hand])
        
    def ReturnScore(self,string=False):
        '''Returns the current score, fully processed. 
If string is True return a humanised score'''
        score=0
        num_of_aces=0

        for card in self.hand:
            score+=card.worth
            #The following is so that if there is an ace in the deck
            #you cannot go bust, and it will subtract ten to play as normal
            if 'Ace' in card.string:
                num_of_aces += 1
            if score >= 22 and num_of_aces != 0:
                score -= 10
                num_of_aces-=1
            
        if string:
            if score >=22:
                return 'Bust'#This will return if there is a blackjack
            if (('Q' in self.ShowHand()) or ('K' in self.ShowHand())\
            or ('J' in self.ShowHand()) and 'Ace' in self.ShowHand())\
            and len(self.hand)==2: 
                return 'Blackjack'
            if score + 10 > 21 and not num_of_aces:
                return 'Hard %d'%score
            else:
                return 'Soft %d'%score
        #The culprit
        if (('Q' in self.ShowHand()) or ('K' in self.ShowHand())\
        or ('J' in self.ShowHand()) and 'Ace' in self.ShowHand())\
         and len(self.hand)==2:score=21    
        return score
        
cards=[BlackjackCard(0,0,0,10,"Queen of Clubs"),
       BlackjackCard(0,0,12,10,"King of Clubs"), 
       ]
cards2=[BlackjackCard(0,0,7,8,"8 of Clubs"),
        BlackjackCard(0,0,1,2,"2 of Clubs")
        ]
cards3=[BlackjackCard(0,1,0,10,"Ace of Spades"),
        BlackjackCard(0,0,12,10,"King of Clubs")
        ]
       
me=Player(cards)
print 'This should not be a blackjack\n',me.ReturnScore(True),'\n',me.ShowHand()
you=Player(cards2)
print 'This should not be either\n',you.ReturnScore(True),'\n',you.ShowHand()
I=Player(cards3)
print 'This should be a blackjack\n',I.ReturnScore(True),'\n',I.ShowHand()
[/PHP]

---

### Post by Def13b on 2008-08-08
It's quite possible I'm wrong here, fairly new to python and programming in general but I'll take a shot.
```

(('Q' in self.ShowHand()) or ('K' in self.ShowHand())
        or ('J' in self.ShowHand()) and 'Ace' in self.ShowHand())
```

This section is bracketed to include the and with the or's, the way or works it will starting from the left check each condition, if the check for Q is True it stops and returns True therefore skipping your check for the Ace.

Moving the Ace check outside of the or's I think will work though you might want to check, the whole bool thing is still a bit mystic to me sometimes.

Something like this anyway:

```
if (('Q' in self.ShowHand()) or ('K' in self.ShowHand())
        or ('J' in self.ShowHand())) and 'Ace' in self.ShowHand()
         and len(self.hand)==2:print 'Blackjack'  
```

---

### Post by geirha on 2008-08-08
I think sets would make the code a little prettier.
[php]from sets import Set as set
hand=set(self.ShowHand())
royal_cards=set(['J','Q','K'])
if len(hand) == 2 and 'Ace' in hand and royal_cards & hand:
    print "Blackjack"
[/php]

---

### Post by tamoneya on 2008-08-08
i think you are missing some parenthesis.

Put a "(" before "'Ace'"

---

### Post by Bachstelze on 2008-08-08
You need to put all the or statements between a single set of parentheses, because and has precendence over or.

[PHP]
if ('Q' in self.ShowHand() or 'K' in self.ShowHand() or 'J' in self.ShowHand()) \
        and 'Ace' in self.ShowHand() and len(self.hand)==2 :
    print 'Blackjack'[/PHP]

Just a side-note:

strictly speaking, a "blackjack" hand **must** contain an ace and a black jack (thus the name). All other "royals" of course still give 21 points, but the player does not earn any bonus (it's like e.g. winning the game with three cards).

---

### Post by Xavieran on 2008-08-08
Thankyou all your replies.

I was getting a bit confused with the parentheses and tried chucking a few in somewhere.

@HymnToLife:
    when I was making this I checked out the rules for blackjack on    wikipedia and apparently in some versions of Blackjack (a.k.a.:Twenty-one) it is a blackjack if any of the royal cards appear with an ace...that's my interpretation, anyway, the game is still under heavy development, and I am still hacking away at ReturnScore to get it to do what I want...

@geirha:
    I'll check sets out...Python has a heap of really cool modules...

EDIT: I've done away with the original if 'string' in ShowHand() stuff, it's a lot simpler to take advantage of each cards attributes like so:
[PHP]c=[card.name for card in self.hand]
            if (10 in c or 11 in c or 12 in c) and 0 in c and len(self.hand) ==2:
                if [card.color for card in self.hand if card.name==10] == [0]:return 'Blackjack'
                else:return 'Royal 21'[/PHP]

---

