---
title: "[SOLVED] accessing private vars in template class"
date: 2008-09-16
forum: Programming Talk
---

### Post by monkeyking on 2008-09-16
Hi I'm doing a template container class abstraction of a math vector.
That should have some basic math stuff.

Now the problem is, that I can access private vars in other instatiations, but not in all cases.

The copyconstructor works but not the comparison operator.

I can of cause just make a const accessor, but I'd like to avoid the function call overhead.

But I don't really understand the problem,
I don't understand why compileren allows access to the private variables sometimes, and sometimes not.
Some consistency would be nice :)
thanks in advance

[PHP]
#include <iostream>

using namespace std;

template<typename T>
class Array {
 public:
  Array() {data_=NULL;x_=0;numOnes_=0;}
  Array(int length):x_(length),data_(new T[length]), numOnes_(0){}
  Array(const Array<T>& var);
  ~Array(){delete [] data_;}
  int length() const                  { return x_;     }
  T& operator() (uint r); 
  T operator() (uint r) const; 

  void print(int x=0, char sep=' ');
  void fillUp(T var) {for(int i=0;i<x_;i++) data_[i]=var;}
  Array<char> operator< (const float &f);
  int numTrues() const {return numOnes_;}

  Array<T> extract(const Array<char>&other);

private:
  int x_;
  T*  data_;
  int numOnes_;
};


template<typename T>
Array<T>::Array(const Array<T>& var){
  puts("array const constructor");
  x_ = var.x_;//this works
  data_ = new T[x_];
  for(int i=0;i<var.x_;i++)
    data_[i]=var.data_[i];
  
}

template<typename T>
void Array<T>::print(int x,char sep){
  printf("printing array with dim=%d\n",x_);
    for(int i=0;i<x_;i++) 
      std::cout << data_[i] << sep;
  std::cout <<endl;
}

template<>
void Array<char>::print(int x,char sep){
  printf("printing array with dim=%d\n",x_);
    for(int i=0;i<x_;i++) 
      std::cout <<(int) data_[i] << sep;
  std::cout <<endl;
}


template <typename T>
T& Array<T>::operator() (uint r){
  return data_[r];
} 


template <typename T>
T Array<T>::operator() (uint r) const{
  return data_[r];
} 

//these are comparison operators, these will return a Array<char> with elems {0,1}
template<class T>
Array<char> Array<T>::operator< (const float  &f){
  Array<char> tmp(x_);

  for(int i=0;i<x_;i++){
    if (data_[i]<f){
      tmp.data_[i]=1;
      tmp.numOnes_++;//this doesn't work
    }
    else
      tmp.data_[i]=0;
  }
  return tmp;

}

int main(){
  Array<int> vars(5);
  vars(0)=5;vars(1)=1;vars(2)=4;vars(3)=5;vars(4)=0;
  vars.print();
  Array<char> posList = vars<3;
  posList.print();
}
[/PHP]

---

### Post by dribeas on 2008-09-16
> **monkeyking said:**
> [PHP]
//these are comparison operators, these will return a Array<char> with elems {0,1}
template<class T>
Array<char> Array<T>:: operator< (const float  &f){
  Array<char> tmp(x_);

  for(int i=0;i<x_;i++){
    if (data_[i]<f){
      tmp.data_[i]=1;
      tmp.numOnes_++;//this doesn't work
    }
    else
      tmp.data_[i]=0;
  }
  return tmp;
}
[/PHP]

Template instantiations (note: not templates, but the instantiations) are classes and behave as such. This means that Array<int> is a class, and Array<char> is a class, but they are different classes, even if you wrote the code only once.

The problem with your template is that class Array<int> is trying to access private members of Array<char> (which is a different class).

There are a couple of solutions, first would be providing accessors, but that would open the internal data to just about anyone. The function call overhead would not really be the problem, as you can make you accessors inlined. The problem would be encapsulation.

