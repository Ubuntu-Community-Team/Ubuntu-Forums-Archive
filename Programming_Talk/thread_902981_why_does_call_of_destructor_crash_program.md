---
title: "why does call of destructor crash program"
date: 2008-08-27
forum: Programming Talk
---

### Post by monkeyking on 2008-08-27
Hi,
code below is a snippet that shows my problem.
I'm doing matrix class, with data and dimensions.
When I run the code without me trying do call the destuctor,
the program works and cleans up the memory, so I do know that,
that allocation and dealloc works. I checked with valgrind.

But When I try to call the destructor, the program will crash.
Not on the call of the destructor but on program exit.
It's like my program doesn't know the the object has been removed.

Isn't there someway to close object?

thanks in advance

[PHP]
#include <iostream>
#include <string>

class Matrix {
 public:
  Matrix()                            {x_=0;y_=0;}
  Matrix(int height,int width);
  ~Matrix();
private:
  int**  data_;
  int x_;
  int y_;

}; 

Matrix::~Matrix() {
  if (x_!=0||y_!=0){
    delete[] *data_ ;
    delete[] data_;}
}

Matrix::Matrix(int height, int width){
  x_ = height;
  y_ = width;
  int **ppi = new int*[x_];
  int *curPtr = new int [x_ * y_];
  
  for( int i = 0; i < x_; ++i) {
      *(ppi + i) = curPtr;
      curPtr += y_;
    }
  for (int i=0;i<x_;i++)
    for(int n=0;n<y_;n++)
      ppi[i][n]=0;
  data_ = ppi;
}

int main(){
  Matrix mat(5,10);
  mat.~Matrix();// THIS  WILL CRASH PROGRAM
  return 0;
}

[/PHP]

---

### Post by DougB1958 on 2008-08-27
C++ automatically destroys local variables (such as your mat) when they go out of scope. So if you explicitly call the destructor, it is indeed running twice, once when you call it and a second time when main returns.

---

### Post by monkeyking on 2008-08-27
> **DougB1958 said:**
> C++ automatically destroys local variables (such as your mat) when they go out of scope. So if you explicitly call the destructor, it is indeed running twice, once when you call it and a second time when main returns.

Thanks for the fast answer, that explains why it is crashing.
But Is there no way to force a manually destroy on an object.
So that the destructer of the object is called, as soon as it goes out of scope?

thanks again

---

### Post by CptPicard on 2008-08-27
> **monkeyking said:**
> 
But Is there no way to force a manually destroy on an object.


If your object is allocated on the heap and you've got a pointer to it, you *must* call **delete** to destroy the object.

> 
So that the destructer of the object is called, as soon as it goes out of scope?

Well, yes, if you are on the stack (a "local variable"), then you don't need to worry about that as the destructor-calling will be automatic. (and explicitly calling it will cause issues as you have discovered)

Actually, I don't think you really ever explicitly *call* a destructor in C++. It happens either through a call to delete or stack frame being rolled back.

---

### Post by dwhitney67 on 2008-08-28
Your code is also "doing" more than it needs for a 2-dim array (err, 2x2 Matrix).

Below is a solution that demonstrates the basics.  Please compare it to yours to see where the differences are at.
[PHP]
#include <new>

class Matrix
{
  public:
    Matrix( size_t height, size_t width )
    {
      m_height = height;                 // save height of Matrix
      m_width  = width;                  // save width of Matrix
      m_data   = new int*[m_height];     // allocate array int pointers for height of Matrix

      for ( size_t i = 0; i < m_height; ++i )
      {
        m_data[i] = new int[m_width];    // allocate array int pointers for width of Matrix
      }
    }

    Matrix( const Matrix &matToCopy );   // copy constructor; not implemented (yet!)

    ~Matrix()
    {
      for ( size_t i = 0; i < m_height; ++i )
      {
        delete [] m_data[i];             // delete array int pointers for each row (width)
      }
      delete [] m_data;                  // delete array int pointers for column (height)
    }

