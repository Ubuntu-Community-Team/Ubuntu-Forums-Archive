---
title: "c++ proper linking"
date: 2008-10-07
forum: Programming Talk
---

### Post by shadylookin on 2008-10-07
I have 3 files DynamicArray.h DynamicArray.cpp and Driver.cpp. 

when I type 
g++ -oFile ./Driver.cpp 
```
Driver.cpp:(.text+0x196): undefined reference to `DynamicArray::DynamicArray()'
Driver.cpp:(.text+0x1a7): undefined reference to `DynamicArray::addAtBack(double)'
Driver.cpp:(.text+0x1b8): undefined reference to `DynamicArray::addAtBack(double)'
Driver.cpp:(.text+0x1c9): undefined reference to `DynamicArray::addAtBack(double)'
Driver.cpp:(.text+0x1da): undefined reference to `DynamicArray::addAtBack(double)'
Driver.cpp:(.text+0x1eb): undefined reference to `DynamicArray::addAtBack(double)'
/tmp/cc6bz2La.o:Driver.cpp:(.text+0x1fc): more undefined references to `DynamicArray::addAtBack(double)' follow
/tmp/cc6bz2La.o: In function `main':
Driver.cpp:(.text+0x25a): undefined reference to `DynamicArray::length()'
Driver.cpp:(.text+0x274): undefined reference to `DynamicArray::DynamicArray(int)'
Driver.cpp:(.text+0x285): undefined reference to `DynamicArray::addAtBack(double)'
Driver.cpp:(.text+0x296): undefined reference to `DynamicArray::addAtBack(double)'
Driver.cpp:(.text+0x2a7): undefined reference to `DynamicArray::addAtBack(double)'
Driver.cpp:(.text+0x2b0): undefined reference to `DynamicArray::length()'
Driver.cpp:(.text+0x2c5): undefined reference to `DynamicArray::~DynamicArray()'
Driver.cpp:(.text+0x2d8): undefined reference to `DynamicArray::~DynamicArray()'
Driver.cpp:(.text+0x2e7): undefined reference to `DynamicArray::~DynamicArray()'
Driver.cpp:(.text+0x302): undefined reference to `DynamicArray::~DynamicArray()'
collect2: ld returned 1 exit status

```

when I type
g++ -c ./DynamicArray.cpp
g++ -c ./Driver.cpp
g++ -oOutput -L/home/shadylookin/Desktop/ -lDynamicArray ./Driver
I get this error
```

/usr/bin/ld: cannot find -lDynamicArray.h.gch
collect2: ld returned 1 exit status

```

can someone tell what I'm doing wrong?

thanks in advance

---

### Post by dwhitney67 on 2008-10-08
Try this, and report back if it does not work.

```

g++ Driver.cpp DynamicArray.cpp -o Output

```

---

### Post by gnusci on 2008-10-08
I think he need to add the actual directory to search for *.h files, use this one:
[PHP]
$ g++ Driver.cpp DynamicArray.cpp -o Output -I.[/PHP]

---

### Post by dwhitney67 on 2008-10-08
> **gnusci said:**
> I think he need to add the actual directory to search for *.h files, use this one:
[PHP]
$ g++ Driver.cpp DynamicArray.cpp -o Output -I.[/PHP]

Not if the header file is in the current directory with the source files.