```

template <typename T>
class Array
{
public:
   // ...
   T* data() { return data_; }
   int& ones() { return numOnes_; }
};

void anotherPieceOfCode()
{
   Array<int> array;
   delete array.data(); // !! problem external code can corrupt your internal data!!!
}

```

Another solution is using friendship:

```

template <typename T>
class Array
{
// ...
   template <typename U>
   friend Array<char> Array<U>::operator<( float const & );
};

```

This has better access control, not all code can access your internals, only operator< from any other Array<> template instantiation. The good point is that you are limiting the access to only a small (controlled) subset of classes, the bad parts are that you are still opening your code more than you should:

- Any Array<T>:: operator< can access any other Array<U> internals, that is Array<int>:: operator< can access Array<char> internals, but also Array<double> internals, or Array<...>

- Templates are tricky here. Any external programmer can break your encapsulation (not that common people might want to, but it is possible) through the use of template specialization.

Anyway, the difference is that in this case, a malicious coder must go out of the way to break your system, while in the first case, with accessors any code can just out of error corrupt your data.

As a side note, why are you overriding operator() instead of operator[] that seems more appropriate? Why are operator() not implemented in the class definition? (if you did, the compiler would be allowed to inline it, and with your implementation that would faster [skip method call] and probably yield smaller binary). Why do you have a numOnes attribute/numTrues() member method? do you plan to use it in all classes or just in your Array<char>?

---

### Post by monkeyking on 2008-09-16
> **dribeas said:**
> ... This means that Array<int> is a class, and Array<char> is a class, but they are different classes, even if you wrote the code only once. 
:) Of cause of cause, that makes perfect sense. This template way of programming is still quite new for me.
> **dribeas said:**
> 
```

template <typename T>
class Array
{
// ...
   template <typename U>
   friend Array<char> Array<U>::operator<( float const & );
};

```

I'm having problems compiling this syntax, I'm getting this nasty compile error, can you elaborate on syntax.
[PHP]
make
g++ testMatrix.cpp alloc.o -Wall -ansi -pedantic -ggdb
In file included from testMatrix.cpp:7:
array.cpp: In instantiation of ‘Array<char>’:
array.cpp:55:   instantiated from here
array.cpp:19: error: no ‘Array<char> Array<T>::operator<(const float&)’ member
function declared in class ‘Array<T>’
array.cpp:136: error: expected 2 levels of template parms for ‘Array<char>
Array<T>::operator<(const float&)’, got 1
array.cpp: In member function ‘Array<char> Array<T>::operator<(const float&)’:
array.cpp:137: error: ‘x_’ was not declared in this scope
array.cpp:140: error: ‘data_’ was not declared in this scope
array.cpp:19: confused by earlier errors, bailing out
Preprocessed source stored into /tmp/ccyMgsiS.out file, please attach this to your
bugreport.
Traceback (most recent call last):
  File "/usr/share/apport/gcc_ice_hook", line 34, in <module>
    pr.write(open(apport.fileutils.make_report_path(pr), 'w'))
IOError: [Errno 13] Permission denied:
'/var/crash/_usr_lib_gcc_x86_64-linux-gnu_4.2.3_cc1plus.1000.crash'
make: *** [allofit] Error 1
[/PHP]

> **dribeas said:**
> 
As a side note, why are you overriding operator() instead of operator[] that seems more appropriate? Why are operator() not implemented in the class definition? (if you did, the compiler would be allowed to inline it, and with your implementation that would faster [skip method call] and probably yield smaller binary). Why do you have a numOnes attribute/numTrues() member method? do you plan to use it in all classes or just in your Array<char>?
I'm overloading'()' since I'm also doing a matrix template,
and the parashift faq said that I should use subsetoperator '(a,b)' instead of '[a][b]'. So I choose '()' just for making the different classes more alike. 

I was told, don't remember who though, that I should always avoid method calling when I had the option of accessing the data directly, something about avoid stack swap or something. That's why I don't just use the overloaded '()' method. Should I just do this?

