---
title: "I am loving this stuff...C++ ?"
date: 2009-02-20
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-20
I am getting an line 35 error: 'p' is not declared in this scope. Is there something I am missing or is it just another text editor fluke? This is lesson in classes.

```
#include <iostream>

using namespace std;

class Computer		// Standered way of defining the class
{
public:
	// This means that all the functions below this ( and any variables)
	// are accessible to the rest of the program.
	// Note: That is a colon, Not a semicolon...
	Computer();
	// Constructer
	~Computer();
	// Destructor
	void setspeed ( int p );
	int readspeed();
protected:
	// This means that all the variables underr this, until a new type of
	// restriction is placed, will only be accessible to other functions in the
	// class. Note: That is a colon, Not a semicolon...
	int processorspeed;
};
	// Do Not forget the trailing semi-colon

Computer::Computer()
{
	// Destructors do not accept arguments
}

[COLOR="RoyalBlue"]Computer::~Computer()  //<- I totaly forgot to put this in also..lol
{
	// Destructors do not accept arguments  
}[/COLOR]

void Computer::setspeed ( int [COLOR="DarkOrchid"]P[/COLOR] )//<- This was the error. It should be lower-case...
{
	// To define a function outside put the name of the class
	// after the return type and then two colons, and then the name
	// of the function.
	[COLOR="DarkOrchid"]processorspeed = p;[/COLOR] // Not declared?
}
int Computer::readspeed()
{
	// The two colons simply tell the compiler that the function is part
	// of the class
	return processorspeed;
}

int main()
{
	Computer compute;
	// To create an 'instance' of the class, simply treat it like you would
	// a structure.  (An instance is simply when you create an actual object
	// from the class, as opposed to having the definition of the class)
	compute.setspeed ( 100 );
	// To call funtions in the class, you put the name of the instance,
	// a period, and then the function name.
	cout<< compute.readspeed();
	// See above note.
}

```

---

### Post by jimi_hendrix on 2009-02-20
try an uppercase P...

---

### Post by Leo Dragonheart on 2009-02-20
> **jimi_hendrix said:**
> try an uppercase P...

Nope, comes back with the same error...

---

### Post by Leo Dragonheart on 2009-02-20
Thanx that was not the problem but the declaration above was a capital p and should have been lower-case. Thanx for helping me see that. Solved!!!

---

### Post by jimi_hendrix on 2009-02-20
i have had similarly stupid errors :)

---

### Post by Leo Dragonheart on 2009-02-20
> **jimi_hendrix said:**
> i have had similarly stupid errors :)

I also came to realise I was missing 1 line of code I forgot to put in....lol

---

