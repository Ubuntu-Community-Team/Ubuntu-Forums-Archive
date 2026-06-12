---
title: "How do I exit a program??"
date: 2007-02-28
forum: Programming Talk
---

### Post by grndslm on 2007-02-28
I'm having a little trouble trying to get the exit() function working.  I'm doing exception handling for school, but I'm the only one who can't get the exit function to work.  I'm afraid this is a bug with g++.  Maybe you guys could take a look (I'm sure it wouldn't take you too long ;-)):

CLOCK HEADER
=========

#ifndef H_Clock
#define H_Clock

#include <iostream>

using namespace std;

class Clock
{
friend ostream& operator<<(ostream& output, const Clock& kcolc);

public:
	Clock(int hours = 0, int minutes = 0);
	void setTime(int hours, int minutes);
	void printTime() const;
	void operator++();	  
	bool operator==(Clock&);
	bool operator<(Clock&);

private: 
    int hr;
    int min;
};

class ValueError
{
//friend ostream& operator<<(ostream& output, const ValueError& VE);
public:
	ValueError(int value);
protected:
	int value;
};

class BadHours : public ValueError
{
friend ostream& operator<<(ostream& output, const BadHours& BH);

public:
	BadHours(int value);
};

class BadMinutes : public ValueError
{
friend ostream& operator<<(ostream& output, const BadMinutes& BM);

public:
	BadMinutes(int value);

};

#endif


CLOCK CPP
=======

#include <iostream>
#include "jrv31-clock.h"

using namespace std;

Clock::Clock(int hours, int minutes)
{
	try
	{
		if (hours > -1 && hours < 24)
		hr = hours;
	else
		throw BadHours(hours);
		
	if (minutes > -1 && minutes < 60)
		min = minutes;
	else
		throw BadMinutes(minutes);
	}
	catch (BadHours bh)
	{
		cout << bh;
	}
	catch (BadMinutes bm)
	{
		cout << bm;
	}
}

void Clock::setTime(int hours, int minutes)
{		
	try
	{
		if (hours > -1 && hours < 24)
			hr = hours;
		else
			throw BadHours(hours);
		
		if (minutes > -1 && minutes < 60)
			min = minutes;
		else
			throw BadMinutes(minutes);
	}
	catch (BadHours bh)
	{
		cout << bh << "hours.\nThe program will end now.";
		exit(-1);
	}
	catch (BadMinutes bm)
	{
		cout << bm << "minutes.\nThe program will end now.";
		exit(-1);
	}
}

void Clock::printTime() const
{
	if (hr < 10)
		cout << "0";
	
	cout << hr << ":";

	if (min < 10)
		cout << "0";
	
	cout << min;
}

void Clock::operator++()
{
	if (min==59)
	{
		if (hr==23)
			hr=0;
		else
			++hr;
		
		min=0;
	}
	else
		++min;
}

bool Clock::operator==(Clock& someClock)
{
	if (hr==someClock.hr && min==someClock.min)
		return true;
	else
		return false;
}
	  
bool Clock::operator<(Clock& someClock)
{
	if (hr<=someClock.hr && min<someClock.min)
		return true;
	else
		return false;	
}

ostream& operator<<(ostream& output, const Clock& someClock)
{
	if (someClock.hr < 10)
		output << "0";
	output << someClock.hr << ":";

	if (someClock.min < 10)
		output << "0";
	output << someClock.min;
	
	return output;
}

ValueError::ValueError(int Value)
{
	value = Value;
}

BadHours::BadHours(int Value): ValueError(Value)
{		
}

BadMinutes::BadMinutes(int Value): ValueError(Value)
{
}

ostream& operator<<(ostream& output, const BadHours& someBH)
{
	output << someBH.value << " is not a valid value for hours.\n";
	
	return output;
}

ostream& operator<<(ostream& output, const BadMinutes& someBM)
{
	output << someBM.value << " is not a valid value for minutes.\n";
	
	return output;
}


CLOCK DRIVER
=========

#include <iostream>
#include "jrv31-clock.h"

using namespace std;

int main()
{
	cout << "Testing constructors and printTime" << endl;

	Clock myClock(15, 06);
	Clock yourClock;
	Clock badClock(56, 67);

	myClock.printTime();		//prints 15:06
	cout << endl;
	yourClock.printTime();		//prints 00:00
	cout << endl;
	badClock.printTime();		//prints 00:00
	cout << endl;

	cout << endl << "Testing setTime" << endl;
	yourClock.setTime(42,5);
	yourClock.printTime();		//prints 23:59
	cout << endl;

    cout << endl << "Testing preincrement operator" << endl;

	myClock.operator++();
	myClock.printTime();		//prints 15:07
	cout << endl;
	++yourClock;
	yourClock.printTime();		//prints 00:00
	cout << endl;

	cout << endl << "Testing == operator" << endl;
	yourClock.setTime(15, 10);
	myClock.printTime();
	cout << " == ";
	yourClock.printTime();
	if (myClock == yourClock)
		cout << "  Yes!" << endl;
	else
		cout << "  No." << endl;	//prints No.

	badClock.setTime(15, 10);
	yourClock.printTime();
	cout << " == ";
	badClock.printTime();
	if (yourClock == badClock)
		cout << "  Yes!" << endl;	//prints Yes!
	else
		cout << "  No." << endl;
  
	cout << endl << "Testing < operator" << endl;
	myClock.printTime();
	cout << " < ";
	yourClock.printTime();
	if (myClock < yourClock)
		cout << "  Yes!" << endl;	//prints Yes!
	else
		cout << "  No." << endl;

	yourClock.printTime();
	cout << " < ";
	myClock.printTime();
	if (yourClock < myClock)
		cout << "  Yes!" << endl;
	else
		cout << "  No." << endl;	//prints No.

	cout << endl;
	cout << "myClock = " << myClock << endl;
	cout << "yourClock = " << yourClock << endl; 

	return 0;
}

---

### Post by WW on 2007-02-28
I don't have an answer to your question, but just a suggestion about posting code.  Please enclose the code samples in [ code ] and [ /code ] tags (but without the spaces inside the brackets), like this:
[ code ]
...your code here...
[ /code ]
 This will put the code in a nice box, and--most importantly--preserve the indentation.  (I had to put extra spaces inside the brackets to prevent my example from actually being interpreted as code and /code tags.  Don't include those spaces in your post.)

---

### Post by thelinuxguy on 2007-02-28
Isn't the exit function supposed to be in stdlib.h?
[http://linux.about.com/library/cmd/blcmdl3_exit.htm](http://linux.about.com/library/cmd/blcmdl3_exit.htm)

---

### Post by WW on 2007-02-28
grndslm,

I ran your program, and it did what you would expect it to do:
>  $ g++ clock.cpp
$ g++ main.cpp
$ g++ main.o clock.o -o main
$ ./main
Testing constructors and printTime
56 is not a valid value for hours.
15:06
00:00
65535:1076109120

Testing setTime
42 is not a valid value for hours.
hours.
The program will end now.

As thelinuxguy pointed out, the code should probably include <cstdlib> before using exit(), but it worked for me without it. (Details: I actually tested this on a computer running Debian, with g++ version 3.3.5, but it should also work fine in Ubuntu.)

What is the problem that you are having?  What do you mean when you say you "can't get  the exit() function working"?

---

