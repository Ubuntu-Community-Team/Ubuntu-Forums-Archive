---
title: "Anyway to loop C++ code so it'll restart from a certain line?"
date: 2011-03-12
forum: Programming Talk
---

### Post by dongk on 2011-03-12
Hi,

So basically I'm trying to make the following code repeat it self from the "Enter a number" line. Is there any way to do this? Also for some reason whenever I put in a decently large number (ie 30,000,000 and up) it'll come out to -858,993,460. I'm just starting to learn how to code, so no extremely technical speak please. It would be great if you could explain to me why my program exhibits this behavior, along with why the solution (that you provide) would fix it. I'm one of those stubborn type of person. So I've basically spent the last hour trying to get this program to work.

> #include "stdafx.h"
#include <iostream>

int main()
{
    using namespace std;
	cout << "The Doubling Machine" << endl;
    cout << "Enter a number: "; // ask user for a number
    int x;
    cin >> x; // read number from console and store it in x
// Display user input, display operation, performs operation, displays result, and prompts to terminate program.
    cout << "You entered " << x << endl;
	cout << x;
	cout << " * 2 = ";
	x = x * 2;
	cout << x << endl;
	cout << "Press 'Enter' to terminate this program.";
// Stops program from closing without user intervention. (Next 3 Lines)
	cin.clear();
	cin.ignore(255, '\n');
	cin.get();
    return 0;
}

Thanks

---

### Post by schauerlich on 2011-03-12
Your first problem: It's most likely an [integer overflow](http://en.wikipedia.org/wiki/Integer_overflow) error of some sort. The number you posted (858993460) looks a lot like 2^33 (8589934592) or 2 times the maximum number an integer can hold on most machines.

As for the looping, try using a "while" loop, and breaking if the user inputs some special value (such as 0). Any decent tutorial should show you how to do something like that.

---

### Post by cgroza on 2011-03-13
That is the sign of an integer overflow. It means that your machine can't keep a number that large into a simple int. You should try a long int or something.

The while loop will to the trick. You learn it among the first few things when you start.

---

### Post by hakermania on 2011-03-13
You can use a double or a float instead of an integer. There are a lot of types that can handle types in C so that no to waste a lot of uneeded memory.
For example, an int takes less memory than a float or a double, so, if you want to play with small numbers you'll use int and with large float/double.
For more info about the size (in memory) of all types see [http://www.cplusplus.com/doc/tutorial/variables/](http://www.cplusplus.com/doc/tutorial/variables/)
As for the loop, I will disagree in a way with the first answers. A for loop would be better, if you want to ask for a number X times:
```

int x=5
for(int i=0;i<x;i++){
//code
}

```

---

### Post by cgroza on 2011-03-13
> **hakermania said:**
> You can use a double or a float instead of an integer. There are a lot of types that can handle types in C so that no to waste a lot of uneeded memory.
For example, an int takes less memory than a float or a double, so, if you want to play with small numbers you'll use int and with large float/double.
For more info about the size (in memory) of all types see [http://www.cplusplus.com/doc/tutorial/variables/](http://www.cplusplus.com/doc/tutorial/variables/)
As for the loop, I will disagree in a way with the first answers. A for loop would be better, if you want to ask for a number X times:
```

int x=5
for(int i=0;i<x;i++){
//code
}

```
I disagree.
Why not let the user chose when to close? He can use a while loop like this:

```
while( ! cin.eof() ){//code here}

```

This will continue until the user will enter Ctrl+D in the input.

---

### Post by lisati on 2011-03-13
I agree with the others that the strange numbers sound a lot like integer overflow/wraparound. Is using an "unsigned" variable type an option?

For the other part of your question (repeating from a particular line), I agree that a "while" or "do" loop (or something of that nature) should do the trick. 

(Friendly aside: As a matter of programming style, I was taught that from the perspective of programming readability, something like "while (1)" is bad. This is largely because you shouldn't have to go feretting about inside the loop to figure out the circumstances that cause the loop to terminate.)

---

