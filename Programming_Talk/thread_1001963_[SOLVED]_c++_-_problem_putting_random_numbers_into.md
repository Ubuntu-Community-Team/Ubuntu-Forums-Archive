---
title: "[SOLVED] c++ - problem putting random numbers into an array"
date: 2008-12-04
forum: Programming Talk
---

### Post by Despot Despondency on 2008-12-04
Hi, I'm having trouble writing a class called potential. I want to initialize it with a vector of integers such that 

1) it creates an array of random numbers 

2) the length of the array is equal to the product of the integers

So here's my code 

potential.cpp

```

#include <vector>

#include "variable.h"
#include "potential.h"
#include "uniform.h"

using std::vector;

potential::potential(vector<int> vars){

  int size = 1;

  for(vector<int>::const_iterator iter = vars.begin(); iter != vars.end(); ++iter)
    size = size*(*iter);

  seed();

  for(int i = 0; i < size; i++)
      values.push_back(unif());
}

```

potential.h

```

#include <vector>

class potential {

 public:
  potential(std::vector<int>);
  std::vector<double> getValues() const {return values;}
 private:
  std::vector<double> values;
};

```

My code to test the potential class, test_potential.cpp

```

#include <iostream>
#include <vector>

#include "potential.h"
#include "uniform.h"

using std::cin;
using std::cout;
using std::endl;
using std::vector;

int main(){

  cout << "Please enter the number of states of your variables ";

  int states = 0;

  vector<int> variables;

  while(cin >> states){
    variables.push_back(states);
  }

  potential x(variables);

  for(vector<double>::iterator iter = x.getValues().begin(); iter != x.getValues().end(); iter++){
    cout << *iter << endl;
  }
  return 0;

}

```

The uniform.h is just a header file for various uniform random number generators.

```
#include <cstdlib>
#include <cmath>
#include <ctime>

#include "uniform.h"

using namespace std;


double unif(){
  return rand() / double(RAND_MAX);}

double unif(double a, double b){
  return (b - a)*unif() + a;
}

void seed(){
  srand(time(0));
}
```

Now when I try 
~/Documents/Programming$ ./test_potential
Please enter the number of states of your variables 2 3 n

I get

0.812538
0.883743
0.283997
0.611596
0.965395
0.75795

so it seems to work fine. Now when I try 
~/Documents/Programming$ ./test_potential
Please enter the number of states of your variables 9 n

It seems to go through a large loop of zeros and then I get a segmentation fault. Any ideas why I'm having this problem? I'm really rather confused so any help would be appreciated.

---

### Post by dwhitney67 on 2008-12-04
The code you posted did not compile.  Nevertheless, I sorted out the issues and built your application and witnessed the same results you reported.

To fix the issue, I modified your potential.h (and .cpp) as follows:
[php]
#ifndef POTENTIAL_H
#define POTENTIAL_H

#include <vector>

class potential {

 public:
  potential(const std::vector<int>&);
  const std::vector<double>& getValues() const {return values;}
 private:
  std::vector<double> values;
};

#endif
[/php]
Note the change in the constructor; it is not really needed, but saves the application the hassle of making a copy of the vector that is passed as a parameter.

The main change is the signature for the getValues().  This ensures that you get the same copy of 'values' when you request it in the main function.

You should use a const_iterator in lieu of regular interator in the main function.

Also, you need to clean up your files to remove unneeded #include statements, and also to add multiple-inclusion guards in the header files.

In a .cpp file, always include the associated header file first, then system header files (e.g. vector) last.

---

### Post by dribeas on 2008-12-04
Besides correcting some issues in the code, which probably come from copying into the post and some other that should not affect the problem (you should really use inclusion guards, see example below), I have runned the program without the problems you describe:

> 
Please enter the number of states of your variables 9 (here I pressed ^D to close the input stream)
0.0880055
0.108383
0.59247
0.637582
0.839511
0.658568
0.544249
0.189661
0.626565


I am currently running i686-apple-darwin9-g++-4.0.1. What compiler are you using?

The small corrections to the code were reagarding this two issues:

[B]Function definitions in header files
[/B]
Defining functions in header files (not just declaring) will force the compiler into creating the symbol for all compilation units. This will later on end in a linker error where a symbol (the function) is defined in more than one compilation unit. The exception are inlined functions, as the compiler will not generate the symbols in the compilation units but rather push the code into the calling method.

[B]Header guards:
[/B]```

// file: a.h
#ifndef _A_H_ // something that identifies your header file and that this is a header guard
#define _A_H_

// ... all header definitions

#endif _A_H_

```

What the guard does is that the first time that a header is included the preprocessor enters the ifndef body and includes all declarations. At the same time it defines a particular preprocessor symbol (_A_H_ in this case) so that the next inclussion of the same header does not really enter all definitions into the compiler unit. This avoids redefinitions of symbols.

---

### Post by Despot Despondency on 2008-12-04
Hey, thanks for your replies. Thanks dwhitney67, you're a legend, used your changes and it all worked perfectly.

Thanks for your advice dribeas, I had my first redefinition error tonight actually. Cheers for the advice though. I will start writing header guards from now on. Thanks for the tip on closing the input stream, that's been bugging me for a while.

I still don't really understand where the error happened in the first place though. I'm using gcc version 4.2.4.

---

### Post by dwhitney67 on 2008-12-04
This line of code in your main function is (was) causing the problem:
```

for(vector<double>::iterator iter = x.getValues().begin(); iter != x.getValues().end(); iter++){

```
Here you are comparing two iterators (iter and end()) from _two_ different vectors.  Each time getValues() is called, a new vector is created, and this vector is not the same as the one that was obtained in the initialization portion of the for-loop.

If you had changed it to be:
```

vector<double> randValues = x.getValues();

for(vector<double>::iterator iter = randValues.begin(); iter != randValues.end(); iter++){
...

```
then it would have worked fine.

Anyhow, by changing the signature of getValues() as I posted earlier, you are always assured to get the reference to the vector that is stored in the potential class object.

---

### Post by Despot Despondency on 2008-12-04
That makes sense. Thanks once again. :)

---

