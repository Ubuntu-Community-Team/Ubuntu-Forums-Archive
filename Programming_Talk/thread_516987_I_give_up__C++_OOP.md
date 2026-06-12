---
title: "I give up:  C++ OOP"
date: 2007-08-03
forum: Programming Talk
---

### Post by Yes on 2007-08-03
I tried teaching myself C++ OOP. but I seem to have failed miserably.  I tried making a program that would convert decimals to fractions and vise-versa, using a Fraction class and a Decimal class.  Here's the code and the errors I'm getting (There's also a ton of errors about strings...as you may be able to tell, it's also my first time using them as well):

Code:

```
#include <iostream>

#include <cstdlib>

#include <string>

using namespace std;

class Decimal {
		double decimal;
	public:
		//double decimal ();
};

Decimal::Decimal () 
{
	
	cout << "Please enter a decimal in the format x.y : " ;
	cin >> decimal;
}

class Fraction 
{
	public:
		int denominatorNum, numeratorNum;
		void convertFractionToDecimal(string);
};

 Fraction::Fraction () 
 {
 	string usersFraction;
 	
	cout << "Please enter a fraction in the format x/b ";
	cin >> usersFraction;
	convertFractionToDecimal (usersFraction);
}

void Fraction::convertFractionToDecimal (string fraction) 
{
	string denominatorChar, numeratorChar;
	int slashIndex = fraction.find('/', 0);
	
	numeratorChar = fraction.substr(0, fraction.length() - shashIndex);
	denominatorChar = fraction.substr(slashIndex+1, fraction.length());
	
	for (int i = 0; i < numeratorChar.length(); i++) 
	{
		for (int a = numeratorChar.length()-a; a < 0; a--) 
		{
			switch (numeratorChar.at(a)) {
				case '1': 
					numeratorNum+=1*10;
					break;
				case '2': 
					numeratorNum+=2*10;
					break;
				case '3': 
					numeratorNum+=3*10;
					break;
				case '4': 
					numeratorNum+=4*10;
					break;
				case '5': 
					numeratorNum+=5*10;
					break;
				case '6': 
					numeratorNum+=6*10;
					break;
				case '7': 
					numeratorNum+=7*10;
					break;
				case '8': 
					numeratorNum+=8*10;
					break;
				case '9': 
					numeratorNum+=9*10;
					break;		
			}		
		}
	}
	
	for (int i = 0; i < denominatorChar.length(); i++)
	{
		for (int a = denominatorChar.length()-a; a < 0; a--) 
		{
			switch (denominatorChar.at(a)) {
				case '1': 
					denominatorNum+=1*10;
					break;
				case '2': 
					denominatorNum+=2*10;
					break;
				case '3': 
					denominatorNum+=3*10;
					break;
				case '4': 
					denominatorNum+=4*10;
					break;
				case '5': 
					denominatorNum+=5*10;
					break;
				case '6': 
					denominatorNum+=6*10;
					break;
				case '7': 
					denominatorNum+=7*10;
					break;
				case '8': 
					denominatorNum+=8*10;
					break;
				case '9': 
					denominatorNum+=9*10;
					break;		
			}		
		}
	}
	
	cout << "\n\nThe decimal form of " << numeratorNum << "/" << denominatorNum 
			<< " is " << numeratorNum/denominatorNum << ".\n" << endl;
			
	system("pause");
}
	

int main()
{
	int userChoice;
	Fraction fraction;
	
	cout << "Welcome to the Fraction Decimal Converter!  Your options are:" << endl;
	cout << "\n1. Convert a decimal to a fraction." << endl;
	cout << "2. Convert a fraction to a decimal." << endl;
	cout << "3. Quit." << endl;
	cout << "\nPlease enter the number for what you want to do: " ;
	cin >> userChoice;
	
	switch (userChoice) {
		
		case 1:
			Decimal decimal ();
			break;
		case 2:
			Fraction fraction ();	
	}
	
	return 0;
}
```

Errors:
```
/home/alex/C++ Files/FractionDecimalConverter.cpp:36: error: definition of implicitly-declared &#8216;Decimal::Decimal()&#8217;
/home/alex/C++ Files/FractionDecimalConverter.cpp:36: error: declaration of &#8216;Decimal::Decimal()&#8217; throws different exceptions
/home/alex/C++ Files/FractionDecimalConverter.cpp:30: error: from previous declaration &#8216;Decimal::Decimal() throw ()&#8217;
/home/alex/C++ Files/FractionDecimalConverter.cpp:50: error: definition of implicitly-declared &#8216;Fraction::Fraction()&#8217;
/home/alex/C++ Files/FractionDecimalConverter.cpp:50: error: declaration of &#8216;Fraction::Fraction()&#8217; throws different exceptions
/home/alex/C++ Files/FractionDecimalConverter.cpp:44: error: from previous declaration &#8216;Fraction::Fraction() throw ()

```

Also, let me know of any bad programming practices I'm using.  I'm pretty sure that my tabs are wrong, for one thing.