numOnes_/numtrues() is only used in Array<char>, is there some nice way of just having them in Array<char>

I stripped my template class definition, for most stuff when I did my original post.

this is my full 'template class header'
[PHP]
template<typename T>
class Array {
 public:
  Array() {puts("empty constructor");data_=NULL;x_=0;numOnes_=0;}
  Array(int length):x_(length),data_(new T[length]), numOnes_(0){}
  void init(int length) {x_=length;data_=new T[length]; }
  Array(const Array<T>& var);
  ~Array(){delete [] data_;}
  int length() const                  { return x_;     }
  T& operator() (uint r); 
  T operator() (uint r) const; 

  void print(int x=0, char sep=' ');
  void fillUp(T var) {for(int i=0;i<x_;i++) data_[i]=var;}
  void plus(const Array<T>&);
  template <typename U>
  friend Array<char> Array<U>::operator< (const float &f);//this makes nasty compile error
  Array<char> operator> (const float &f);
  Array<char> operator== (const float &f);
  int numTrues() const {return numOnes_;}

  Array<T>& operator= (const Array<T>&);
  Array<T> operator+ (const Array<T>&);
  Array<T> operator/ (const float &other);
  
  Array<T> extract(const Array<char>&other);

private:
  int x_;
  T*  data_;
  int numOnes_;
};
[/PHP]

thanks for your response

---

### Post by dwhitney67 on 2008-09-16
Monkeyking, although this suggestion has nothing to do with the coding issues you are facing, I would suggest that you use more white-space (and vertical space) when you write code.

Your code is very to hard to read.

---

### Post by monkeyking on 2008-09-16
> **dwhitney67 said:**
> Monkeyking, although this suggestion has nothing to do with the coding issues you are facing, I would suggest that you use more white-space (and vertical space) when you write code.

Your code is very to hard to read.

Ok, I'll indent by 8 the next time. :)
It's not that I like writing unreadable code,
but when I started to program some years ago,
my teachers wanted a printout.
So I just got used to use 2 space tab and no lines with more than 78 chars wide.

It's just a bad habit.

---

### Post by monkeyking on 2008-09-16
```
Ok,         I'll     indent    by    8    the     next     time.    :)
It's        not      that   I   like    writing     unreadable code   ,
but     when     I    started    to   program    some   years    ago  ,
my    teachers    wanted   a    printout       .
So      I      just       got        used      to       use      2 space   tab         and   no    lines    with    more    than    78    chars   wide  .

It's    just     a     bad      habit  .
```

:guitar:

---

### Post by dwhitney67 on 2008-09-16
It's not the indent that vexes me; I personally only indent two-spaces too.

It's stuff like:
[PHP]for(int i=0;i<5;++i)[/PHP]
versus
[PHP]for (int i = 0; i < 5; ++i)[/PHP]

---

### Post by dribeas on 2008-09-17
> **monkeyking said:**
> [PHP]
template<typename T>
class Array {
 public:
   // ...
  template <typename U>
  friend Array<char> Array<U>::operator< (const float &f);//this makes nasty compile error
   // ...
};
[/PHP]

The problem here is that you are declaring operator< from an external Array<U> class as a friend (which I suggested) but you removed Array<T>:: operator< from the template class. A friendship declaration is not a method declaration, the compiler knows that operator< can have access to the internal data, but it cannot find the operator< anywhere.

```

class Array {
 public:
   // ...
  Array<char> operator< (const float & f); // declaration of the method
  template <typename U>
  friend Array<char> Array<U>::operator< (const float &f);// friendship declaration for all other Array<U> operator<
   // ...
};

```

More on the design later on, if I find the time :)

---

### Post by dribeas on 2008-09-17
> **monkeyking said:**
> numOnes_/numtrues() is only used in Array<char>, is there some nice way of just having them in Array<char>


I don't like the idea of having a member attributes and/or methods in a template if you know before hand that it will be used only in one template instantiation.

Then I don't like the idea of having external code modifying internal data (numOnes_), which is the only solution with your current Array<> interface.

