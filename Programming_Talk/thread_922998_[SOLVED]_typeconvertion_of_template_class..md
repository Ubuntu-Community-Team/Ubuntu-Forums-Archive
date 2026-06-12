---
title: "[SOLVED] typeconvertion of template class."
date: 2008-09-17
forum: Programming Talk
---

### Post by monkeyking on 2008-09-17
Hi, this is a very simple code snippet of want I want to do

[PHP]
#include <iostream>

template <typename T>
class vector{
public:
  int len;
  T* data_;
  vector(int a):         len(a),data_(new T[a])        {}
  
};


template<typename T,typename U>
vector<T> force_conv(vector<U> &a){
  vector<T> retVec(a.len);
  
 for(int i=0 ;  i<a.len ;  i++)
    retVec.data[i] = (T) a.data[i];
  return retVec;
}

int main(){
  vector<int> iVec(10);
  vector<float> res = force_conv(iVec);
  
  return 0;
}
[/PHP]

If I have a template class of type vector<int>, I would like to have a function that can convert to a diffent type of vector for instanse vector(char).

Is this even possible?

thanks in advance

---

### Post by dwhitney67 on 2008-09-17
A char can hold a value ranging from -254 to 255; if you want the char to be printable, then the upper limit is 127.

Now, armed with this information, how do you propose to convert an int, say with a value of 256 or greater, into a char?

P.S.  I tend not to remember char limits; the information above may be incorrect.

---

### Post by dwhitney67 on 2008-09-18
Btw, I tried to compile your original code, and it didn't compile.

So I made some changes to allow me to test your program.  Here they are:
[PHP]#include <stdexcept>
#include <iostream>


template <typename T>
class array
{
  public:
    array( size_t size = 5 )
      : m_size(size), m_data(new T[ size ])
    {
    }

    virtual ~array()
    {
      delete []m_data;
    }

    size_t getSize() const
    {
      return m_size;
    }

    T & operator[]( const size_t index )
    {
      if ( index >= m_size )
      {
        throw std::range_error( "Index is too big!" );
      }

      return m_data[ index ];
    }

  private:
    size_t m_size;
    T *    m_data;
};


template<typename T,typename U>
array<T> forceConv( array<U> &other )
{
  const size_t size = other.getSize();

  array<T> retArray( size );
  
  for ( size_t i = 0; i < size; ++i )
  {
    retArray[i] = (T) other[i];   // C-style cast???
  }

  return retArray;
}


template<typename U>
void displayValues( array<U> &arr )
{
  for ( size_t i = 0; i < arr.getSize(); ++i )
  {
    std::cout << arr[i] << " ";
  }
  std::cout << std::endl;
}


int main()
{
  array<float> floatArr(10);

  for ( size_t i = 0; i < floatArr.getSize(); ++i )
  {
    floatArr[i] = (i+1)*3.3;
  }

  array<int> intArr = forceConv<int,float>( floatArr );

  displayValues( floatArr );
  displayValues( intArr );

  return 0;
}[/PHP]  
Concerning typecasting one data type to an arbitrary different data type does not always make sense.  This program was an interesting challenge in that it took me a while to fix compile issues, but would I ever use it in the real world?... the answer is no.

---

### Post by monkeyking on 2008-09-18
> **dwhitney67 said:**
> A char can hold a value ranging from -254 to 255; if you want the char to be printable, then the upper limit is 127.

Now, armed with this information, how do you propose to convert an int, say with a value of 256 or greater, into a char?

P.S.  I tend not to remember char limits; the information above may be incorrect.
Hi thanks for your reply,

I should of cause have elaborated on this.
My chars will always be within the value of 0-4.
So this doesn't pose a problem, and I'll only be using using
this function with primitive types. [int,float,double]

My original question is more into to the syntax of calling a function that has multiple templated types.

Sorry for not mentioning this.

---

### Post by kjohansen on 2008-09-18
i think what you are asking for is template specialization.  you can have a template and then if you want some specific functionality for a particular type you can specify that.

This link talks about it near the end:
[http://www.cplusplus.com/doc/tutorial/templates.html](http://www.cplusplus.com/doc/tutorial/templates.html)

---

### Post by monkeyking on 2008-09-18
> **dwhitney67 said:**
> 
[PHP]
  array<int> intArr = forceConv<int,float>( floatArr );
[/PHP]  
Concerning typecasting one data type to an arbitrary different data type does not always make sense.  This program was an interesting challenge in that it took me a while to fix compile issues, but would I ever use it in the real world?... the answer is no.
Thanks I just saw that you had responded again.
And thanks for you help this is what I couldn't figure out.

And for the sake of completeness this is my fixed code

[PHP]

#include <iostream>

template <typename T>
class vector{
public:
  int len;
  T* data_;
  vector(int a):len(a),data_(new T[a]){}
  
};


template<typename T,typename U>
vector<T> force_conv(vector<U> &a){
  vector<T> retVec(a.len);
  for(int i=0;i<a.len;i++)
    retVec.data_[i] = (T) a.data_[i]; // <- just need to add underscore
  return retVec;
}

int main(){
  vector<int> iVec(10);
  for (int i=0;i<10;i++)
    iVec.data_[i]=i*2;
  vector<float> res = force_conv<float, int>(iVec);

  for(int i=0;i<10;i++)
    printf("%f ",res.data_[i]);
  return 0;
}
[/PHP]

---

### Post by dwhitney67 on 2008-09-18
[php]
array<int> intArr = forceConv<int,float>( floatArr );
[/php]

The template types are required in this instance since the function only accepts one parameter.  If it had accepted two arrays, then I suspect the compiler would have been happy, with respect to knowing the data-types of T and U.

Btw, one thing I don't quite understand from the code I posted, is why the array destructor is not called at the end of the forceConv() function.  When I analysed the program using valgrind, there were no reports of memory leaks.  It makes me wonder how that temporary array was destroyed.

P.S.  I didn't use the name 'vector', and instead chose 'array'.  I didn't want someone to confuse the homemade class from the STL vector template class.

---

### Post by monkeyking on 2008-09-18
> **dwhitney67 said:**
> 
Btw, one thing I don't quite understand from the code I posted, is why the array destructor is not called at the end of the forceConv() function.  When I analysed the program using valgrind, there were no reports of memory leaks.  It makes me wonder how that temporary array was destroyed.

P.S.  I didn't use the name 'vector', and instead chose 'array'.  I didn't want someone to confuse the homemade class from the STL vector template class.

I'm in no way a c++ shark,
but i don't see a problem.
You are creating a array<T> retArray, that you return.
The destructor shouldn't be called in forceConv.
You create 2 arrays, and you clean up 2 arrays, on main exit.
no leaks.

But thanks again,

---

### Post by dwhitney67 on 2008-09-18
You're right.  I had a momentary lapse in brain function.

However, the destructor (for the temp object) would be called if the code where like:
[PHP]array<int> intArray;
intArray = forceConv<int, float>( floatArray );[/PHP]
Of course, an operator=() method would need to be defined/implemented for the statement to properly function.

---

