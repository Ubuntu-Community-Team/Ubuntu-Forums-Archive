---
title: "Square root algorithm"
date: 2014-05-01
forum: Programming Talk
---

### Post by spacerocket on 2014-05-01
Hello!

I wrote function like this in text editor example was in C++ book



double sgrt(double arg)
{
      // code for calculating a square root
}

void f()
{
      double root2 = sqrt (2) ;
      // ...
}


Then I typed as follows:

```
 g++ Documents/squareroot.cpp

```

Documents/squareroot.cpp: In function ‘void f()’:
Documents/squareroot.cpp:8:29: error: ‘sqrt’ was not declared in this scope
       double root2 = sqrt (2) ;
                             ^


I wrote something incorrectly? Anyone could explain that function to me (I don`t fully understand it).

> Curly braces, { }, express grouping in C++. Here, they indicate the start and end of the function
bodies. The double slash, / /, begins a comment that extends to the end of the line. T[B]he keyword
void indicates that a function does not return a value.[/B]

I don`t understand. Integer variable does return a value?

Here is  declared the function (told the compiler  what the type of its parameters and result are, which is all it needs to  know to invoke the function at run time). For this function what are the parameters and results?

---

### Post by spjackson on 2014-05-01
When you declare (and define) the function you spell it sgrt. When you use it, you spell it sqrt. These are not the same: g is not q.

---

### Post by spacerocket on 2014-05-01
Yep, I changed sgrt to sqrt. The is still some syntax errors in the code?

```
g++ Documents/squareroot.cpp
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 0 has invalid symbol index 11
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 1 has invalid symbol index 12
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 2 has invalid symbol index 2
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 3 has invalid symbol index 2
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 4 has invalid symbol index 11
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 5 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 6 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 7 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 8 has invalid symbol index 12
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 9 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 10 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 11 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 12 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 13 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 14 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 15 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 16 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 17 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 18 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 19 has invalid symbol index 21
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_line): relocation 0 has invalid symbol index 2
/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../x86_64-linux-gnu/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: error: ld returned 1 exit status

```

---

### Post by steeldriver on 2014-05-01
As indicated by the error message

```
 (.text+0x20): undefined reference to `main'
```

your code doesn't have an entry point (main function) so you can't create an executable program from it as-is. You can either compile it to an *object file* to be linked at some later point to create an actual executable program by adding the -c switch e.g.
 
```
g++ **-c** squareroot.cpp -o squareroot.o
```

or you can add a main function to your file

```

int main()
{
    // do stuff

    return 0;
}

```

---

### Post by spacerocket on 2014-05-01
I got error message as follows:

 g++ Documents/squareroot.cpp
Documents/squareroot.cpp: In function ‘int main()’:
Documents/squareroot.cpp:6:1: error: a function-definition is not allowed here before ‘{’ token
 {
 ^
Documents/squareroot.cpp:11:1: error: a function-definition is not allowed here before ‘{’ token
 {
 ^
Documents/squareroot.cpp:16:1: error: expected ‘}’ at end of input
 }
 ^


My actual code looks like this:

```
int main()
{
    //

double sqrt(double arg)
{
      // code for calculating a square root
}

void f()
{
      double root2 = sqrt (2) ;
      // ...
      
    return 0;
}
```

---

### Post by steeldriver on 2014-05-01
where's the closing brace } for your main() ?

---

### Post by spacerocket on 2014-05-01
Now I have as follows:

```
int main()
{
    //

double sqrt(double arg)
{
      // code for calculating a square root
}

void f()
{
      double root2 = sqrt (2) ;
      // ...
}
      
    return 0;
}
```


g++ Documents/squareroot.cpp
Documents/squareroot.cpp: In function ‘int main()’:
Documents/squareroot.cpp:6:1: error: a function-definition is not allowed here before ‘{’ token
 {
 ^
Documents/squareroot.cpp:11:1: error: a function-definition is not allowed here before ‘{’ token
 {
 ^

---

### Post by steeldriver on 2014-05-01
AFAIK C++ does not support function nesting - you need to define your subfunctions **outside** of main() { ... }

[http://en.wikipedia.org/wiki/Nested_function#Languages](http://en.wikipedia.org/wiki/Nested_function#Languages)

---

### Post by Vaphell on 2014-05-01
nested functions are not C/C++ feature.
edit too late to the party :-)

---

### Post by spacerocket on 2014-05-01
g++ Documents/squareroot.cpp


worked correctly after I changed the code.


./Documents/squareroot.cpp
bash: ./Documents/squareroot.cpp: Permission denied

Something wrong again??

---

### Post by steeldriver on 2014-05-01
The squareroot.cpp file is your *source code* file - you need to execute the compiler's *output *file. By default, that will be called a.out but you can change that using the compiler's -o flag

```

g++ -o squareroot squareroot.cpp

./squareroot

```

You really should try to find a good beginner's guide to C++ programming with g++, it will be very frustrating otherwise. Are you taking a class, or following some kind of online tutorial?

---

### Post by spacerocket on 2014-05-02
Ok now 

```
 g++ -o squareroot Documents/squareroot.cpp

```

```
 ./squareroot

```

-> Nothing. What should the program really do? If I put 4 -> 4: command not found. What is the purpose of this program?

And yep, I`m not in any C++ class because I haven`t made it to university yet. Maybe after a year or so.

I have been following this [http://e-maxx.ru/bookz/files/stroustrup.pdf](http://e-maxx.ru/bookz/files/stroustrup.pdf)

And considered buying this [http://www.stroustrup.com/programming.html](http://www.stroustrup.com/programming.html)

---

### Post by steeldriver on 2014-05-02
Do you actually have any code inside your function definitions? so far you have only posted placeholders like
```

double sqrt(double arg)
{
      // code for calculating a square root
}

void f()
{
      double root2 = sqrt (2) ;
      // ...
      
    return 0;
}
```

---

### Post by spjackson on 2014-05-02
> **spacerocket said:**
> Ok now 

```
 g++ -o squareroot Documents/squareroot.cpp

```

```
 ./squareroot

```

-> Nothing. What should the program really do? If I put 4 -> 4: command not found. What is the purpose of this program?

And yep, I`m not in any C++ class because I haven`t made it to university yet. Maybe after a year or so.

I have been following this [http://e-maxx.ru/bookz/files/stroustrup.pdf](http://e-maxx.ru/bookz/files/stroustrup.pdf)

And considered buying this [http://www.stroustrup.com/programming.html](http://www.stroustrup.com/programming.html)

I'm not sure what your current code is or what you want it to do, but here's a simplified example. (It doesn't check for unreasonable input values or format the output in a fancy way.)

```

#include <iostream>
#include <cstdlib> // for atof


double f(double estimate , double target)
{
    return estimate * estimate - target;
}


double fdash(double estimate)
{
    return 2 * estimate;
}


// calculate the square root using 20 iterations of the Newton-Raphson
// method. http://en.wikipedia.org/wiki/Newton%27s_method
double mysqrt(double square)
{
    const int maxIterations = 20;
    double estimate = 1.0;


    for (int iteration = 0; iteration < maxIterations; ++iteration) {
        estimate = estimate - f(estimate, square) / fdash(estimate);
    }


    return estimate;
}


int main(int argc, char * argv[])
{
    double x = 0.0;
    if (argc > 1) {
        x = atof(argv[1]); // convert the 1st argument to a number
        // calculate the square root of x and display the result.
        std::cout << "The square root of " << x << " is approximately " << mysqrt(x) << "." << std::endl;
    }
    else {
        std::cerr << "Usage: " << argv[0] << " square " << std::endl;
        return 1;
    }
    return 0;
}

```
Examples:
```

$ g++     mysqrt.cpp   -o mysqrt
$ ./mysqrt 2
The square root of 2 is approximately 1.41421.
$ ./mysqrt t 6.5
The square root of 6.5 is approximately 2.54951.
$ ./mysqrt 9
The square root of 9 is approximately 3.

```
Does that help?

---

### Post by spacerocket on 2014-05-02
To understand C++ I also need to know [http://en.wikipedia.org/wiki/Standard_Template_Library](http://en.wikipedia.org/wiki/Standard_Template_Library)    They are explained somewhere?

To the code you posted, I understand that **double** = / / double-precision floating-point number, for example, 3.14 and 299793.0  and is somehow needed in square root.

#include <iostream>
#include <cstdlib> // for atof

In cstdlib library some functions are  defined, which the program will need to perform input/output. Can you explain what are they because I have relatively little knowledge about libraries or how they work.

For each function is defined what would be given to program code to specify what it should do, in some .c file. #including is neither necessary nor helpful for that, it would just displace the problem to another f
file.
 

In the above code iostream and cstdlib are included but how you use them in the rest of the code is unclear to me.


[B]// calculate the square root using 20 iterations of the Newton-Raphson
// method. [http://en.wikipedia.org/wiki/Newton%27s_method](http://en.wikipedia.org/wiki/Newton%27s_method)
[/B]
Double allows you to declare your own fuctions included in 
<cstdlib> ?

I thought that was a property of class.

---

### Post by spjackson on 2014-05-04
I am not really sure how to respond since I don't really understand much of what you are saying, but I'll do my best.

> **spacerocket said:**
> To understand C++ I also need to know [http://en.wikipedia.org/wiki/Standard_Template_Library](http://en.wikipedia.org/wiki/Standard_Template_Library)    They are explained somewhere?

You posted a link to a copy of Stroustrup's The C++ Programming Language. What do you need to know at this stage beyond what is covered in Part III of that book?

> 
To the code you posted, I understand that **double** = / / double-precision floating-point number, for example, 3.14 and 299793.0  and is somehow needed in square root.

I don't understand your point.
> 
#include <iostream>
#include <cstdlib> // for atof

In cstdlib library some functions are  defined, which the program will need to perform input/output. Can you explain what are they because I have relatively little knowledge about libraries or how they work.

The program I posted uses std::cout and std::cerr for output. <iostream> is needed to declare these items. The program uses the library function atof() and therefore <cstdlib> is needed to declare this. Try removing each of these lines in turn and see what compilation errors you get; perhaps that will clarify this.
> 
For each function is defined what would be given to program code to specify what it should do, in some .c file. #including is neither necessary nor helpful for that, it would just displace the problem to another f
file.
 
I don't understand.
> 
In the above code iostream and cstdlib are included but how you use them in the rest of the code is unclear to me.

See above. Have you managed to write any C++ (or C) program that does any output?
> 
[B]// calculate the square root using 20 iterations of the Newton-Raphson
// method. [http://en.wikipedia.org/wiki/Newton%27s_method](http://en.wikipedia.org/wiki/Newton%27s_method)
[/B]
Double allows you to declare your own fuctions included in 
<cstdlib> ?

I thought that was a property of class.
I don't understand.

---

### Post by spacerocket on 2014-05-04
I want some book and found this [http://www.amazon.com/Programming-Principles-Practice-Using-Edition/dp/0321992784](http://www.amazon.com/Programming-Principles-Practice-Using-Edition/dp/0321992784)  that is newer version of the old (2008) book. The standard libraries are covered in the end.

---

### Post by spacerocket on 2014-05-04
" The program uses the library function atof() "

Well if I delete that part of the code atof() 

```
g++ -o squareroot squareroot.cpp
g++: error: squareroot.cpp: No such file or directory
g++: fatal error: no input files

```

So atof() is a library function of square root?

If I want to perform something in C++ I first need to include a library with the needed function? I picked up these from a source code of a  C++ chess program(I have many of them)

#include <intrin.h>

#include <nmmintrin.h>

#include <string.h>

They were in a file called bitboard.h.

So to determine some action in the code(in text editor) I need to refer to a library which contains the instructions to perform output from certain functions(needed in that code)?


<cstdlib>
>
C-style string functions
§20.4.1
&#63724; _ ________________________________________________________
&#63724; The <cstdlib>
declares atof() and a atoi i() that convert C-style strings to numeric values.

The Numeric values are obviously needed in squareroot?

I posted above some include# stuff but don`t know their meaning as libraries or how to use them in a code. To the original question I didn`t know what **double** stands for.

---

### Post by dwhitney67 on 2014-05-04
> **spacerocket said:**
> " The program uses the library function atof() "

Well if I delete that part of the code atof() 

```
g++ -o squareroot squareroot.cpp
g++: error: squareroot.cpp: No such file or directory
g++: fatal error: no input files

```


Buy a C++ book, start at chapter 1.  If you are unable to even perform a simple compilation/linking of a program (ie. you get errors like the one above), then I suggest that you procure a Linux book that teaches the fundamentals regarding directory structure, files, etc.

As for the error above, the compiler is merely telling you that it cannot find the file 'squareroot.cpp'.  That's it... nothing more.

P.S.  In case you are unable to afford a C++ book, here's a basic online tutorial:  [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by spacerocket on 2014-05-05
Hello

Of course I can afford to buy a C++ book : ) I just wait for the newer version which I posted above to be published.

Sorry about that mess, of course I ment 

```
g++ -o squareroot Documents/squareroot.cpp

```

```
./squareroot 4
The square root of 4 is approximately 2.

```

Now that`s strange. The program still works even though I deleted **for atof**

And how about my earlier questions, sorry about that mess.

---

### Post by steeldriver on 2014-05-05
In the line

```
#include <cstdlib> // for atof
```

the **for atof** part is a **comment **(as indicated by the // in front of it) - it has no effect on whether the cstdlib header file is actually included or not. If you want to see what happens if it's not included, comment out the whole line

```
// #include <cstdlib> // for atof
```

and then try to recompile the program - you should see something line

```

$ g++ -o squareroot squareroot.cpp
squareroot.cpp: In function ‘int main(int, char**)’:
squareroot.cpp:38:25: error: ‘atof’ was not declared in this scope

```

Please do yourself (and us!) a favor by taking the time to read a basic tutorial such as this one --> [http://www.cplusplus.com/doc/tutorial/program_structure/](http://www.cplusplus.com/doc/tutorial/program_structure/)

---

### Post by spacerocket on 2014-05-05
How is a variable function declared in C++, 

If I want to enter x (assuming x is an integer **and changing** number) and receive output from a mathematical operation (eg. 
int addition (int a, int b)
{
  int r;
  r=a+b;
  return r;
}

If still unclear I referred to the square root functon: After compiling eg. 
./squareroot **4**
The square root of 4 is approximately 2.

I meant that the **4** is a variable; How can I implement this part in C++? Or in what part of the squareroot function is this  property determined.

Is still unclear feel free to ask, thanks for support anyway.

---

### Post by spacerocket on 2014-05-06
I mean that for example here is written a program that calculates the permutation of 9

```
[TABLE="class: split"]
[TR]
[TD="class: source"]// factorial calculator
#include <iostream>
using namespace std;

long factorial (long a)
{
  if (a > 1)
   return (a * factorial (a-1));
  else
   return 1;
}

int main ()
{
  long number = 9;
  cout << number << "! = " << factorial (number);
  return 0;
}[/TD]
[TD="class: output"]9! = 362880[/TD]
[/TR]
[/TABLE]
 
```


How would I change the code above for the program to calculate **any **permutation for **any** number?

---

### Post by dwhitney67 on 2014-05-06
You would either a) handle a input number from the console, and/or b) prompt the user for input.

For example:
```

#include <iostream>
#include <sstream>

long factorial (long a)
{
    if (a > 1)
        return (a * factorial (a-1));

    return 1;
}

int main (int argc, char** argv)
{
    long number = -1;
    bool have_num = false;

    if (argc == 2)
    {
        std::istringstream iss(argv[1]);

        iss >> number;

        have_num = iss.good();
    }

    if (!have_num)
    {
        std::cout << "Enter a number: ";
        std::cin  >> number;
    }

    std::cout << number << "! = " << factorial (number) << std::endl;
}

```

---

### Post by spacerocket on 2014-05-06
Nice one,

 To the code you posted I try to understand it. In part 1 you define the  properties of permutation using variable a. Because permutation has a  return type, the call is evaluated as having a value, and this value is  the value specified in the return statement that ended permutation. 

In this  case the value would be 1, which I don`t understand. Why would a permutation for any number have a value of 1? Or does **1** stand for the whole definition for permutation? ( return 1; )

The formula for the permutation of **k!** would be

[IMG]http://upload.wikimedia.org/math/5/7/e/57ebc3aeb6205cff7793b579c46c9223.png[/IMG]

---

### Post by dwhitney67 on 2014-05-06
> **spacerocket said:**
>  

In this  case the value would be 1, which I don`t understand. Why would a permutation for any number have a value of 1? Or does **1** stand for the whole definition for permutation?

For starters, read this:  [http://en.wikipedia.org/wiki/Factorial](http://en.wikipedia.org/wiki/Factorial)

As for the function factorial(), it accepts a number that technically can be signed (that is, ca be less than zero), but for sake of argument, let's pretend it will always be a value greater than or equal to zero.  if you wish, change the parameter to be an "unsigned long", thus affording one extra bit to permit larger numbers.

As far as how the function works, if the number that is given is greater than 1, then the formula (which you posted previously) is applied and the resulting value is returned.  Otherwise, and this is ONLY if the value is LESS THAN or EQUAL to 1, then 1 is returned.

It is redundant/superfluous/silly to code an if-else statement in the factorial() function when only one of two possible outcomes may occur.  Either the if-conditional is true, and the factorial value is computed/returned OR the value 1 is returned.

---

### Post by spacerocket on 2014-05-06
Yes,

The recursive definition for factorial (I mixed it to permutation earlier sorry) is actually



n!          =        1        if   n=0


                                       (n-1)! x n   if   n>0
 
    



I would write something like

{
    if (a > 0)
        return (a * factorial (a-1));

    if (a=0)
    return 1;
}


To the rest of the code you posted I don`t yet fully understand, I will need to look more at the C++ tutorial and try to figure it out later.

---

### Post by dwhitney67 on 2014-05-06
> **spacerocket said:**
> 
I would write something like

{
    if (a > 0)
        return (a * factorial (a-1));

    if (a=0)
    return 1;
}

It is not necessary to apply the function when the number given is 1.  1! = 1.

Also, it is not necessary to have the 2nd if-statement in the function.  Either the value of 'a' is greater than 1, or it is not.  There is no other possibility.  Thus the following is sufficient.

```

unsigned long factorial(unsigned long number)
{
    if (number > 1)
    {
        // The function factorial is called recursively IF and ONLY IF the number is greater than 1.
        return (number * factorial(number - 1));

        // This point in the if-block is NEVER reached!
    }

    // The value of 1 is returned IF and ONLY IF number is 1 or 0.
    return 1;
}

```

---

### Post by spacerocket on 2014-05-07
A stream can be attached to a string. That is, we can read from a string and write to a string using
the formatting facilities provided by streams. Such streams are called a stringstreams
ms. They are
defined in **<sstreams>**

An **istringstream**  is an input stream reading from a string.


Now I was able to collect this data from STL library but can`t connect this information to this:

```
int main (int argc, char** argv)
{
    long number = -1;
    bool have_num = false;

    if (argc == 2)
    {
        std::istringstream iss(argv[1]);

        iss >> number;

        have_num = iss.good();
    }


```

I don`t understand what is the meaning of **istrinstream** here; Understanding what something means like (string= marksequence) and connecting this information to understand what is does in C++ are two different

things, straight to speak I can´t understand the code or the meaning of streams there.

I would guess it is something relating to finding the nth term in factorisation (n!)

---

### Post by dwhitney67 on 2014-05-07
The streams that you are probably familiar with are the standard-out/err/in streams.  In C++, these can be accessed using std::cout, std::cerr and std::cin, respectively.

Now ask yourself, what is the difference between how we operate with those streams versus a virtual stream, such as one created using std::ostringstream or std::istringstream.

As the name of these object denote, they are streams that work with strings... either as output or as input.

If I prompt a user to enter their name (i.e. a string) and their age (i.e. an int), something like this could be used:
```

std::string name;
int age;

std::cout << "Enter your name and age: ";
std::cin  >> name >> age;
...

```
What if I do not want to prompt a user for information; say I already have a string that appears as "Fred 26".  How would I read the name and age?  Well...
```

std::string data = "Fred 26";    // maybe this came from a network socket

std::string name;
int age;

std::istringstream iss(data);    // initialize the istringstream with the data string

iss >> name >> age;

```

Hopefully you can see that there is a similarity between the functionality of std::cin and std::istringstream.  There's also a similarity between std::cout and std::ostringstream.

Perhaps you should study this UML diagram to see the relationships of each type of object:  [http://www.cplusplus.com/reference/iolibrary/](http://www.cplusplus.com/reference/iolibrary/)

---

### Post by spacerocket on 2014-05-08
"A stream is an abstraction that represents a device on which input and  ouput operations are performed. A stream can basically be represented as  a source or destination of characters of indefinite length."

> int main (int argc, char** argv)

   In this part integrer means that the user performs input in fortm of integer( n!) and main initiates the declaration of a function.
                                     Char is a parameter, that determines the type of elements that are going to be manipulated, in this case argc which is integer.

             As you pointed out what if we do not want to prompt a user for information but initialize the istringstream with the data string (eg. user enters a random number and program calculates it`s factorial). In our case you want to tell the code to perform <iostream> 
                                   objects. Narrow-oriented objects include cin, cout, cerr and clog. What do they do? (cout calculates).

In summary <iostream> declares the objects used to communicate through the standard input and output (including cin and cout) and whose properties I don`t exactly understand.

---

### Post by dwhitney67 on 2014-05-08
> **spacerocket said:**
> 
   In this part integrer means that the user performs input in fortm of integer( n!) and main initiates the declaration of a function.
                                     Char is a parameter, that determines the type of elements that are going to be manipulated, in this case argc which is integer.

NO.  The main() is declared that way because I expected to pass arguments to the application.  argc is an integer that denotes the number of arguments that are being passed to the program, and argv is the array of pointers to char (i.e. strings).

A main() function that declares the variables argc and argv (which by the way, are arbitrarily chosen names) will always have at least 1 argument... that is, the program name.

> 
             As you pointed out what if we do not want to prompt a user for information but initialize the istringstream with the data string (eg. user enters a random number and program calculates it`s factorial). In our case you want to tell the code to perform <iostream> 
                                   objects. Narrow-oriented objects include cin, cout, cerr and clog. What do they do? (cout calculates).

You're spending way too much effort analyzing the program.  Input has to arrive in a certain manner into the main() function, and it just so happens it is always as one or more null-delimited strings; in other words, all input arguments are treated as strings.  For your particular application, a number is required, and thus it is necessary to convert a string into a number.

I could have foolishly used atoi() to convert the string to a number, however this system function is replete with problems/limitations.  Thus I chose to use istringstream, which is a useful way of converting a string to a number.

> 
In summary <iostream> declares the objects used to communicate through the standard input and output (including cin and cout) and whose properties I don`t exactly understand.
At your stage of learning C++, rather than worry about how these constructs are implemented, why not just focus on merely *using* these tools to accomplish a task.

I cannot, nor will most people, spend day-in/day-out explaining all of the details about C++ to you.  I can say that it is not a trivial language, but on the other hand not super-complex, but I strongly believe that you would probably get better help by reading a good book on the C++ language.  Or just experiment with small little programs so that you understand the basics.


P.S.  Why don't you run this program, and supply command-line arguments to see the results:
```

#include <iostream>

int main(int argc, char* argv[])
{
    for (int i = 0; i < argc; ++i)
    {
        std::cout << "argv[" << i << "] = " << argv[i] << std::endl;
    }
}

```

---

### Post by spacerocket on 2014-05-09
I have named the program as "experiment" and now

```
./experiment
argv[0] = ./experiment

```

What did make the factorial program unique compared to the original program that calculates factrorial for 9? In other words what did make the program to calculate factorials for n ?

If we have a program that calculates factorials for n number (integer), we can combine this property of the program to other program I guess.

Let`s imagine that a program prompts a user to enter two numbers,** n** and** k**. Then the program would use this formula 

[IMG]http://upload.wikimedia.org/math/e/e/d/eed76baaa00cf639ad1c1cecd11247f1.png[/IMG] 

 
to calculate the combination of these numbers. The program would first calculate the factorial of **n** (first number) like our program did. Then it would divide the result with k!(n-k)!.  First it would calculate the factorial of **k** (second number) and then multiply the result with (n-k)!. We could mark the 

substraction n-k with a letter **r**, so **r**=n-k. Then we would only have **k**! multiplied with **r**!.

---

### Post by dwhitney67 on 2014-05-09
Yep, something like:
```

unsigned long factorial(unsigned long n)
{
    ...
}

int main(int argc, char* argv[])
{
    // Get values for n and k...

    unsigned long result = factorial(n) / (factorial(k) * factorial(n - k));

    ...
}

```

P.S.  The program should attempt to ensure that n > k, and that both are unsigned numbers (thus negating the possibility of dealing with negative numbers).

---

### Post by spacerocket on 2014-05-10
```


#include <iostream>
#include <sstream>

unsigned long factorial(unsigned long n)

{
    

   if (n>k) 
       return factorial (n) / factorial(k) * factorial(n-k));
       else
       return 0;

}


int main () argc, char* argv[]  // The declaration of the function, argv is the array of pointers to character. The initializer can even have no values, just the braces: argv[]

{
  long number = negative;   // Takes into account the possibility number=negative
  bool have_num =false;    // This is the boolean function, possible values are true/false 
```
  
 

This is part of the  program and it`s **incomplete**. Before I go any further though, I don`t understand the statement " argv is the array of pointers to a character". Is it somehow related to 

"it may be useful for a program to be able to obtain the address of a 
variable during runtime in order to access data cells that are at a 
certain position relative to it."

---

### Post by dwhitney67 on 2014-05-10
A couple of problems:

1.  You are implementing the equation (n! / (k! * (n-k)!) in the wrong place.
2.  You are checking that n is greater than k (n > k) in the wrong place.

You want something similar to this:
```

#include <iostream>
#include <sstream>

unsigned long factorial(unsigned long a)
{
    if (a > 1)
        return (a * factorial(a-1));

    return 1;
}

int main(int argc, char** argv)
{
    unsigned long n = 0;
    unsigned long k = 0;
    bool input_valid = false;

    if (argc == 3)
    {
        // Attempt to get the value n
        //
        std::istringstream iss(argv[1]);
        iss >> n;
        input_valid = !iss.fail(); // check whether iss was able to extract an unsigned long

        iss.clear();  // clear the status

        // Attempt to get the value k
        //
        iss.str(argv[2]);
        iss >> k;
        input_valid = input_valid && !iss.fail(); // combine status with previous status
    }

    while (n <= k || !input_valid)
    {
        std::cout << "Invalid or missing input values for n and k...\n" << std::endl;

        // Note:  There are insufficient checks below to ensure that the input given is valid.
        //        For example, if the user enters 'abc' instead of a number.
        //
        std::cout << "Enter n: ";
        std::cin  >> n;

        std::cout << "Enter k: ";
        std::cin  >> k;

        input_valid = n > k;
    }

    unsigned long result = factorial(n) / (factorial(k) * factorial(n - k));

    std::cout << n << "! / (" << k << "! * (" << n << " - " << k << ")!) = " << result << std::endl;
}

```


P.S.  Earlier I had posted code that employed the use of good() when checking the status of the istringstream object.  That was an error;  I should have been checking the status with fail().

---

### Post by spacerocket on 2014-05-10
```
g++ Documents/combination.cpp -o combination
Documents/combination.cpp: In function ‘int main(int, char**)’:
Documents/combination.cpp:53:100: error: expected ‘}’ at end of input
     std::cout << n << "! / (" << k << "! * (" << n << " - " << k << ")!) = " << result << std::endl;

```


Sorry, I understand maybe 20% of the code, I have looked at that C++ tutorial, but can`t understand. How about that array question I posted earlier.

---

### Post by dwhitney67 on 2014-05-10
> **spacerocket said:**
> ```
g++ Documents/combination.cpp -o combination
Documents/combination.cpp: In function ‘int main(int, char**)’:
Documents/combination.cpp:53:100: error: expected ‘}’ at end of input
     std::cout << n << "! / (" << k << "! * (" << n << " - " << k << ")!) = " << result << std::endl;

```
You did not copy/paste the code in its entirety.  You are probably missing the ending curly bracket.

[quote]
Sorry, I understand maybe 20% of the code, I have looked at that C++ tutorial, but can`t understand. How about that array question I posted earlier.
Your questions are not crystal clear.  If you had a question about an array, I did not see it.  Also, just so we are clear, a statement containing a question should end with a question mark (e.g. What does a question mark look like?).

---

### Post by spacerocket on 2014-05-10
Well, is it possible that you explain what each of the functions in the code do and why they are implemented like they are.

To the array issue, why can´t I write a 8x8 board for a chess engine? That was my original project. I think combinations are important in evaluation and search. [http://chessprogramming.wikispaces.com/8x8+Board](http://chessprogramming.wikispaces.com/8x8+Board).

I can use arrays I think. Arrays are found here: [http://www.cplusplus.com/doc/tutorial/arrays/](http://www.cplusplus.com/doc/tutorial/arrays/)

I would write 

```
void init_board()
{
for (int r = 0; r < 8; ++i)
{
for (int c = 0; c < 8; ++i)
{
board[64] ={0,  8, 16, 24, 32, 40, 48, 56,
              1,  9, 17, 25, 33, 41, 49, 57,
              2, 10, 18, 26, 34, 42, 50, 58,
              3, 11, 19, 27, 35, 43, 51, 59,
              4, 12, 20, 28, 36, 44, 52, 60,
              5, 13, 21, 29, 37, 45, 53, 61,
              6, 14, 22, 30, 38, 46, 54, 62,
              7, 15, 23, 31, 39, 47, 55, 63};
 ;
```


Now you migh start wondering why the numbers are in this order; well I know. If you look at the chessprogramming link I posted above you can notice a similarity between the 8x8 board picture and the order of my numbers: First go up the first rank, then return to the second file and go up that and so on. It was also like this in parrots source code (not this exact code, I constructed it myself).

That is just an example how to use arrays I guess.

---

### Post by dwhitney67 on 2014-05-10
> **spacerocket said:**
> Well, is it possible that you explain what each of the functions in the code do and why they are implemented like they are.

First of all, this is not a teaching forum.  It is expected that you would take the time to learn the basic constructs of a programming language before delving into Tic-Tac-Toe games or other complex problems.

I assume you know what a function is, what an array is, and how they are used.  I also assume you know how to collect user input.  If not, then I suggest that you find a good C++ book and start reading it at Chapter 1.  During your studies don't skip chapters of the book because your interests only lie in designing software for a space rocket.  Learn the basics first, then come back with intelligent questions.

So, before you switch topics back to your other project (chess engine?  or TTT?), if you have any questions regarding the "Square Root Algorithm" which some how lead to computing factorials, I would suggest that you carefully examine what your goals are.

PS:

> **spacerocket said:**
> 
I would write 

```
void init_board()
{
for (int r = 0; r < 8; ++i)
{
for (int c = 0; c < 8; ++i)
{
board[64] ={0,  8, 16, 24, 32, 40, 48, 56,
              1,  9, 17, 25, 33, 41, 49, 57,
              2, 10, 18, 26, 34, 42, 50, 58,
              3, 11, 19, 27, 35, 43, 51, 59,
              4, 12, 20, 28, 36, 44, 52, 60,
              5, 13, 21, 29, 37, 45, 53, 61,
              6, 14, 22, 30, 38, 46, 54, 62,
              7, 15, 23, 31, 39, 47, 55, 63};
 ;
```

Yep, you could write that code, but good luck in getting a compiler to deal with it.

---

