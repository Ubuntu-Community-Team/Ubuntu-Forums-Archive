---
title: "gcc errors"
date: 2007-09-10
forum: Programming Talk
---

### Post by fourthdimension on 2007-09-10
Hey All

I'm trying to teach myself C++ from "C++ for Dummies".  I copied an example program from the book to see if I understood how to compile it using gcc, but I got some errors.  

This is the program:
```
//
// Program to convert temperature from Celsius degree
// units into Fahrenheit degree units:
// Fahrenheit = Celsius * (212 - 32)/100 + 32
//
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;
int main(int nNumberofArgs, char* pszArgs[])
{

                       // enter the temperature in Celsius
                       int celsius;
                       cout << “Enter the temperature in Celsius:”;
                       cin >> celsius;
                       // calculate conversion factor for Celsius
                       // to Fahrenheit
                       int factor;
                       factor = 212 - 32;
                       // use conversion factor to convert Celsius
                       // into Fahrenheit values
                       int fahrenheit;
                       fahrenheit = factor * celsius/100 + 32;
                       // output the results (followed by a NewLine)
                       cout << “Fahrenheit value is:”;
                       cout << fahrenheit << endl;
                       // wait until user is ready before terminating program
                       // to allow the user to see the program results
                       system(“PAUSE”);
                       return 0;
                     }
```






And these are the errors:

```
mymachine:~$ gcc -o Temperature_Conversion_Test_Program '/home/secondgenesis/Desktop/Temparature_Conversion_Test.c' 
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:6:18: error: cstdio: No such file or directory
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:7:19: error: cstdlib: No such file or directory
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:8:20: error: iostream: No such file or directory
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:9: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘namespace’
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c: In function ‘main’:
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: ‘cout’ undeclared (first use in this function)
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: (Each undeclared identifier is reported only once
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: for each function it appears in.)
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: stray ‘\342’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: stray ‘\200’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: stray ‘\234’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: ‘Enter’ undeclared (first use in this function)
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: expected ‘;’ before ‘the’
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: stray ‘\342’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: stray ‘\200’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:15: error: stray ‘\235’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:16: error: ‘cin’ undeclared (first use in this function)
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:26: error: stray ‘\342’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:26: error: stray ‘\200’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:26: error: stray ‘\234’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:26: error: ‘Fahrenheit’ undeclared (first use in this function)
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:26: error: expected ‘;’ before ‘value’
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:26: error: stray ‘\342’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:26: error: stray ‘\200’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:26: error: stray ‘\235’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:27: error: ‘endl’ undeclared (first use in this function)
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:30: error: stray ‘\342’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:30: error: stray ‘\200’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:30: error: stray ‘\234’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:30: error: stray ‘\342’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:30: error: stray ‘\200’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:30: error: stray ‘\235’ in program
/home/secondgenesis/Desktop/Temparature_Conversion_Test.c:30: error: ‘PAUSE’ undeclared (first use in this function)

```

I used the same process to compile other test programs without errors, and since I got the program from the book, I wouldn't expect it to be flawed.  By the way, I've installed the build-essential package.

Does anyone know what's going on?
Thanks a lot.

---

### Post by aks44 on 2007-09-10
.c files are, well... C files.
gcc is a C compiler.


If you want to compile C++ code, rename your source file as .cpp and use the g++ compiler (same command line options). I'm pretty sure it will solve your problem.

---

### Post by ubuntukerala1980 on 2007-09-10
Change " use g++
:lolflag:



//
// Program to convert temperature from Celsius degree
// units into Fahrenheit degree units:
// Fahrenheit = Celsius * (212 - 32)/100 + 32
//
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;
int main(int nNumberofArgs, char* pszArgs[])
{

                       // enter the temperature in Celsius
                       int celsius;
                       cout << "Enter the temperature in Celsius:";
                       cin >> celsius;
                       // calculate conversion factor for Celsius
                       // to Fahrenheit
                       int factor;
                       factor = 212 - 32;
                       // use conversion factor to convert Celsius
                       // into Fahrenheit values
                       int fahrenheit;
                       fahrenheit = factor * celsius/100 + 32;
                       // output the results (followed by a NewLine)
                       cout << "Fahrenheit value is:";
                       cout << fahrenheit << endl;
                       // wait until user is ready before terminating program
                       // to allow the user to see the program results
                       system("PAUSE");
                       return 0;
                     }

---

### Post by ubuntukerala1980 on 2007-09-10
If you need some help please ask
:guitar:

---

### Post by fourthdimension on 2007-09-10
Thanks for the quick response!  Well, unless I missed something again, I changed what you said, but the result isn't much different...

