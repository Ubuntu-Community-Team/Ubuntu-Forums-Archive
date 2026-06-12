---
title: "(probably simple) Problems with C++"
date: 2008-10-03
forum: Programming Talk
---

### Post by Calmatory on 2008-10-03
Well, I wanted to fool around with [SPECIAL](http://en.wikipedia.org/wiki/SPECIAL) RPG system used in Fallout games. Obviously, I ran into problems.

```


#include <stdio.h>
#include <iostream>
#include <math.h>

struct character {
	short ST;
	short PE;
	short EN;
	short CH;
	short IN;
	short AG;
	short LK;

	int HP; // HitPoints
	int AC; // Armor Class
	int DR; // Damage Resistance
	int DT; // Damage Thresold
	int MD; // Melee Damage
};

void generateEntity(character genE);
int rollDice(int lp, int max); 
// Rolls the dice. First argument defines the amount of rolls
//and the second one defines the max. value. 
//Thus 1d6 would be rollDice(1,6) and 4d10 would be rollDice(4,10) etc.

int main() {
	
	srand(time(NULL));	

	character PC;
	character enemy;

	generateEntity(PC); 
	

	printf("\n\n----------\nEntity called Playing Character:\n----------\n   ST %i \n   PE %i \n   EN %i \n   CH %i \n   IN %i \n   AG %i \n   LK  %i \n---------\n\n", PC.ST, PC.PE, PC.CH, PC.EN, PC.IN, PC.AG, PC.LK );
	printf("DEBUG: rollDice(3,10) = %i\n\n", rollDice(3,10));
}

void generateEntity(character genE) {

	short statPoints = 35;
	short tempStat = 0;

        //This loop is used to spend around 35 "points" to SPECIAL stats. 
        //Not the best implementation, and thus causes problems.
	while(statPoints>0) {

		tempStat = rollDice(1,3);
		genE.ST += tempStat;
		statPoints -= tempStat;
		if(statPoints <= 0) break;
		
		tempStat = rollDice(1,3);
		genE.PE += tempStat;
		statPoints -= tempStat;
		if(statPoints <= 0) break;

		tempStat = rollDice(1,3);
		genE.CH += tempStat;
		statPoints -= tempStat;
		if(statPoints <= 0) break;

		tempStat = rollDice(1,3);
		genE.IN += tempStat;
		statPoints -= tempStat;
		if(statPoints <= 0) break;

		tempStat = rollDice(1,3);
		genE.AG += tempStat;
		statPoints -= tempStat;
		if(statPoints <= 0) break;

		tempStat = rollDice(1,3);
		genE.LK += tempStat;
		statPoints -= tempStat;

	}
	
	genE.HP = 15 + (genE.ST*2) + (genE.EN*2);
	genE.AG = 3; // Force the AG to 3. Does nothing. Why?
}


int rollDice(int lp, int max) {

	int value =0;
	for(int i=0; i<lp;i++) {
		value = value + 1 + rand()%max;
		//printf("DEBUG: rollDice lp LOOP\n");
	}
	printf("DEBUG: Returned value: %i with max of %i and lp of %i.\n", value, max, lp);
	return (int)value;
}


```

**What it should do?** Create entity called **PC** and assign 35 points to the SPECIAL stats. Then print the stats.

**What it does?** Assigns the stat points, but the SPECIAL stat values are way off. I.e. they should be between 1-10, but instead being, they are something like 38329 or 390202 etc. They are something they by no means are supposed to be.

**What is known?** At least the point spending *should* work as the DEBUG: messages show, the 35 points are spent on something. The whole loop is not rolled more than twice or trice. Also, some values do not change at all. Those being ST, PE and IN. Forcing the values inside the function does not work neither for some reason, but works after the generateEntity() call. Thus I assume the problem lies in the way I handle the value assignment to the data type *character*. (E.g. it shouldn't be passed as argument, instead, pointers should be used. But how?)

I hope I made even slight sense with the post and I hope someone could look at this. While this is not anything important, may this be a lesson for me to learn something. :)

---

### Post by Tony Flury on 2008-10-03
You are right - it is about how you are passing the structures.

The values are passed by Value - so your generate entity function is operating on a copy of the structure, not on the original.

You need to pass pointers - and use the -> operator to get to the data that is being pointed at.

Try this : 
Declaration
```

void generateEntity(character *genE);

```

in main : 
```

generateEntity(&PC); 

```

in generateEntity
```

void generateEntity(character *genE) {

...
		genE -> ST += tempStat;
...
		genE -> PE += tempStat;
...
		genE -> CH += tempStat;
...
		genE -> IN += tempStat;
...
		genE -> AG += tempStat;
...
		genE -> LK += tempStat;
	genE -> HP = 15 + (genE -> ST*2) + (genE -> EN*2);
...

	genE -> AG = 3; // Force the AG to 3. Does nothing. Why?
}

```

i also note that you are not initialising your structure to zeros - i assume they should start at zero - and good code should not assume that variables start at 0.

---

### Post by Calmatory on 2008-10-03
Big tank you. That fixed the problem! :)

There was another mistake in the generateEntity() where EN would not be  assigned. I missed that and it didn't get added, which caused some problems which are fixed now.

Thanks. :)

---

### Post by dribeas on 2008-10-03
> **Tony Flury said:**
> You need to pass pointers - and use the -> operator to get to the data that is being pointed at.


If you want to use C++, references are easier/better than pointers (until you need pointers for some other reason):

```

void generateEntity( character & genE ); // implement as the original code

```

In C you must use pointers for all this stuff, but in C++ it is clearer using references.

---

### Post by escapee on 2008-10-03
And just as kind of a follow up/contrast to dribeas post, since you aren't really using any C++ code, you may as well remove <iostream> and just compile under gcc.

---

