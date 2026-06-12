---
title: "Python Issue"
date: 2010-06-12
forum: Programming Talk
---

### Post by lewisforlife on 2010-06-12
I am brand new to python.  I am trying to write a blackjack simulation.  So far I created a list, and shuffled it.  Now I am trying to deal the cards but am getting an invalid syntax error on line 55 that I can't figure out.  Here is my code:

```

#! /usr/bin/python

import random

### editable variables ###
num_decks = 1
num_players = 3
###

# standard deck of cards
cards = [    '2h', '2d', '2s', '2c',
            '3h', '3d', '3s', '3c',
            '4h', '4d', '4s', '4c',
            '5h', '5d', '5s', '5c',
            '6h', '6d', '6s', '6c',
            '7h', '7d', '7s', '7c',
            '8h', '8d', '8s', '8c',
            '9h', '9d', '9s', '9c',
            'th', 'td', 'ts', 'tc',
            'jh', 'jd', 'js', 'jc',
            'qh', 'qd', 'qs', 'qc',
            'kh', 'kd', 'ks', 'kc',
            'ah', 'ad', 'as', 'ac',
            ]
        

# add appropriate number of decks of cards to shoe
for i in range (1, num_decks, 1):
    for j in range (0, 52, 1):
        cards.append (cards [j])

# shuffle shoe
random.shuffle (cards)

# player and dealer structure, indexes: 0 - players, 1 - 1st cards, 2 - 2nd card
dealer = [['dealer'], [], []]
players = [[], [], []]

# sit players at table
for i in range (0, num_players, 1):
    players [0].append (i + 1)

#deal cards
for i in range (0, 4, 1):
    for j in range (0, num_players, 1):
        if (i < 2):
            cardnum = 1
        else:
            cardnum = 2
            
        players [cardnum].append (cards [len (cards)])
        cards.pop ()
        
    dealer [cardnum].append (cards [len (cards)]
    cards.pop ()


print dealer
print players


# list out cards in shoe
#for i in range (0, len (cards), 1):
#    print cards [i]


```

Any help would be much appreciated.

---

### Post by xsinsx on 2010-06-12
The pop function needs a value. You are currently telling the pop function to activate and its waiting for an argument. The function has no idea what it is "popping", so you need to insert a value for the pop function. Python documentation to the rescue. [http://docs.python.org/tutorial/datastructures.html](http://docs.python.org/tutorial/datastructures.html)

---

### Post by lewisforlife on 2010-06-12
Am I missing something, the documentation you provided says that no argument is required for the pop function, and if no argument is given, then it will pop the last value of the list:

> 
list.pop([*i*])Remove the item at the given position in the list, and return it.  If no index is specified, a.pop() removes and returns the last item in the list.  (The square brackets around the *i* in the method signature denote that the parameter is optional, not that you should type square brackets at that position.  You will see this notation frequently in the Python Library Reference.)

---

### Post by lewisforlife on 2010-06-12
I gave pop an index number just to try it out, and I am still getting the same error.  Here is the new section of code:

```
#deal cards
for i in range (0, 4, 1):
    for j in range (0, num_players, 1):
        if (i < 2):
            cardnum = 1
        else:
            cardnum = 2
            
        players [cardnum].append (cards [len (cards)])
        cards.pop (len (cards) - 1)
        
    dealer [cardnum].append (cards [len (cards)]
    cards.pop (len (cards) - 1)
```

---

### Post by lewisforlife on 2010-06-12
I figured out the error, it was the line before the pop statment:

```

players [cardnum].append (cards [len (cards)])
```

should have been:
```
players [cardnum].append (cards [len (cards) - 1])
```

because this was out of the range of the list.

---

### Post by 23dornot23d on 2010-06-12
You have a hidden control character somewhere in the original program file I think ....

I went through it and cut and pasted each section without the control character to another program listing (below)


Try cutting and pasting this ........here is a clean copy ...... 

  ...... I too kept getting a error on line 55 ( an invalid syntax error on line 55 )

even after deleting all the text on it ...... it gave the same error ...... 
(a hidden control character my best guess in the original file)

Heres a link to it formatted .....

[_CardFile_]("http://sites.google.com/site/23dornot23d/home/allsorts/cards2.py?attredirects=0&d=1")

---

### Post by wmcbrine on 2010-06-12
> **xsinsx said:**
> The pop function needs a value.Please don't post nonsense.

The actual first error triggered in the code as posted -- the syntax error on line 55 -- is a missing closing parentheses on the line before it:

```
dealer [cardnum].append (cards [len (cards)]
```

(Only once you fix this will you see the "list index out of range" error.)

---

### Post by lavinog on 2010-06-12
Actually, I think what you want is:
```
#deal cards
for i in range (0, 4, 1):
    for j in range (0, num_players, 1):
        if (i < 2):
            cardnum = 1
        else:
            cardnum = 2
            
        players [cardnum].append ( cards.pop() )
        
    dealer [cardnum].append ( cards.pop() )


```

also, for something like this:
```

cards [len (cards) - 1]

```

the python way is this:
```

cards[-1] # result is last item in list

```

---

### Post by xsinsx on 2010-06-12
I apologize I didnt take a real good look at it I apologize. I always had given my pop function a value. I had misunderstood that you didnt have to apply a value to it. I didnt mean for my post to be nonsensical.

---