```
mymachine:~$ g++ -o TEST3 '/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp' 
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:15: error: stray &#8216;\342&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:15: error: stray &#8216;\200&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:15: error: stray &#8216;\234&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:15: error: stray &#8216;\342&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:15: error: stray &#8216;\200&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:15: error: stray &#8216;\235&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:26: error: stray &#8216;\342&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:26: error: stray &#8216;\200&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:26: error: stray &#8216;\234&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:26: error: stray &#8216;\342&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:26: error: stray &#8216;\200&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:26: error: stray &#8216;\235&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:30: error: stray &#8216;\342&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:30: error: stray &#8216;\200&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:30: error: stray &#8216;\234&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:30: error: stray &#8216;\342&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:30: error: stray &#8216;\200&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:30: error: stray &#8216;\235&#8217; in program
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp: In function &#8216;int main(int, char**)&#8217;:
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:15: error: &#8216;Enter&#8217; was not declared in this scope
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:15: error: expected `;' before &#8216;the&#8217;
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:26: error: &#8216;Fahrenheit&#8217; was not declared in this scope
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:26: error: expected `;' before &#8216;value&#8217;
/home/secondgenesis/Desktop/C++/Temparature_Conversion_Test.cpp:30: error: &#8216;PAUSE&#8217; was not declared in this scope

```

---

### Post by ubuntukerala1980 on 2007-09-10
mv fahren.txt  fahren.cc
 (fahren.txt is my attachemnt) 

g++ -o farehn farehn.cc

./farehn

:guitar:

---

### Post by LaRoza on 2007-09-10
Your quotes didn't look right, and are not the same as these " ", so they caused an error.

[php]
#include <iostream>
using namespace std;
int main(int argc, char ** argv)
{


                       int celsius;
                       int factor;
                       int fahrenheit;
//Shouldn't fahrenheit be a float?

                       cout << "Enter the temperature in Celsius:";
                       cin >> celsius;

                       factor = 212 - 32;


                       fahrenheit = factor * celsius/100 + 32;

                       cout << "Fahrenheit value is:";
                       cout << fahrenheit << endl;

                       system("PAUSE");
                       return 0;
}
[/php]


```

g++ sourceFile.cpp
./a.out

```

---

### Post by darsu on 2007-09-10
What editor did you use to write the code? Those stray characters might be "gremlins", special characters which are invisible because the editor can't display them. I sometimes get them in XEmacs by hitting AltGr-space instead of space, and need to fix it by rewriting the line.

---

### Post by aks44 on 2007-09-10
Oh my, didn't notice that at first glance... but looks like you're not using plain double quotes **"** but rather some strange **&#8220;** (kiran.bhaskaran.nair was right).

EDIT: lol, 3 answers in a row :)

---

### Post by the_unforgiven on 2007-09-10
You seem to have typed it in an editor that wrote the file in UTF-8 (or some variant of UNICODE) format. You need to convert it into plain ASCII and then try to compile.

---

### Post by ubuntukerala1980 on 2007-09-10
Try to use vi editor
I am addicted to it :guitar:

---

### Post by LaRoza on 2007-09-10
For an editor use GEdit, Kwrite, Kate, or Vim.

---

### Post by fourthdimension on 2007-09-10
Thanks.  Now it works, though when I run the program I get one last error:

```
sh: PAUSE: not found

```

I don't understand... what changed?  Was it all a matter of the .cc extension?

---

### Post by LaRoza on 2007-09-10
> **fourthdimension said:**
> 
```
sh: PAUSE: not found

```


system() executes a shell commandl. PAUSE is not in bash, so sh (shell) is saying it can't do that. You can use sleep in place of PAUSE but don't, just eliminate that line. You are invoking from the command line, and that line is useless in that context.

It is for Windows users who are running the program by double clicking, and PAUSE is the DOS command to wait for the user to press the "any" key, before continuing.

---

### Post by fourthdimension on 2007-09-10
> **darsu said:**
> What editor did you use to write the code? Those stray characters might be "gremlins", special characters which are invisible because the editor can't display them. I sometimes get them in XEmacs by hitting AltGr-space instead of space, and need to fix it by rewriting the line.

I used the default test editor called "Text Editor".

---

### Post by the_unforgiven on 2007-09-10
> **LaRoza said:**
> system() makes a system call. PAUSE is not in bash, so sh (shell) is saying it can't do that. You can use sleep in place of PAUSE but don't, just eliminate that line. You are invoking from the command line, and that line is useless in that context.

Not quite right.
System call is a totally different concept.
Take a look at the man page of system(3):
[http://linux.die.net/man/3/system](http://linux.die.net/man/3/system)

---

### Post by LaRoza on 2007-09-10
> **the_unforgiven said:**
> Not quite right.
System call is a totally different concept.


Thanks, just a stupid error in typing, not thinking about what I was saying. I should have know better...

---

### Post by fourthdimension on 2007-09-10
So g++ should only be used for compiling source with a .cc extension?

---

### Post by LaRoza on 2007-09-10
> **fourthdimension said:**
> So g++ should only be used for compiling source with a .cc extension?

It also works with .c files.

Usually, I use .cpp for C++ files, and that works with g++.

---

### Post by fourthdimension on 2007-09-10
Thanks, everyone!

---