The ./, /usr/include, and /usr/include/c++/*gcc-version* are known to the compiler, and hence do not need to be specified.

Note these paths are built into the compiler, thus the path to the C++ header files may differ than that shown above.  If I recall correctly, Fedora uses a different path.

---

### Post by shadylookin on 2008-10-08
> **dwhitney67 said:**
> Try this, and report back if it does not work.

```

g++ Driver.cpp DynamicArray.cpp -o Output

```

Thanks this works. Unfortunately now my compiled code gives a segmentation fault. I'm guessing it have to do with the fact that I tried reinitializing an array. I want to assign a predefined array to another array. 

It's simple in java the code would be something like this
```

double array[] = new double[10];
double tmp[] = new double[20];
array = tmp;

```

any advice on how to pull this off in c++?

---

### Post by snova on 2008-10-08
There's no obvious way to do that in C++. It's much more low-level than Java. Think about arrays as they are, because that's what you get- nothing more. In this case an array is a pointer to a location in memory. That location and all addresses from that location up to the length makes up the array.

To copy, then, you have to manually move each piece. Object oriented wrappers will often provide routines to do this transparently, but if you're just using plain old arrays, there is no builtin way to copy entire arrays in a single statement. (Unless the array is one element long. :))

In addition, if you moved an array of 20 elements over an array of 10 elements, you'd be accessing memory past the end of the array, and that's not good, and possibly even the cause of your error. Off-by-one mistakes could also be the cause, among dozens of other potential conditions.

---

### Post by nvteighen on 2008-10-08
For your error, the best would be you use a debugger. For that, compile your program with the command you were given, adding the **-g** flag (which creates a debuggable binary), like this:

```

g++ -g Driver.cpp DynamicArray.cpp -o Output

```Then, start the debugger. gcc is associated to gdb (GNU Debugger). Start using:
```

gdb *<program>*

```Basic gdb commands are **run** (which starts the program until an error is found or execution stops), **break** which sets a breakpoint (it accepts line numbers, function names and some other stuff... for line numbers, which may be interesting, use **break *<source filename>*:*<line number>***), **continue** (when you want to resume execution), Ctrl+C (which interrupts execution) and **quit** (to exit).

There are also other nice stuff you can do in gdb, but refer to them using the **help** command or the manual.

---

### Post by dribeas on 2008-10-08
> **shadylookin said:**
> ```

double array[] = new double[10];
double tmp[] = new double[20];
array = tmp;

```


That in Java will make two reference to the same array, which might not be what you want. If it is, then use pointers, that are closer to Java references:

```

double *array; // don't create memory for nothing
double *tmp = new double[20];
// use tmp array:
tmp[ 5 ] = 5.0;

array = tmp; // copy pointers

delete [] array; // don't forget to free memory

```

Note that if array did point to an allocated block of memory you will have to free it before the assignment or the memory will be lost.

Of course, that is still low level, I would advice using std::vector instead of plain old arrays:

```

std::vector<double> array; // default constructed
std::vector<double> tmp;
// use / fill in tmp
array = tmp; // makes a copy of the whole vector contents

```

A couple of difference in this code snippet: unlike Java/pointer versions, the assignment does make a copy, that is, it reserves enough memory and applies copy construction to fill in the array elements.

> **snova said:**
> To copy, then, you have to manually move each piece. Object oriented wrappers will often provide routines to do this transparently, but if you're just using plain old arrays, there is no builtin way to copy entire arrays in a single statement. (Unless the array is one element long. :))

Well, not really. Even if most people just do it manually. As you said, you will have to handle memory allocation/array sizes by hand, but the copy can be performed with just one line of code:

```

double from[ 10 ];
double to[10];
std::copy( from, from+10, to );

```

Array to must have space for at least 10 elements, and only the first 10 elements will be modified. Had it 11 elements, the last of them would be unmodified by the algorithm. Destination pointer does not need to be the beginning of the array, it could be any other position as long as there are at least 10 positions afterwards.

Note that the docs for std::copy (as most other algorithms in STL) talks about iterators and not pointers, but pointers are just one type of iterator. (In fact iterators were designed to be substitutes to pointers, and try mimicking pointer behavior as much as possible.

Oh, I could go into the C++ being much lower level than Java type of argument, but I won't discuss it. I will only state that my perception (won't state it as a fact so that this won't fire a language flamewar) is that in C++ you can choose whether you want to code at a lower or higher level (where higher does not go all the way to lisp, but surely goes at least as high level as Java).

---

### Post by shadylookin on 2008-10-08
> **dribeas said:**
> That in Java will make two reference to the same array, which might not be what you want. If it is, then use pointers, that are closer to Java references:

```

double *array; // don't create memory for nothing
double *tmp = new double[20];
// use tmp array:
tmp[ 5 ] = 5.0;

array = tmp; // copy pointers

delete [] array; // don't forget to free memory

```


when I do this I get an error
error: incompatible types in assignment of ‘double*’ to ‘double [0]’

here's my code

```

class DynamicArray{
	
	public:
		void setData(int index, double value);
		double getData(int index);
		void addAtBack(double value);
		DynamicArray();
		DynamicArray(int sizeOfArray);	
		void doubleArraySize();
		int length();
		~DynamicArray();
		
	private:
		double* arrayOfDoubles;
		int maxLength;
		int numberOfElements;
};

```

```

#include "DynamicArray.h"
#include <iostream>


using namespace std;


/*set the value of a certain index if possible*/
void DynamicArray::setData(int index, double value){
	if(index < numberOfElements && index >= 0){
		arrayOfDoubles[index]=value;
	} else{
		cout << "index out of bounds";
	}
}

