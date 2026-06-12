---
title: "[SOLVED] C++ multi-dimensional arrays"
date: 2008-05-18
forum: Programming Talk
---

### Post by MDSmith2 on 2008-05-18
[LEFT]I was reading a c++ tutorial and am wondering why you would use a multi-dimensional array instead of just a plain array?

[/LEFT]

---

### Post by LaRoza on 2008-05-18
> **MDSmith2 said:**
> [LEFT]I was reading a c++ tutorial and am wondering why you would use a multi-dimensional array instead of just a plain array?

[/LEFT]

If you were doing something with matrices you would want that. It is good for coordinate systems. How would you references the squares on a chess board? You could have an array with 64 elements, or you could have an eight by eight two dimensional array.

---

### Post by sq377 on 2008-05-18
In my c++ class we had to make a tic tac toe program.  Makes sense there to have a char board[3][3].  I haven't used it very often, but it's handy to know how to use them.

---

### Post by MDSmith2 on 2008-05-18
Ok i guess that makes sense.
Thanks

---

### Post by dwhitney67 on 2008-05-18
One would use a multi-dimensional array to store matrices, etc.

For an example on how:
[PHP]#include <iostream>

using namespace std;


void displayArray( int *twoDimArray, const int rows, const int cols )
{
  for ( int i = 0; i < rows; ++i )
  {
    for ( int j = 0; j < cols; ++j )
    {
      cout << "twoDimArray[" << i << "][" << j << "] = "
           << twoDimArray[(i * cols) + j]
           << endl;
    }
  }
}

int main()
{
  const int rows    = 3;
  const int columns = 3;

  int array[rows][columns] = { {1,2,3},
                               {4,5,6},
                               {7,8,9} };

  displayArray( &array[0][0], rows, columns );

  return 0;
}
[/PHP]

---

### Post by drubin on 2008-05-18
Just a tip when accessing 2d arrays always remember what order they go in :P

Kinda like always having 
```
board[row][col]
```

And always making sure you remember the row is the first param. 

(helps with nested loops!!)

---

### Post by DavidBell on 2008-05-19
A word of caution, declaring multidimed arrays like
```
int test[10][100][100];
```
will eat your stack up quickly and cause a crash if you go too big. It's better to get into the habit of declaring arrays dynamically. 
I use the following macros to make life easy for creating and destroying them
```
// Easy one dimensional arrays
#define BCDECLAREARRAY_1D(bcTYPE, bcNAME)			bcTYPE *bcNAME;
#define BCCREATEARRAY_1D(bcTYPE, bcNAME, bcXSIZE)		bcNAME = new bcTYPE[(bcXSIZE)];
#define BCCREATEINITARRAY_1D(bcTYPE, bcNAME, bcXSIZE, bcVALUE)	bcNAME = new bcTYPE[(bcXSIZE)]; for (int tempx = 0; tempx < (bcXSIZE); tempx++) bcNAME[tempx] = (bcVALUE);
#define BCDESTROYARRAY_1D(bcNAME)				delete[] bcNAME;

// Easy two dimensional arrays
#define BCDECLAREARRAY_2D(bcTYPE, bcNAME)				bcTYPE **bcNAME;
#define BCCREATEARRAY_2D(bcTYPE, bcNAME, bcXSIZE, bcYSIZE)		bcNAME = new bcTYPE*[(bcXSIZE)]; for (int tempx = 0; tempx < (bcXSIZE); tempx++) bcNAME[tempx] = new bcTYPE[(bcYSIZE)];
#define BCCREATEINITARRAY_2D(bcTYPE, bcNAME, bcXSIZE, bcYSIZE, bcVALUE)	bcNAME = new bcTYPE*[(bcXSIZE)]; for (int tempx = 0; tempx < (bcXSIZE); tempx++) {bcNAME[tempx] = new bcTYPE[(bcYSIZE)]; for (int tempy = 0; tempy < (bcYSIZE); tempy++) bcNAME[tempx][tempy] = (bcVALUE);}
#define BCDESTROYARRAY_2D(bcNAME, bcXSIZE)				for (int tempx = 0; tempx < (bcXSIZE); tempx++) delete[] bcNAME[tempx]; delete[] bcNAME;

// You can keep going for more dims if you want

```

---

### Post by dwhitney67 on 2008-05-19
Here's another "easy" way to implement an 2-dimensional array in C++:

[PHP]#include <vector>
...
std::vector< std::vector<int> >[/PHP]

---

### Post by drubin on 2008-05-19
> **dwhitney67 said:**
> Here's another "easy" way to implement an 2-dimensional array in C++:

[PHP]#include <vector>
...
std::vector< std::vector<int> >[/PHP]

Is that not really only a 2D vector??

---

### Post by dwhitney67 on 2008-05-19
ok, you got me... I should have stated a 2-dimensional "glorified" array.

---

### Post by drubin on 2008-05-19
:P I am learning c++ at the moment still not as strong as my other langs, so need to ask to make sure!! 

He that asks stupid questions looks stupid once. He that does not ask remains stupid for ever! :P

---

