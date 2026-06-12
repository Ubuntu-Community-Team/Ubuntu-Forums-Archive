---
title: "C++ read the Enter key"
date: 2009-10-09
forum: Programming Talk
---

### Post by myromance123 on 2009-10-09
Ok I know this is probably really basic but whats the  (i think its called escape character) I use to capture the press of the Enter key in C++?

 This problem stemmed from the silly #include <conio.h> from this book thats supposedly multi-platform codewise...

 Is it '\r'  ??

If it is then I have a bigger problem with my loop but for now please help me confirm that ( I did google but found nothing).

Thanks in Advance

---

### Post by SouthOfHell on 2009-10-09
```
fgetc(stdin);
```

---

### Post by myromance123 on 2009-10-09
I'm guessing here but you wanted me to replace my method of taking input with fgetc(stdin) right?
 no can do, changes nothing.

here's my code, maybe someone will understand ?
```
#include <iostream>
#include <sstream>
//#include <conio.h>
#include "functions.h"


string EnterOnlyNumbers()
{
    string numAsString = ""; //Holds the numeric string
    char ch = getch();

    //keep requesting characters until the user presses  Enter
    while (ch != '\r') // '\r' is the enter key
    {
        // Add characters only if they are numbers.
        if (ch >= '0' && ch <= '9')
        {
            cout << ch;
            numAsString += ch;
        }

        // Get the next character from the user
        ch = getch();
    }
    return numAsString;
}

string EnterPassword()
{
    string numAsString = ""; //holds the password string
    char ch = getch();

    while ( ch != '\r')
    {
        cout << '*';

        numAsString += ch;

        ch = getch();
    }

    return numAsString;
}

```

<conio.h> will not compile as I have recently found out its for DOS (really retarded for dummies books this one is).

I tried replacing getch() with  cin.get() but to no avail. 
my problem here is that when I press Enter it should stop the function EnterOnlyNumbers and continue to the Password part (as written in main.cpp).
 Instead it accepts the Enter key and prints it out... and thus never moves onto the EnterPassword function.

---

### Post by Arndt on 2009-10-09
> **myromance123 said:**
> I'm guessing here but you wanted me to replace my method of taking input with fgetc(stdin) right?
 no can do, changes nothing.

here's my code, maybe someone will understand ?
```
#include <iostream>
#include <sstream>
//#include <conio.h>
#include "functions.h"


string EnterOnlyNumbers()
{
    string numAsString = ""; //Holds the numeric string
    char ch = getch();

    //keep requesting characters until the user presses  Enter
    while (ch != '\r') // '\r' is the enter key
    {
        // Add characters only if they are numbers.
        if (ch >= '0' && ch <= '9')
        {
            cout << ch;
            numAsString += ch;
        }

        // Get the next character from the user
        ch = getch();
    }
    return numAsString;
}

string EnterPassword()
{
    string numAsString = ""; //holds the password string
    char ch = getch();

    while ( ch != '\r')
    {
        cout << '*';

        numAsString += ch;

        ch = getch();
    }

    return numAsString;
}

```

<conio.h> will not compile as I have recently found out its for DOS (really retarded for dummies books this one is).

I tried replacing getch() with  cin.get() but to no avail. 
my problem here is that when I press Enter it should stop the function EnterOnlyNumbers and continue to the Password part (as written in main.cpp).
 Instead it accepts the Enter key and prints it out... and thus never moves onto the EnterPassword function.

You want '\n'.

---

### Post by myromance123 on 2009-10-09
Thanks, I thought the enter key wasn't '\r'.
 Although there's still a problem.

I get this output when running the program and coming up to using the EnterOnlyNumbers() function:
```
This time you'll only be able to enter a number!
Enter a number, any number!
You entered -1209187616
```

That seems to happen from pressing Enter in my previous function, so I'm guessing input isn't being cleared out before it reaches the EnterOnlyNumbers() function so it immediately bypasses the loop (although I'm not sure where those numbers came from, maybe somewhere in memory).
 What should I do to clear out the input before trying to fetch new input?
or is this not the problem?

---

### Post by Arndt on 2009-10-09
> **myromance123 said:**
> Thanks, I thought the enter key wasn't '\r'.
 Although there's still a problem.

I get this output when running the program and coming up to using the EnterOnlyNumbers() function:
```
This time you'll only be able to enter a number!
Enter a number, any number!
You entered -1209187616
```

That seems to happen from pressing Enter in my previous function, so I'm guessing input isn't being cleared out before it reaches the EnterOnlyNumbers() function so it immediately bypasses the loop (although I'm not sure where those numbers came from, maybe somewhere in memory).
 What should I do to clear out the input before trying to fetch new input?
or is this not the problem?

I see none of those strings in your program, so I can't say what the problem is.

---

### Post by myromance123 on 2009-10-09
Oh ! Sorry, here's main (I separated them to different source files).

```
#include <iostream>
#include <sstream>
//#include <conio.h>
#include "functions.h"

using namespace std;

int main()
{
    string name;
    cout << "What is your name? " ;
    cin >> name;

    cout << "Hello " << name << endl;

    int x;
    cout << endl;
    cout << "enter a number, any number";
    cin >> x;
    cout << "You chose " << x << endl;

    //This time you can only enter a number
    cout << endl;
    cout << "This time you'll only be able to enter a number!"<< endl;
    cout << "Enter a number, any number! " ;
    string entered = EnterOnlyNumbers();
    int num = StringToNumber(entered);
    cout << endl << "You entered " << num << endl;

    //now enter a password
    cout << endl;
    cout << "Enter a password!";
    string password = EnterPassword();
    cout << endl << "Shhh, its " << password << endl;

    return 0;
}
```

---

### Post by dwhitney67 on 2009-10-09
A lot of newbies to C++ come across the same issue you are having with respect to inputting data.

When inputting a number, say for instance 10, one would enter 1, then 0, and then finally <return>.  The last entry is interpreted as a '\n' character by the program.

Now, when cin is told to read a number, it happily obliges by parsing the input stream an it acquires the 1 and 0, thus magically formulating the number 10.  The newline, or '\n', is left on the input stream since it is obvious it is not part of the number.

If after, the program attempts to read a string, cin once again will happily oblige by doing such... although it will not need to wait for user input.  The reason is because a newline character is sitting there in the input stream from the previous entry (the 10).

The moral of the story, when performing terminal input of mixed data types (ie ints, floats, strings), employ the use of cin.ignore() to rid the input stream of unwanted newline characters.

For example:
```

int    num = 0;
string str;

cout << "Enter a number: ";
cin  >> num;
cin.ignore(100, '\n');    // discard chars until new line found

cout << "Enter a string: ";
cin  >> str;

...

```
Btw, fgetc() is wonderful in C.  Don't use it in C++; there are other alternatives.

---

### Post by MadCow108 on 2009-10-09
this will query until a valid number is entered
```
#include <iostream>
#include <limits>
using namespace std;

double GetNumber()
{
	double in;
	do {
		if (cin.fail()) {
			cout << "no number!" << endl;
			cin.clear();
			cin.ignore(numeric_limits<streamsize>::max(), '\n');
		}
		cout << "enter number: " << flush;
		cin >> in;
	} while (cin.fail());
	return in;
}

int main (int argc, char *argv[])
{
	cout << GetNumber() << endl;
	return 0;
}

```

---