    Matrix & operator=( const Matrix &other );   // assignment operator; not implemented (yet!)

  private:
    size_t m_height;                     // use size_t to denote size (which is always a +num!)
    size_t m_width;                      // use size_t to denote size (which is always a +num!)
    int ** m_data;
};


int main()
{
  Matrix mat( 5, 10 );

  {
    Matrix mat2( 5, 10 );

    // when this block of code ends (see curly bracket just below!), mat2 will cease to exist.
  }

  // when main() returns, mat will be automatically destroyed
  return 0;
}
[/PHP]

P.S.  For the methods that are defined, but not implemented, well I have left for you to complete (if necessary).

---

### Post by monkeyking on 2008-08-28
Hi dwhitney most of your code makes perfect sense,
I have 2 questions though.

1. The use of the size_t, can you elaborate on this.
2. Your internal representation of the matrix.

[PHP]for ( size_t i = 0; i < m_height; ++i )
      {
        m_data[i] = new int[m_width];    // allocate array int pointers for width of Matrix
      }[/PHP]

vs my version

[PHP]  int **ppi = new int*[x_];
  int *curPtr = new int [x_ * y_];
  
  for( int i = 0; i < x_; ++i) {
      *(ppi + i) = curPtr;
      curPtr += y_;
    } [/PHP]


I just copy pasted the above code from a different website.
Is all my pointer resolving not necessary.

thanks in advance

---

### Post by dwhitney67 on 2008-08-28
The code you have, and the one I presented, yield the same results.  It was not clear what you were doing because I saw in your OP two for-loops after you had performed the initial allocation for the number of rows.

Anyhow, choose which ever you think is best.

Btw, another thing that threw me for a spin was your class member-data names.

M$ long ago came out with a concept that many developers dubbed as the "Hungarian notation"; that is, a variable would be prefixed with the type of data that it represented.  For instance, a pi_SomeValue indicates that this variable is a pointer to an integer (hence the "pi_" prefix).

Long ago when I worked at the second largest defense company in the US, they recommended using the "m_" to denote member-data of a class.  Hence the bias in the code I presented.

Lately I have seen developers use the underbar ("_") at the end of member-data in classes.  Personally, I find it harder to read (but not confusing), thus because of such, I may not have misunderstood the code you presented in your OP.

Some code fascist think that writing code in a clear concise manner (for others to read) is overrated, but for me clarity in the way one writes code is paramount.  It allows "newbies" to read code quickly and understand it easily.  If the "m_" I used in my code is confusing, then please accept my apologies.

Once I was "corrected" by a newbie (btw, that's my presumption), because I named my member data the same as the local variable in my function/method.  If you understand the difference between function and class variables, then there is not a problem, although with respect to "clarity" there might be.

For instance
[php]
public:
...
  void myClassFunction( int value )
  {
    this->value = value;
  }
...
private:
  int value;
[/php]
Anyhow, good luck with your s/w development endeavors.  Let me know if I can be of further assistance.

---

### Post by monkeyking on 2008-08-28
hi dwhitney,
thanks for the response, and some good advices.

I'm of cause listening for good advices from more experienced users than myself.

And if your code for doing the mem allocation, is the same as mine,
I will be using yours. 
I understand yours, I don't understand mine...

Regarding your use of size_t, I wasn't questioning your nomenclatura, 
but your use of the type size_t.
Apparently ( [http://www.embedded.com/200900195](http://www.embedded.com/200900195) ), a programmer should always use size_t,
whenever you are referring to dimensions or sizes.

thanks again

---

### Post by nvteighen on 2008-08-29
size_t is just a variable that only stores positive integers (usually, it's just a shortcut to "unsigned int"). So, by using it, you don't run into weird things because of negative sizes (which don't make any sense, of course :))

---

