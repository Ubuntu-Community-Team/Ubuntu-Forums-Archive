---
title: "Problem with remove() in Python"
date: 2010-11-21
forum: Programming Talk
---

### Post by Bigmon on 2010-11-21
Sorry if this seems a bit trivial, but it is driving me mad. I cannot remove an element from a list. I can print the element, but cannot remove it. I get an error. Any help much appreciated.

cards = [("AH",1),("2H",2),("3H",3),("4H",4),("5H",5),("6H",6),("7H",7),("8H",8)
         ,("9H",9),("10H",10),("JH",10),("QH",10),("KH",10),
         ("AS",1),("2S",2),("3S",3),("4S",4),("5S",5),("6S",6),("7S",7),("8S",8)
         ,("9S",9),("10S",10),("JS",10),("QS",10),("KS",10),
         ("AD",1),("2D",2),("3D",3),("4D",4),("5D",5),("6D",6),("7D",7),("8D",8)
         ,("9D",9),("10D",10),("JD",10),("QD",10),("KD",10),
         ("AC",1),("2C",2),("3C",3),("4C",4),("5C",5),("6C",6),("7C",7),("8C",8)
         ,("9C",9),("10C",10),("JC",10),("QC",10),("KC",10)]



first_card = cards[:1]
cards.remove(first_card)
print (cards)

---

### Post by Arndt on 2010-11-21
> **Bigmon said:**
> Sorry if this seems a bit trivial, but it is driving me mad. I cannot remove an element from a list. I can print the element, but cannot remove it. I get an error. Any help much appreciated.

cards = [("AH",1),("2H",2),("3H",3),("4H",4),("5H",5),("6H",6),("7H",7),("8H",8)
         ,("9H",9),("10H",10),("JH",10),("QH",10),("KH",10),
         ("AS",1),("2S",2),("3S",3),("4S",4),("5S",5),("6S",6),("7S",7),("8S",8)
         ,("9S",9),("10S",10),("JS",10),("QS",10),("KS",10),
         ("AD",1),("2D",2),("3D",3),("4D",4),("5D",5),("6D",6),("7D",7),("8D",8)
         ,("9D",9),("10D",10),("JD",10),("QD",10),("KD",10),
         ("AC",1),("2C",2),("3C",3),("4C",4),("5C",5),("6C",6),("7C",7),("8C",8)
         ,("9C",9),("10C",10),("JC",10),("QC",10),("KC",10)]



first_card = cards[:1]
cards.remove(first_card)
print (cards)

You don't say what error you get, and where.

But it's probably 'remove', because you are not giving it an element in the list; you are giving it a list of one element. Look at what first_card contains.

Since you know that it's the first element you want to remove (as long as the card doesn't occur several times - I don't know if it does), you can use the array slice operation here too: cards = cards[1:]

---

### Post by Bigmon on 2010-11-21
The error I get is "ValueError: list.remove(x): x not in list"

This confuses me becauses I can "append" the value to another list but not remove it from the "cards" list.

Thanks for your input.

---

### Post by StephenF on 2010-11-21
cards.pop(0) will remove and return the first element in the list. Maybe this is what you need?
Or to just get rid of the first element del cards[0]

---

### Post by Bigmon on 2010-11-21
Many thanks."Cards.pop(0)" provides the solution.

---

