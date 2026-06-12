---
title: "cross platform c++ newb question"
date: 2008-04-09
forum: Programming Talk
---

### Post by iansane on 2008-04-09
Hi, this is newb stuff probably. I wrote a simple program to average 3 numbers.

The end asks for user to press enter to quit.

the code
```
cin.ignore(cin.rdbuf()->in_avail() + 1 )
```followed by```
 cin.get() 
```
tells it to wait for the user to press enter.

I halfway understand the use of ignore to ignore the last "ENTER" in the stream but to compile for Windows, I have to take out the "+ 1". Otherwise the user has to hit ENTER twice in windows if I use the same code.

My question is: Is there some reason that linux terminal is adding and extra "ENTER" or white space that has to be ignored, that is not present in Windows command line? Also is this just part of terminal that I will need to always keep in mind and allow for in other apps when writing for both platforms?

Thanks

---

### Post by dwhitney67 on 2008-04-09
I don't quite understand what the problem is that you are having.  If I run this code under linux, I have to press the carriage-return (enter key) twice to exit.
[PHP]#include <iostream>

using namespace std;

int main()
{
  cin.ignore( cin.rdbuf()->in_avail() + 1 );
  cin.get();
  return 0;
}[/PHP]
If I take out the "+ 1", then all I have to do is press the carriage-return once.  Is this not the same behavior you describe for windows?

P.S.  I do not have a windows system, so I cannot test the code above on that particular OS.

---

### Post by iansane on 2008-04-09
that is the behavior I get in windows (two times if the + 1 is left in.)

In Ubuntu, I only press the enter key once.(with the +1 left in)

If I take out the "+ 1", in Windows it works with only one press of the enter key

If I take out the "+ 1" in Ubuntu, it closes the program without waiting for me to press the enter key. It acts as if the line of code isn't there unless I include the "+ 1"

Thats why I ask if Ubuntu terminal is adding an extra blank space in the extraction stream for some reason.

Here is the code for the whole thing. This works in Ubuntu with only one carriage-return

```
 //Program:     Average Score

//Author:      Ian Simmons



/*Description: This program takes 3 numbers from the user, one at a time, and then outputs the average of the three numbers.*/

               

#include <iostream>

using namespace std;



int main()



{

	long int numone;

	long int numtwo;

	long int numthree;

	long int numTotal;

	long int numAverage;

	

	//input numbers

	cout << "Hello. To get an average, start by typing in the first number and pressing enter. " << endl;

	cin >> numone;

	

	cout << "Now please enter the second number" << endl;

	cin >> numtwo;

	

	cout << " And the third number? " << endl;

	cin >> numthree;

	

	//process

	numTotal= numone + numtwo + numthree;

	numAverage= numTotal/3;

	
	//output

	cout << "The average of the three numbers you entered is " << endl;

	cout << numAverage << endl;

	

			

	

	//press enter to exit

	cout << "To close the program press the enter key. To enter another set of numbers, upgrade to the next release :-)\n" << endl;

	
	/*"ignore" instructs to ignore the last extraction from cin
	otherwize, "cin.get()" will read the last "enter press" and 
	except it, appearing to ignore the line of code and close.
	In order for this to work in linux, the user has to press the enter
	key twice in windows. This is a known compatibility issue that will
	be worked out later*/


	cin.ignore(cin.rdbuf()->in_avail() + 1);

	cin.get();

	

	return 0;

	}

	

	

	



```

---

### Post by dwhitney67 on 2008-04-09
Ok, now I understand. Try something like this (i.e. gobble up the carriage return that is present after you have inputted your data):
[PHP]#include <iostream>

using namespace std;

int main()
{
  int value = 0;

  cout << "Enter a value:  ";
  cin >> value;
  cin.get();   // gobble up carriage return

  cout << "Press <enter> to continue...";
  //cin.ignore( cin.rdbuf()->in_avail() );
  cin.get();

  return 0;
}[/PHP]

---

### Post by iansane on 2008-04-09
Wow that evened it out.

Now with both linux and windows it works without the + 1

So now I'm assuming that in windows, it throws that return away by default but not in linux?

Anyway, that fixed it and I'll just always clear the stream after the last user input as a safety. Unless for some reason I need the last return to be there.

Thank you for setting me straight. This is confusing to me as a newb.

---

