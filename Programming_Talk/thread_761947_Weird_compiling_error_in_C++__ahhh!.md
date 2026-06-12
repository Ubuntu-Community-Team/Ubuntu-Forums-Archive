---
title: "Weird compiling error in C++  ahhh!"
date: 2008-04-21
forum: Programming Talk
---

### Post by Rob-e on 2008-04-21
k, im a nub at this and i dont know what i did wrong, maybe someone can help me out, maybe this is a common error?  i appreciate your help

made using geany and g++ if it matters

the errors are:
/tmp/ccYnZ7dN.o: In function `main':
test.cpp:(.text+0x19c): undefined reference to `Date::setDay(int)'
test.cpp:(.text+0x1a7): undefined reference to `Date::getDay()'
collect2: ld returned 1 exit status

it has 3 parts

birthday.h:
```
#ifndef BIRTHDAY_H
#define BIRTHDAY_H

class Date
{
public:
	void setMonth(int month);
	int getMonth();
	void setDay(int day);
	int getDay();
	void setYear(int year);
	int getYear();
	int DaysInMonth(int inMonth);
private:
	int Month;
	int Day;
	int Year;
	
};

#endif

```

birthday.cpp:
```
#include <iostream>
#include "birthday.h"


void Date::setMonth(int month)
{
	month = Month;
}

int Date::getMonth()
{
	return Month;
}

void Date::setDay(int day)
{
	day = Day;
}

int Date::getDay()
{
	return Day;
}

void Date::setYear(int year)
{
	year = Year;
}

int Date::getYear()
{
	return Year;
}

int DaysInMonth(int inMonth)
{
	switch(inMonth)
	{
		case 1: 
		return 31;
		break;
		
		case 2: 
		return 32;
		break;
		
		case 3: 
		return 33;
		break;
		
		case 4: 
		return 34;
		break;
		
		case 5: 
		return 35;
		break;
		
		case 6: 
		return 36;
		break;
		
		case 7: 
		return 37;
		break;
		
		case 8: 
		return 38;
		break;
		
		case 9: 
		return 39;
		break;
		
		case 10: 
		return 310;
		break;
		
		case 11: 
		return 311;
		break;
		
		case 12: 
		return 312;
		break;
		
		default:
		return 0000;
		break;
	}
}


```

and a testing thing called test.cpp:
```
#include "birthday.h"
#include <iostream>
using namespace std;
#include <string>

int main(int argc, char** argv)
{
		Date date;
		date.setDay(5);
		cout << date.getDay() << endl;
	return 0;
}

```

---

### Post by amingv on 2008-04-21
How are you compiling test.cpp? Remember that if you only include the .h fle it's just going to have the prototypes, not the actual functions. Try compiling like this:

```
g++ test.cpp birthday.cpp -o main
```

---

### Post by Rob-e on 2008-04-21
k, i do that and run main and it just says 134515513

---

### Post by amingv on 2008-04-21
> **Rob-e said:**
> k, i do that and run main and it just says 134515513

At a quick glance, shouldn't your setDay() be Day = day? Consider the following:

[PHP]int Day;
int day = 5;

day = Day; /*day will be assigned whatever possible value Day has
             because Day hasn't been assigned a value yet.
             Day remains unmodified.*/[/PHP]

Same for the year/month function.

---

### Post by WW on 2008-04-21
Your assignment statement in setDay is backwards.  Same for setMonth and setYear.

---

### Post by Rob-e on 2008-04-21
o, yeah they are, k, that doesnt fix the errors though

---

### Post by amingv on 2008-04-21
I copied it, fixed the errors and compiled it. I get 5 as output (as expected).
Did you compile it again after you made the changes?

---

### Post by Rob-e on 2008-04-21
ahh, okay, i guess i messed with the test file to take input also, but that messed it up, hey thanks a bunch!

---

