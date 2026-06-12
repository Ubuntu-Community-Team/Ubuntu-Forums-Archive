---
title: "[C++] interpret 1D array as 2D array."
date: 2010-01-18
forum: Programming Talk
---

### Post by BramWillemsen on 2010-01-18
Hello everyone,

I'm fairly new to programming in C++. For an assignment i programmed a general purpose (square matrix of arbitrary size) math library that could for instance calculate the inverse of a 2D array. The heap allocated 2D array was passed to the function as a **array. 

The problem now is that i want to load the array in openGL (glLoadMatrix). This function accepts a one dimensional array. because the 2D array is allocated on the heap, the different rows have different memory locations so a pointer to the 2D array wont do. 

**main question**
My teacher suggested me to use stack allocated 1D arrays in the function declarations instead of heap allocated 2D arrays. He said i could overload the [] operator in order to work with the 1D array like it was a 2D (being able to use [i][j] element addressing). That way it would be much easier to write code for matrix calculations. I googled around for how to do this but i can't find the right information. Could anyone give me a tip ? I know there are other ways to tackle the problem i stated but i'm really curious about how to  overload the [] operator in the specified way.

with kind regards,

Bram

---

### Post by MadCow108 on 2010-01-18
its generally better to overload the () operator instead of the [] operator for this kind of stuff
[http://burks.bton.ac.uk/burks/language/cpp/cppfaq/operator.htm#](http://burks.bton.ac.uk/burks/language/cpp/cppfaq/operator.htm#)[13.9]

linearizing the memory is trivial, just encapsulate this:
ar[nrows*ncols];
ar[row*ncols + col]

if you use stack or heap depends on the size of the matrix
in general use the heap as matrices tend to get quite large and the stack size is very limited

---

### Post by BramWillemsen on 2010-01-19
Thanks a lot ! Using () would maybe be better indeed, but i felt like the [] are more intuitive when working with array like behaviour. I will post the way i did it so other people may benefit from it. 

```

template <class T>
class Matrix
{
public:
	T *m; //pointer to array that will be allocated on the heap
    Matrix(int i,int j){ //constructor
    	nRow = i;
    	nCol = j;
    	m = new T[i*j];
    }

    T* operator[] (const int Row){ //to alter elements
    	return m + (Row*nCol); //return pointer to row
    }

    //float operator[] (const int nIndex) const{ //to read elements

    //}
private:
	int nRow;
	int nCol;
};

```
A Matrix object is created like this:

```
Matrix <float>mat1(3,3);
```

elements of the array can now be called in the standard way, like this:

```
 mat1[i][j] 
```

The [i] calls the overloaded [] function of the Matrix object, which returns a pointer to the required memory location (row). [j] is then applied to this pointer (treated like an array) and the column is retrieved.

---

### Post by dwhitney67 on 2010-01-19
> **BramWillemsen said:**
> Thanks a lot ! Using () would maybe be better indeed, but i felt like the [] are more intuitive when working with array like behaviour. ...

The [i] calls the overloaded [] function of the Matrix object, which returns a pointer to the required memory location (row). [j] is then applied to this pointer (treated like an array) and the column is retrieved.

Your way, however "pretty" it might look to the casual s/w developer, exposes the data member within the class.  You also fail to provide proper range checking of the index within the operator[] method.  As for range checking the column index when accessing the data pointer, in that regard you are SOL because you have no means to do that.

Rather than "reinvent the wheel", you should consider using Boost's matrix class.  You can find documentation/examples here:
[http://www.boost.org/doc/libs/1_38_0/libs/numeric/ublas/doc/index.htm](http://www.boost.org/doc/libs/1_38_0/libs/numeric/ublas/doc/index.htm)

If you desire using the [] operator so much, and prefer to develop your own Matrix class, you could consider using the Boost array.  I think you should be able to pull something off like:
```

#include <boost/array.hpp>
#include <iostream>

int main()
{
  const size_t numRows = 3;
  const size_t numCols = 3;

  typedef boost::array<int, numRows> Row;
  typedef boost::array<Row, numCols> Matrix;

  Matrix array2D;

  array2D[0][0] = 10;
  array2D[1][1] = 20;
  array2D[2][2] = 30;

  std::cout << "array2D[0][0] = " << array2D[0][0] << std::endl;
  std::cout << "array2D[1][1] = " << array2D[1][1] << std::endl;
  std::cout << "array2D[2][2] = " << array2D[2][2] << std::endl;

  return 0;
}

```
The TR1 also provides an array object (which was probably lifted from Boost).  The plan is that it will be available when the c++0x standard is finalized... hopefully sometime in the coming century!

---

### Post by BramWillemsen on 2010-01-19
I agree with what you say, my solution is not the most practical. The main goal for me was to understand the mechanics of operator overloading though. I'm quite new to C++ and writing own code instead of using (superior) existing libraries is good practice i think.

i'll have a look at boost matrix class for further projects. thanks for the suggestion and the code you provided!

---

### Post by dwhitney67 on 2010-01-19
You could also do something like the following, which once again, is overkill:
```

#include <iostream>
#include <cassert>

class Row
{
public:
   Row(const size_t numRows)
      : myNumRows(numRows),
        myData(new double[numRows])
   {
      assert(myNumRows > 0);
   }

   ~Row()
   {
      delete [] myData;
   }

   double operator[](const size_t rowNum) const
   {
      assert(rowNum >= 0 && rowNum < myNumRows);
      return myData[rowNum];
   }

   double& operator[](const size_t rowNum)
   {
      assert(rowNum >= 0 && rowNum < myNumRows);
      return myData[rowNum];
   }

   friend std::ostream& operator<<(std::ostream& os, const Row& r)
   {
      for (size_t i = 0; i < r.myNumRows; ++i)
      {
         os << r[i] << " ";
      }
      return os;
   }

private:
   size_t  myNumRows;
   double* myData;
};

class Matrix
{
public:
   Matrix(const size_t numRows, const size_t numCols)
      : myNumCols(numCols),
        myRows(new Row*[numCols])
   {
      assert(myNumCols > 0);

      for (size_t c = 0; c < myNumCols; ++c)
      {
         myRows[c] = new Row(numRows);
      }
   }

   ~Matrix()
   {
      for (size_t c = 0; c < myNumCols; ++c)
      {
         delete myRows[c];
      }
      delete [] myRows;
   }

   Row& operator[](const size_t colNum) const
   {
      assert(colNum >= 0 && colNum < myNumCols);
      return *myRows[colNum];
   }

   friend std::ostream& operator<<(std::ostream& os, const Matrix& m)
   {
      for (size_t c = 0; c < m.myNumCols; ++c)
      {
         os << m[c] << std::endl;
      }
      return os;
   }

private:
   size_t myNumCols;
   Row**  myRows;
};

int main()
{
   Matrix m(3,3);

   m[0][0] = 5.0;
   m[1][1] = 5.0;
   m[2][2] = 5.0;

   std::cout << m << std::endl;
}

```
This code is probably full of bugs.  Its probably a disaster waiting to happen.

---

### Post by TheStatsMan on 2010-01-19
> **BramWillemsen said:**
> Thanks a lot ! Using () would maybe be better indeed, but i felt like the [] are more intuitive when working with array like behaviour. 

How is X[i][j] and more intuitive than X(i,j). Surely, they are equally intuitive, it is just one is generally works better. Mathematically we would tend to use a subscript i or j to denote the ith or jth element, we can't do that on a computer (well we could but it would be inconvenient), but surely these are both reasonable compromises. Why would you allow such a minor aesthetic difference dictate your decision.

---

