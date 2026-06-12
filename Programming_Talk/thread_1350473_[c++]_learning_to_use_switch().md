---
title: "[c++] learning to use switch()"
date: 2009-12-09
forum: Programming Talk
---

### Post by karimruan on 2009-12-09
I mainly plan to use c++ for making console games for linux and other console apps (for linux). I learn best by jumping write into getting a project started and going until it is working and finished! So, to learn to use switch, I am creating a useless program that asks you to look up or down, and then prints "You look up" or "You look down", depending on input.

I don't really understand the code I wrote, I use other peoples source code as a base for my learning, and try to rewrite it and expand on it. Here is what I have so far...

```


#include <iostream>
#include <string>
using namespace std;




int main()
{
	int 1, 2;
	cout << "You can either 1. look up, or 2. look down\n";
	cin >> number;
	switch()int))
	{
		case 1: cout << "You look up!\n";
		case 2: cout << "You look down!\n";
		break;
		default: cout << "You must pick either 1 or 2 \n";
		break;
	}
	return 0;
}

```

The problem is that when the user chooses '1' it prints both:
You look up
You look down

choosing 2 just prints;
you look down.

Any ideas?


EDIT: In geany, I can execute the code, and get this message. But if I build the code, I get the following errors:

```

test.cpp: In function &#8216;int main()&#8217;:
test.cpp:32: error: expected unqualified-id before numeric constant
test.cpp:34: error: &#8216;number&#8217; was not declared in this scope
test.cpp:35: error: expected primary-expression before &#8216;)&#8217; token
test.cpp:35: error: expected unqualified-id before &#8216;)&#8217; token
mat@mat-laptop:~$ 

```

---

### Post by MadCow108 on 2009-12-09
you have a syntax error
switch()int))
should be
switch(number)

to get only one output when you enter 1 you need a break after the: case 1:

if you have troubles with switch use if, else if, else
they have a more natural syntax and perform the same

---

### Post by dwhitney67 on 2009-12-09
And you need a break statement after...
```

case 1: cout << "You look up!\n";

```

---

### Post by Xyro on 2009-12-09
The fact that it executes for both cases is actually quite handy, for example:

```
char c;

cin >> c;

switch ( c ) {
  case 'h':
  case 'H':
  case '?':
    executeHelpFunction();
    break;
  case 'q':
  case 'Q':
    executeQuitFunction();
    break;
  default:
    cout << "Don't know what you mean!" << endl;
    break;
}
```

The result here would be that if c is equal to 'h', or 'H', or '?', the executeHelpFunction() would be run. Likewise, 'q' or 'Q' will result in executeQuitFunction() to be run. The 'case' keyword is ike an entry point in the switch statement for the program to start executing. It goes down the list of cases, and when it finds the one that fits, it starts executing until it hits a 'break' statement (or the end of the switch) and then continues beyond the switch.

EDIT: Also, you've not declared 'number', which is where the "test.cpp:34: error: &#8216;number&#8217; was not declared in this scope" error is coming from. So stick an "int number;" where you have "int 1,2;". Remember, variable names cannot begin with an digit.

---

### Post by Can+~ on 2009-12-09
```
int 1, 2;
```

You can't name variables as numbers. In fact, I think you got the wrong idea of variable declaration. This doesn't declare 1 and 2 as possible things for switch-case, it just creates variables.

```
cin >> number;
```

Number was never declared.

```
	switch()int))
```

That line doesn't make sense. Switch takes a variable name, not a type definition. And the parenthesis are all wrong, should be [FONT="Courier New"][COLOR="#00AAFF"]switch[/COLOR](variable)[/FONT]

```
		case 1: cout << "You look up!\n";
		case 2: cout << "You look down!\n";
		break;
```

Switch behaves as a "cascade", it goes from top to bottom, if something matches, it will start executing everything until it finds a break, or the switch block ends.

The corrected code is:

[PHP]#include <iostream>
#include <string>

using namespace std;

int main()
{
	int number;
	cout << "You can either 1. look up, or 2. look down" << endl;
	cin >> number;
	
	switch(number)
	{
		case 1: cout << "You look up!"  << endl; break;
		case 2: cout << "You look down!"  << endl; break;
		default: cout << "You must pick either 1 or 2"  << endl; break;
	}
	
	return 0;
}[/PHP]

---

### Post by karimruan on 2009-12-10
> **Can+~ said:**
> ```
int 1, 2;
```

You can't name variables as numbers. In fact, I think you got the wrong idea of variable declaration. This doesn't declare 1 and 2 as possible things for switch-case, it just creates variables.

```
cin >> number;
```

Number was never declared.

```
	switch()int))
```

That line doesn't make sense. Switch takes a variable name, not a type definition. And the parenthesis are all wrong, should be [FONT="Courier New"][COLOR="#00AAFF"]switch[/COLOR](variable)[/FONT]

```
		case 1: cout << "You look up!\n";
		case 2: cout << "You look down!\n";
		break;
```

Switch behaves as a "cascade", it goes from top to bottom, if something matches, it will start executing everything until it finds a break, or the switch block ends.

The corrected code is:

[PHP]#include <iostream>
#include <string>

using namespace std;

int main()
{
	int number;
	cout << "You can either 1. look up, or 2. look down" << endl;
	cin >> number;
	
	switch(number)
	{
		case 1: cout << "You look up!"  << endl; break;
		case 2: cout << "You look down!"  << endl; break;
		default: cout << "You must pick either 1 or 2"  << endl; break;
	}
	
	return 0;
}[/PHP]


thanks can, that helped alot! the switch()int)) thing was a typo, but now i know the code i was trying to type would have been wrong anyway!

---

