---
title: "Can't seed the random generator"
date: 2007-05-07
forum: Programming Talk
---

### Post by Shack_ on 2007-05-07
I'm just getting into programming with C++. So far, everything has worked well, except for this particular issue.

I'm trying to seed the random generator with the system time by using the  following command:

```
srand ( time(NULL) );
```

But for some reason when I compile the program (then run it from a terminal [it's text-based]) the following error message pops up:

```
Program has been terminated receiving signal 11 (Segmentation fault)
```

First of all, what does that mean? And second of all, how do I fix it?

---

### Post by amo-ej1 on 2007-05-07
Well this code works perfectly

```

#include <stdlib.h>
#include <time.h>

int main(int argc, char **argv)
{
    srand(time(NULL));
}

```

So probably your error lies elsewhere. It could be usefull to provide us with the rest of your code, this will make it easier to pinpoint your error.

A segmentation fault is a signal that your process receives when the system detects that you program is accessing memory that was not allocated to it. Typically this happens with uninitialized pointers, or when overflowing buffers. The easiest way to get a segmentation fault is when you try to dereference a NULL pointer. 

In order to trace your error do the following. Given the following code, which returns a segmentation fault:

```

#include <stdlib.h>
#include <time.h>
#include <stdio.h>

int main(int argc, char **argv)
{
    srand(time(NULL));
    int * nullpointer = NULL;
    printf("%d\n", *nullpointer);

    return 0;
}

```

(This gives a segmentation fault because you try to dereference a NULL pointer)

Compile it with debugging signals enabled (the -g switch)

```

e@lap:/tmp$ gcc -g -Wall test.c 

```

Now run it through gdb:

```

e@lape:/tmp$ gdb a.out
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) run
Starting program: /tmp/a.out 

Program received signal SIGSEGV, Segmentation fault.
0x08048413 in main () at test.c:9
9           printf("%d\n", *nullpointer);
(gdb) where
#0  0x08048413 in main () at test.c:9

```

This clearly illustrates the error occurs at line 9.

---

### Post by Zdravko on 2007-05-07
In C/C++ I use:
> 
#include <ctime>
#include <cstdlib>
/*...*/
srand((unsigned)(rand() + clock() + time(0)));


---

### Post by Shack_ on 2007-05-07
Here's my program (it's far from complete). I seed the random generator in the function "GenerateWordToGuess()", and I tried to test it by assigning the variable "thing" to a random number.


```
//Hangman
//A text-based version of the classic word-guessing game
//Written by Bryan Verble on May 5, 2007

#include <iostream>
#include <string>
#include <strings.h>
#include <ctime>
#include <cstdlib>

using namespace std;

void Instructions() { 
	
	//Define the answer
	string answer;
	//Give question
	cout << "Welcome to Hangman. Would you like instructions? ";
	cin >> answer;
	
	//Start the instruction loop
	while (answer == "yes" || answer == "Yes" || answer == "YES") { 
	
		//Get answer
		//cin >> answer;
		//If answer is yes, give instructions
		if (answer == "yes" || answer == "Yes" || answer == "YES") { 
			cout << "\n";
			cout << "To play, all you have to do is enter a letter to guess.";
			cout << "Please use lowercase letters only.";
			cout << "If the answer is correct, it will be added to the display.";
			cout << "If the answer is incorrect, you will have one less guess, ";
			cout << "and the letter will be added to the incorrectly guessed";
			cout << " display.";
			cout << "\n \n Do you need these instructions repeated? ";
			
			//Get answer again
			cin >> answer;
		}
		
	}
	
}

string GenerateWordToGuess() { 
	
	//Seed the random generator
	srand ( time(NULL) );
	int thing;
	thing = rand();
	cout << thing;
	
}


int main() { 
	
	//Ask the user if they want instructions
	Instructions();
	//Pick the word to guess for
	GenerateWordToGuess();
	
}

```

I hope this helps.

---

### Post by Shack_ on 2007-05-07
Never mind. I just figured out what went wrong.

---

### Post by WW on 2007-05-07
Your function GenerateWordToGuess() is supposed to return a string, but it reaches the end of the function without returning anything. If you use the **-Wall** option to g++, the compiler will warn you about this.  I don't know enough about g++ to know why this causes a seg. fault, but if you add something as simple as
```

    return "";

```
to the end of the function, it should work.

EDIT:
> Never mind. ...
Too late :)

---

