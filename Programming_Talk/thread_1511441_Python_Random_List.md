---
title: "Python Random List"
date: 2010-06-16
forum: Programming Talk
---

### Post by lewisforlife on 2010-06-16
I am creating a poker simulation in Python.  I am using a 6 decks all shuffled together.  To shuffle them together I am using

```

random.shuffle (cards)

```cards is a list.  Here is what the python website says about random.shuffle:

> 
random.shuffle(*x*[, *random*])[¶]("http://docs.python.org/library/random.html#random.shuffle")Shuffle the sequence *x* in place. The optional argument *random* is a 0-argument function returning a random float in [0.0, 1.0); by default, this is the function [random()]("http://docs.python.org/library/random.html#random.random").
 **Note that for even rather small len(x), the total number of permutations of *x* is larger than the period of most random number generators; this implies that most permutations of a long sequence can never be generated.**
 
I bolded the part I am curious about.  Is 312 list items considered a long sequence, because this is the number of cards in the deck that I am using.  The reason that I am asking is because the cards to not seem to be shuffled up sufficiently , and over many thousands of iterations of the program, the winning percentage of the players are way to high.  Does anyone have any insite.  I will post code if needed, but I figured this was a more general question.

Sorry for being long winded.

---

### Post by StephenF on 2010-06-16
From help(random):

>     General notes on the underlying Mersenne Twister core generator:
    
    * The period is 2**19937-1.
    * It is one of the most extensively tested generators in existence.
    * Without a direct way to compute N steps forward, the semantics of
      jumpahead(n) are weakened to simply jump to another distant state and rely
      on the large period to avoid overlapping sequences.
    * The random() method is implemented in C, executes in a single Python step,
      and is, therefore, threadsafe.


2**19937 > 52! by a large margin.

---

### Post by schauerlich on 2010-06-16
> **StephenF said:**
> 2**19937 > 52! by a large margin.

He's using 6 decks, so the whole pool is 312 cards. But, 2^19937 is still larger than 312!.

---

### Post by lewisforlife on 2010-06-17
> **schauerlich said:**
> He's using 6 decks, so the whole pool is 312 cards. But, 2^19937 is still larger than 312!.

Yeah, 312 is slightly smaller than 2^19937 isn't it?  I think I have some other bug in my program.  For example, after simulating 25 hands the win percentage in the simulation is about 8%, after playing 5000 hands, the win percentage goes up to 80%.  If I can't figure it out today I will post my code.

---

### Post by simeon87 on 2010-06-17
> **lewisforlife said:**
> Yeah, 312 is slightly smaller than 2^19937 isn't it?

The exclamation mark indicates factorial. So 312! = 312 times 311 times 310 times ... times 1. This is related to permutations because a finite set of n items has n! permutations.

---

### Post by lewisforlife on 2010-06-17
> **simeon87 said:**
> The exclamation mark indicates factorial. So 312! = 312 times 311 times 310 times ... times 1. This is related to permutations because a finite set of n items has n! permutations.

Hmmm.  So it seems that even 52 cards would be way to large to create a true random list, and I am using 312.  52! and 312! are very large numbers!  How should I shuffle my 312 card deck, does anyone have any suggestions?

(or am I just really confused?)

---

### Post by simeon87 on 2010-06-17
> **lewisforlife said:**
> Hmmm.  So it seems that even 52 cards would be way to large to create a true random list, and I am using 312.  52! and 312! are very large numbers!  How should I shuffle my 312 card deck, does anyone have any suggestions?

From what I gather, it only goes wrong when *n*! > 2**19937-1, in the sense that some permutations won't appear. However, as 2**19937-1 is a very large number, the user won't notice. According to Wolfram Alpha, this will occur when *n* is around 2100. Since 312 << 2100, you're safe and you can use random.shuffle.

---

### Post by lewisforlife on 2010-06-17
Ok, it seems I have a bug in the program.  Basically what my program is doing is shuffling 6 decks of cards, dealing out blackjack hands, and playing a poker side bet.  So it is a 3 card poker hand, only 3 of a kind, straight, or flush.  It uses both of the players cards, and the dealers first card for the poker hand.  I believe the probability should of winning should be around 8%.

