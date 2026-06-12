---
title: "Undefined reference to my function"
date: 2010-09-16
forum: Programming Talk
---

### Post by loopyloop on 2010-09-16
I am extremely new to coding in C++ (I started learning yesterday!) So please bare with me!

I keep getting the following error code:

```
/tmp/cc6zQ9Li.o(.text+0x251): In function `main':
: undefined reference to `Factorial(int)'
collect2: ld returned 1 exit status

```

This is my main.cc:

```
#include <cmath>
#include <iomanip>
#include <iostream>
#include "factorial.h"

using namespace std;
 
int main(){
    int nmax;
        cout <<"Enter the maximum value to be used for n"<<endl;
        cin >> nmax;

    for (int i=1; i<=nmax; i++){
      int n = i;
      cout.width(5); cout << n;

      double sn = sqrt(n);
      cout.setf(ios::fixed);
      cout.precision(5);
      cout.width(12); cout << sn;

      double lnn = log(n);
      cout.setf(ios::fixed);
      cout.precision(5);
      cout.width(12); cout << lnn;

      int M = Factorial (n);
      cout << M << endl;
     
    }
}
```

This is factorial.cc:

```
#include "factorial.h"

int Factorial(int M){

int i, factorial=1;

	for (i=1; i<=M; i++)
	{
		factorial = factorial * i;
	}
	return factorial;
}
```


And factorial.h:

```
#ifndef FACTORIAL_H
#define FACTORIAL_H

// function to find the factorial

int Factorial(int);

#endif
```

---

### Post by dwhitney67 on 2010-09-16
Try building your project using ***both*** .cc files.  For example:
```

g++ main.cc factorial.cc -o factorial

```

---

### Post by loopyloop on 2010-09-16
Ah! It works, thank you!! :)

---

### Post by dwhitney67 on 2010-09-16
Please mark the thread as "solved".

---

