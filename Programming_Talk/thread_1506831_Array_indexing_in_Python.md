---
title: "Array indexing in Python?"
date: 2010-06-10
forum: Programming Talk
---

### Post by McRat on 2010-06-10
<--Newbie

There must be something simple I'm not seeing.  
If you have:

x = [10,20,30]

then 

x[2] == 30 is TRUE.

But then why doesn't this work?

```
########################
##### Card Generator ###
########################

import random

card = int(0)

deck = [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20, \
        21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,\
        39,40,41,42,43,44,45,46,47,48,49,50,51,52]

deck = random.shuffle(deck)

num = int(input("How many cards do you want? "))

while num > 0:

    # Grab a new card off the deck
    [COLOR="red"]**card = deck[num]**[/COLOR]

```

The error is:

> Python 3.1.2 (r312:79360M, Mar 24 2010, 01:33:18) 
[GCC 4.0.1 (Apple Inc. build 5493)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> ================================ RESTART ================================
>>> 
How many cards do you want? 4
[COLOR="Red"]Traceback (most recent call last):
  File "/Users/patrickmcswain/Documents/cards2.py", line 20, in <module>
    card = deck[num]
TypeError: 'NoneType' object is not subscriptable[/COLOR]
>>> 

---

### Post by McRat on 2010-06-10
Huh.  The example for [COLOR="Red"]random.shuffle(x)[/COLOR] doesn't operate like it appears.

So, WRONG TITLE!  :D

---

### Post by McRat on 2010-06-10
OK, the .shuffle(x) method actually alters the array in the argument.

To "shuffle" a deck:

[COLOR="SeaGreen"]null = random.shuffle(deck)[/COLOR]

will permanently alter the array.

---

### Post by wmcbrine on 2010-06-10
There's no need for that "null =". Just "random.shuffle(deck)".

Also, you don't need to type out all the numbers like that... just use "list(range(1, 53))" (although personally, I'd number the cards 0-51).

Oh, also, even if you did have to type out a long list like that, you don't need the continuation characters ('\') -- just having the list in brackets ('[', ']') is enough. Parentheses ('(', ')') and curly brackets ('{', '}') also work that way.

---

### Post by McRat on 2010-06-10
> **wmcbrine said:**
> There's no need for that "null =". Just "random.shuffle(deck)".

Also, you don't need to type out all the numbers like that... just use "list(range(1, 53))" (although personally, I'd number the cards 0-51).

Oh, also, even if you did have to type out a long list like that, you don't need the continuation characters ('\') -- just having the list in brackets ('[', ']') is enough. Parentheses ('(', ')') and curly brackets ('{', '}') also work that way.

Thanks!

---

### Post by schauerlich on 2010-06-10
Also, there's a distinction between input() and raw_input(). input() will read in a python expression, evaluate it, and then return the result. raw_input() will read in and return a literal string.

```
>>> x = input("Type something: ")
Type something: 4 ** 5 + 7
>>> x
1031
>>> y = raw_input("Type something: ")
Type something: 4 ** 5 + 7
>>> y
'4 ** 5 + 7'
>>> eval(y)
1031
>>>
```

It's good practice to use raw_input() and then deal with the input yourself later. You can't always rely on the user to give you what you want, or even anything that makes sense. :)

---

### Post by wmcbrine on 2010-06-10
> **schauerlich said:**
> Also, there's a distinction between input() and raw_input().Not in Python 3, which McRat is using -- the old input() is gone, and raw_input() has become input().

Edit: I just noticed this line -- "card = int(0)". This is also unnecessary; "card = 0" would be sufficient, although in this case (without seeing what comes after the while loop), the entire line is probably unneeded.

---

### Post by schauerlich on 2010-06-10
> **wmcbrine said:**
> Not in Python 3, which McRat is using -- the old input() is gone, and raw_input() has become input().

Right, well, ignore me, then. :)

---

### Post by McRat on 2010-06-11
> **wmcbrine said:**
> ...
Edit: I just noticed this line -- "card = int(0)". This is also unnecessary; "card = 0" would be sufficient, although in this case (without seeing what comes after the while loop), the entire line is probably unneeded.

That was an attempt to "fix" the problem the wrong way.  You're right, not needed.  I thought it was mismatched data types.

---

### Post by McRat on 2010-06-11
> **schauerlich said:**
> Right, well, ignore me, then. :)

No, tips on 2.5/2.6 are appreciated also!

---

### Post by Can+~ on 2010-06-11
> **McRat said:**
> ```
while num > 0:

    # Grab a new card off the deck
    [COLOR="red"]**card = deck[num]**[/COLOR]

```


Also, I'm guessin you're doing something like a loop and getting each card from the list, right? Well, you could've done (with the deck already shuffled):

[PHP]cards = deck[:num][/PHP]

This is called the slice operator, it cuts the range, as "[start:end:step]", in this case, starting from the base, and cutting to the amount of cards wanted.

Also, if you want to be more.. pythonic, you'd use the already provided method in the random module:

[PHP]cards = random.sample(deck, num)[/PHP]

Which returns a random selection of cards from the deck (thus, you don't need to shuffle everyting).

Edit: Also:

```
card = int(0)
```

You're not on C/Java here, variables are dynamically typed.

---

### Post by McRat on 2010-06-11
Thanks everyone!

Well, the kids gave up for today, so I put in the suggestions and got:

```
[COLOR="green"]########################
##### Card Generator ###
########################[/COLOR]

import random   

cardname = ["Ace","Two","Three","Four","Five","Six","Seven","Eight",
         "Nine","Ten","Jack","Queen","King"]

suit = ["Hearts","Diamonds","Spades","Clubs"]

[COLOR="Green"]## Create a random deck of cards[/COLOR]
deck = list(range(0,52))
random.shuffle(deck)

[COLOR="green"]## Hand out the right number of cards[/COLOR]
for card in range(int(input("How many cards do you want? "))):
    
    print ("Card",card+1,"is a", cardname[deck[card]%13],"of",suit[deck[card]%4]
```

---