You can update the number of iterations of the program and the probability of winning gets really high for whatever reason.  There is something I have noticed, I put in a line of code to print str (len (cards)) when a new 6 decks are added (because the previous cards ran out), and it gives varying amounts, 324, 328, etc...  This number should always be 312, and I can't figure out why.  Here is my program.  Any help on fixing it would be much appreciated.

```

#! /usr/bin/python

import random

### editable variables ###
num_decks = 6
num_players = 7
iterations = 50
on_screen = False
#threshold = [10, 11, 12, 13, 14, 15, 16]
###    

# basic 52 card deck
cards = [    [2, 'h'], [2, 'd'], [2, 's'], [2, 'c'],
            [3, 'h'], [3, 'd'], [3, 's'], [3, 'c'],
            [4, 'h'], [4, 'd'], [4, 's'], [4, 'c'],
            [5, 'h'], [5, 'd'], [5, 's'], [5, 'c'],
            [6, 'h'], [6, 'd'], [6, 's'], [6, 'c'],
            [7, 'h'], [7, 'd'], [7, 's'], [7, 'c'],
            [8, 'h'], [8, 'd'], [8, 's'], [8, 'c'],
            [9, 'h'], [9, 'd'], [9, 's'], [9, 'c'],
            [10, 'h'], [10, 'd'], [10, 's'], [10, 'c'],
            ['j', 'h'], ['j', 'd'], ['j', 's'], ['j', 'c'],
            ['q', 'h'], ['q', 'd'], ['q', 's'], ['q', 'c'],
            ['k', 'h'], ['k', 'd'], ['k', 's'], ['k', 'c'],
            ['a', 'h'], ['a', 'd'], ['a', 's'], ['a', 'c']
            ]



# Poker card values
card_dictionary = { 2:2, 3:3, 4:4, 5:5, 6:6, 7:7, 8:8, 9:9, 10:10, 'j':11, 'q':12, 'k':13, 'a':14 }
card_dictionary_alternate = { 'a':1, 2:2, 3:3, 4:4, 5:5, 6:6, 7:7, 8:8, 9:9, 10:10, 'j':11, 'q':12, 'k':13 }

#backup orig deck
orig_cards = cards

# add appropriate number of decks of cards to shoe
for i in range (1, num_decks, 1):
    for j in range (0, 52, 1):
        cards.append (cards [j])



# shuffle shoe
random.shuffle (cards)


shuffle = random.shuffle

#def shuffle(x):
#    for i in xrange(len(x)-1, 0, -1):
#        j = int(random.random() * (i+1))
#        x[i], x[j] = x[j], x[i]

#shuffle (cards)

print str (len (cards))


# win/loss lists
player_wins = [[0], [0], [0], [0], [0], [0], [0]]


for a in range (0, iterations, 1):
    
    # check nuber of cards in shoe and refill
    if len (cards) <= 78:
        cards = orig_cards
        
        
        
        for i in range (1, num_decks, 1):
            for j in range (0, 52, 1):
                cards.append (cards [j])
        
        print "*****************" + str (len (orig_cards))
                
                
                
    random.shuffle (cards)
    #shuffle (cards)

    # player and dealer structure
    dealer = [['dealer'], []]
    players = [[], [], [], [], [], [], [], []]
    poker_hand = [[0], [0], [0], [0], [0], [0], [0]]

    # sit players at table
    for i in range (0, num_players, 1):
        players [0].append (i + 1)

    # deal initial cards
    for i in range (0, 2, 1):
        for j in range (0, num_players, 1):
            players [j + 1].append (cards [-1])
            cards.pop ()
        dealer [1].append (cards [-1])
        cards.pop ()


    # check for flush
    for i in range (0, num_players, 1):
        counter = 0
        suit = players [i + 1][0][1]
        if players [i + 1][1][1] == suit:
            counter += 1
            if dealer [1][0][1] == suit:
                counter += 1
        if counter == 2:
            if on_screen:
                print "Player " + str (i + 1) + ": flush!"
            poker_hand [i].insert (1, 1)
            poker_hand [i].pop (0)
            
            

    # check for 3 of a kind
    for i in range (0, num_players, 1):
        if poker_hand [i][0] != 1:
            counter = 0
            value = players [i + 1][0][0]
            if players [i + 1][1][0] == value:
                counter += 1
                if dealer [1][0][0] == value:
                    counter +=1
                if counter == 2:
                    if on_screen:
                        print "Player " + str (i + 1) + ": 3 of a kind!"
                    poker_hand [i].insert (1, 1)
                    poker_hand [i].pop (0)
                    


    # temp holder to order cards
    holder = [0, 0, 0]
    holder_alternate = [0, 0, 0]

    # check for straight
    for i in range (0, num_players, 1):
        if poker_hand [i][0] != 1:
            for j in range (0, 3, 1):
                holder.pop ()
                
            holder.append (card_dictionary [players [i + 1][0][0]])
            holder.append (card_dictionary [players [i + 1][1][0]])
            holder.append (card_dictionary [dealer [1][0][0]])
            holder.sort ()
            
            #if holder [2] - holder [0] == 2:
            #    print "Player " + str (i + 1) + ": straight!"
            #    poker_hand [i].insert (0, 1)
            if (holder [1] + 1 == holder [2]) and (holder [1] - 1 == holder [0]):
                if on_screen:
                    print "Player " + str (i + 1) + ": straight!"
                poker_hand [i].insert (0, 1)
            
            else:
                for j in range (0, 3, 1):
                    holder_alternate.pop ()

                holder_alternate.append (card_dictionary_alternate [players [i + 1][0][0]])
                holder_alternate.append (card_dictionary_alternate [players [i + 1][1][0]])
                holder_alternate.append (card_dictionary_alternate [dealer [1][0][0]])
                holder_alternate.sort ()
                
                #if holder_alternate [2] - holder_alternate [0] == 2:
                if (holder_alternate [1] + 1 == holder_alternate [2]) and (holder_alternate [1] - 1 == holder_alternate [0]):
                    if on_screen:
                        print "Player " + str (i + 1) + ": straight!"
                    poker_hand [i].insert (1, 1)
                    poker_hand [i].pop (0)
                    
        
                    
    # tally up wins
    for i in range (0, num_players, 1):
        if poker_hand [i][0] == 1:
            player_wins [i].insert (0, player_wins [i][0] + 1)
            player_wins [i].pop (1)

    if on_screen:
        print dealer
        print players
        print player_wins
        #print poker_hand
        print str (a + 1) + "---------------------------" + str (a + 1)
        
print "Player Wins"
print "-----------"
for i in range (0, num_players, 1):
    percentage = float (player_wins [i][0]) / float (iterations) * 100
    print "Player " + str (i + 1) + ": " + str (player_wins [i][0]) + "/" + str (iterations) + " = " + str (percentage) + "%"



```

---

### Post by xblong on 2010-06-17
# check nuber of cards in shoe and refill
    if len (cards) <= 78:                                  # actual length? 
        cards = orig_cards
                
        for i in range (1, num_decks, 1):               # always adding 260
            for j in range (0, 52, 1):
                cards.append (cards [j])
        
        print "*****************" + str (len (orig_cards))

The bug is that you are always adding 5 complete decks regardless of what the actual length is at that moment. The length is less than 78, but it could be 64 or 72 or 76, etc.

---

### Post by StephenF on 2010-06-17
```
#backup orig deck
orig_cards = cards

```
This does no such thing, instead it creates an additional reference to the same object and modifications to one will appear in the other.

If you need a copy, a shallow copy that uses the same internal elements may be enough.
```

orig_cards = cards[:]

```
This example used the slice syntax to get a slice the same size as the original object.

Python also has a module called copy for, guess what?

This is all moot anyway because to make your shoe you only need to
```

shoe = cards * num_decks

```
And that takes care of needing to back up cards into the bargain providing you use shoe instead of cards within the rest of your program.

---

