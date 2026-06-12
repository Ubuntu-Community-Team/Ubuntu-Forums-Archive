---
title: "Function returning an instance of a class in C++"
date: 2009-04-10
forum: Programming Talk
---

### Post by JFASI on 2009-04-10
This is probably the sort of question that a beginner would ask, which makes me feel kind of silly, considering how I've been writing large projects for school in C++ for a while now. 

When you have a class that contains a pointer, a matrix class for instance, and you want to overload operator+, for example, how would you go about that without leaking memory? 

Here is my prototype: 

```

#include <iostream>

class Matrix {
  private :
  int rows;
  int cols;
  int ** matrix;
  
  Matrix(int rows, int cols);
  ~Matrix();
  
  operator+();
};

```

If you create a local copy of the Matrix and return a reference to it, we get a dangling reference when the function's copy is destroyed, and possible segfaults waiting for us when we try to follow that pointer. 

If you create a copy of the object using new and return a pointer to the object, then you raise the specter of having to manually call delete, which is sloppy and kind of inelegant (although coming from C, I'm used to fun things like that...) 

If you create a local copy for the function and return the object by value, the whole thing is inefficient, and the pointer might lead down a dark unallocated path when the destructor gets called. 

So what is the standard idiom here?

---

### Post by Jiraiya_sama on 2009-04-11
My book mentions a couple of ways of handling this, use-counted and value-like, but I really hate use-counting so here is how you would do the matrix class with value-like pointers.

Matrix.h
```
class Matrix {
  friend Matrix operator+(const Matrix &lhs, const Matrix &rhs);
  private :
    int rows;
    int cols;
    int ** matrix;

  public:
    Matrix(int rows, int cols);
    Matrix(const Matrix &orig);
    ~Matrix();

    Matrix& operator+=(const Matrix &rhs);
};
```

Matrix.cpp
```
#include "Matrix.h"

Matrix::Matrix(int c, int r) : cols(c), rows(r)
{
  matrix = new int*[cols];
  for(int i = 0; i != cols; i++)
  {
    matrix[i] = new int[rows];
    for(int j = 0; j != rows; j++)
      matrix[i][j] = 0;
  }
}

Matrix::Matrix(const Matrix &orig) : cols(orig.cols), rows(orig.rows)
{
  matrix = new int*[cols];
  for(int i = 0; i != cols; i++)
  {
    matrix[i] = new int[rows];
    for(int j = 0; j != rows; j++)
      matrix[i][j] = orig.matrix[i][j];
  }
}

Matrix::~Matrix()
{
  for(int i = 0; i != cols; i++)
    delete [] matrix[i];
  delete [] matrix;
}

Matrix& Matrix::operator+=(const Matrix &rhs)
{
  int **temp = new int*[cols + rhs.cols];
  for(int i = 0; i != cols + rhs.cols; i++)
  {
    temp[i] = new int[rows + rhs.rows];
  }

  for(int i = 0; i != cols; i++)
    for(int j = 0; j != rows; j++)
      temp[i][j] = matrix[i][j];
  
  for(int i = 0; i != rhs.cols; i++)
    for(int j = 0; j != rhs.rows; j++)
      temp[i+cols][j+rows] = rhs.matrix[i][j];

  for(int i = 0; i != cols; i++)
    delete [] matrix[i];
  delete [] matrix;

  cols += rhs.cols;
  rows += rhs.rows;
  matrix = temp;

  return *this;
}

Matrix operator+(const Matrix &lhs, const Matrix &rhs)
{
  Matrix temp(lhs);
  temp += rhs;
  return temp;
}

```

These are very likely not the best examples, since I myself am a newbie programmer, but I've tested them with valgrind and they don't leak (unless the program using them crashes I believe). Hope this helps.

---

### Post by CptPicard on 2009-04-11
This is one of these fun things about C++ that I complain about.. :) you really need to understand the underlying implementation deeply regardless of the abstraction-sugar you're putting on top of things.

