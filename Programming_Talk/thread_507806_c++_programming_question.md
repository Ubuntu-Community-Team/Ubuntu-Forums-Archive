---
title: "c++ programming question"
date: 2007-07-23
forum: Programming Talk
---

### Post by babyboss on 2007-07-23
Hello, I am trying the learn some c++ programming.

I tried to test a sample program that comes from a c++ book, but it doesn't work.

There are 3 files in this program: clockType.h, clockTypeImp.cpp, testClock.cpp

I got the following compiling error when I compiled it:

/tmp/cckuzbJE.o: In function `main':
testClock.cpp:(.text+0xa2): undefined reference to `clockType::setTime(int, int, int)'
testClock.cpp:(.text+0xad): undefined reference to `clockType::printTime() const'
collect2: ld returned 1 exit status

clockType.h:
1#include <iostream>
2class clockType
3{
4	public:
5		void setTime(int hours, int minutes, int seconds);
6
7		void getTime(int& hours, int& minutes, int& seconds);
8
9		void printTime() const;
10
11		void incrementSeconds();
12	
13		void incrementMinutes();
14
15		void incrementHours();
16
17		bool equalTime(const clockType& otherClock) const;
18	
19	private:
20		
21		int hr;
22
23		int min;
24
25		int sec;
26};


clockTypeImp.cpp:
#include<iostream>
#include "clockType.h"

using namespace std;

void clockType::setTime(int hours, int minutes, int seconds)
{
	if(0 <= hours && hours < 24)
		hr = hours;
	else
		hr = 0;

	if(0 <= minutes && minutes < 60)
		min = minutes;
	else
		min = 0;

	if(0 <= seconds && seconds < 60)
		sec = seconds;
	else
		sec = 0;
}

void clockType::getTime(int& hours, int& minutes, int& seconds)
{
	hours = hr;
	minutes = min;
	seconds = sec;
}

void clockType::printTime() const
{
	if(hr<10)
		cout << "0";
		cout << hr << ":";

	if(min < 10)
		cout << "0";
		cout << min << ":";

	if(sec < 10)
		cout <<  "0";
		cout << sec;
}

void clockType::incrementHours()
{
	hr++;
	if(hr>23)
		hr=0;
}

void clockType::incrementMinutes()
{
	min++;
	if(min > 59)
	{
		min = 0;
		incrementHours();
	}
}

void clockType::incrementSeconds()
{
	sec++;
	if(sec > 59)
	{
		sec = 0;
		incrementMinutes();
	}
}

bool clockType::equalTime(const clockType& otherClock) const
{
	return(hr == otherClock.hr && min == otherClock.min && sec == otherClock.sec);
}	



testClock.cpp
#include<iostream>
#include "clockType.h"

using namespace std;

int main()
{
	clockType myClock;
	
	myClock.setTime(6, 27, 46);

	myClock.printTime();
}


thank you very much!

---

### Post by babyboss on 2007-07-23
i used the following command under ubuntu to compile the program
g++ testClock.cpp -o testClock

---

### Post by LaRoza on 2007-07-23
Your code is hard to read, place any code between the [ code ] [ / code ] tags to make it readable. (No spaces in the tags.)

You are not including "clockTypeImp.cpp".

---

### Post by aks44 on 2007-07-23
> **babyboss said:**
> collect2: ld returned 1 exit status

This should hint you that this is a linker error, not a compiler error...

You have to compile each .cpp file into a .o using g++, then link all the .o together using ld (I don't remember / care about the exact command lines needed, for anything bigger than a single .cpp file you should definitely use a makefile).

As I'm still a newb to the Linux programming environment I personnaly use KDevelop which takes care of creating all those make / automake / autoconf thingies. It really makes life easier. I guess any IDE will do the trick (could anyone programming under GNOME help on this one and give the OP some decent IDE names?).

BTW LaRoza is right, please use [ code ] tags when posting to make your code more readable, it is a pain to read as it is ;)

---

### Post by rahul.gupta on 2007-07-23
you can try this in oder to compile the code

> g++ -c  clockTypeImp.cpp
This would produce as output clockTypeImpl.o file

Now issue the command
> g++ -o a.out main.cpp clockTypeImpl.o
This would compile the code in main.cpp and link with the compile object file in one step

---

### Post by hod139 on 2007-07-23
> **rahul.gupta said:**
> you can try this in oder to compile the code

> g++ -c  clockTypeImp.cpp
This would produce as output clockTypeImpl.o file

Now issue the command
> g++ -o a.out main.cpp clockTypeImpl.o
This would compile the code in main.cpp and link with the compile object file in one step
You can alternatively list all the source files on the same line:
```

g++ main.cpp clockTypeImp.cpp -o testClock

```

As aks44 said, dealing with multiple source files can quickly become annoying, and learning how to write makefiles will be beneficial.

---

