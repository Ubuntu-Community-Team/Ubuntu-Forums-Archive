---
title: "Libraries in Code::Blocks"
date: 2008-07-08
forum: Packaging and Compiling Programs
---

### Post by terminator14 on 2008-07-08
I'm trying to learn some C++ during my time off from school this summer, and would like to get a compiler working well in Ubuntu to test some stuff from the book I'm reading. So far, I've tried Anjuta, g++ (in console), and my latest attempt is with Code::Blocks. I didn't like the way Anjuta would run, and since g++ is only a compiler and not an editor that organizes the code and shows you your mistakes, I've moved to Code::Blocks which seems to organize the code well and has easy to use compile buttons. Unfortunately however I'm having a bit of a problem with getting code to work with libraries. Here's what I mean:

When I run the following code,

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

copied and pasted directly from the first example of code in the C++ for Dummies pdf, and compile it with either g++ or Code::Blocks (my Code::Blocks is using the g++ compiler so the errors are exactly the same), I get the following errors:

```
1.cpp:14: error: stray ‘\342’ in program
1.cpp:14: error: stray ‘\200’ in program
1.cpp:14: error: stray ‘\234’ in program
1.cpp:14: error: stray ‘\342’ in program
1.cpp:14: error: stray ‘\200’ in program
1.cpp:14: error: stray ‘\235’ in program
1.cpp:25: error: stray ‘\342’ in program
1.cpp:25: error: stray ‘\200’ in program
1.cpp:25: error: stray ‘\234’ in program
1.cpp:25: error: stray ‘\342’ in program
1.cpp:25: error: stray ‘\200’ in program
1.cpp:25: error: stray ‘\235’ in program
1.cpp:29: error: stray ‘\342’ in program
1.cpp:29: error: stray ‘\200’ in program
1.cpp:29: error: stray ‘\234’ in program
1.cpp:29: error: stray ‘\342’ in program
1.cpp:29: error: stray ‘\200’ in program
1.cpp:29: error: stray ‘\235’ in program
1.cpp: In function ‘int main(int, char**)’:
1.cpp:14: error: ‘Enter’ was not declared in this scope
1.cpp:14: error: expected `;' before ‘the’
1.cpp:25: error: ‘Fahrenheit’ was not declared in this scope
1.cpp:25: error: expected `;' before ‘value’
1.cpp:29: error: ‘PAUSE’ was not declared in this scope
```

I assume it's not an error in the code, since it is a published book, and seems complete to me, so it looks like the compiler isn't including the libraries it is told to. Is that the problem? If so how can I fix this?

---

### Post by WW on 2008-07-09
Apparently the double quotes in the PDF file from which you copied the code are not really regular double quotes.  Here is the code again, with the double quotes fixed:

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

```
By the way, this
```

  system("PAUSE");

```
won't work; there is no PAUSE command in Linux. A possible alternative is
```

  system("read -p 'Hit Enter to continue. '");

```
but, depending on how you run the program, you might not even need this command.

---

### Post by terminator14 on 2008-07-09
Thanks. I'll give that a try when I get a chance and post back the results.

---

### Post by terminator14 on 2008-07-10
Works great! Finally I can test code in Ubuntu in a nice looking compiler. Thanks a lot.

---

### Post by charnet3d on 2008-11-08
Hello everyone, I'm new to ubuntu and I want to continue practicing C, I tried the instruction:   > system("read -p 'Hit Enter to continue. '");  but it gives me some kind of error in the output window and doesn't wait for a key press, here what it says:   > Hit Enter to continue. read: 1: arg count
the same problem goes with the NetBeans IDE.

but when I type command "read -p 'Hit Enter to continue.'" in a terminal it works perfectly.

can someone tell me what may have gone wrong?

---