There are a couple of things you can do:
1- Specialize Array<char> and include numOnes_/numTrues()
2- Provide a separate non templated class (Mask?) to use as return value from Array<>:: operator<

In either case you will need to provide most method implementations again, even if it just delegates into the general template Array<>. I don't like from the template specialization that you will have a different behavior for an specific type of Array<>.

Without knowing your particular requirements, so I will probably be way off, I would go for option (2), with an implementation in these lines:
```

class ArrayMask
{
public:
   ArrayMask( int size ) : data_(0), numOnes_(0) {}
   void set( int pos, bool value = true ) // replaces bool& operator()
   {
      if ( data_(pos) ) --numOnes_;
      data_(pos) = value;
      if ( value ) ++numOnes_;
   }
   bool operator( int pos ) const // most methods can be delegated
   {
      return data_( pos );
   }
   int numTrues() const { return numOnes_; }
   // You'll need to delegate other needed methods as with bool operator(int) const
private:
   Array<bool> data_;
   int numOnes_;
};

template<typename T>
ArrayMask Array<T>::operator< ( float value ) // there is no point in using references for basic types
{
  ArrayMask result( length_ ); // in your code x_
  for ( int i = 0; i < length_; ++i )
  {
    if ( data_[ i ] < value ) result.set( i );
  }
  return result;
}

```

The change in the interface (replacing non-const operator() with a set method) is to keep control of the 'true' count.

If you want to use Mask in operations with Array<> you can go through a couple of ways: provide operators that work on both types, or provide an accessor (possibly constant) to your inner Array<bool>.

This solution is cleaner, and you don't want to use friendship (it is the strongest coupling relationship) and Array<int> won't need to have attributes/methods you don't need.

On a side note, instead of your print signature, it is recommended having either a friend operator<< or a non-friend operator<< that calls a print/dump method with this signature:

```

template<typename T>
class Array
{
   // ...
public:
   std::ostream& dump( std::ostream& o, char separator = ' ' ) const
   {
      o << "Array of size " << x_; 
      // ... print all data
      return o;
   }
};

template <typename T>
std::ostream & operator<<( std::ostream & out, Array<T> const & a )
{
   return a.dump( out );
}

```

This will allow you to use the same method for printing to any kind of stream (stdout/stderr/file stream/string stream...) with just one implementation.

---

### Post by monkeyking on 2008-09-17
> **dribeas said:**
> The problem here is that you are declaring operator< from an external Array<U> class as a friend (which I suggested) but you removed Array<T>:: operator< from the template class. A friendship declaration is not a method declaration, the compiler knows that operator< can have access to the internal data, but it cannot find the operator< anywhere.

Very very informative, I had to reread this a couple of times before it made sense. But I got it now.
> **dribeas said:**
> 
There are a couple of things you can do:
1- Specialize Array<char> and include numOnes_/numTrues()
2- Provide a separate non templated class (Mask?) to use as return value from Array<>:: operator<

I got your idea, and I think I'll go with the second one, but just to clarify.
There is no way to say. Let Array<char> have all the public methods from Array<T> plus some extra internal vars?
Without having to duplicate the general code?
> **dribeas said:**
> 
...
This will allow you to use the same method for printing to any kind of stream (stdout/stderr/file stream/string stream...) with just one implementation.
Very clever, this one is indeed a keeper.

Thanks for your reply

---

### Post by dribeas on 2008-09-18
> **monkeyking said:**
> There is no way to say. Let Array<char> have all the public methods from Array<T> plus some extra internal vars?
Without having to duplicate the general code?

You can do many things with the language, but nothing is really free, everything has its own implications. I don't quite like the solution below, but for the sake of completeness here it is. The reason I prefer the previous solution is that it requires more code, but the code is cleaner. You are sharing the internal implementation by aggregating (just providing one-line methods that delegate into the internal data structure) and the solution has a clean interface.  

