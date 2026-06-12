---
title: "Reset variables in C++?"
date: 2008-02-27
forum: Programming Talk
---

### Post by fourthdimension on 2008-02-27
Hey

I'm writing a small program in C++.  What I want it to do is spit out random binary until it is terminated (kind of like one of those hacker movies. lol).  The code I have now works, but I have to create a new variable for each number I want displayed.  Is there a way to reset the variable after each use so I can use just one variable in an infinite loop?  Here's what I have now:
```
#include <cstdlib>
#include <iostream>

using namespace std;
int main (int argc, char** argv)
{	
	static const int MAX = 2;
	const int number, number2, number3, number4, number5 /*etc*/ = rand() % MAX;
		while (number == number)
	{
		cout<< number <<number2 <<number3 <<number5 /*etc*/;		
	}
		return 0;
}



```
Like I said, this code works (although I'll be the first to admit it's ugly), I'd like to achieve a better effect by using one single random variable and just resetting it after each use so that another random value is stored in it.  How would I do that?
Thanks a lot.

---

### Post by WW on 2008-02-27
You could just do this:
```
#include <cstdlib>
#include <iostream>

using namespace std;

int main (int argc, char** argv)
{	
static const int MAX = 2;

while (1)
    {
    cout  << rand() % MAX;
    }
return 0;
}
```

---

### Post by dwhitney67 on 2008-02-27
Also consider seeding the random number generator.

[PHP]
#include <cstdlib>
#include <ctime>
...

int main()
{
  srand( time(0) );
  ...
}[/PHP]

---