Thanks.

Edit:  I think I fixed the string-related issues.  I've updated the errors and the code.

---

### Post by pmasiar on 2007-08-04
If C++ is your first language and you are self-learner - you tried to bite too much. Try Python first 9links in my sig), *then* C++ will be easier and make more sense (and some parts of C++ will feel after Python like unnecessary hassle, but... yes they are :-) )

---

### Post by Dancingwllamas on 2007-08-04
Your main problem is that you have not declared the constructor ([http://www.fredosaurus.com/notes-cpp/oop-condestructors/constructors.html](http://www.fredosaurus.com/notes-cpp/oop-condestructors/constructors.html)) functions (that is what Decimal() and Fraction() are called) within your class. You need to put the lines "Decimal()" under public in your Decimal Class and "Fraction()" under public in your fraction class. The compiler is complaining because you are defining functions without declaring they are there.

Additionally, there is a misspelling in the convertToDecimal() function. On the third statement, make sure that slashIndex is spelled correctly.

The file should be able to compile now. Hope this helps.

---

### Post by slavik on 2007-08-04
> **Dancingwllamas said:**
> Your main problem is that you have not declared the constructor ([http://www.fredosaurus.com/notes-cpp/oop-condestructors/constructors.html](http://www.fredosaurus.com/notes-cpp/oop-condestructors/constructors.html)) functions (that is what Decimal() and Fraction() are called) within your class. You need to put the lines "Decimal()" under public in your Decimal Class and "Fraction()" under public in your fraction class. The compiler is complaining because you are defining functions without declaring they are there.

Additionally, there is a misspelling in the convertToDecimal() function. On the third statement, make sure that slashIndex is spelled correctly.

The file should be able to compile now. Hope this helps.
to reiterate about the constructor stuff, in the decimal class, you only have the private member. in the declaration of the constructor, you told it that it belongs in the Decimal class, but not where exactly in Decimal class (public, private, protected). same with the Fraction constructor

---

### Post by badactress on 2007-08-04
Hi,

Hopefully this is a working version of your code :) Done early before even my 2nd cup of coffee so please forgive any stupid errors that could be lurking! :p

I'm trying to remember what I changed now!! 

You were defining your own constructors for the classes, but not declaring them in the class declaration. I added deconstructors too just because it's good practice. They don't actually do anything in this case so could just as easliy not be there.

The code for getting user input for the classes was inside the constructor. This means it would be called as soon as you declared an instance of the class at the beginning of main. I moved it to a separate class function so it can be called when you need it.

It compiled fine at this point, and correctly extracted the numerator & denominator from the string input, but was core-dumping somewhere in or after your case->switch statements. Instead of fixing them, I cheated and replaced them with the sstream functions (which you gotta read up on cos they're very useful!) to convert the string characters into integers.

Finally, it's a bit dirty, but I used cast to convert the ints to pointers to get the correct output.

Hope this helps :)


```

#include <iostream>
#include <cstdlib>
#include <string>
#include <sstream>

using namespace std;

class Decimal {
	public:
		Decimal();
		~Decimal();
		//double decimal ();
		void userinput();
		double decimal;
		
	protected:

};

Decimal::Decimal() 
{

}

Decimal::~Decimal()
{
	
}

void Decimal::userinput()
{
	cout << "Please enter a decimal in the format x.y : " ;
	cin >> decimal;
}
	

class Fraction 
{
	public:
		Fraction();
		~Fraction();
		void convertFractionToDecimal(string);
		void userinput();
		
	protected:
		int denominatorNum;
		int numeratorNum;
};

Fraction::Fraction () 
{

}

Fraction::~Fraction()
{
	
}

void Fraction::userinput()
{
	 	string usersFraction;
 	
	cout << "Please enter a fraction in the format x/b ";
	cin >> usersFraction;
	convertFractionToDecimal (usersFraction);
}

void Fraction::convertFractionToDecimal (string fraction) 
{
	string denominatorChar, numeratorChar;
	int slashIndex = fraction.find('/', 0);

	numeratorChar = fraction.substr(0, fraction.length() - slashIndex);
	denominatorChar = fraction.substr(slashIndex+1, fraction.length());

    std::stringstream SN(numeratorChar);
    SN >> numeratorNum;
    
    std::stringstream SD(denominatorChar);
    SD >> denominatorNum;
	
	cout << "\n\nThe decimal form of " << numeratorNum << "/" << denominatorNum 
			<< " is " << (float)numeratorNum/(float)denominatorNum << ".\n" << endl;
}
	

int main()
{
	int userChoice;
	Fraction fraction;
	Decimal decimal;
	
	cout << "Welcome to the Fraction Decimal Converter!  Your options are:" << endl;
	cout << "\n1. Convert a decimal to a fraction." << endl;
	cout << "2. Convert a fraction to a decimal." << endl;
	cout << "3. Quit." << endl;
	cout << "\nPlease enter the number for what you want to do: " ;
	cin >> userChoice;
	
	switch (userChoice) {
		
		case 1:
			decimal.userinput();
			break;
		case 2:
			fraction.userinput();	
	}
	
	return 0;
}

```

---

### Post by kpatz on 2007-08-04
Here's my go at fixing it.  I added comments to the parts I changed.

```
#include <iostream>

#include <cstdlib>

#include <string>

using namespace std;

class Decimal {
		double decimal;
	public:
		Decimal ();
		void getDecimal(void);
};

Decimal::Decimal()
{
 	// This is a constructor.  It is used to initialize the members
 	// of the Decimal class.
	decimal = 0;
}
void Decimal::getDecimal () 
{
 	// This was originally Decimal::Decimal().  I renamed it to
 	// Decimal::getDecimal(), since a class's constructor should only
 	// be used to initialize the class.
	cout << "Please enter a decimal in the format x.y : " ;
	cin >> decimal;
}

class Fraction 
{
	public:
        Fraction();
		int denominatorNum, numeratorNum;
		void convertFractionToDecimal(string);
		void getFraction(void);
};

 Fraction::Fraction()
 {
 	// This is a constructor.  It is used to initialize the members
 	// of the Fraction class, since a class's constructor should only
 	// be used to initialize the class.
 	numeratorNum = 0;
 	denominatorNum = 0;
 }
 
 void Fraction::getFraction (void) 
 {
 	// This was originally Fraction::Fraction().  I renamed it to
 	// Fraction::getFraction().
 	string usersFraction;
 	
	cout << "Please enter a fraction in the format x/b ";
	cin >> usersFraction;
	convertFractionToDecimal (usersFraction);
}

void Fraction::convertFractionToDecimal (string fraction) 
{
	string denominatorChar, numeratorChar;
	int slashIndex = fraction.find('/', 0);
	
	numeratorChar = fraction.substr(0, slashIndex);
	denominatorChar = fraction.substr(slashIndex+1, fraction.length() - slashIndex - 1);
	// I fixed this code, but there are much better ways to do this...
	for (int i = 0; i < numeratorChar.length(); i++) 
	{
		numeratorNum *= 10;
		switch (numeratorChar.at(i)) {
			case '1': 
				numeratorNum+=1;
				break;
			case '2': 
				numeratorNum+=2;
				break;
			case '3': 
				numeratorNum+=3;
				break;
			case '4': 
				numeratorNum+=4;
				break;
			case '5': 
				numeratorNum+=5;
				break;
			case '6': 
				numeratorNum+=6;
				break;
			case '7': 
				numeratorNum+=7;
				break;
			case '8': 
				numeratorNum+=8;
				break;
			case '9': 
				numeratorNum+=9;
				break;		
		}		
	}
	
	for (int i = 0; i < denominatorChar.length(); i++)
	{
		denominatorNum *= 10;
		switch (denominatorChar.at(i)) {
			case '1': 
				denominatorNum+=1;
				break;
			case '2': 
				denominatorNum+=2;
				break;
			case '3': 
				denominatorNum+=3;
				break;
			case '4': 
				denominatorNum+=4;
				break;
			case '5': 
				denominatorNum+=5;
				break;
			case '6': 
				denominatorNum+=6;
				break;
			case '7': 
				denominatorNum+=7;
				break;
			case '8': 
				denominatorNum+=8;
				break;
			case '9': 
				denominatorNum+=9;
				break;		
		}		
	}
    // Checking for zero here is a Good Idea.
	if (denominatorNum == 0)
	  cout << "\n\nInvalid fraction, denominator cannot be zero." << endl;
	else
	  cout << "\n\nThe decimal form of " << numeratorNum << "/" << denominatorNum 
			<< " is " << (float)numeratorNum/(float)denominatorNum << ".\n" << endl;
			
	//system("pause");  This doesn't work anyway so I removed it
}
	

int main()
{
	int userChoice;
	Fraction fraction;
	Decimal decimal;
	
	cout << "Welcome to the Fraction Decimal Converter!  Your options are:" << endl;
	cout << "\n1. Convert a decimal to a fraction." << endl;
	cout << "2. Convert a fraction to a decimal." << endl;
	cout << "3. Quit." << endl;
	cout << "\nPlease enter the number for what you want to do: " ;
	cin >> userChoice;
	
	switch (userChoice) {
		
		case 1:
			decimal.getDecimal();
			break;
		case 2:
			fraction.getFraction();
	}
	
	return 0;
}

```

Some tips:

1.  As others have mentioned, you forgot to declare the constructor in the class.

2.  The constructor should only initialize the class.  You'll see in my version that the Fraction constructor sets the values to zero.  This prevents random data from ending up in your fractions.

3.  The function to prompt the user for input has been moved out of the constructor, into another function, which is called.

4.  I fixed up your fraction parsing code to enable it to work, but there are far easier and better ways to do it.  I'll leave that as an exercise.

5.  I added code to detect when the denominator is zero, to prevent the program crashing if you enter something like 2/0 as a fraction.

---