Using inheritance you could go with:
```

class ArrayMask : public Array<bool>
{
public:
   ArrayMask( int length ) : Array<bool>( length ), numOnes_(0) {} // Constructor must be explicitly added

   int numTrues() const { return numOnes_; }

   template <typename T>
   friend ArrayMask Array<T>::operator< ( const float & );
private:
   int numOnes_;
};

```

In this case ArrayMask is an Array<bool> and thus has all the methods and attributes as its parent, but if Array<> was not meant to be inherited (as in your case), all private's of Array<> are not accessible from ArrayMask.

Advantages: It can be used (almost) anywhere that Array<bool> is used. You don't need to provide all the interface, it is directly inherited.

Disadvantages: Either you modify your parent class to allow for inheritance or you are in risk of incorrectly deleting from a Array<bool> pointer an ArrayMask --which would call Array<bool> destructor but fail to destroy ArrayMask. If you modify your parent class to allow destruction from the base class you'll have to make ~Array<> virtual, which means that you are adding the cost of a virtual method table to the class and its members.

You are indeed getting all parent's methods, and you will need to take care of hiding those you don't want, which means that you will need to provide accessors to numOnes_ or try hiding your parents methods (mark non-const operator() as private for your derived class) --which cannot really be done anyway.

```

// With
class ArrayMask : public Array<bool>
{  // All the same
public:
   void set( int pos, bool value = true )
   {
      // must be implemented in terms of public/protected stuff from Array<bool>
      if ( Array<bool>::operator()( pos ) ) --numOnes_;
      Array<bool>::operator()(pos) = value;
      if ( value ) ++numOnes_;
   }
   std::ostream& dump( std::ostream& o, char delim = ' ' )
   {
      o << "numOnes_ = " << numOnes_;
      return Array<bool>::dump( o, delim );
   }
private:
   bool& operator()( int x ); // no need to implement, not meant to be called
};
std::ostream& operator<<( std::ostream& o, ArrayMask const & a )
{
   return a.dump( o );
}

void f()
{
   ArrayMask *p = new ArrayMask( 100 );

   (*p)( 10 ) = true; // fails: operator(int) marked private, OK   
   p->set( 10 ); // ok, updates data and numOnes_
   std::cout << (*p) << std::endl; // prints ArrayMask

   Array<bool> *ab = b; // now you can

   (*ab)( 10 ) = true; // !!! operator(int) called through a base *!!!
   // numOnes_ now is skewed, there is one more true than numOnes_
   std::cout << (*ab) << std::endl; // will print Array<bool>, even if it is overwritten in ArrayMask

   delete ab; // !!! ~Array<bool> called instead of ~ArrayMask !!! 
}

```

Mixing specialization in makes it all even harder. 
```

template<>
class Array<bool> : public Array<char> // must inherit from something different from Array<bool> = itself
{
   Array( int length ) : Array<char>( length ), numOnes_(0) {}
   bool operator()( int pos ) const 
   {
      return Array<char>::operator()( pos ) != 0;
   }
   void set( int pos, bool value )
   {
      if ( Array<char>::operator()( pos ) != 0 ) --numOnes_;
      Array<char>::operator()( pos ) = ( value? 1 : 0 );
      if ( value ) ++numOnes;
   }
private:
   bool& operator()( int pos ); 
   // cannot delegate to Array<char> due to incompatible 
   // return types (a char& cannot be mapped to bool&)
};

```

All other methods share Array<char> interface, that is, fillUp takes a char and not a bool, and are outside of Array<bool> control unless you recode them. That is calling fillUp takes a char as parameter and does not update numOnes_.

You need to code less, but you'll have all these subtleties. Also, consider that some authors (and I agree) say that inheritance is to be reused by code that works with your bases, not to reuse the code your bases have.

---

### Post by monkeyking on 2008-09-18
Very nice example,
I won't use it though, but I'll keep it as a reference.

I'm almost done with my template,
and I'm beginning to use it.
But I was just wondering over this.

