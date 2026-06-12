---
title: "deck of cards in c++"
date: 2011-03-05
forum: Programming Talk
---

### Post by chris200x9 on 2011-03-05
```

void deck::populate()
{
	char suits[4] = {'d','c','s','h'};
	int counter = 0;
	int counter2 = 0;
	
	while (counter2 < 4)
	{
	
	while (counter < 13)
	{
		card x(suits[counter2], counter);
		cards.push_back( x );
		counter++;
	}
	counter2++;
	}
	
}
```

Attached is the relevant portion of my code, it works fine with the first suit but doesn't move on everything after 0-12 of 'd' is just 0. I'd appreciate very much any help, I just don't see what's wrong.

---

### Post by lisati on 2011-03-05
Hint: when you've finished with the 13 cards in one suit, you need to reset your counter to start at the beginning for the next suit.

---

### Post by chris200x9 on 2011-03-05
> **lisati said:**
> Hint: when you've finished with the 13 cards in one suit, you need to reset your counter to start at the beginning for the next suit.

mother effer! I knew it was something REALLY stupid! I have a bad habit of overlooking the simplest things :P. Thank you so much though!

---

### Post by lisati on 2011-03-05
Sometimes it's the simplest things that catch us out.

---

### Post by cgroza on 2011-03-05
May I ask what kind of container are you using? My bet is a vector, but a stack would work much better.

---

### Post by chris200x9 on 2011-03-06
> **cgroza said:**
> May I ask what kind of container are you using? My bet is a vector, but a stack would work much better.

a vector, why would a stack be better?

---

### Post by cgroza on 2011-03-06
> **chris200x9 said:**
> a vector, why would a stack be better?
Well, a deck of cards is basically a "stack", if you don't need to shuffle the deck during the game and just top pick a card from the top or put it back, it is way easier.

---

### Post by chris200x9 on 2011-03-06
> **cgroza said:**
> Well, a deck of cards is basically a "stack", if you don't need to shuffle the deck during the game and just top pick a card from the top or put it back, it is way easier.

how would it be much easier? All you do is return the last element of the array then pop it off then take theVector.back() and pop that off and repeat. I don't see how a stack would be much, if at all, easier. i.e

```

card deck::pop_off()
{
	card mycard = cards.back();
	cards.pop_back();
	return mycard;
}

```

---

### Post by cgroza on 2011-03-07
A stack is specially built for this, so I think you would get more speed also.

---

### Post by forrestcupp on 2011-03-07
How much speed do you really need to set up a deck of cards and shuffle them?

I don't really see the point in using a stack *or* a vector for this. I always just use a simple array because you know you're going to have 52 cards and there's really not much benefit in having the overhead.

---

### Post by cgroza on 2011-03-07
> **forrestcupp said:**
> How much speed do you really need to set up a deck of cards and shuffle them?

I don't really see the point in using a stack *or* a vector for this. I always just use a simple array because you know you're going to have 52 cards and there's really not much benefit in having the overhead.

I would consider that too low level, you would have to manage adding a card back to deck and taking it from deck, when with a stack a simple pop and push will do it.

---

### Post by TheBuzzSaw on 2011-03-07
[http://www.cplusplus.com/reference/stl/stack/](http://www.cplusplus.com/reference/stl/stack/)

The STL stack does not even have a custom implementation. It just narrows the interface on an existing container. There is nothing to be gained by using a stack specifically.

---

### Post by cgroza on 2011-03-07
> **TheBuzzSaw said:**
> [http://www.cplusplus.com/reference/stl/stack/](http://www.cplusplus.com/reference/stl/stack/)

The STL stack does not even have a custom implementation. It just narrows the interface on an existing container. There is nothing to be gained by using a stack specifically.
Just realized it, you can give it a vector as a template argument and it will use that as a item keeper.

---

### Post by forrestcupp on 2011-03-07
> **cgroza said:**
> I would consider that too low level, you would have to manage adding a card back to deck and taking it from deck, when with a stack a simple pop and push will do it.

> **cgroza said:**
> Just realized it, you can give it a vector as a template argument and it will use that as a item keeper.

But you can do that with a plain vector. What's the benefit in using a vector inside a stack? That ends up being more complicated than just doing it yourself with an array.

---

### Post by cgroza on 2011-03-07
> **forrestcupp said:**
> But you can do that with a plain vector. What's the benefit in using a vector inside a stack? That ends up being more complicated than just doing it yourself with an array.
It prevents bugs a little, imagine some messed up iterator that is used to read the end of the vector, but instead it reads from the middle.

---

### Post by forrestcupp on 2011-03-07
Maybe I'll look into that more sometime when I have a need.

Now that I think of it, I think a deque would be the best option. You can add or remove cards from either end. That would make it easier to pull one off the top and put it back on the bottom of the deck if you need to.

---