/*return the data at a certain index*/
double DynamicArray::getData(int index){
	if(index < numberOfElements && index >= 0){
		return arrayOfDoubles[index];
	} else{
		cout << "index out of bounds";
		return NULL;
	}
}


/*add a value at the end if there is space otherwise double the array size
and then add the value*/
void DynamicArray::addAtBack(double value){
	if(numberOfElements < maxLength){
		arrayOfDoubles[numberOfElements] = value;
		numberOfElements++;
	} else{
		doubleArraySize();
		arrayOfDoubles[numberOfElements] = value;
		numberOfElements++;
	}
}

/*default constructor calls the other construtor to set max length at 10*/
DynamicArray::DynamicArray(){
	maxLength = 10;
	numberOfElements = 0;
	double *tmp = new double[10];
	**arrayOfDoubles = tmp;**
	for(int i = 0; i < maxLength; i++){
		arrayOfDoubles[i] = 0.0;
	}
}		


/*the constructor with the parameter that sets the maxLength*/
DynamicArray::DynamicArray(int sizeOfArray){
	maxLength = sizeOfArray;
	numberOfElements = 0;
	double *tmp = new double[sizeOfArray];
	**arrayOfDoubles = tmp;**
	for(int i = 0; i < maxLength; i++){
		arrayOfDoubles[i] = 0.0;
	}
}		


void DynamicArray::doubleArraySize(){
	maxLength = maxLength*2;
	double *tmp = new double[maxLength];
	for(int i = 0; i <numberOfElements; i++){
		tmp[i] = arrayOfDoubles[i];
	}
	for(int i = numberOfElements; i < maxLength; i++){
		tmp[i] = 0.0;
	}
	**arrayOfDoubles = tmp;**
}

int DynamicArray::length(){
	return numberOfElements;
}

/*destructor*/
DynamicArray::~DynamicArray(){

}

```


Also are there any good resources for c++ for people that know java?

---

### Post by Sydius on 2008-10-08
Spend some time getting to know STL and BOOST (Google either).  They are libraries you can use in C/C++ that effectively make it behave much like higher-level languages (handling garbage collection, etc. for you).  C/C++ with STL/BOOST is a lot like Java.

---

### Post by dwhitney67 on 2008-10-08
> **shadylookin said:**
> when I do this I get an error
error: incompatible types in assignment of &#8216;double*&#8217; to &#8216;double [0]&#8217;

here's my code

```

class DynamicArray{
	
	public:
		void setData(int index, double value);
		double getData(int index);
		void addAtBack(double value);
		DynamicArray();
		DynamicArray(int sizeOfArray);	
		void doubleArraySize();
		int length();
		~DynamicArray();
		
	private:
		double* arrayOfDoubles;
		int maxLength;
		int numberOfElements;
};

```

```

#include "DynamicArray.h"
#include <iostream>


using namespace std;


/*set the value of a certain index if possible*/
void DynamicArray::setData(int index, double value){
	if(index < numberOfElements && index >= 0){
		arrayOfDoubles[index]=value;
	} else{
		cout << "index out of bounds";
	}
}

/*return the data at a certain index*/
double DynamicArray::getData(int index){
	if(index < numberOfElements && index >= 0){
		return arrayOfDoubles[index];
	} else{
		cout << "index out of bounds";
		return NULL;
	}
}