With large objects you should avoid creating value-copies just for things like returning from function. Check out the reference-counted pointer wrappers in the boost library, that's what I would probably do.

There is also for this particular case the so called Return Value Optimization, that compilers may or may not do, so I usually don't dare rely on it without experimenting a little each time I plan on relying on it. That means that a large object that gets returned from function gets allocated straight at the return value location, thus avoiding the copy-construction of temporaries.

---

### Post by JFASI on 2009-04-12
The trouble with the solution Jiraiya_sama offered, it seems, is that when you return the object by value, the pointer is still contained in the object, which violates encapsulation and causes hell. 

I can see why people complain about C++ so much, since if something as basic as returning a class instance is this difficult, then the language is deeply flawed. On the other hand, it's faster than Java and prettier than C, so what choice do I have... 

Is there an Objective C compiler for Windows? :D

---

### Post by CptPicard on 2009-04-12
You may want to take a look at D for a replacement, I pretty much like it -- just hope that language spec 2.0 would get there already. The issue with objective-C is, as far as I can tell, is that you get both low-levelness and slow dispatching...

---

### Post by dwhitney67 on 2009-04-12
> **JFASI said:**
> ...

I can see why people complain about C++ so much, since if something as basic as returning a class instance is this difficult, then the language is deeply flawed...

C++ may have some shortcomings, but this is not really one of them.  If a class object has allocated memory, and the programmer wants a unique/independent copy of this object, then the programmer needs to define/implement the copy-constructor that makes a deep-copy of the original object.  I don't see a flaw in this?  Sure, it requires a little bit of extra programming effort, but that it is not that difficult.

For what the OP seemed to be asking, the copy-constructor never comes into the picture; only the regular constructor is used.

```

class Matrix
{
  public
    Matrix(const size_t rows = 3, const size_t cols = 3)
    {
      // allocate space for matrix buffer
    }

    ~Matrix()
    {
      // deallocate space in matrix buffer
    }

    friend Matrix operator+(const Matrix& rhs, const Matrix& lhs)
    {
      // assert rhs and lhs are the same size

      Matrix matrix(rhs.rows, rhs.cols);

      // add values of rhs and lhs, and insert results into new matrix

      return matrix;
    }

  private:
    size_t rows;
    size_t cols;
    int**  matrix;
};

int main()
{
  Matrix a;
  Matrix b;
  Matrix c = a + b;   // only regular constructor called

  // For something like...

  Matrix d = a;       // then a copy-constructor is needed.
}

```

---

### Post by dribeas on 2009-04-12
> **JFASI said:**
> The trouble with the solution Jiraiya_sama offered, it seems, is that when you return the object by value, the pointer is still contained in the object, which violates encapsulation and causes hell. 

I can see why people complain about C++ so much, since if something as basic as returning a class instance is this difficult, then the language is deeply flawed. On the other hand, it's faster than Java and prettier than C, so what choice do I have... 

Is there an Objective C compiler for Windows? :D

The thing is that you get to select whether you want value semantics or not. And if you do want value semantics, then for non-trivial classes (and a matrix holding heap memory is not trivial) you must provide copy constructors that maintain your value semantics.

The solution Jiraiya_sama offeredis clean for the problem at hand. I would have given a different option for some of the details that are unrelated to the problem (I prefer having just a int* into a MxN integer array instead of building bidimensional arrays). But there are two interesting things in the code that most people will not notice:

Implement X= operator first as a member function (you cannot do it otherwise) and implement operatorX as a free function delegating on operatorX= for the real operation.

I believe you are confused about the original problem. I thought Jiraiya's answer would solve but lets work on it a little more.

You have a class Matrix, and you want to implement adition. The semantics of the operation are (I believe) rather simple: given two matrices A and B that have the same size, the operation should yield a third matrix C (different from A and B, that will be unmodified by the operation), such that for each x,y, C[x,y] = A[x,y] * B[x,y].

