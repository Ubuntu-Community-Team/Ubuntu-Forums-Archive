---
title: "C++ rand"
date: 2009-09-23
forum: Programming Talk
---

### Post by kevCast on 2009-09-23
Hello. I'm new to programming and trying to write a very simple C++ program that simulates a craps game. So far, I have:

```
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main()
{
	srand((unsigned)time(NULL));
	int point;
	char play_again;
	play_again = 'y';
	cout << "Welcome to the craps game simulator!\n";
	cout << "The game is about to begin.\n";
	cout << "Press enter to continue...";
	cin.get();
	point = (rand() % 6 + 1);
	while (play_again == 'y')
	{
		if ((point == 7) || (point == 11))
			cout << "Congradulations! You win!\n";
		else if (point == 2)
			cout << "Snake eyes. You lost. :(";
		else if ((point == 12) || (point == 3))
			cout << "Aww...you lost.";
		else

		while(point != 7)
		{
			cout << point << endl;
			cout << "Press enter to roll again.";
			cin.get();
		} while (point!= 7);
		
		cout << "Play again? y or n";
		cin >> play_again;
		
		while ((play_again != 'y') || (play_again != 'n'))
		{
			cout << "I'm sorry, I'm not familiar with that character.\n";
			cout << "Please use y or n\n";
		}
	}
	return 0;
}
```

It's a mess, and not finished. The problem is the rand function. I declare it as point, on the assumption it's random. However, it's a static integer. I'm trying to wrap my head around this.

How do I make the first roll a random one, and assign that value to variable? It's very difficult for me to articulate right now, sorry.

Any and all help is appreciated. Thank you.

---

### Post by ve4cib on 2009-09-24
First off you do not need to put "while(point!=7)" both before *and* after the loop.  It should be in one place, and one place only.

Secondly, inside your loop you are never assigning a new value to point inside the loop.  You are setting the value once initially, and then looping forever checking that same value over and over.  If it wasn't 7 the first time it won't be 7 the 100 millionth time either.

Finally, the way you're producing the random number will give you a result in the range of 1-6, with an even distribution.  Point can never, ever be 7; rand() % 6 will give you a number in the range [0,5], adding 1 gives you [1,6].  No way to get 7, 8, ..., 11, or 12 with that.

To solve the last problem I would create a new function:

```

int rollDice() {
    // roll two "dice" (random numbers in range 1-6) and add them together
    return (rand() % 6 +1) + (rand() %6 +1);
}

int main() {
    ...
}

```

To solve the infinite loop just add this line inside the loop:

```

...
while(point!=7) {
    cout << point << endl;
    cout << "Press enter to roll again.";
    cin.get();
    point = rollDice();    // <-- this is the new line you need to add
}

```

---

### Post by A_Fiachra on 2009-09-24
From the manpages:


```

 The rand() function returns a pseudo-random integer between 0 and RAND_MAX.

 The srand() function sets its argument as the seed for a new sequence of pseudo-random integers to be returned by rand().  These sequences are repeatable by calling srand() with the same seed value.

 If no seed value is provided, the rand() function is automatically seeded with a value of 1.


```

A common way to seed a random sequence is to use ctime() to get seconds since the epoch.  Or use seconds since the epoch mod some arbitrary prime number (2 and 3 are probably not very interesting!)

Example:

```

int main() {
    srand ( time(NULL) );
    int r;
    for (int i = 0; i < 10; i++) {
        r = rand() % 10 + 1;
        std::cout << r << "\n";
        insert(r); //insert into heapq
    }
return 0;

}



```

Will print 10 "random" numbers between 1 and 10, that will be different each time it is run.

---

### Post by kevCast on 2009-09-24
Is there a way to get the variable point to refer to its previous value before it was assigned the value ((rand() % 6 + 1) + (rand() % 6 + 1)) at the end of the loop?

---

### Post by ve4cib on 2009-09-24
I'm afraid I don't understand what you mean.  Can you elaborate?

---

### Post by hessiess on 2009-09-24
rand isn't nesoserraly verry random, you could also read from /dev/urandom or /dev/random which will probably produce a more random result.

---

