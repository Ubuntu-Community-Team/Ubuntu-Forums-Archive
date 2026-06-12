---
title: "Questions about C++"
date: 2010-01-25
forum: Programming Talk
---

### Post by smdawson on 2010-01-25
I am a c++ newb, just to give you a reference point. I am taking a class in college right now and my homework is writing a program that performs simple addition. I am pretty sure I know how to successfully do this. My question is, what do "using" statements do? In my homework I am supposed to "write the necessary using statements" in my program.

Some examples of using statements in my book show
using std::cin;
(or)
using std::cout;
(or)
using std::endl;

I thought "#include <iostream>" named routines I could use, like input/output. So what does the using statement do?

---

### Post by lisati on 2010-01-25
I'm fairly new to C++ as well, but believe the "using" statement is connected with the idea of a "[namespace]("http://en.wikipedia.org/wiki/Namespace_(computer_science)")".

---

### Post by smdawson on 2010-01-25
Yeah, I just built the previously mentioned program. when I didn't specify "using namespace std;" I had to write a "using statement" for each routine(not sure if that's correct terminology) So I guess the namespace is a group of predefined routines that are commonly used. the "using statements" can be used to specifiy things not in the namespace, or you can just write it a couple different ways. I think...maybe

---

### Post by Can+~ on 2010-01-25
One of the problems on C, is having function names clash with each other. Sometimes you declare a function "void foo(int *bar)", and you accidentally create a function with the same name, or viceversa.

It's more a semantical issue, for example, you may want to use the word "append" for a certain task (add an element to a list) but also you would like to use "append" for adding something to the end of a file. So while in C you would do "file_append", "list_append", to circumvent this issue, C++ provides you a language element to do it, which are called "namespaces".

And that's all what it is, it just helps there to help us organize the code.

The statement "using" in C++, implies that you'll use all the things inside said namespace, like you'll be "inside" this particular namespace. And the "::" operator does that for a single time (and also works with method definitions inside a class).

---

### Post by smdawson on 2010-01-25
That makes sense. So, are there a few main namespaces that are used the majority of the time, or are there many to use depending on what you need each instance? I mean, can I basically use the same namespace in all my assignments, or do I need to look into which ones would best fit what I do each time?

---

### Post by nmccrina on 2010-01-25
> **smdawson said:**
> That makes sense. So, are there a few main namespaces that are used the majority of the time, or are there many to use depending on what you need each instance? I mean, can I basically use the same namespace in all my assignments, or do I need to look into which ones would best fit what I do each time?

Yes, generally what you would do is something like

```

#include <iostream>
// other header files
using namespace std;
```

All the standard functions (cout, cin, pow, etc.) are in the "std" namespace, so the "using namespace std;" line is saying that you want to refer to those functions without saying "std::<name of function>" all the time.

---

### Post by smdawson on 2010-01-25
Now I understand. Thanks for clarifying. I want to make sure I learn the code, and the theory behind it, so when class gets more advanced my knowledge is not full of holes.

---

### Post by dribeas on 2010-01-26
> **smdawson said:**
> "write the necessary using statements"

I am quite sure that in your problem there is no 'necessary' using statement. I've been writting C++ for quite some time and avoid 'using' statements all the time (prefer qualified names, or namespace aliases for deeply nested namespaces.

There are just a few situations where a 'using' statement is required, but most probably beyond the scope of your whole course (has to do with sfinae in metaprogramming).

---

### Post by smdawson on 2010-02-15
I have a hmwk assignment that presents me with 
(double) 17 / 2; 
where 17 is of data type 'double' and 2 is of data type 'int'

I am supposed to answer what the value and data type of the expression is. I know the value is 8, but what is the data type? Since the answer is just 8 and does not exceed the number of digits 'int' can hold, is that what it is?

---

### Post by MadCow108 on 2010-02-15
the answer 8 is wrong.

float data types have precedence over integers in calculations.

the data type of the result is actually non-trivial. Probably double is asked. But these calculations (assuming the compiler could not do them at compile time) are done in the FPU which uses long double (80 bit) on many systems (including x86).
When compiled with optimization the result may never be spilled back into memory and the return type is then long double.
This is important to know when dealing with rounding errors in numerical calculations (as it leads to nasty compiler flag dependent bugs).

---

### Post by smdawson on 2010-02-15
Ok, so the result is of type 'double' when two variables 'double' and 'int' are in an equation? Also, then what is the numerical answer for the expression?

---

### Post by MadCow108 on 2010-02-15
just try it.

your never going to learn if you don't experiment by yourself.

---

### Post by smdawson on 2010-02-15
I did. But I set the result as type 'int'. should I have set it as 'double'?
```
double x;
int y;
double z;

x = 17;
y = 2;
z = x / y;

cout << z << endl;
```

---

### Post by smdawson on 2010-02-15
Oh, nevermind, that works! Previously I did not know that the 'double' would take precedence and wrote
```
int z;
```
as opposed to 
```
double z;
```
using the later the answer is 8.5! to confirm, if double or float is used, then it takes precedence over integer in all expressions? Making the result the data type that stores more.

---

### Post by MadCow108 on 2010-02-15
int a = (double)17/(int)2
will of course result in an int because there is another implicit cast to int of the return type of the calculation.
so the above effectively is this:
int a = (int)((double)17/(int)2)

to see the result without casting to other type use the result directly in cout.
the << operator is overloaded for all types and the compiler chooses the best one. In this case double.

cout << ((double)17/(int)2) << endl;
outputs 8.5

whereas this
cout << (int)((double)17/(int)2) << endl;
outputs 8

using an interpreter like CINT you can even see which type is outputted.

@ your question:
if float and int are in the same expression the result will be float by default.
But note that each operator is an expression on its own:
17/2 + 1.5
would be 2 ints + one double. but 17/2 is one expression with both integers so the result of this is again an integer (*/ are evaluated before +- like in mathematics)!
so you get:
8 + 1.5 = (int + float = float) = 9.5

just play around a with it.

---

### Post by smdawson on 2010-02-15
ok, thank you. That way seems more helpful and uses less code.

---

