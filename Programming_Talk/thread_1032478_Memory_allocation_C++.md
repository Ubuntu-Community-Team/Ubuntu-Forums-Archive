---
title: "Memory allocation C++"
date: 2009-01-06
forum: Programming Talk
---

### Post by Benzaa on 2009-01-06
Hi, 

Im working with a small class in C++. I want to create a matrix class that can store a bunch of numbers on it.

It should be easy, but im having an issue with the destructor. As soon as the program finishes, the destructor generates an error that I can not understand.

Please, could someone help me with this
 
here is the code that I made:

```
//Matrix object 
#include <iostream>

class Matrix {
    protected:
	int m_iRow, m_iCol;
	double* m_pdData;
	void copy(const Matrix&);

    public:
	Matrix(int, int);
	~Matrix();
	Matrix(const Matrix&);
	Matrix& operator=(const Matrix&);
	int nRow(void);
	int nCol(void);
	double get(int, int);
	void set(int,int,double);
	void create(void);
};

Matrix::Matrix(int a, int b) {
    //Initialise the matrix with the row and column
    m_iRow = a;
    m_iCol = b;
    create();
}

Matrix::~Matrix() {
    //Deletes the space of the data
    delete m_pdData;
}

void Matrix::create(void) {
    //Creates container with zeros
    m_pdData = new double[m_iRow*m_iCol];
}

Matrix::Matrix(const Matrix& mat) {
    //Copy constructor 
    //Used when a copy of an object is produced
    this->copy(mat);
}
    
Matrix& Matrix::operator=(const Matrix& mat) {
    //Assignment operator function
    //Overloads the equal sign operator to work
    //with Matrix objects
    if (this==&mat) return *this;
    delete [] m_pdData;
    this->copy(mat);
    return *this;
}

int Matrix::nRow(void) {
    //Returns number of rows
    return m_iRow;
}

int Matrix::nCol(void) {
    //Returns number of columns
    return m_iRow;
}

double Matrix::get(int i, int j) {
    //Parenthesis operator function
    //Allows acces to values of matrix via (i,j)
    return m_pdData[m_iCol*(i-1) + (j-1)];
}

void Matrix::set(int i,int j,double val) {
    //set the value val into the matrix
    if (i < m_iRow && j < m_iCol)
	m_pdData[m_iCol*(i-1) + (j-1)] = val;
}

void Matrix::copy(const Matrix& mat) {
    //private copy functions
    //copies values from one matrix to another
    m_iRow = mat.m_iRow;
    m_iCol = mat.m_iCol;
    int iData = m_iRow * m_iCol;
    create();
    for (int i=0; i<iData; i++)
	m_pdData[i] = mat.m_pdData[i];
}

int main() {
    int n=3;
    Matrix A(n,n);
    A.set(1,0,9.0);

    for (int i=0; i<n; i++) 
	for (int j=0; j<n; j++) {
	    std::cout << i << "," << j << ":" << A.get(i,j) << "\n";
	}

    return 0;
}


```

---

### Post by namegame on 2009-01-06
I just glanced over it quickly and I did not see anything obvious. It may help if you post the error as well.

EDIT: I'm not sure of what your goal is. Wouldn't it be easier to dynamically allocate a two-dimensional array?

---

### Post by jpmelos on 2009-01-06
Don't hit the Submit button twice, man.

[http://ubuntuforums.org/showthread.php?t=1032482&highlight=matrix](http://ubuntuforums.org/showthread.php?t=1032482&highlight=matrix)

Glad you already found your answer, anyways.

---

### Post by kcode on 2009-01-06
Program is crashing at Matrix::get() function. Give it a check. (Used gdb)

---

### Post by stroyan on 2009-01-06
The destructor is using ```
delete m_pdData;
``` instead of ```
delete [] m_pdData;
```
The difference between the array and non-array delete is crucial.

---

### Post by mdurham on 2009-01-06
> The difference between the array and non-array delete is crucial.Why is that? It's only an array of doubles.

---

### Post by dwhitney67 on 2009-01-06
I ran the program using 'ddd'.  The error is occurring here:
```

return m_pdData[m_iCol*(i-1) + (j-1)];

```
when the values i = 0 and j = 0 are passed to the function (m_iCol = 3).

Oh, and as pointed out already, the destructor should be:
```

delete [] m_pdData;

```
Without the [], you will have a memory leak.


P.S.  Don't forget to fix the set() method as well; it has the same bug as the get() method.

---

### Post by Benzaa on 2009-01-07
> **jpmelos said:**
> Don't hit the Submit button twice, man.

[http://ubuntuforums.org/showthread.php?t=1032482&highlight=matrix](http://ubuntuforums.org/showthread.php?t=1032482&highlight=matrix)

Glad you already found your answer, anyways.


Sorry for the double post.
I didnt notice the error until I saw the duplicated post.


Thanks for the help I found the error on the code. It was the index that I was using for accessing the array.

btw, what is ddd?
is it a debugging tool?

---

### Post by dwhitney67 on 2009-01-07
'ddd' is the GUI front-end to 'gdb' (which is a debugger).

---

### Post by mdurham on 2009-01-07
> Without the [], you will have a memory leak.
Why is that? It's only an array of doubles. I don't get it!
Cheers, Mike

---

### Post by dwhitney67 on 2009-01-07
> **mdurham said:**
> Why is that? It's only an array of doubles. I don't get it!
Cheers, Mike

I don't have a worthy explanation (I tossed away my Stroustroup book long ago).  But when allocating an array, you use the [] operator.  I believe this calls a distinct method other than the regular operator delete(void*) method.

Read here for some (basic) information concerning allocating and deallocating memory in C++:  [http://www.cplusplus.com/doc/tutorial/dynamic.html](http://www.cplusplus.com/doc/tutorial/dynamic.html)

---------

Edit... play with this program:
[php]
#include <iostream>

void operator delete[](void* mem) throw()
{
  std::cout << "delete[](void*) called" << std::endl;
}

void operator delete(void* mem) throw()
{
  std::cout << "delete(void*) called" << std::endl;
}

int main(int argc, char** argv)
{
  double* array = new double[20];

  if (argc > 1)     // check if command line arg passed
    delete array;
  else
    delete [] array;

  return 0;
}
[/php]

---

### Post by mdurham on 2009-01-07
> I don't have a worthy explanation (I tossed away my Stroustroup book long ago). But when allocating an array, you use the [] operator. I believe this calls a distinct method other than the regular operator delete(void*) method.

dwhitney67, I would say you are correct if the array is an array of objects. In that case (without []), the object destructors wouldn't be called. But, doubles don't have destructors, therefore there would be no memory leak.
If you see what I mean.
Cheers, Mike

---

### Post by monkeyking on 2009-01-07
I havn't looked at your code closely,
but when you type
```
new []
```
then you should do
```
delete []
```
It's that simple, your not removing the doubles themselves,
but the array that has the doubles.

try checking your program with valgrind to verify there are no leaks

---