[PHP]
  Array<int> ary1(3);ary1(0)=2;ary1(1)=4;ary1(2)=7; //just an array
  Array<int> ary2(3);ary2(0)=1;ary2(1)=2;ary2(2)=6; //just an array
  cout << ary1;
  cout << ary2;
  Array<int> ary3 = ary1+ary2;
  cout << ary3;
//everything till this point works

  //is this possible
  cout << (Array<int>) ary1+ary2;
  return 0;
[/PHP]

Do I have to make a temp Array<T> for just outputting it?

thanks in advance

---

### Post by dribeas on 2008-09-20
> **monkeyking said:**
> //...
  Array<int> ary3 = ary1+ary2;
// ...
  cout << (Array<int>) ary1+ary2;
[/PHP]

Do I have to make a temp Array<T> for just outputting it?

You are making the temporary, whether you name it or not. Now there are subtleties there... I wanted to jump in in a [previous post]("http://ubuntuforums.org/showthread.php?t=922998") with you and dwitney67 about construction, copy and destruction of objects, but did not have time.

The thing is that the C++ standard says that whenever you return a value (not reference) a temporary is created, so dwitney67 would be right asking why there are no more destructor calls. 

The same C++ standard states that the compiler can optimize away those copies, and that is what goes on. But there are subtleties there: even if the compiler optimizes the copy away, it must still consider the code as if the copy was being done. Note that the copy on function exit into the temporary object is really a call to the copy constructor not the assignment operator as the temporary did not exist before

```

class X
{
public:
   X();
   X& operator=( X const & );
private:
   X( X const & );
};

X f()
{
   X tmp;
   return tmp; // Error: X( X const & ) is private
}

int main()
{
   X a = f();  // Error: X( X const & ) is private
   f(); // Correct (assuming that f() would compile: friend of X)
   X b;
   b = f(); // Correct if f() compiles
}

```

---

### Post by monkeyking on 2008-09-21
Hmm, ok, it makes sense that the temporary object has to be created.
But my code
[PHP]
  Array<int> ary1(3);ary1(0)=2;ary1(1)=4;ary1(2)=7; //just an array
  Array<int> ary2(3);ary2(0)=1;ary2(1)=2;ary2(2)=6; //just an array
  cout << ary1;
  cout << ary2;
  Array<int> ary3 = ary1+ary2;
  cout << ary3;
//everything till this point works

  //This gives me an error trying to compile
  cout <<  ary1+ary2;
  return 0;
[/PHP]

Then I don't understand why the line above won't even compile.
It does work, when I do it like
[PHP]
tmp=ary1+ary2
cout <<tmp
[/PHP]

thanks for your replies

---

### Post by dribeas on 2008-09-22
> **monkeyking said:**
> [PHP]
  //This gives me an error trying to compile
  cout <<  ary1+ary2;
[/PHP]

Then I don't understand why the line above won't even compile.


What's the error? How is operator+ defined?

---

### Post by monkeyking on 2008-09-22
Hi,
This is some of my class definition
[PHP]
class Array{
...
  std::ostream& dump(std::ostream &o=(std::cout),char sep=' ');
  Array<T> operator+ (const Array<T>&);
  Array<T>operator+( const float f );
...
}
[/PHP]

