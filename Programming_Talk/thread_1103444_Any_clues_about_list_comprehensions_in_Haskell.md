---
title: "Any clues about list comprehensions in Haskell?"
date: 2009-03-22
forum: Programming Talk
---

### Post by EvenStevens on 2009-03-22
I've got an enumerated type "suit" and an enumerated type "rank", then a data type Card which has the fields of suit and rank...

```
data Card = Card Suit Rank
```

and now I need to list out all the cards in order, so ace of clubs, two of clubs etc. king of spades, with the function...

```
deck :: [Card]
```

And I have no clue... I've tried everything

I tried something like
```
deck::[Card]
deck = [Card(x,y) | x <- [Ace .. King], y <- [Club .. Spade]]
```

but alas, parse error :-(

Halp?

---

### Post by Reiger on 2009-03-22
A number of ideas/things:
1
```

data Card = Card Suit Rank
```

Suit & Rank are distinct arguments to the constuctor `Card'. This doesn't seem to match up to the tuple notation you use elsewhere.
Perhaps you meant?
```

data Card = Card (Suit, Rank)
```

2
[s]```

x <- [Ace .. King], y <- [Club .. Spade]

```

Both Suit and Rank are part of the Enum class, I take it...?[/s] Yes they are, you wrote that in post #1: I should read... 

3
```

Card(x,y) | x <- [Ace .. King], y <- [Club .. Spade]
```

Forgive me if I am wrong, but I thought that Club..Spade represented the Suit and Ace..King the Rank? So in that case, your Card(x,y) is incompatible with the type as defined in the data declaration of Card? 

Perhaps you meant:
```

Card(y,x) | x <- [Ace .. King], y <- [Club .. Spade]

```

Or perhaps you meant:
```

(Card y x) | x <- [Ace .. King], y <- [Club .. Spade]

```
In case (point 1) does not apply and the tuple notation was not intended after all.

---

### Post by EvenStevens on 2009-03-22
Ah I realise where I went wrong there, cheers :)

---

