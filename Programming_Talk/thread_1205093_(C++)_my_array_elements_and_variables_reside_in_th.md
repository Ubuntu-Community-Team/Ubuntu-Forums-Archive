---
title: "(C++) my array elements and variables reside in the same memory addresses..."
date: 2009-07-05
forum: Programming Talk
---

### Post by sp0tz on 2009-07-05
```
//math test
//a program that asks a lot of math questions, then records your answers
//it's fun.

#include <iostream>
#include <cstdlib>
#include <ctime>
#include <string>
#include <fstream>
using namespace std;


int main(){
	srand((unsigned)time(0));
	int questions[4][1];
	int answer_sane=0;
	int operation=0;
	#define ADDITION 		1
	#define SUBTRACTION 	2
	#define MULTIPLICATION 	3
	#define DIVISION 		4
	#define ANSWERED_CORRECTLY 0
	#define ANSWERED_INCORRECTLY 1
	questions[MULTIPLICATION][ANSWERED_CORRECTLY]=0;
	questions[DIVISION][ANSWERED_CORRECTLY]=0;
	questions[ADDITION][ANSWERED_CORRECTLY]=0;
	questions[SUBTRACTION][ANSWERED_CORRECTLY]=0;
	questions[MULTIPLICATION][ANSWERED_INCORRECTLY]=0;
	questions[DIVISION][ANSWERED_INCORRECTLY]=0;
	questions[ADDITION][ANSWERED_INCORRECTLY]=0;
	questions[SUBTRACTION][ANSWERED_INCORRECTLY]=0;

	cout<<"before:";
	cout<<endl<<questions[DIVISION][ANSWERED_CORRECTLY];
	cout<<endl<<questions[DIVISION][ANSWERED_INCORRECTLY];
	cout<<endl<<questions[MULTIPLICATION][ANSWERED_INCORRECTLY];

	answer_sane=55555;
	operation=44444;

	cout<<endl<<"after:";
	cout<<endl<<questions[DIVISION][ANSWERED_CORRECTLY];
	cout<<endl<<questions[DIVISION][ANSWERED_INCORRECTLY];
	cout<<endl<<questions[MULTIPLICATION][ANSWERED_INCORRECTLY];

	cout<<endl<<"memory addresses:"<<endl;
	cout<<endl<<&questions[DIVISION][ANSWERED_CORRECTLY];
	cout<<endl<<&questions[MULTIPLICATION][ANSWERED_INCORRECTLY];
	cout<<endl<<&operation;
	cout<<endl<<"more addresses:"<<endl;
	cout<<endl<<&questions[DIVISION][ANSWERED_INCORRECTLY];
	cout<<endl<<&answer_sane;
	return 0;
}
```

This code is a small slice from a program I'm writing that asks a bunch of math questions, then records the answers and draws statistics from them (what percentage of multiplication questions you answer correctly, etc.). I've removed most of the code and edited what was left to highlight the problem here.

The odd thing is that the array elements "questions[DIVISION][ANSWERED_CORRECTLY]" and "questions[MULTIPLICATION][ANSWERED_INCORRECTLY]" reside at the same memory address. Furthermore, it's the same memory address that the variable "operation" resides at! *Furthermore* the array element "questions[DIVISION][ANSWERED_INCORRECTLY]" resides at the same address as the variable "answer_sane"...

I broke the problem down as far as I could, but I don't know where to go from here. Did I name these things incorrectly or something?

---

### Post by MadCow108 on 2009-07-05
because your array indizes are invalid.
you go over the boundaries
the first dimension has no element with index 4, the highest is 3
and the second dimension has the size 1 which makes it useless

set questions to questions[4][2]
and change ADD SUBSTRACTION etc definies from 1-4 to 0-3

also as you are using c++ use vectors instead of arrays...

---

### Post by sp0tz on 2009-07-05
Sure enough, that's fixed it. Thanks!

So, if you create (what I think is) an array, then assign a value to a nonexistent element, the value gets assigned to some random location in the memory allocated for the program?

Also, these are vectors and not arrays?

---

### Post by MadCow108 on 2009-07-05
if you write something over the boundary of an array it lands in a memory location which does not belong to the array.
the result is unpredictable as anything could be in that memory location. (in your case it was the value of another unrelated variable)

your using c arrays which is unnecessarily error prone.

