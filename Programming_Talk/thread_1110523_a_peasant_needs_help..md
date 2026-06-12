---
title: "a peasant needs help."
date: 2009-03-29
forum: Programming Talk
---

### Post by Squigy Dunkens on 2009-03-29
[FONT="Courier New"]I'm learning c++, and started making a little game to kinda learn some of the basics. your a peasant, and you can go fishing, and sell fish.(there is a function for mining, but its not used yet because i want to fix the program first). here is the code.

```
#include <iostream>

#include <string>

#include <stdlib.h>
#include <string.h>

using namespace std;



/*variables*/

int fish=0, pellets=0, veggies=0, bones=0, weapons[]={0,0,0};

int number=0, ore[]={0,0,0}, counter, chance;

char action[20], item[20];



/*hardhat time, i'm goin minin*/

void gomining()

{

	counter = 3;

	cout << "you mine for ore";

	while(counter > 0)

	{

		cout << "you mine for ore...";

		chance = rand() % 100 + 1;
		

		if(chance <= 40)

		{

			cout << "You get steel...\n";

			ore[2] += 1;

		}

		else if(chance <= 65)

		{

			cout << "You get iron...\n";

			ore[1] += 1;

		}

		else if(chance <= 85)

		{

			cout << "You get bronze...\n";

			ore[0] += 1;

		}

		else

		{

			cout << "A couple of rocks shoot up and hit you in the eye...";

		}
		
		counter--;

	}

}

	



/*gone fishin*/

void getfish()

{

	cout << "you go fishin..." << endl << "you catch a fish\n";

	fish += 1;

}

/*Time to sell my fishies*/

void sell()

{

	if(number <= fish)

	{

		cout << "What would you like to sell? ";

		cin.get(item,20);

		if(action == "fish")

		{

			cout << "How many? ";

			cin >> number;

			if(number <= fish)

			{

				cout << "you sell " << number << " fish\n";

				pellets += 2*number;

				fish -= number;

			}

			else

			{

				cout << "You don't have that many fish.";

			}

		}

		else

		{

			cout << "Hmmm... Yeah?... Interesting... Na, I don't like it, keep it.";

		}

	}

}

/*start playin*/

int main()

{

	while (action != "die")

	{

		cout << "\nyou have:\n" << fish << " fish\n";

		cout << pellets << " poo pellets\n";

		cout << ore[0] << " bronze ore\n";

		cout << ore[1] << " iron ore\n";

		cout << ore[2] << "steel ore\n";

		cout << "What would you like to do? ";
		cin.ignore();

		cin.get(action,20);
		cout << "'" << action << "'" << endl;

		if (strncmp(action, "go fishing", 10) == 0)

		{

			getfish();

		}

		else if (action == "sell")

		{

			sell();

		}

		else if (action == "go mining")

		{

			gomining();

		}

		else

		{

			cout << "Thats not an option\n";

		}

	}

	return 0;

}

```

heres what happens when i run it

[SIZE="1"]you have:
0 fish
0 poo pellets
0 bronze ore
0 iron ore
0steel ore
What would you like to do? go fishing
'**[COLOR="Red"]o fishing[/COLOR]**'
Thats not an option

you have:
0 fish
0 poo pellets
0 bronze ore
0 iron ore
0steel ore
What would you like to do? go fishing
'go fishing'
you go fishin...
you catch a fish

you have:
1 fish
0 poo pellets
0 bronze ore
0 iron ore
0steel ore
What would you like to do? 

[/SIZE]

see when i first type go fishing? i made it repeat the action so i can see whats wrong. for some reason the program only see's "o fish"(highlighted in red, and bold). but the second time i type "go fishing" it gets it correctly, and proceeds with the getfish function. why is it that it doesn't get the first letter the first time?[/FONT]

---

### Post by nealh149 on 2009-03-29
The problem lies in your placement of cin.ignore().  Basically that takes a single character and discards it.  So it discards your 'g' in 'go fishing'.  If you place it after cin.get() it should work fine.

---

### Post by Squigy Dunkens on 2009-03-29
haha, i spent along time tryin to figure this out, and didn't even think of that, lol. thanx!

---