And I've implemented '<<' as a free function
[PHP]
//overloading of '<<' for Array type
template<typename T>
 std::ostream& operator<<(std::ostream &o,Array<T> &a){
  return a.dump(o,' ');
}
[/PHP]
This gives me a very informative, but still quite useless error message.
[PHP]
file.cpp: In function ‘int main()’:
file.cpp:175: error: no match for ‘operator<<’ in ‘std::cout <<
Array<T>::operator+(float) [with T = int](1.0e+0f)’
/usr/include/c++/4.2/ostream:112: note: candidates are: std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT,
_Traits>& (*)(std::basic_ostream<_CharT, _Traits>&)) [with _CharT = char, _Traits =
std::char_traits<char>]
/usr/include/c++/4.2/ostream:121: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ios<_CharT,
_Traits>& (*)(std::basic_ios<_CharT, _Traits>&)) [with _CharT = char, _Traits =
std::char_traits<char>]
/usr/include/c++/4.2/ostream:131: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::ios_base&
(*)(std::ios_base&)) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:169: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long int) [with _CharT =
char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:173: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long unsigned int) [with
_CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:177: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(bool) [with _CharT = char,
_Traits = std::char_traits<char>]
/usr/include/c++/4.2/bits/ostream.tcc:92: note:                
std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT,
_Traits>::operator<<(short int) [with _CharT = char, _Traits =
std::char_traits<char>]
/usr/include/c++/4.2/ostream:184: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(short unsigned int) [with
_CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/bits/ostream.tcc:106: note:                
std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT,
_Traits>::operator<<(int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:195: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(unsigned int) [with _CharT
= char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:204: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long long int) [with
_CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:208: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long long unsigned int)
[with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:213: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(double) [with _CharT =
char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:217: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(float) [with _CharT =
char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:225: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long double) [with _CharT
= char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:229: note:                 std::basic_ostream<_CharT,
_Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(const void*) [with _CharT
= char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/bits/ostream.tcc:120: note:                
std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT,
_Traits>::operator<<(std::basic_streambuf<_CharT, _Traits>*) [with _CharT = char,
_Traits = std::char_traits<char>]
matrix.cpp:1050: note:                 std::ostream& operator<<(std::ostream&,
Array<U>&) [with T = int]
make: *** [last] Error 1
[/PHP]

If I make the array in the overloaded '<<' const I get a somewhat smaller error message, that is.
[PHP]
//overloading of '<<' for Array type
template<typename T>
 std::ostream& operator<<(std::ostream &o,const Array<T> &a){
  return a.dump(o,' ');
}
[/PHP]
Gives

[PHP]
matrix.cpp: In function ‘std::ostream& operator<<(std::ostream&, const Array<U>&)
[with T = char]’:
file.cpp:54:   instantiated from here
matrix.cpp:1051: error: passing ‘const Array<char>’ as ‘this’ argument of
‘std::ostream& Array<T>::dump(std::ostream&, char) [with T = char]’ discards
qualifiers
matrix.cpp: In function ‘std::ostream& operator<<(std::ostream&, const Array<U>&)
[with T = int]’:
thorfinn.cpp:65:   instantiated from here
matrix.cpp:1051: error: passing ‘const Array<int>’ as ‘this’ argument of
‘std::ostream& Array<T>::dump(std::ostream&, char) [with T = int]’ discards
qualifiers
matrix.cpp: In function ‘std::ostream& operator<<(std::ostream&, const Array<U>&)
[with T = float]’:
thorfinn.cpp:75:   instantiated from here
matrix.cpp:1051: error: passing ‘const Array<float>’ as ‘this’ argument of
‘std::ostream& Array<T>::dump(std::ostream&, char) [with T = float]’ discards
qualifiers
make: *** [last] Error 1
[/PHP]
But making it const doesn't make sense, since theres no way that I can const my implementation of dump
And my implementation of dump

[PHP]std::ostream& Array<T>::dump(std::ostream &o,char sep){
  o<<"length of array is: " <<x_<<std::endl;
  for(uint i=0;i<x_;i++)
    o<< data_[i]<<sep;
  o<<std::endl;
  return o;[/PHP]

thanks for your reply

---

### Post by dribeas on 2008-09-22
> **monkeyking said:**
> [PHP]
class Array{
...
  std::ostream& dump(std::ostream &o=(std::cout),char sep=' ');
  Array<T> operator+ (const Array<T>&);
  Array<T>operator+( const float f );
...
}

//overloading of '<<' for Array type
template<typename T>
 std::ostream& operator<<(std::ostream &o,Array<T> &a){
  return a.dump(o,' ');
}
[/PHP]
This gives me a very informative, but still quite useless error message.


You cannot use a temporary (unnamed) object as parameter to a function that takes a non-const reference.
Your signature for the operator should be:
```

template <typename T>
std::ostream& operator<<( std::ostream& o, Array<T> const & a );

```

> **monkeyking said:**
> 
[PHP]
//overloading of '<<' for Array type
template<typename T>
 std::ostream& operator<<(std::ostream &o,const Array<T> &a){
  return a.dump(o,' ');
}
[/PHP]
[PHP]
matrix.cpp: In function &#8216;std::ostream& operator<<(std::ostream&, const Array<U>&)
[with T = char]&#8217;:
file.cpp:54:   instantiated from here
matrix.cpp:1051: error: passing &#8216;const Array<char>&#8217; as &#8216;this&#8217; argument of
&#8216;std::ostream& Array<T>::dump(std::ostream&, char) [with T = char]&#8217; discards
qualifiers
[/PHP]

Right, now the error is that you are passing a constant reference into a method that is not const. Modify your signature of dump() to:

```

std::ostream& Array<T>::dump( std::ostream&, char ) const;

```

> **monkeyking said:**
> But making it const doesn't make sense, since theres no way that I can const my implementation of dump
And my implementation of dump

[PHP]std::ostream& Array<T>::dump(std::ostream &o,char sep){
  o<<"length of array is: " <<x_<<std::endl;
  for(uint i=0;i<x_;i++)
    o<< data_[i]<<sep;
  o<<std::endl;
  return o;
}[/PHP]

It does make perfect sense: your dump() method does not modify your data, the object (as perceived externally) should be exactly the same before and after calling dump(). That is the criteria to use when deciding if a method should be const.

Note that it is the state of the object as perceived externally, in some cases you want to make changes to internal member attributes and still the operation is overall const:
```

class X
{
public:
   // ...
   Data retrieve() const
private:
   ComplexDataStructure data_; // Real data
   mutable Mutex mutex_; // thread safety mutex
   mutable Data cache_; // optimization
   mutable Key cacheKey_; // optimization
};

Data X::retrieve( Key key ) const
{
   Guard guard(mutex_); // modifies mutex_!!!

   if ( cacheKey_ == key )
   {
      return cache_;
   } else {
      cache_ = data_.expensive_retrieval_operation( key ); // modifies cache_!!!
      // data_.expensive_retrieval_operation() is const
   }
   return cache_;
}
// Guard is a RAII to release the lock whenever it goes out of scope:
class Guard
{
public:
   Guard( Mutex& mutex ) : mutex_( mutex ) { mutex_.acquire(); }
   ~Guard() { mutex_.release(); }
private:
   Mutex& mutex_;
};

```

Note that in the above code both mutex_ and cache_ are marked as mutable: they are not part of the perceived state of the object. The data structure does not change, but you need to modify your mutex_ as to acquire the lock. Also as the operation is expensive, you may cache_ the result so that it can be returned on consecutive calls.

This is a stupid example, but I hope it gives the idea: even if changes are being made inside your object, the perceived net result is that there was no change. Any method call in the object will yield the same result.

---

### Post by monkeyking on 2008-09-22
> **dribeas said:**
> You cannot use a temporary (unnamed) object as parameter to a function that takes a non-const reference.
Right, now the error is that you are passing a constant reference into a method that is not const. Modify your signature of dump() to:
```

template <typename T>
std::ostream& Array<T>::dump( std::ostream&, char ) const;

```

Of cause...
I really need to get a grip on these signatures
 
> **dribeas said:**
> 
Note that it is the state of the object as perceived externally, in some cases you want to make changes to internal member attributes and still the operation is overall const:

This is quite nice to know.
Untill a few weeks ago,
I actually never used const declarations.

But I'm beginning to find them quite handy.
Some annoying problems can be caught at compile time.

I still havn't found a practic use for static, except for making a var shared among objects.

But thanks, dribeas!,
you have been most helpfull,
and I've learned more c++/stl programming in the last week,
than I have en the last year,

thanks again.

---

