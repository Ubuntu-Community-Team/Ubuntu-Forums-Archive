---
title: "C++ Questions on type"
date: 2007-06-13
forum: Programming Talk
---

### Post by TreeFinger on 2007-06-13
I am doing some exercises from a C++ book chapter one. So far it has only discussed type int. I am on a problem at the end of a chapter where you write a program to find circumference, etc. of a circle. I am wondering how I would get exact numbers for the answers the program gives. I tried changing all of my variables to type double and type float and also the main function to type double but it just gave me more errors when compiling. 

The book said to just use the constant value 3.14159 for pie. I try using ```
const pie
``` but get an error.

So far in Chapter 1 of this book the only types discussed were int so I am trying to solve it based on prior experience. Here is my code:

```

// User enters radius of circle
// Prints circle's diameter, circumference and area

#include <iostream>
using std::cout;
using std::cin;
using std::endl;

int main()
{
	int pie;
	int radius;
	int diameter;
	int circumference;
	int area;

	cout << "I will calculate diameter, circumference, and area of your circle\n";
	cout << "Please enter the radius of your circle\n";

	cin >> radius;
	pie = 3.14159;
	diameter = 2 * radius;
	circumference = pie * diameter;
	area = pie * radius * radius;

	cout << "You entered " << radius << " as your radius\n";
	cout << "The diameter is: " << diameter << "\t";
	cout << "The circumference is: " << circumference << "\t";
	cout << "The area is: " << area << endl;
	
	return 0;
}


```

Here are the error messages during compiling.

```

$ g++ circle.cpp -o circle.out
circle.cpp: In function ‘int main()’:
circle.cpp:22: warning: converting to ‘int’ from ‘double’

```

---

### Post by HackingYodel on 2007-06-13
It's giving you a warning because you are doing a type demotion.

See this article for details about type casting in C++ [http://en.wikibooks.org/wiki/C++_Programming/Type_Casting](http://en.wikibooks.org/wiki/C++_Programming/Type_Casting).

The trick here is to initialize your types as a "larger" type and do a type promotion.  Find which is the "larger" of int, float, or double. ;)

Hope that helps!

---

### Post by TreeFinger on 2007-06-13
So would changing all of my variable types to double help? I guess I should just keep reading  my book :popcorn:

---

### Post by Modred on 2007-06-13
In short:

Integers only hold exact, whole numbers.  So when you assign pie = 3.14159, you're actually getting pie = 3 and the rest is truncated.  (And it's pi, by the way, not pie.)

Anything that can have a decimal should be a double, so at least **pi, circumference,** and **area** should be doubles.  Multiplication involving an int and a double is automatically promoted to a double, so you shouldn't need to worry about losing digits when multiplying if you store the result in a double.

Assuming you're using g++, the cmath library should have a constant M_PI that holds the value of pi.  You can use it like so:

```

#include<cmath>
...
circumference = M_PI * diameter;
...

```
If you do that, then you can delete your declaration and assignment of **pie** and replace all the times you used it with M_PI.

And no, not all of your numbers need to be doubles.  Well, you could make all of your variables doubles, but leave the main function as returning an int.  I don't know if g++ gives you grief for changing main's return type, but I know other compilers will.

---

### Post by TreeFinger on 2007-06-13
Thank you Modred. I just found it odd that they would ask to write a program like this when the book hasn't even talked about the double data type and I like to get the exact number for a mathematical answer.

And Pi slipped my mind :) I have taken trigonometry already but a long time ago. I guess my mother's pie was on my mind when assigning that variable :p

---

### Post by danhm on 2007-06-13
The reason "const pie" gave you an error is becaues consts are variables too, just unchangable ones. You need to declare what type they are and also assign a value to them (or else they'll get stuck with whatever happened to be in that particular memory location -- a garbage value).

In short (no pun intended!), you'd want something like "const double PI = 3.14159".

Also, "#define PI 3.14159" would work too. This, if I remember correctly, doesn't make PI a variable, but is similar to the find and replace tool. On compile time, it'll go through your code and replace all instances of PI with 3.14159. It doesn't search in words, so if you have a variable name with pi in it (say, "pie"), it'll leave that alone. It won't touch stuff in quotes, either (like cout statements).

Oh, and the reason I kept capitalizing pi was because that is a good habbit to get into when declaring constants; variables with lowercase names are free to be changed while variables with uppercase names are constant values. It's not a big deal for little things like finding the area of a circle, but useful when you have much larger projects with a gross of variables.

---

