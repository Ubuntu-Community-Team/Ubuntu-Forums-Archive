---
title: "Sort c++"
date: 2007-10-15
forum: Programming Talk
---

### Post by Takuhari on 2007-10-15
I have been working on my blackjach/war game... i was wondering if anyone knew of a simple sort that will sort out the current values into position (1,2,3,4) and choose the highest value...(1st place)

I was able to do it with if statements but it turned out to be a few pages>_<... it would be better to use a sort function^^

---

### Post by dwhitney67 on 2007-10-15
What does your data look like?  If it is simple numbers, use an STL set.  If it is complex data use an STL map where do can use a "key" to control the sorting.

---

### Post by Takuhari on 2007-10-15
let see....

here are the basic dec...

void Game::playwar(){  

  	bool cont = true;

  	deck.setDeck();

  	deck.shuffle();

  	for(int i = 0; i < 1; i++){

    		player1.hit(deck);
    		player2.hit(deck);
    		player3.hit(deck);
    		player4.hit(deck);
    		player5.hit(deck);

    		dealer.hit(deck);

  	}

  	p1 = player1.addPoints();
  	p2 = player2.addPoints();
  	p3 = player3.addPoints();
  	p4 = player4.addPoints();
  	p5 = player5.addPoints();

  	p0 = dealer.addPoints();


int players=1;........ and so on...
i will use the sort as sort.cpp and call the function

---

### Post by aks44 on 2007-10-15
Not sure what you're after since you didn't show/explain your **data structures** despite dwhitney67's suggestion, but the STL has the std::sort algorithm (#include <algorithm>).

Hope this helps, please provide more info if you need a more accurate answer. ;)

---

### Post by dwhitney67 on 2007-10-15
From the code you posted, I can't make heads/tails out of what you are asking.

The for-loop is not needed if you are only going to loop one time, which from your code, it appears that is exactly what is happening.

There is nothing to indicate what the purpose of addPoints() is, thus I cannot comment on that, must less the purpose of p1, p2, etc.

Why not try to get the game working with one player and a dealer?  Then after it is working, consider adding additional players.

Also, try to capture the "rules" of the BJ game into a Use Case before even touching the keyboard to write code.  Maybe things will become clearer to you.

Last year I studied how to use RatRose RT, and one of the examples in the tutorial was the development of a simple BJ game.  I don't recall the need to have any sorter.

---

