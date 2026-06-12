---
title: "C++ member function error message confusion"
date: 2009-07-06
forum: Programming Talk
---

### Post by Volt9000 on 2009-07-06
I'm trying to bone up on my C++ skills, as the last time I wrote any C++ code was well before ISO C++, so a lot of things are new to me.

As an exercise I'm writing the ubiquitous Matrix class (so at the same time I can also bone up on my matrix mathematics skills. ;))

So far it's going well but I've encountered something odd.
I've created my Matrix class and overloaded the parentheses () so I can use them as my getter/setter for the class.

When I try to compile I get an error in the following code:

[php]
// Assignment
Matrix& Matrix::operator=(const Matrix& m)
{
    // Check for self-assignment
    if (this == &m)
        return *this;

    // De-allocate any existing data
    if (_data != 0)
        delete[] _data;

    // Allocate new data and assign
    _rows = m.Rows();
    _cols = m.Cols();
    _data = new double[_rows * _cols];

    int i, j;
    for (i = 0; i < _rows; i++)
        for (j = 0; j < _cols; j++)
            _data[j + i * _cols] = m(i, j);    // Error on this line

    return *this;
}
[/php]

I get the following error message:

```

matrix.cpp: In member function &#8216;Matrix& Matrix::operator=(const Matrix&)&#8217;:
matrix.cpp:42: error: passing &#8216;const Matrix&#8217; as &#8216;this&#8217; argument of &#8216;double& Matrix::operator()(int, int)&#8217; discards qualifiers

```

I don't really understand that, but it sounds like it's complaining about how I access the elements of the m object, i.e. how I implemented my parenthetical override.

Here's the code for that:

[php]
// Return a reference to the specified element (for getting and setting)
double& Matrix::operator()(int row, int col)
{
    row--; col--;
    return _data[col + row * _cols];
}
[/php]

What am I missing here?

---

### Post by dwhitney67 on 2009-07-06
Thanks for the complete posting of your code... oops, NOT!

Please, those of us that know C++ are not compilers.  The error messages sometimes make sense, but sometimes it takes experimentation to deduce what the issue is.

Here's my crappy code, which resolves your issue... look carefully for the subtle differences between it and your code.
```

class Foo
{
public:
  Foo& operator=(const Foo& f);

  double operator()(int row, int col) const;

private:
  int    _cols;
  double _data[200];
};

Foo&
Foo::operator=(const Foo& f)
{
   _data[0] = f(0,0);
   return *this;
}

double
Foo::operator()(int row, int col) const
{
  return _data[col + row * _cols];
}

int main()
{
  Foo f;
  f(10, 20);
}

```

---

### Post by Volt9000 on 2009-07-06
Ok, well excuse me for not posting my code. I've attached it all here.

The only real difference I see between your implementation and mine is that I have

[php]
double& operator()(int, int);
[/php]

and you have

[php]
double operator()(int row, int col) const;
[/php]

I notice that my code passes by reference whereas yours passes by (constant) value. The problem with the latter is that I can't use it as a setter, only a getter. So something like

[php]
Matrix foo(5, 5);
foo(5, 5) = 2;
[/php]

won't work. I tried it out by changing my overloaded function to match yours, and I get the compiler error

```

error: lvalue required as left operand of assignment

```

So is there a way to have this overloaded function work as both a getter AND a setter?

---

### Post by Volt9000 on 2009-07-06
Ok, well it seems I can have both:

[php]
double& operator()(int, int);
double operator()(int, int) const;
[/php]

But now I have a new problem.

I've tried to expand my class by adding a private method for easier access to the data, as follows:

[php]
// Internal access to data
double& Matrix::val(int row, int col)
{
    assert(row >= 0 && row < _rows);
    assert(col >= 0 && col < _cols);
    return _data[col + row * _cols];
}
[/php]