```

class Matrix
{
public:
   Matrix( int sizex, int sizey ) : sizeX_(sizex), sizeY_(sizey), data_( new int[ sizex*sizey ] ) {}
   Matrix( Matrix const & a );
   ~Matrix() { delete [] data_; }

   Matrix& operator+=( Matrix const & a ); // define += operator in the class
private:
   int sizeX_;
   int sizeY_;
   int * data_;
};
// Implementation of copy constructor
Matrix::Matrix( Matrix const& rhs )
   : sizeX_( rhs.sizeX_ ), sizeY_( rhs.sizeY_ ), data_( new int[rhs.sizeX_* rhs.sizeY_] )
{
   std::copy( rhs.data_, rhs.data_ + (sizeX_*sizeY_), data_ );
}

// Implementation of +=
Matrix& Matrix::operator+= ( Matrix const & rhs )
{
   if ( (sizeX_ != rhs.sizeX_) || (sizeY_ != rhs.sizeY_)) {
      throw std::logic_error( "cannot add a different size matrix");
   }
   std::copy( rhs.data_, rhs.data_+(sizeX_*sizeY_), data_ );
   return *this;
}

// Implementation of + as a free function
Matrix operator+( Matrix lhs_copy, Matrix const & rhs) // by value, compiler will generate a copy of the first argument
{
    return lhs_copy += rhs;
}

```

As you see the code is rather simple. In Jiraiya code there is a lot more work just for dealing with the pointer stuff, but not related to your problem.

You were concern how you should return: return by value. Always. That is the natural thing to do, that is what makes the code simpler to write, provides lesser problems and removes concerns. You were concerned about performance of the copy: don't be. While CptPicard is rather exceptic about the value return optimization, that optimization is defined in the standard and all (not home made) compilers do it. And I am talking all: Visual Studio 6 and on, g++ all versions that I recall. Intel compiler, Comeau, Sun, IBM, Metrowerks, Borland, SGI...

---

### Post by nvteighen on 2009-04-12
> **JFASI said:**
> 
Is there an Objective C compiler for Windows? :D

gcc can compile Objective-C. I guess there should be a Win32 version of the GNU ObjC runtime (libgobjc.so in GNU/Linux)...

> **CptPicard said:**
> You may want to take a look at D for a replacement, I pretty much like it -- just hope that language spec 2.0 would get there already. The issue with objective-C is, as far as I can tell, is that you get both low-levelness and slow dispatching...

The issue with Objective-C is that is just C + OOP :).. it is meant to be a low-level OOP language. I really don't know about the speed issues... given the fact that Mac OS X is written in ObjC, these might not be very critical.

If you want high-level constructs, then you have to learn the *Step libraries (Apple NeXTStep/OpenStep, GNUStep, SideStep), which are really good... (though GNUStep is a bit tricky to install... and to link with).

---

### Post by eye208 on 2009-04-12
> **dwhitney67 said:**
> For what the OP seemed to be asking, the copy-constructor never comes into the picture; only the regular constructor is used.

```
  Matrix a;
  Matrix b;
  Matrix c = a + b;   // only regular constructor called

  // For something like...

  Matrix d = a;       // then a copy-constructor is needed.

```
You are confusing copy constructor and assignment operator. While
```
Matrix c = a + b;
```
is indeed the same thing as
```
Matrix c(a + b);
```
the copy constructor is used in both cases. On the other hand, for an expression like
```
Matrix c;
c = a + b;
```
the assignment operator is used, although the difference may not be obvious to someone who is merely using the class, not implementing it.

Therefore I strongly recommend to overload both the copy constructor _and_ the assignment operator for any class that contains pointers. Or, if you think you don't need either of them, declare it private, so that it cannot be called by accident.

By the way, it is not necessary to implement operator+ as a friend function if both operands are the same type. It's perfectly valid to declare it as a class member like this:
```
Matrix operator+(Matrix const &other) const;
```

---

