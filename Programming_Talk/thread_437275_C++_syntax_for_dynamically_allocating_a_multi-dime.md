---
title: "C++ syntax for dynamically allocating a multi-dimensional array"
date: 2007-05-08
forum: Programming Talk
---

### Post by e^(i*pi) on 2007-05-08
I'm in the process of switching from Java to C++ and I've come across something that is confusing me.  I"m trying to create a multi-dimensional array using new. Here is what I have been trying:

```
int firstNumber;
int secondNumber;

cout << "Enter first number: ";
cin >> firstNumber;
cout << "Enter second number: ";
cin >> secondNumber;

int* array = new int[firstNumber][secondNumber];
```

when I try this I always get error messages saying there is some issue with the line where I create the array.  Any ideas?

---

### Post by Dancingwllamas on 2007-05-08
I believe you have to create an array of pointers to an array of ints to get this to work. Here is an example:

```

int **array_ptr;    //two * are needed because it is a pointer to a pointer

array_ptr=new int*[firstnumber]; //creates a new array of pointers to int objects
for(int i=0; i<firstnumber; ++i)
     array_ptr[i]=new int[secondnumber];

//now, you can access the members like you can with normal 2d arrays
//like array_ptr[1][3]

```

Hope this helps. :)

---

### Post by psusi on 2007-05-08
There is no such thing as a multidimensional array where more than one dimension is dynamic, per se.  You can get much the same effect though, from a vector of vectors.  Take a look at std::vector<>.

vector< vector< int > > foo;

You should reevaluate what you are doing though, because if you think you need a dynamic 2d array, you are probably doing something really weird.

---

### Post by thk on 2007-05-08
#include "boost/multi_array.hpp"

---

### Post by hod139 on 2007-05-08
I agree with Dancingwllamas and thk, when using C++ you should avoid the old C style arrays when at all possible and use alternatives such as std::vector or boost.  However, if you really want to use C arrays you can, and to try and clear up some confusion from earlier posts, I'll show you how.  The first thing to remember, is that the following declarations of multi-dimensional arrays are basically the same,
```

int matrix[2][3];
int *matrix[3];
int **matrix

```the differences are in how the space is allocated and freed.  In the next code snippet I show how to allocate and free the second and third example to be the same size as the first.

```

int main(void)
{
  // Allocation
  int matrix1[2][3];

  int *matrix2[3];
  for(int i = 0; i < 3; ++i)  
     matrix2[i] = new int[2];

  int **matrix3;
  matrix3 = new int*[3];
  for(int i = 0; i < 3; ++i)  
     matrix3[i] = new int[2]; 

  // Deletion
  // No nead to delete matrix1
  for(int i = 0; i < 3; ++i)  
     delete [] matrix2[i];

  for(int i = 0; i < 3; ++i)  
     delete [] matrix3[i];
  delete [] matrix3;
 

  return 0;
}

```

---

### Post by baltimark on 2007-05-08
> **Dancingwllamas said:**
> I believe you have to create an array of pointers to an array of ints to get this to work. Here is an example:

```

int **array_ptr;    //two * are needed because it is a pointer to a pointer

array_ptr=new int*[firstnumber]; //creates a new array of pointers to int objects
for(int i=0; i<firstnumber; ++i)
     array_ptr[i]=new int[secondnumber];

//now, you can access the members like you can with normal 2d arrays
//like array_ptr[1][3]

```

Hope this helps. :)
Right. I do what dancingwllamas  does.

You first need to declare an array of pointers to pointers
```
int **array;

```

then allocate the space for an array of pointers
```

array = new int*[firstNumber];

```

then, for each of those pointers, allocate the amount of space you need
```

for (int i = 0; i < firstNumber; i++)
   arrary[i] = new int[secondNumber];

```

then, you can access it with array[i][j]

---

### Post by DavidBell on 2007-05-09
I use this 'cause I keep forgetting the syntax, you can do as many dimensions as you need if you keep going with the pattern.

```


// Easy one dimensional arrays
#define BCDECLAREARRAY_1D(TYPE,NAME)			TYPE *NAME;
#define BCCREATEARRAY_1D(TYPE,NAME,XSIZE)		NAME = new TYPE[(XSIZE)];
#define BCDESTROYARRAY_1D(NAME)			delete[] NAME;

// Easy two dimensional arrays
#define BCDECLAREARRAY_2D(TYPE,NAME)			TYPE **NAME;
#define BCCREATEARRAY_2D(TYPE,NAME,XSIZE,YSIZE)	NAME = new TYPE*[(XSIZE)]; for (int tempi = 0; tempi < (XSIZE); tempi++) NAME[tempi] = new TYPE[(YSIZE)];
#define BCDESTROYARRAY_2D(NAME,XSIZE)		for (int tempi = 0; tempi < (XSIZE); tempi++) delete[] NAME[tempi]; delete[] NAME;


```

---

### Post by jamescox84 on 2007-05-10
I would do something like this, but then I'm a C programmer not C++. So this code is translated from C to C++.

```

#include <iostream>

enum
{
    WIDTH = 16,
    HEIGHT = 12
};

int main()
{
    /* The array is just one dimentional.  */
    int *array = new int[WIDTH * HEIGHT];
    
    /* This macro allows it to be accessed as if it was 2D.  */
    #define ARRAY(X, Y) (array[(X) + (Y) * (WIDTH)])
    
    /* Setting the int at [2, 4].  */
    ARRAY(2, 4) = 10;
    
    /* Getting the int at [2, 4].  */
    std::cout << ARRAY(2, 4) << std::endl;
    
    delete[] array;
    
    return 0;
}

```

I think using this approach takes less housekeeping than using the staggered array approach. But then they are many ways to skin a cat.

---

### Post by bobdevis on 2009-06-11
Dancingwllamas, you are my hero. Thank you.
That example you gave indeed works as advertised.

---