/*add a value at the end if there is space otherwise double the array size
and then add the value*/
void DynamicArray::addAtBack(double value){
	if(numberOfElements < maxLength){
		arrayOfDoubles[numberOfElements] = value;
		numberOfElements++;
	} else{
		doubleArraySize();
		arrayOfDoubles[numberOfElements] = value;
		numberOfElements++;
	}
}

/*default constructor calls the other construtor to set max length at 10*/
DynamicArray::DynamicArray(){
	maxLength = 10;
	numberOfElements = 0;
	double *tmp = new double[10];
	**arrayOfDoubles = tmp;**
	for(int i = 0; i < maxLength; i++){
		arrayOfDoubles[i] = 0.0;
	}
}		


/*the constructor with the parameter that sets the maxLength*/
DynamicArray::DynamicArray(int sizeOfArray){
	maxLength = sizeOfArray;
	numberOfElements = 0;
	double *tmp = new double[sizeOfArray];
	**arrayOfDoubles = tmp;**
	for(int i = 0; i < maxLength; i++){
		arrayOfDoubles[i] = 0.0;
	}
}		


void DynamicArray::doubleArraySize(){
	maxLength = maxLength*2;
	double *tmp = new double[maxLength];
	for(int i = 0; i <numberOfElements; i++){
		tmp[i] = arrayOfDoubles[i];
	}
	for(int i = numberOfElements; i < maxLength; i++){
		tmp[i] = 0.0;
	}
	**arrayOfDoubles = tmp;**
}

int DynamicArray::length(){
	return numberOfElements;
}

/*destructor*/
DynamicArray::~DynamicArray(){

}

```


Also are there any good resources for c++ for people that know java?

If you are learning C++, the only thing you should carry over from Java are the OOP/OOD concepts.  An array in C++ is not the same as it is in Java.  Just accept this little fact.

As for your code above, consider ridding yourself of the no-arg constructor, and replacing the definition of the 1-arg constructor with the following:
[PHP]DynamicArray( size_t sizeOfArray = 10 );[/PHP]
If 'sizeOfArray' is not given, then it is defaulted to a value of 10.  I also declared it as a size_t, because declaring the value as an int makes no sense; after all, a size of -1 should not be permitted, right?

The implementation would be:
[PHP]DynamicArray::DynamicArray( size_t sizeOfArray ) {
...
}[/PHP]
Note that the default value is not required, nor should be specified, when implementing the method.

The other problem I see in your code is in the doubleArraySize() method.  Before you assign 'tmp' to 'arrayOfDoubles', you need to delete 'arrayOfDoubles'.
[PHP]delete []arrayOfDoubles;[/PHP]
Also place this statement in your destructor; it is missing!

Now lastly, if you really want to pursue learning C++ to enjoy the features it offers, I really suggest you dump the DynamicArray in favor of the STL vector.  Dribeas emphasized this in his earlier post.

P.S.
[PHP]
#include <iostream>

int main()
{
  double *array = 0;  // always initialize variable; in this case to 0 (NULL)
  double *tmp   = new double[20];  // allocate some memory

  tmp[ 5 ] = 5.0;   // use tmp

  array = tmp; // copy pointers (not contents!)

  std::cout << array[5] << std::endl;   // should be 5.0

  delete [] array; // free memory; could also use tmp here (if it is in scope).

  return 0;
}
[/PHP]
This code works fine; check your test program to make sure you implemented it similarly as shown above.  Dribeas' example worked fine for me.

---

### Post by dribeas on 2008-10-09
> **shadylookin said:**
> when I do this I get an error
error: incompatible types in assignment of ‘double*’ to ‘double [0]’


I tried to compile your code and got a different error:
```

dynarray.cpp: In member function ‘double DynamicArray::getData(int)’:
dynarray.cpp:23: warning: converting to non-pointer type ‘double’ from NULL

```

The line reads:
```

double DynamicArray::getData(int index){
    if(index < numberOfElements && index >= 0){
        return arrayOfDoubles[index];
    } else{
        cout << "index out of bounds";
        [color=RED]return NULL;[/color]
    }
}

```

You must return a double, and NULL is not a double. Consider using exceptions to report errors.

---

