---
title: "C++ static question"
date: 2009-03-29
forum: Programming Talk
---

### Post by swappo1 on 2009-03-29
I have the following code.
```
#include <iostream>

using namespace std;

class tollBooth
{
	private:
		static unsigned int cars;
		static double amount;
	public:
		tollBooth()
			{ cars = 0;	amount = 0.0; }
		void payingCar()
			{ cars++; amount += 0.5; }
		void nopayCar()
			{ cars++; }
		void display()
			{ cout << "cars = " << cars << "    amount = " << amount << endl; }
};

int main()
{
	tollBooth x;
	char ch;
	
	cout << "Enter '1' to count a car that pays." << endl;
	cout << "Enter '0' to count a car that does not pay." << endl;
	cout << "Enter 'q' to quit." << endl;
	
	while((ch = getchar()) != 'q')
		{
		if(ch == 0)
			{
			x.payingCar();
			}
		else if(ch == 1)
			{
			x.nopayCar();
			}
		}
	x.display();
	
	return 0;
}
	 
```
Here is the output:
```
/tmp/ccb0yd5w.o: In function `tollBooth::tollBooth()':
C++7.2.cpp:(.text._ZN9tollBoothC1Ev[tollBooth::tollBooth()]+0xa): undefined reference to `tollBooth::cars'
C++7.2.cpp:(.text._ZN9tollBoothC1Ev[tollBooth::tollBooth()]+0x1a): undefined reference to `tollBooth::amount'
/tmp/ccb0yd5w.o: In function `tollBooth::payingCar()':
C++7.2.cpp:(.text._ZN9tollBooth9payingCarEv[tollBooth::payingCar()]+0xa): undefined reference to `tollBooth::cars'
C++7.2.cpp:(.text._ZN9tollBooth9payingCarEv[tollBooth::payingCar()]+0x13): undefined reference to `tollBooth::cars'
C++7.2.cpp:(.text._ZN9tollBooth9payingCarEv[tollBooth::payingCar()]+0x1b): undefined reference to `tollBooth::amount'
C++7.2.cpp:(.text._ZN9tollBooth9payingCarEv[tollBooth::payingCar()]+0x2f): undefined reference to `tollBooth::amount'
/tmp/ccb0yd5w.o: In function `tollBooth::nopayCar()':
C++7.2.cpp:(.text._ZN9tollBooth8nopayCarEv[tollBooth::nopayCar()]+0xa): undefined reference to `tollBooth::cars'
C++7.2.cpp:(.text._ZN9tollBooth8nopayCarEv[tollBooth::nopayCar()]+0x13): undefined reference to `tollBooth::cars'
/tmp/ccb0yd5w.o: In function `tollBooth::display()':
C++7.2.cpp:(.text._ZN9tollBooth7displayEv[tollBooth::display()]+0x12): undefined reference to `tollBooth::amount'
C++7.2.cpp:(.text._ZN9tollBooth7displayEv[tollBooth::display()]+0x18): undefined reference to `tollBooth::cars'
collect2: ld returned 1 exit status
scott@scott-laptop:~$ 

```
If I remove static from the class data cars and amount, I don't get the any error messages.  However, I need the class data to be static to keep from reseting cars and amount each time the function is called.  Any ideas why I am getting these errors?

---

### Post by FFfanatic on 2009-03-29
You need to initialize the variables outside the class.
IIRC, it should be:
```

class tollBooth
{
	private:
		static unsigned int cars;
		static double amount;
	public:
		tollBooth()
			{}
		void payingCar()
			{ cars++; amount += 0.5; }
		void nopayCar()
			{ cars++; }
		void display()
			{ cout << "cars = " << cars << "    amount = " << amount << endl; }
};
//though I'm not sure if the unsigned belongs here
[b]unsigned int tollBooth::cars = 0;
double tollBooth::amount = 0.0;[/b]

```

---

### Post by dwhitney67 on 2009-03-29
One can get away with initializing ints (and unsigned ints) within a class, but for other types, it has to be done outside the class.  If a class is going to have a mixed-collection of static variables, one might as well initialize them all in the same place as demonstrated by FFfanatic.

P.S.  If the application only calls out for one tollBooth object (as was demonstrated by the OP), then there is no need to have static data members in the class.

---

### Post by Dejai on 2009-03-29
Hello, I have some suggestions to  make, firstly there are some logic errors.. At least when you are testing if a car has payed or not payed you are using decimal or integer values to test that, when your reading in a character... Also I believe static members must be first initialized outside of the class don't take my word for it I am not a very good C++ programmer but thats what I got out of the following reference: 
[http://www.cprogramming.com/tutorial/statickeyword.html](http://www.cprogramming.com/tutorial/statickeyword.html)

Here is your code with some editing, I would also watch the indentation(What style is that?) :P Besides that its pretty good code, I only had to make a few changes. You may notice that I declare all instances of the static variables with tollBooth:: thats good practice to remind you that its static. I would read that above URL as well.

```

#include <iostream>

using namespace std;

class tollBooth
{
	private:
		static unsigned int cars;
		static double amount;
	public:
		tollBooth()
		  { }
		void payingCar()
		{ tollBooth::cars++; tollBooth::amount += 0.5; }
		void nopayCar()
		{ tollBooth::cars++; }
		void display()
		{ cout << "cars = " << tollBooth::cars << "    amount = " << tollBooth::amount << endl; }
};
unsigned int tollBooth::cars = 0;
double tollBooth::amount = 0.0;

int main()
{
	tollBooth x;
	char ch;
	
	cout << "Enter '1' to count a car that pays." << endl;
	cout << "Enter '0' to count a car that does not pay." << endl;
	cout << "Enter 'q' to quit." << endl;
	
	while((ch = getchar()) != 'q')
		{
		if(ch == '1')
			{
			x.payingCar();
			}
		else if(ch == '0')
			{
			x.nopayCar();
			}
		}
	x.display();
	
	return 0;
}


```

```

//Compile Command:
g++ -Wall -Werror cars main.c

```

---

### Post by Dejai on 2009-03-29
Wow I was amazed at the quality of responses that came before I compiled the project and refreshed the page! Good work!

---

### Post by swappo1 on 2009-03-29
I got it to compile ok by initializing the variables outside the class.  The problem is that I am still not getting the variables cars and amount to increment. With static, shouldn't the count keep incrementing by one each time the function is called?  I keep getting 0 and 0.0 for my output.

---

### Post by dwhitney67 on 2009-03-30
You are reading in a character, and comparing it to a numeral.  Try comparing the character to um, a character (e.g. '0', '1', etc).

The menu choices and the implementation that is associated with the choices does not jive; '1' is for a car that pays, '0' is for one that does not.  Your implementation states otherwise.

Also, unless you plan to design a "road-way system" with multiple toll-booths, I do not see the need to have statically declared variables within the class.

P.S.  The menu should be displayed again and again, after each user input is accepted.

---

