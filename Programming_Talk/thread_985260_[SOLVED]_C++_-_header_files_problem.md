---
title: "[SOLVED] C++ - header files problem"
date: 2008-11-17
forum: Programming Talk
---

### Post by Despot Despondency on 2008-11-17
Hi, I'm having some problems using header files with C++. I've got my main program, which calculates a specified number of squares and prints them off in aligned columns. It's kept in a file called exercise4_2.cpp as follows

```

#include <iostream>
#include <algorithm>
#include <string>
#include <vector>
#include <ios>
#include <iomanip>
#include "numberOfDigits.h"

using std::vector;
using std::cout;
using std::endl;
using std::setw;
using std::cin;

int main(){

  cout << "Enter the number of squares you wish to calculate: ";
 
  int n = 0;
  cin >> n;

  vector<int> squares;

  for(int i = 0; i < n; i++){
    squares.push_back(i*i);
  }

  int square_length = numberOfDigits(squares[n - 1]);

  int length = numberOfDigits(n - 1);

  for(int i = 0; i < n; i++){
    cout << setw(length);
    cout << i;
    cout << setw(square_length + 1);
    cout << squares[i] << endl;
  }

  return 0;
}

```

It uses a function called numberOfDigits, which I wrote, and which is kept in the file numberOfDigits.cpp which is given by

```

#include "numberOfDigits.h"

int numberOfDigits(int n)
{
  int length = 0;

  while(n >= 1){
    length++;
    n = n/10;
  }

  return length;
}

```

and then I've got my header file, numberOfDigits.h, which is 

```

#ifndef GUARD_numberOfDigits_h
#define GUARD_numberOfDigits_h

int numberOfDigits(int);

#endif

```

Now when I try to compile exercise4_2.cpp I get the following error

```

g++ -o exercise4_2 ./exercise4_2.cpp
/tmp/cccmXCrU.o: In function `main':
exercise4_2.cpp:(.text+0x230): undefined reference to `numberOfDigits(int)'
exercise4_2.cpp:(.text+0x241): undefined reference to `numberOfDigits(int)'
collect2: ld returned 1 exit status


```

I'm confused. How come it can't find the function numberOfDigits?

---

### Post by dynamethod on 2008-11-17
in your header file you have the function Decleared as:

int numberOfDigits(**int**)

but in the source code the function is defined as:

int numberOfDigits(**int n**)


int numberOfDigits(**int n**) != int numberOfDigits(**int**)


I think anyway, dont quote me im a noob.

---

### Post by Despot Despondency on 2008-11-17
Hi, thanks for your response. My book says that in the header file we ignore the parameter names because the are irrelevant without the function body. This is why I have don't like this in the header file.

---

### Post by Despot Despondency on 2008-11-17
Hi, I managed to get it to work. Just changed the way I compiled the program. Cheers for your time anyway.

---

### Post by ggaaron on 2008-11-17
You compile it wrong. You should do something like this:
gcc -c file.c
gcc -c included_file.c
gcc -o executable file.o included_file.o
For c++ it will be g++. First two commands compile your code and the third links it (-c switch disables linking). I thing that you can also do:
gcc -o executable file.c included_file.c
This becomes bothering though when you've got more files. I personally use Makefiles even for little compiles - several lines with only a few words in it will give you the power to only write 'make' and get compiled executables.

---

