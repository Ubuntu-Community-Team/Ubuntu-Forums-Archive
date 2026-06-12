---
title: "My Calculator in C++"
date: 2008-04-02
forum: Programming Talk
---

### Post by joshdudeha on 2008-04-02
Would anyone take the time in compiling my source code :
```
#include <iostream>
using namespace std;

int main()
{
  double number1;
  double number2;
  char choice;  

 for(;;) {
  do {
  cout << "Hello - welcome to the joshcalculator . . .\n";
  cout << "This program calculates two numbers for you.\n";
  cout << "\n";
  cout << "1. Addition\n";
  cout << "2. Subtraction\n";
  cout << "3. Multiplication\n";
  cout << "4. Division\n";
  cout << "\n";
  cout << "Please select a type of calculation by typing the number next to the calculation you'd like to do, press q to quit\n";
  cout << "\n";
  cin >> choice;
} while( choice < '1' || choice > '4' && choice != 'q');

if (choice == 'q') break;
 
 switch(choice) {
  case '1':
   cout << "Addition\n";
   cout << "Please enter a number: ";
   cin >> number1;
   cout << "\n";
   cout << "Please enter another number: ";
   cin >> number2;
   cout << "\n";
   cout << "The answer is: " << number1 + number2 << "\n";
   break;
  
 case '2':
   cout << "Subtraction\n";
   cout << "Please enter a number: ";
   cin >> number1;
   cout << "\n";
   cout << "Please enter another number: ";
   cin >> number2;
   cout << "\n";
   cout << "The answer is " << number1 - number2 << "\n";
   break;

case '3':
   cout << "Multiplication\n";
   cout << "Please enter a number: ";
   cin >> number1;
   cout << "\n";
   cout << "Please enter another number: ";
   cin >> number2;
   cout << "\n";
   cout << "The answer is " << number1 * number2 << "\n";
   break;

case '4':
   cout << "Division\n";
   cout << "Please enter a number: ";
   cin >> number1;
   cout << "\n";
   cout << "Please enter another number: ";
   cin >> number2;
   cout << "\n";
   cout << "The answer is " << number1 / number2 << "\n";
   break;
}
}

return 0;
}
```

Quite proud of it, just a really **simple** calculator made in C++, I haven't used C++ before - and just got into it tonight.
What do you think for a 13 year old? xD

---

### Post by WW on 2008-04-02
Works for me.  Keep going! For example, try using **double** instead of **int** for the variables number1 and number2.


(I could quibble about your indentation style, but that could lead to a mega-thread!)

---

### Post by Martin Witte on 2008-04-02
If you take two varaibles of type 'int', and divide them you have an 'integer division', try e.g 3/2. You can get the floating point result with a cast, change e.g. to this
```
cout << "The answer is " << (float)number1 / (float)number2 << "\n";
```

---

### Post by joshdudeha on 2008-04-02
Thanks =]
Yeah, so I can use decimals.

And yes, i will brush up on my alignment =]
Thanks for the "constructive criticism" as it's called.

---

### Post by Nemooo on 2008-04-02
I believe I was at the same stage at your age. Just keep learning.

I made the stupid mistake to stop learning (spent time on some web development and other computer stuff instead), but am starting again).

---

### Post by joshdudeha on 2008-04-02
Yeah, I wanted to do programming, but caught up in design.
I like design, but I like programming too - So I'm gonna try and balance the two out. Thanks everyone for taking your time to sample my code :] I'm sure I'll be inspired and a learn a lot from you.

---

### Post by Can+~ on 2008-04-02
Great for your age. Now you should start learning how to do functions, instead of putting all into main

Example:
+: f(x, y) = x + y 
-: f(x, y) = x - y 
*: f(x, y) = x * y 
/: f(x, y) = x / y

Sample on C++:

[PHP]int sum(int a, int b)
{
   return a + b;
}

int  main()
{
   ...

   cout << sum(2, 5);
   
   ...
}
[/PHP]

Later on, as a challenge, try to:
- build your whole program with functions
- make it with functions by reference (pointers).
- build a complex number calculator (a + bj).

---

### Post by joshdudeha on 2008-04-02
I like that code :]
I'm gonna do some studying with the book I have (C++ the beginners guide, by Herbert Schildt) 

Then, I'll start experimenting with things you have suggested, Can+~
Thanks again

---

### Post by Lster on 2008-04-02
Very nice! :) I also started programming at thirteen and thoroughly enjoyed it. I hope you do, too!

Something you may have already found, but if not:

[http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

You may also like to consider languages such as Python. I, myself, am currently learning it and find it easier than C++ for most coding. Then again, C++ is a very good language to learn. :)

Hope you enjoy yourself!

---

### Post by Caduceus on 2008-04-02
I don't want to start a flame war, but if you are looking to learn another language besides C++, look into languages other Python. Sure, Python is a good language, but it's certainly not the only one out there. For example, I looked into Ruby and fell in love with it. I had some decent C++ knowledge before starting Ruby and it's easy to learn if you understand OOP concepts.

---

### Post by LaRoza on 2008-04-02
You did that in one night of study? Quite good.

If you enjoy programming (which I do), you might find my wiki interesting. It has a lot for C++, among other languages.

If you are like me at all, you might find it possible to learn more than one language at a time if they are of the same paradigm.

C++ has some things in it which make it difficult to use, so when you get there, be prepared to do some reading.

---

### Post by joshdudeha on 2008-04-03
Thank you for everyone for all of your suggestions and contributions. 
I think I am going to stick with C++ for the mean-time, but after advancing a bit more, I will look into other languages, including Python.

I will try and make a more efficient version of the calculator using as you've suggested, functions.
Maybe a more advanced calculator next time.
Again, thank you for your suggestions.

---

