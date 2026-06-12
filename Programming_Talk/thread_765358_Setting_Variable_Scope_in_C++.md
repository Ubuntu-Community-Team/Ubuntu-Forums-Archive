---
title: "Setting Variable Scope in C++"
date: 2008-04-24
forum: Programming Talk
---

### Post by vergenzt on 2008-04-24
In C++, is there any way to expressly set the scope of a variable?  

I need my program to declare an array of a given size from within 
a function (given by an argument), but it needs to be accessible 
globally.  Any advice would be appreciated.

---

### Post by LaRoza on 2008-04-24
> **vergenzt said:**
> In C++, is there any way to expressly set the scope of a variable?  

I need my program to declare an array of a given size from within 
a function (given by an argument), but it needs to be accessible 
globally.  Any advice would be appreciated.

The scoping rules are reliable, the compiler follows them.

This sounds like a job for pointers and using the heap.

---

### Post by lnostdal on 2008-04-24
use

```

extern int* your_array;

```

..in a common header file ..note that this is a declaration only

then define the variable in, say, the same file you have the function that assigns to it or initializes it

```

int* your_array;

void setIt(unsigned int size){
  your_array = malloc(size * sizeof(int));
}

```

..orsomethinglikethat..

if this doesn't work for you, other languages have better options like:

```

(defvar *your-array*)

(defun set-it (size)
  (setf *your-array* (make-array size :element-type 'fixnum)))

```

..no need to worry about linking etc.

---

### Post by dwhitney67 on 2008-04-24
Here's how in C++:
[PHP]#include <iostream>

using namespace std;


void function( int **array, const int sizeNeeded )
{
  *array = new int[ sizeNeeded ];
}

int main()
{
  int *array = 0;

  cout << "verify array is unallocated; array = " << array << endl;

  // allocate space for array
  function( &array, 10 );

  cout << "verify array is allocated; array = " << array << endl;

  for ( int i = 0; i < 10; ++i )
  {
    array[i] = (i + 1) * 2;
    cout << "array[" << i << "] = " << array[i] << endl;
  }

  // don't forget to clean up allocated memory!
  delete []array;

  return 0;
}[/PHP]

Please don't degrade your C++ code with global variables!  If you need globals, then you might as well program in C.

---

### Post by LaRoza on 2008-04-24
> **dwhitney67 said:**
> 

Please don't degrade your C++ code with global variables!  If you need globals, then you might as well program in C.

Why C? That code you posted could easily be written in C as well.

---

### Post by dwhitney67 on 2008-04-24
Global variables should be avoided in OOP.  At least that is what I was taught/learned.  Try porting a C++ application replete with globals variables to Java.  It ain't gonna happen easily.

---

### Post by CptPicard on 2008-04-24
Well... wrt. Java you can always fill a class with public statics, or use Singletons :)

---

### Post by LaRoza on 2008-04-24
> **dwhitney67 said:**
> Global variables should be avoided in OOP.  At least that is what I was taught/learned.  Try porting a C++ application replete with globals variables to Java.  It ain't gonna happen easily.

I see now. That makes sense.

> **CptPicard said:**
> Well... wrt. Java you can always fill a class with public statics, or use Singletons :)

Singleton: Fancy name for a global object.

---

### Post by Sporkman on 2008-04-24
> **CptPicard said:**
> Well... wrt. Java you can always fill a class with public statics, or use Singletons :)

...or make a [God object]("http://en.wikipedia.org/wiki/God_object")...

---