### Post by dribeas on 2009-04-12
> **eye208 said:**
> 
Therefore I strongly recommend to overload both the copy constructor _and_ the assignment operator for any class that contains pointers. Or, if you think you don't need either of them, declare it private, so that it cannot be called by accident.


True. I was thinking in the implementation of operator+ and I left the assignment operator aside. Destructor, copy constructor and assignment operator go side by side, if you need one then you need the others (there may be a corner case that I cannot think of).

---

### Post by dwhitney67 on 2009-04-12
> **eye208 said:**
> You are confusing copy constructor and assignment operator. While
```
Matrix c = a + b;
```
is indeed the same thing as
```
Matrix c(a + b);
```
the copy constructor is used in both cases. On the other hand, for an expression like
```
Matrix c;
c = a + b;
```
the assignment operator is used, although the difference may not be obvious to someone who is merely using the class, not implementing it.

Therefore I strongly recommend to overload both the copy constructor _and_ the assignment operator for any class that contains pointers. Or, if you think you don't need either of them, declare it private, so that it cannot be called by accident.

By the way, it is not necessary to implement operator+ as a friend function if both operands are the same type. It's perfectly valid to declare it as a class member like this:
```
Matrix operator+(Matrix const &other) const;
```

Many times I am confused, but when it comes to my experimentation, I can only believe what I see.

For example:
```

#include <iostream>

class Foo
{
  public:
    Foo()                               { std::cout << "constructor" << std::endl; }
    Foo(const Foo& other)               { std::cout << "copy constructor" << std::endl; }
    Foo& operator=(const Foo& other)    { std::cout << "operator=" << std::endl; return *this; }

    friend Foo operator+(const Foo& rhs, const Foo& lhs) { std::cout << "operator+" << std::endl; return Foo(); }
};


int main()
{
  Foo f1;             // regular constructor
  Foo f2;             // regular constructor
  Foo f3 = f1 + f2;   // friend operator+() called, which invokes regular constructor
}

```
The code above is similar to what I had posted earlier; thus I do not think I am confused at all.  My intent was clear with respect to the operator+() method.

---

### Post by eye208 on 2009-04-13
> **dwhitney67 said:**
> The code above is similar to what I had posted earlier; thus I do not think I am confused at all.  My intent was clear with respect to the operator+() method.
OK, you didn't confuse copy constructor and assignment operator. However, I'm still taking issues with this statement of yours:
> For what the OP seemed to be asking, the copy-constructor never comes into the picture; only the regular constructor is used.
This doesn't work as a blanket statement. Of course you can implement operator+() without calling the copy constructor, but many times it is inefficient to do it that way. Constructors are expected to initialize objects, not just allocate space for them. In many cases, it will be more efficient to initialize a copy, then modify it.
```
a = 0        // normal constructor
a = b + c

vs.

a = b        // copy constructor
a += c
```
Furthermore, the copy constructor is used for so many basic operations (e.g. call-by-value) that it's irresponsible not to overload it if the class contains pointers. That doesn't make C++ a flawed language, but CptPicard is right when he says that these things require special attention.

---

### Post by namegame on 2009-04-14
I may be completely offbase, but would an implementation of the [Singleton Design Pattern]("http://en.wikipedia.org/wiki/Singleton_pattern") be appropriate for this situation?

I may not understand the OP's question, so I could be way off in left field.

---

### Post by dwhitney67 on 2009-04-14
> **namegame said:**
> I may be completely offbase, but would an implementation of the [Singleton Design Pattern]("http://en.wikipedia.org/wiki/Singleton_pattern") be appropriate for this situation?

I may not understand the OP's question, so I could be way off in left field.

A Singleton pattern is used (or I should say, can be used) to define a one-of-a-kind object; for a Matrix this does not apply because after all, one can have more than one Matrix.

---

### Post by namegame on 2009-04-14
> **dwhitney67 said:**
> A Singleton pattern is used (or I should say, can be used) to define a one-of-a-kind object; for a Matrix this does not apply because after all, one can have more than one Matrix.

Ok. I just didn't understand the OP's problem then.

---