This is so I can easily access elements internally by using val(row, col) instead of _data[[col + row * _cols].
This works fine except for the case of the newly added method.

I've attached my new code. The error occurs on Line 26 of matrix.cpp.

---

### Post by c0mput3r_n3rD on 2009-07-07
And check your ampersands

---

### Post by TheStatsMan on 2009-07-07
Just a couple of design issues.

You would be better off using column major order rather than row major order, simply because this is the default in fortran and there is a lot of high quality linear algebra stuff to link to. It is possible to write faster c++ code if you try hard enough but the fortran stuff will be way faster than a naive implementation and can at least be used as a benchmark.

Second issue is you should really check if your matrix is the same size as the one on the one you are equating it to as this can save you from having to delete _data. Personally I think it is preferable to not even allow the size of the matrices to be different in size, this is just encouraging unforeseen error and bringing unnecessary inefficiency into the code.

---

### Post by Volt9000 on 2009-07-07
Thank you for the replies but this doesn't solve my problem.

---

### Post by TheStatsMan on 2009-07-07
Get rid of the internal matrix val (altogether), and access the data through _data and it will work (as you did in line 25, which is commented out). Do the same for line 18.  Note you will also have to change line 48. Either use (*this)(i,j) instead of val or preferably add a function that returns the underling C-array and copy that directly. Preferably do this in a separate function that just copies and then you can call that if you define a copy constructor as well.

---

### Post by Roptaty on 2009-07-07
Remember that if you try to access methods from a object you have declared as const, the methods need to be declared as const as well.

---

### Post by Volt9000 on 2009-07-07
> **TheStatsMan said:**
> Get rid of the internal matrix val (altogether), and access the data through _data and it will work (as you did in line 25, which is commented out). Do the same for line 18.  Note you will also have to change line 48.

That's what I had originally, but it can be quite tedious typing that _data line every time.

> Either use (*this)(i,j) instead of val or preferably add a function that returns the underling C-array and copy that directly. Preferably do this in a separate function that just copies and then you can call that if you define a copy constructor as well.

That's exactly what val is doing-- it's just a wrapper for returning the proper value from _data.
Can you give an example of a different way of doing it?

> **Roptaty said:**
> Remember that if you try to access methods from a object you have declared as const, the methods need to be declared as const as well.
That's the thing, I haven't declared ANY object as a constant. But for some reason the compiler insists I have two parenthetical overloaded functions-- one const and one not. Hence my confusion.

---

### Post by dwhitney67 on 2009-07-07
> **Volt9000 said:**
> Thank you for the replies but this doesn't solve my problem.

Here's the "more" C++-ish way to implement a matrix.
```

#include <tr1/array>
#include <iostream>
#include <cassert>

static const size_t ROWS = 3;
static const size_t COLS = 3;

// Define what the Matrix is...
typedef std::tr1::array<double, COLS> Row;
typedef std::tr1::array<Row, ROWS>    Matrix;


void verifySame(const Matrix& m1, const Matrix& m2);


int main()
{
  Matrix m;

  // assign values
  m[0][0] = 1.0;
  m[0][1] = 2.0;
  m[0][2] = 3.0;

  m[1][0] = 4.0;
  m[1][1] = 5.0;
  m[1][2] = 6.0;

  m[2][0] = 8.0;
  m[2][1] = 8.0;
  m[2][2] = 9.0;

  // copy constructor in action
  Matrix m2 = m;
  verifySame(m, m2);

  // operator= in action
  Matrix m3;
  m3 = m2;
  verifySame(m2, m3);
}


void verifySame(const Matrix& m1, const Matrix& m2)
{
   assert(m1.size() == m2.size());
   assert(m1[0].size() == m2[0].size());

   for (size_t r = 0; r < m1.size(); ++r)
   {
      const Row& row = m1[r];

      for (size_t c = 0; c < row.size(); ++c)
      {
         assert(m1[r][c] == m2[r][c]);
      }
   }
}

```

---

### Post by Volt9000 on 2009-07-07
What is this trl stuff? I've never seen it before.

Thanks for the suggestion, but I'd like to continue implementing my own way, as I'd like to get the hang of a lot of concepts that at the moment are impeding my progress.

---

### Post by Volt9000 on 2009-07-07
Alright I seem to have fixed it. I'm not 100% sure if this is "correct" as overloaded operators are new to me to begin with.

What I've done is changed the signature of the assignment overloaded operator from

[php]
Matrix& operator=(const Matrix&);
[/php]

to

[php]
Matrix& operator=(Matrix&);
[/php]

So I've eliminated the need for the right-hand side of the assignment to be a constant. This seems to have eliminated all errors in addition to the requirement of having two overloaded parenthetical operators. I've attached my code for anyone interested.

Now can someone explain it to me? :)
I don't understand why the overloaded assignment operator needs a constant for the RHS to begin with. I only made it this way because of all the examples I've seen online.

---

### Post by dwhitney67 on 2009-07-07
I'm not 100% sure what you are trying to accomplish.  Here's some code I threw together in 10 minutes.

