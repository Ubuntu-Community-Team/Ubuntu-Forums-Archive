---
title: "trouble with g++"
date: 2009-12-17
forum: Programming Talk
---

### Post by somedaypilot on 2009-12-17
I am just getting started learning C++, and I am having some issues. I am trying to make a hello world with the following code:

// firsttest.gcc

#include <iostream> // for user input/output
//#include <fstream> // for file input/output
//#include <cmath> // for advanced math

using namespace std;

int main ()
{
 cout << "it compiled";
 cout << '\n';
 return 0;
}

saved as firsttest.gcc, compiled it using:

g++ -Wall firsttest.gcc

and I got this error:

/usr/bin/ld:firsttest.gcc: file format not recognized; treating as linker script
/usr/bin/ld:firsttest.gcc:1: syntax error
collect2: ld returned 1 exit status

I have build-essentials installed. I looked up ld and saw that it is the linker, but I have no idea how to fix it. it worked on my friend's computer also running 9.10 with the same build-essential installed (I think)

Any ideas?

---

### Post by dribeas on 2009-12-17
The compiler is not detecting the type of file you are passing onto it (.gcc is not a common extension for c++ code). You can either change your code file to have one of the standard recognized extensions (.cpp, .cxx, .C... probably others) or else you must provide the compiler with a hint to determine the type of file (-x c++)

---

### Post by somedaypilot on 2009-12-17
Eureka. Thank you. It works now

---

