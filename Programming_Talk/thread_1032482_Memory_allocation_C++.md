---
title: "Memory allocation C++"
date: 2009-01-06
forum: Programming Talk
---

### Post by Benzaa on 2009-01-06
Hi, 

Im working with a small class in C++. I want to create a matrix class that can store a bunch of numbers on it.

It should be easy, but im having an issue with the destructor. As soon as the program finishes, the destructor generates an error that I can not understand.

The error only happens when I use the method "set" at 1,0

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

### Post by Martin Witte on 2009-01-06
It is not the destructor but it is the  get method which gives problems. Change it to 
```
double Matrix::get(int i, int j) {
    //Parenthesis operator function
    //Allows acces to values of matrix via (i,j)
	std::cout << i << j << std::endl;
    return m_pdData[m_iCol*(i-1) + (j-1)];
}

``` 
to get a hint whats going wrong

---

### Post by Benzaa on 2009-01-06
> **Martin Witte said:**
> It is not the destructor but it is the  get method which gives problems. Change it to 
```
double Matrix::get(int i, int j) {
    //Parenthesis operator function
    //Allows acces to values of matrix via (i,j)
	std::cout << i << j << std::endl;
    return m_pdData[m_iCol*(i-1) + (j-1)];
}

``` 
to get a hint whats going wrong


I found the mistake
the index had to be [m_iCol*(i) + (j)]

This small mistakes make your programing life a bit disturbing.

Thanks for the help

---