```

#include <iostream>
#include <cassert>

class Matrix
{
public:
   Matrix(const size_t rows = 0, const size_t cols = 0);
   Matrix(const Matrix& other);

   ~Matrix();

   Matrix& operator=(const Matrix& other);

   double  operator()(const size_t row, const size_t col) const;
   double& operator()(const size_t row, const size_t col);

   size_t rows() const { return m_rows; }
   size_t cols() const { return m_cols; }

private:
   size_t   m_rows;
   size_t   m_cols;
   double** m_data;
};


Matrix::Matrix(const size_t rows, const size_t cols)
   : m_rows(rows),
     m_cols(cols),
     m_data(new double*[m_rows])
{
   for (size_t r = 0; r < m_rows; ++r)
   {
      m_data[r] = new double[m_cols];
   }
}

Matrix::Matrix(const Matrix& other)
   : m_rows(other.m_rows),
     m_cols(other.m_cols),
     m_data(new double*[m_rows])
{
   for (size_t r = 0; r < m_rows; ++r)
   {
      m_data[r] = new double[m_cols];

      for (size_t c = 0; c < m_cols; ++c)
      {
         m_data[r][c] = other.m_data[r][c];
      }
   }
}

Matrix::~Matrix()
{
   for (size_t r = 0; r < m_rows; ++r)
   {
      delete [] m_data[r];
   }
   delete [] m_data;
}

Matrix& Matrix::operator=(const Matrix& other)
{
   if (this == &other) return *this;

   if (m_data)
   {
      for (size_t r = 0; r < m_rows; ++r)
      {
         delete [] m_data[r];
      }
      delete [] m_data;
   }

   m_rows = other.m_rows;
   m_cols = other.m_cols;
   m_data = new double*[m_rows];

   for (size_t r = 0; r < m_rows; ++r)
   {
      m_data[r] = new double[m_cols];

      for (size_t c = 0; c < m_cols; ++c)
      {
         m_data[r][c] = other.m_data[r][c];
      }
   }

   return *this;
}

double Matrix::operator()(const size_t row, const size_t col) const
{
   assert(row < m_rows && col < m_cols);

   return m_data[row][col];
}

double& Matrix::operator()(const size_t row, const size_t col)
{
   assert(row < m_rows && col < m_cols);

   return m_data[row][col];
}


void verifySame(const Matrix& m1, const Matrix& m2);

int main()
{
   Matrix m(3,3);

   m(0,0) = 1.0;
   m(0,1) = 2.0;
   m(0,2) = 3.0;

   m(1,0) = 4.0;
   m(1,1) = 5.0;
   m(1,2) = 6.0;

   m(2,0) = 7.0;
   m(2,1) = 8.0;
   m(2,2) = 9.0;

   // exercise copy constructor
   Matrix m2 = m;
   verifySame(m, m2);

   // exercise operator=()
   Matrix m3;
   m3 = m2;
   verifySame(m2, m3);
}

void verifySame(const Matrix& m1, const Matrix& m2)
{
   assert(m1.rows() == m2.rows());
   assert(m1.cols() == m2.cols());

   for (size_t r = 0; r < m1.rows(); ++r)
   {
      for (size_t c = 0; c < m1.cols(); ++c)
      {
         assert(m1(r,c) == m2(r,c));
      }
   }
}

```

---

### Post by Volt9000 on 2009-07-07
Ah, thanks for that dwhitney67, that double-pointer method seems a bit cleaner than using a private method to access the elements.

However I have a few questions about the code.

[php]
Matrix::Matrix(const size_t rows, const size_t cols)
   : m_rows(rows),
     m_cols(cols),
     m_data(new double*[m_rows])
[/php]

I've never seen something like this before. Putting a colon after the function name, and then a bunch of... what? Constructors? Forgive my noobishness, it's been a long time since I did any C++. :)

Also, as per the question in my last post, why does

[php]
Matrix& operator=(const Matrix& other);
[/php]

this assignment operator overload require that "other" be a const? If I leave out the const the program still compiles and works fine.

---

### Post by TheStatsMan on 2009-07-07
> **Volt9000 said:**
> That's what I had originally, but it can be quite tedious typing that _data line every time.



You only type it twice inside the container. It is hardly a burden.

The other approach of using a pointer to a pointer (mentioned by others) is not as good as the original approach. Storing all the data in a one dimensional array is better as it can be better optimised if you write linear algebra routines yourself and can also be linked to Fortran code. It should just be in column major order rather than row major. You won't be able to get anywhere close to the speed of fortran code, or other c++ libraries(eg eigen for instance), with a two dimensional array. If you want to look at an implementation for a two dimensional array have a look at TNT( template numerical toolkit), which is extremely slow by the way, but I guess you may be able to learn what you want to from the source code.

---

### Post by dwhitney67 on 2009-07-07
> **Volt9000 said:**
> Ah, thanks for that dwhitney67, that double-pointer method seems a bit cleaner than using a private method to access the elements.