### Post by MadCow108 on 2009-09-24
rand is mostly enough except you're writing some security relevant stuff like encryption or numerical simulations which rely on good random numbers.

for the latter case /dev/random is mostly to slow, in those cases you should simply use a better random number generator like a mersenne twister (rand() is a linear congruential generator)
boost provides this one (along with others)
[http://www.boost.org/doc/libs/1_40_0/libs/random/index.html](http://www.boost.org/doc/libs/1_40_0/libs/random/index.html)

---

### Post by kevCast on 2009-09-26
```
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main()
{
	srand((unsigned)time(NULL));
	int roll_1, roll_x;
	char again;
	again = 'y';
	while (again == 'y')
	{
		cout << "Welcome to the craps game simulator!\n";
		cout << "The game is about to begin! ";
		cout << "Press enter to continue.\n";
		cin.get(); /*Using a linux system. DOS system calls don't work.
		:( */
		roll_1 = ((rand() % 6 + 1) + (rand() % 6 + 1));

		if ((roll_1 == 7) || (roll_1 == 11))
		{
			cout << roll_1 << endl;
			cout << "Congradulations! You won!";
		}
		else if ((roll_1 == 3) || (roll_1 == 12))
		{
			cout << roll_1 << endl;
			cout << "Awww, bummer.";
		}
		else if (roll_1 == 2)
		{
			cout << roll_1 << endl;
			cout << "Snake eyes.";
		}
		else

		while ((roll_x != 7) || (roll_x != roll_1))
		{
			cout << roll_x << endl;
			cout << "Press enter to roll them bones.";
			cin.get();
			roll_x = ((rand() % 6 + 1) + (rand() % 6 + 1));
		}

		cout << "\nWould you like to play again? y or n";
		cin >> again;
	}
	return 0;
}

```

I'm getting incorrect values for roll_1. Why?

---

### Post by dwhitney67 on 2009-09-26
The value for roll_1 seems ok; what is wrong is your timing when it comes to displaying roll_x, and more importantly your usage of roll_x.

You compared roll_x with roll_1 (and 7) before roll_x was ever initialized.

When you know you may have to do something repeatedly until some condition is met, and that this thing must be done _at least once_, then you rely on the _do-while_ loop, not the while-loop.

I've taken your code to sort out the bugs, and simplify it a bit.  Peruse it to compare with your version.
```

#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

unsigned int roll_dice()
{
   return (rand() % 6) + (rand() % 6) + 2;
}

int main()
{
   srand(time(0));

   char again = 'y';

   do
   {
      cout << "Welcome to the craps game simulator!\n";
      cout << "The game is about to begin! ";
      cout << "Press enter to continue.\n";
      cin.get();

      unsigned int roll_1 = roll_dice();
      cout << "you rolled a: " << roll_1 << endl;

      if (roll_1 == 7 || roll_1 == 11)
      {
         cout << "Congratulations! You've won!" << endl;
      }
      else if (roll_1 == 3 || roll_1 == 12)
      {
         cout << "Awww, bummer." << endl;
      }
      else if (roll_1 == 2)
      {
         cout << "Snake eyes." << endl;
      }
      else
      {
         unsigned roll_x = 0;

         do
         {
            cout << "Press enter to roll them bones again.";
            cin.get();

            roll_x = roll_dice();
            cout << "\nyou rolled a: " << roll_x << endl;

         } while (roll_x != 7 && roll_x != roll_1);
      }

      cout << "\nWould you like to play again? y or n  ";
      cin >> again;
      cin.ignore(1024, '\n');  // this is need to gobble newline character (and any other garbage input)

   } while (again == 'y');
}

```

P.S.  Changes I made:
1.  Added roll_dice() function.
2.  Move declarations closer to where they are first used.
3.  Changed initial while-loop to a do-while-loop.
4.  Printed out roll_1 as soon as the value is known.
5.  Placed curly brackets for final else-block.
6.  Used do-while-loop in lieu of while-loop in else-block.
7.  Printed out roll_x at correct place (ie after it is known).
8.  Fixed comparison between roll_x and roll_1.
9.  Added white-space after play-again prompt.
10. Added cin.ignore() statement.
11. Remove return 0; C++ apps automatically return this value.
12. Corrected spelling of "Congradulations".

---

