---
title: "[Java] Going over code/logic for blackjack"
date: 2013-10-29
forum: Programming Talk
---

### Post by 7nQecEL on 2013-10-29
Hi,

I'm working on an assignment for a blackjack game and I need some help figuring out how to fix an Exception error: "java.lang.ArrayIndexOutOfBoundsException: 52" which has something to do with the shuffle(). I think I implemented it correctly, but maybe there is something I'm not seeing?

Hopefully someone can help me out?
Note 1: For the shuffle() in Deck class, you can replace it with collections if you want. Part of the assignment was to use my own random generator (based on an example in class)

---

### Post by 7nQecEL on 2013-10-29
I think I've fixed one of the error that I was having. But I'm still getting the "java.lang.ArrayIndexOutOfBoundsException: 52" error...

---

### Post by Bachstelze on 2013-10-29
What does RandomGenerator.generateRandomNum() do?

---

### Post by 7nQecEL on 2013-10-30
it's suppose to generate a random number to use when shuffling the deck and getting random cards. Part of the assignment was to call a method from a jar file. I made that from an example shown in class. You think that might be the problem? It's almost the exact same thing as what was shown in class

---

### Post by ofnuts on 2013-10-30
I'm ready to bet that the way you call it your random generator generates numbers in the range 1..52(*) while your array indices are in the range 0..51. 

(*) 52, that, not so surprisingly, appears in the error message...

---

### Post by 7nQecEL on 2013-10-30
Gah that was it. Haha can't believe I missed that

Thank you!

---

### Post by ICanHasNick on 2013-11-01
[SIZE=3][FONT=century gothic]If you can use the Collection Class and it's shuffle() method [note 1], what is the random generator good for?
[/FONT][/SIZE][SIZE=3][FONT=century gothic]
[COLOR=#222222]I'm just asking because the whole task of simulating a (black jack) card deck is already perfectly solved
 in the LinkedList Class which implements the Queue interface. You just take cards from the beginning of
 the queue and put them to it's end after usage. When you arrive at the first card again you can use 
Collection.shuffle(cardDeck)[/COLOR][/FONT][/SIZE]

---

