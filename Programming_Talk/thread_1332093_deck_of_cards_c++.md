---
title: "deck of cards c++"
date: 2009-11-20
forum: Programming Talk
---

### Post by chris200x9 on 2009-11-20
I made a program to calculate the probability of getting 3 cards with the same suit. I checked and have the deck modeled correctly but am having trouble getting and checking the suit. Right now my program just hangs at 100% cpu usage. I do not know what is wrong, any help would be much appreciated.

```

#include <iostream>
#include <time.h>
#include <stdlib.h>
using namespace std;
struct card
{
	int val;
	int suit;
};
int main(int argc, char** argv)
{
	card deck[52];
	int index = 0;
	int value = 1;
	int suit = 0;
	while (index < 52)
	{
		deck[index].val = value;
		if (value >= 13)
		{
			value = 1;
		}
		deck[index].suit = suit;
		value++;
		index++;
		if ( deck[index].val % 13 == 0)
		{
			suit++;
		}
	}
	int in = 0;
	// pick card
	int counter = 0;


	while (in < 10000)
	{
	int pickedsuit[3];
	
	srand ( time(NULL) );
int random = rand() % 52;

 deck[random].suit = pickedsuit[0];
deck[random].suit = pickedsuit[1];
deck[random].suit = pickedsuit[2];

if(pickedsuit[0] == pickedsuit[1] && pickedsuit[0] == pickedsuit[2])
{
counter++;
}
in++;
}
cout << counter / 10000;
	
	
	return 0;
}

```

thank you.

---

### Post by nvteighen on 2009-11-20
Check what's the condition of your last loop and you'll see it never yields false (in order to stop the while-loop). Follow the code ("execute it in your mind") and you'll spot it very quickly.

---

### Post by Arndt on 2009-11-20
> **nvteighen said:**
> Check what's the condition of your last loop and you'll see it never yields false (in order to stop the while-loop). Follow the code ("execute it in your mind") and you'll spot it very quickly.

Or follow it in a debugger. Either step by step, or let it run for a bit and then stop it and see what it's doing.

---

### Post by chris200x9 on 2009-11-20
wow...I don't know how I over looked that for about an hour...on a related note can anyone see a problem in my logic? I keep just getting 0.

---

### Post by Arndt on 2009-11-20
> **chris200x9 said:**
> wow...I don't know how I over looked that for about an hour...on a related note can anyone see a problem in my logic? I keep just getting 0.

You set deck[random].suit to three different things, and those things are never given a value (pickedsuit[0] etc.).

Besides, it's not a good idea to have srand within a loop. Do srand only once, at the start of your program.

---

### Post by Paul Miller on 2009-11-20
Just a quick question... are you interested in the answer to this question for its own sake, or are you doing this as a programming exercise?  If the former, there's an easy way to calculate the probability exactly.

---

### Post by issih on 2009-11-20
```
	srand ( time(NULL) );
int random = rand() % 52;

 deck[random].suit = pickedsuit[0];
deck[random].suit = pickedsuit[1];
deck[random].suit = pickedsuit[2];

if(pickedsuit[0] == pickedsuit[1] && pickedsuit[0] == pickedsuit[2])
{
counter++;
}

```

Your errors are here...
you intend (I think) to pick three cards at random, and see if they have the same suit.

what you actually do is select one card at random (the rand() function is is only evaluated once, so deck[random] goes to the same card all three times).

You then set the suit of that one randomly selected card to match the "suit" stored in the pickedsuit array, first setting it to the value in pickedsuit[0], then the value in pickedsuit[1] and finally the value in pickedsuit[2].

You then check if the pickedsuit array has the same value in bins 0,1 and 2 - which it won't because it still has whatever random garbage was in memory when you instantiated the variable....N.B you really should initialise variables to a value when you create them, or the program attempts to interpret the pre-existing contents of the memory allocated to the variable as a value.

Consequently you never get anything other than 0, because the pickedsuit array never contains anything sensible, all you do is slowly pollute your deck of cards with spurious suit values.

Oh and the analytical answer should be (13/52)*(13/52)*(13/52) = 1/4*1/4*1/4 = 1/64 = .015625. Note that you are not accounting for the reduction in deck size if you were actually drawing from the pack...you behave as if each card is returned to the pack between each draw. The answer in the other case is 13/52*12/51*11/50 = 0.01294 (4sf)

Hope that helps

---

### Post by chris200x9 on 2009-11-20
> **Paul Miller said:**
> Just a quick question... are you interested in the answer to this question for its own sake, or are you doing this as a programming exercise?  If the former, there's an easy way to calculate the probability exactly.

the latter, though I already turned it in wrong because it was due. I just started this thread because I personaly wanted to know what I did wrong.

thank you all

---