However I have a few questions about the code.

[php]
Matrix::Matrix(const size_t rows, const size_t cols)
   : m_rows(rows),
     m_cols(cols),
     m_data(new double*[m_rows])
[/php]

I've never seen something like this before. Putting a colon after the function name, and then a bunch of... what? Constructors? Forgive my noobishness, it's been a long time since I did any C++. :)

Also, as per the question in my last post, why does

[php]
Matrix& operator=(const Matrix& other);
[/php]

this assignment operator overload require that "other" be a const? If I leave out the const the program still compiles and works fine.

The initialization immediately after the colon can be thought of as pre-initialization, although in reality it is the initialization of the class.  The stuff in the constructor body (that you typically see) can be thought of as post-construction.

In layman's terms, suppose your class has an int member data.  This data item is already constructed (and initialized to 0) before entering the constructor body, where it might be set to another value.  This is typically not a big deal (when considering performance), but when dealing with certain class objects, that require specific initialization parameters (unlike int), you would need to construct them in the "pre-initialization" area.

As for the assignment operator, the const is not required, but nevertheless is good practice to define.  Bear in mind that when using const, you are merely "advertising" to the callee that their data object will remain unchanged.

---

### Post by TheStatsMan on 2009-07-07
> **Volt9000 said:**
> 
[/php]I've never seen something like this before. Putting a colon after the function name, and then a bunch of... what? Constructors? Forgive my noobishness, it's been a long time since I did any C++. :)


That is initializing the variables

---

### Post by Volt9000 on 2009-07-07
> **TheStatsMan said:**
> You only type it twice inside the container. It is hardly a burden.

Certainly not a burden, but as the class grows and I add more methods I will have to call that line more often, and it would just be easier to have a method I can call that does it for me. Besides, isn't laziness one of the marks of a good programmer? ;)

> The other approach of using a pointer to a pointer (mentioned by others) is not as good as the original approach. Storing all the data in a one dimensional array is better as it can be better optimised if you write linear algebra routines yourself and can also be linked to Fortran code. It should just be in column major order rather than row major. You won't be able to get anywhere close to the speed of fortran code, or other c++ libraries(eg eigen for instance), with a two dimensional array. If you want to look at an implementation for a two dimensional array have a look at TNT( template numerical toolkit), which is extremely slow by the way, but I guess you may be able to learn what you want to from the source code.

What's with the obsession with Fortran? I have no plans to integrate my code with Fortran, nor do I plan to do performance comparisons with Fortran code.

This is something I'm writing "just for me", to get back into the swing of things. Although that doesn't mean I don't appreciate your and everyone else's input, I do-- I'm just confused as to why you keep mentioning such an ancient language.

> **dwhitney67 said:**
> As for the assignment operator, the const is not required, but nevertheless is good practice to define.  Bear in mind that when using const, you are merely "advertising" to the callee that their data object will remain unchanged.
Gotcha, thanks.

---

### Post by TheStatsMan on 2009-07-08
> **Volt9000 said:**
> Certainly not a burden, but as the class grows and I add more methods I will have to call that line more often, and it would just be easier to have a method I can call that does it for me. Besides, isn't laziness one of the marks of a good programmer? ;)



Well I just thought (*this)(i,j) was clearer. You would never write that line of code in any other function obviously.

> 

What's with the obsession with Fortran? I have no plans to integrate my code with Fortran, nor do I plan to do performance comparisons with Fortran code.

This is something I'm writing "just for me", to get back into the swing of things. Although that doesn't mean I don't appreciate your and everyone else's input, I do-- I'm just confused as to why you keep mentioning such an ancient language.


Gotcha, thanks.

Well the reason for linking the code with fortran is twofold. Firstly, so many linear algebra functions have been written in fortran so why write them again, yourself, and if you do write them again you need a benchmark. At this point in time the fortran code, for linear algebra, is still the best by they way, that is at least until eigen is paralised and the sparse matrix library is completed. (It is worth taking a look at eigen by the way, very promissing)

Since you are doing it for fun, why don't you write a matrix matrix multiplication and compare the time taken, (for decent size matricies) with the BLAS DGEMM subroutine. Make sure you are using an optimised version of BLAS, ATLAS should do. It is mostly straightforward to install from source. Then see how your function does when compared against one written in an "ancient language".

By the way even if you don't link with fortran using a one dimensional array is preferable, in that it allows for more optimsations and things like a reshape function become trivial. Even if you are doing this for fun you may as well do it correctly. Since column major order is compatiple with more code and it is equally as easy it still should be prefered.

---