in c++ you have a better alternative named vectors which handle allocation boundary checking, resizing and most important destruction for you. (and if used correctly just as fast)
[http://www.cplusplus.com/reference/stl/vector/](http://www.cplusplus.com/reference/stl/vector/)

an example of a more STL like version of your code (not necessarily the best):
```

#include <iostream>
#include <vector>
using namespace std;
int main (int argc, char *argv[])
{
	vector< pair<int,int> > questions;
	questions.resize(4);
	
	questions[0] = make_pair(1,4);
	
	std::cout <<"multiplication right:"<< questions[0].first <<" wrong: "<<questions[0].second << std::endl;
		
	return 0;
}

```

---

### Post by sp0tz on 2009-07-05
... thank you for the words. I will go find out what they mean.

---

### Post by monkeyking on 2009-07-05
Yes I use vector extensively,
its very usefull.

If you are using it for large amounts of data,
the trick is to use .reserve(max number of elements).

This will save all these nasty resizing you might otherwise experience.

But knowing and feeling at home with the old style arrays are essential.

For these out of bounds mistakes and checks,
valgrind is a very usefull tool

---

### Post by c0mput3r_n3rD on 2009-07-05
That code is harsh on the eyes man.

---

### Post by sp0tz on 2009-07-06
anything particularly harsh?

---

### Post by Volt9000 on 2009-07-06
Never put #defines into your function like that. All #defines should be at the top of the file, right after the #includes.

There's no spacing.
```

cout<<"This can be difficult to read"<<" especially when you "<<"concatenate multiple items"<<endl;
cout << "This is must easier to read" << " as there is spacing." << endl;

```

Having a multidimensional array like that is pointless; you could accomplish the same with a single dimensional array.

```

int questionsAnswered[4];

questionsAnswered[MULTIPLICATION] = 0;
questionsAnswered[ADDITION]++;

```

---

### Post by sp0tz on 2009-07-06
I agree with you on the spacing. Readable syntax has been a problem of mine for awhile, so thank you for reminding me to work on it.

However, the point of the multidimensional array was to hold a lot of data in one place. Maybe the small chunk of code I entered here isn't a good example but if the array includes one dimension for the operation and another for whether the question was answered correctly or not, it's going to be relatively easy to determine the % of multiplication questions answered correctly, what operation the user most commonly answers incorrectly/correctly, etc. The point of this array is to hold data to analyze the player's performance with, so being more detailed is better, I think.

Using the suggested array questionsAnswered[operation], we can't determine the player's aptitude for a given question type.

Later on, I was thinking I would add another array (or something) to keep track of things like how often the player got double-digit multiplication problems correct. This is advanced stuff that will need thorough blueprinting, but the idea is to keep a detailed record of the player's performance, so that the program is capable of doing something other than barraging the user with random math problems.

---

### Post by c0mput3r_n3rD on 2009-07-07
Yes you should always have your #define one line down from the #include statements.  As well, any time you use << or >> (input/output operator) you should always have a space before and after.

ex:
```
cout << "Hello World!" << std::endl;
```

Math operations and assignment are the same thing.
```
int a = 0;   
```
```
num1 = mu2 + num3;    
```

You can actually read about it here:  [http://www.possibility.com/Cpp/CppCodingStandard.html](http://www.possibility.com/Cpp/CppCodingStandard.html)
    Don't forget how ever that you can have your own stile, but for the most part you keep it standard. Plus it's easier for you to read too! A lot of people use their own way of commenting.

---

### Post by MadCow108 on 2009-07-07
> **sp0tz said:**
> I agree with you on the spacing. Readable syntax has been a problem of mine for awhile, so thank you for reminding me to work on it.

However, the point of the multidimensional array was to hold a lot of data in one place. Maybe the small chunk of code I entered here isn't a good example but if the array includes one dimension for the operation and another for whether the question was answered correctly or not, it's going to be relatively easy to determine the % of multiplication questions answered correctly, what operation the user most commonly answers incorrectly/correctly, etc. The point of this array is to hold data to analyze the player's performance with, so being more detailed is better, I think.

Using the suggested array questionsAnswered[operation], we can't determine the player's aptitude for a given question type.

Later on, I was thinking I would add another array (or something) to keep track of things like how often the player got double-digit multiplication problems correct. This is advanced stuff that will need thorough blueprinting, but the idea is to keep a detailed record of the player's performance, so that the program is capable of doing something other than barraging the user with random math problems.

I would consider writing a class to handle the statistics.
would be easier to handle and more flexible than raw multidimensional arrays

---

### Post by sp0tz on 2009-07-07
damn. I keep trying to write something simple that I can solidify my knowledge of the basics with, but then it turns out I need all this stuff I barely know how to use. I'll look up implementing classes after I finish this program, maybe use them to add the more complicated stat tracking, but I'm gonna be so f%*#^ng bored when I take intro to programming next semester....

---

### Post by Mirge on 2009-07-07
> **sp0tz said:**
> damn. I keep trying to write something simple that I can solidify my knowledge of the basics with, but then it turns out I need all this stuff I barely know how to use. I'll look up implementing classes after I finish this program, maybe use them to add the more complicated stat tracking, **but I'm gonna be so f%*#^ng bored when I take intro to programming next semester....**

:lolflag:

---

### Post by c0mput3r_n3rD on 2009-07-07
Haha sp0tz I know how it is, I have already learned a lot of C when I took computer programming I using C++ and it was very boring.  But on the bright side, I got an A and didn't even have to go to class, and I (as you will also) still learned a good bit mate.

---

### Post by c0mput3r_n3rD on 2009-07-07
```

//math test
//a program that asks a lot of math questions, then records your answers
//it's fun.

#include <iostream>
#include <cstdlib>
#include <ctime>
#include <string>
#include <fstream>
using namespace std;

//Global variables
#define ADDITION             1
#define SUBTRACTION          2
#define MULTIPLICATION          3
#define DIVISION          4
#define ANSWERED_CORRECTLY   0
#define ANSWERED_INCORRECTLY 1


int main(){
    //Set seed to 0
    srand((unsigned)time(0));

    //initialize integers
    int questions[4][1];
    int answer_sane = 0;
    int operation   = 0;
    
    questions[MULTIPLICATION][ANSWERED_CORRECTLY]   = 0;
    questions[DIVISION][ANSWERED_CORRECTLY]         = 0;
    questions[ADDITION][ANSWERED_CORRECTLY]         = 0;
    questions[SUBTRACTION][ANSWERED_CORRECTLY]      = 0;
    questions[MULTIPLICATION][ANSWERED_INCORRECTLY] = 0;
    questions[DIVISION][ANSWERED_INCORRECTLY]       = 0;
    questions[ADDITION][ANSWERED_INCORRECTLY]       = 0;
    questions[SUBTRACTION][ANSWERED_INCORRECTLY]    = 0;

    cout << "before:\n";
    cout << questions[DIVISION][ANSWERED_CORRECTLY]         << endl;
    cout << questions[DIVISION][ANSWERED_INCORRECTLY]       << endl;
    cout << questions[MULTIPLICATION][ANSWERED_INCORRECTLY] << endl;

    answer_sane = 55555;
    operation   = 44444;

    cout << endl << "after:\n";
    cout << questions[DIVISION][ANSWERED_CORRECTLY]               << endl;
    cout << questions[DIVISION][ANSWERED_INCORRECTLY]             << endl;
    cout << questions[MULTIPLICATION][ANSWERED_INCORRECTLY] << endl;

    cout << endl << "memory addresses:\n";
    cout << &questions[DIVISION][ANSWERED_CORRECTLY]         << endl;
    cout << &questions[MULTIPLICATION][ANSWERED_INCORRECTLY] << endl;

    cout << &operation                                 << endl;
    cout << "\nmore addresses:\n";
    cout << &questions[DIVISION][ANSWERED_INCORRECTLY] << endl;
    cout << &answer_sane;

    return 0;
}
```

It's formatted differently when i paste it into here but, but that's general style you use when programming, not only in C++, but in any language

---

### Post by sp0tz on 2009-07-08
n3rD, I could look at a text file, but in the meantime, what I'm getting from first glance is that it's important to space between operands and operators, and it is ideal to tab stuff out so as to make columns and patterns and such. Maybe this doesn't make sense but, like:

```
int stuff,things,penguin;

cout <<  whatever_blablahblah << endl;
cout <<  another_thing        << endl;
cout <<  a_third_thing        << endl;
cout <<  ^same_charcount?!    << endl;

stuff   = things + 7;
penguin = things + stuff;
```

---

### Post by Mirge on 2009-07-08
[http://en.wikipedia.org/wiki/Programming_style](http://en.wikipedia.org/wiki/Programming_style)

---

