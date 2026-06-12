---
title: "How to 'pause' c++ programs"
date: 2008-06-10
forum: Programming Talk
---

### Post by Scooter7 on 2008-06-10
Hi,

I'm learning C++, and practicing by writing a basic text rpg.   I'm using Arch Linux.

At one point, the player encounters an NPC, who then speaks to the player.   I want the program to pause and wait for the player to hit a key to continue, so that they have time to read what the NPC says before moving on.

From what I've done in the past, I figured **cin.get();** would work, but it doesn't seem to have any effect.

Here is the code I have so far:

```

//--------------------------------------
//|	A simple(?) text rpg           |
//|	By Vertimyst                   |
//|  (http://www.darknet-fusion.co.cc) |
//--------------------------------------

#include <iostream>
using namespace std;

char cfname[50];	// Character's first name
char clname[50];	// Character's last name
char cgender;		// Character's gender
char crace[50];		// Character's race

int experience;		// (Exp)erience points
int exp_cap;		// Exp cap - can grow over time
int level;		// Level - grows as you gain exp
int exp();		// The function that manages exp

int main()
{
   exp_cap = 1000;	// Set the experience cap

   cout << "Shadowgate Productions Presents...\n";
   cout << "A simple(?) text rpg\n";
   cout << "Written, directed, and programmed...\n";
   cout << "Entirely by ME (Vertimyst)!\n";
   cout << "\n";
   cout << "So I'm assuming you want to start playing.\n";
   cout << "You can do that (and currently only that), so let's proceed.\n";
   cout << "\n";
   cout << "First, enter your character's first name (Must be less than 50 characters): ";
   cin >> cfname;
   cout << "\nAnd now, your character's last name (same limit as before): ";
   cin >> clname;
   cout << "\nExcellent, now your gender (M/F): ";
   cin >> cgender;
   cout << "\nVery good, and now your race (50 characters or less\n";
   cout << "and I'm too lazy to make a list, so just make something up, Human is as good as any): ";
   cin >> crace;
   cout << "\n";
   cout << "Okay, here is your (currently basic) character sheet:\n";
   cout << "Name: " << cfname << " " << clname << endl;
   cout << "Gender: " << cgender << endl;
   cout << "Race: " << crace << endl;
   cout << "\n";
   cout << "Good, now that we have that over with, I'll send you\n";
   cout << "into the world.   If you arrive with your limbs intact, you may\n";
   cout << "meet someone helpful.   Good luck!\n";
   cout << "\n";
   cout << "You wake up (although you didn't know you were sleeping O.o), and\n";
   cout << "you see a mage.   Yea, a mage... dunno his name yet.\n";
   cout << "\n";
   cout << "Mage:\n";
   cout << "\"Hello, hello.   I shall give you experience!\"\n";
   cin.get();
   experience = 20;
   exp();
	return 0;
}

int exp()
{
   cout << "You have recieved " << experience << " experience points!\n";
   if (experience == 1000)
   {
      cout << "You have gained a level!   DING! GRATZ ^^;\n";
      (level++);
      cout << "You are now level: " << level << "!\n";
      experience = 0;
   }
   if (experience < 1000)
   {
      cout << "You need " << (exp_cap - experience) << " more experience points (out of " << experience << ") to level up.   Keep it up!\n";
   }
}

```

Also (and this isn't really a problem, I just find it odd), I've read that without **using namespace std;**, I have to put **std::** before every **cout** and such.   However, I had been using them before without the namespace std.

Any suggestions?

---

### Post by KingTermite on 2008-06-10
In C I've used getch() or getchar(). See if there's something similar with the cin class. You may need to flush the buffer before you call it so it doesn't grab a char already buffered (fflush(stdin)).

---

### Post by iansane on 2008-06-10
Well several cin.get()'s in a row will work if you know how many space characters are in the input stream, but that would be silly to do.

The right way is:
```
 cin.ignore(cin.rdbuf()->in_avail() + 2) 
```

Where the "2" at the end represents the number of characters left in the input stream.

If you look back through your code and count up the number of cin >> statements, you can find what number to add instead of 2. That is just an example.

Also, if you want you can look at this:

[http://www.daniweb.com/forums/thread90228.html](http://www.daniweb.com/forums/thread90228.html)

and copy/paste Narue's code into a cpp or .h file to use as an include in your programs. If you read the whole post you'll see where a minor change had to be made for it to work on Linux systems.

It gives you a way to flush the input stream and also a way to pause the system. I've been using it a lot and would like to know if more experienced programmers have any thoughts on whether or not it is good programming practice since it is not part of the standard library.

---

### Post by Scooter7 on 2008-06-10
Well, I couldn't really get Narue's code to compile or include properly for some reason, even after renaming all the 'pause' to 'pause2' and such.

So I tried this instead (suggested by a friend):

```
cout << "Mage:\n";
   cout << "\"Hello, hello.   I shall give you experience!\"\n";
   cout << "(C)ontinue\n";

   char looper[50] = "";

   cin >> looper;
```

So the player has to hit 'c' (or any other letter, really) then enter to continue.   I guess it'll have to work for now.

Thanks everyone for your help!

If anyone has a better suggestion, though, feel free to share.

---

### Post by dwhitney67 on 2008-06-10
This works for me...
[PHP]std::cout << "Press any key to continue...";
std::cin.ignore( std::cin.rdbuf()->in_avail() + 1 );[/PHP]

Or alternatively:
[PHP]std::cout << "Press Ctrl-d to continue...";
char ch;
std::cin >> ch;[/PHP]

---

