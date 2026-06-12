---
title: "C++ can't deallocate memory."
date: 2010-03-07
forum: Programming Talk
---

### Post by OVERPOWER8 on 2010-03-07
I have a program that allocated memory for 2d array, and then deallocates it.
**operator[] is forbidden**! (homework exercise)

The function *destroyArray* throws huge exception.

How to fix it?

```
int** createArray(int rows, int cols)
{
    int** Array = (int **) malloc(rows * sizeof(int *));
    
    if(Array == NULL)
    {
        free(Array); 
        cout << "Memory allocation failed while "
            << "allocating for Array[].\n";
        exit(-1);
    }
    
    int** pRow = &(*Array);
    
    for(int i=0; i<cols; i++)
    {
        *(pRow+i) = (int*) malloc(cols * sizeof(int));
        
        if( *(pRow+i) == NULL)
        {
            free( *(pRow+i));
            cout << "Memory allocation failed while "
                << "allocating for Array[i][].\n";
            exit(-1);
        }
    }
        
    return Array;
}

void destroyArray(int** Array, int rows)
{
    int** pRow = &(*Array);

    for(int i=0; i<rows; i++)
        free( *(pRow+i) );

    free(Array);
}

int main()
{
    int** Array = createArray(5, 8);
    // SomeOperations with an Array...
    destroyArray(Array, 5);                 // ERROR
}

```

---

### Post by MadCow108 on 2010-03-07
you've mixed up your rows and cols
check again what you allocate and on what your looping
valgrind is helpful for finding these bugs.

also this is equivalent:
int** pRow = &(*Array);
int** pRow = Array);


and if an allocation fails, no memory is allocated so you can't free it
(free on null actually even crashes your program)
so remove your free's in the allocation checks

Also your code hardly qualifies as C++ code. Its C with cout

---

### Post by OVERPOWER8 on 2010-03-07
>> **MadCow108**

> you've mixed up your rows and colsYou are right:

in function createArray the loop should look like this:
[I]
for(int i=0; i<rows; i++)[/I]
...

> Also your code hardly qualifies as C++ code. Its C with cout
I disagree. It's native C++.

---

### Post by MadCow108 on 2010-03-07
it may be compiled with a C++ compiler but it uses only C functions which makes it pretty much C code (throw out the cout and a C compiler will compile it)

new and delete are C++
malloc and free are C

C++ compiles most C code, but it is generally considered bad style to mix C and C++ code
Of course its ok for testing/learning, just don't make a habit out of it

---

### Post by OVERPOWER8 on 2010-03-07
>> **MadCow108**

How to transform this code to C++?

---

### Post by OVERPOWER8 on 2010-03-07
> 
new and delete are C++
malloc and free are C


I know that.

> 
C++ compiles most C code, but it is generally considered bad style to mix C and C++ code
Of course its ok for testing/learning, just don't make a habit out of it

Alright, I will keep that in mind.

---

### Post by dwhitney67 on 2010-03-07
> **OVERPOWER8 said:**
> >> **MadCow108**

How to transform this code to C++?

It appears that you want a 2D matrix.  One could use a vector, which contains another vector (of ints).

Here's one way:
```

#include <vector>
#include <iterator>
#include <algorithm>
#include <iostream>


template <size_t cols>
void resizeColumns(std::vector<int>& row)
{
   row.resize(cols);
}

void displayRow(const std::vector<int>& row)
{
   std::copy(row.begin(), row.end(), std::ostream_iterator<int>(std::cout, " "));
   std::cout << std::endl;
}

int main(void)
{
   std::vector< std::vector<int> > matrix;
   const size_t                    rows = 3;
   const size_t                    cols = 3;

   // reserve space for matrix based on rows/cols above.
   matrix.resize(rows);
   std::for_each(matrix.begin(), matrix.end(), resizeColumns<cols>);

   // populate matrix
   for (size_t r = 0; r < rows; ++r)
   {
      for (size_t c = 0; c < cols; ++c)
      {
         matrix[r][c] = (r + 1) * (c + 1) * 10;
      }
   }

   // display matrix
   std::for_each(matrix.begin(), matrix.end(), displayRow);

   return 0;
}

```

---

### Post by wieman01 on 2010-03-07
Hey, we have a policy here, right? Homework is what it is... HOMEwork. Please.

---

