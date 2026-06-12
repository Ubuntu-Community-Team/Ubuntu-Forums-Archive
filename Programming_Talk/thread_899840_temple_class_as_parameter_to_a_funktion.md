---
title: "temple class as parameter to a funktion"
date: 2008-08-24
forum: Programming Talk
---

### Post by monkeyking on 2008-08-24
Hi I'm still in the learning process of basic templates,

given the following code

```

#include <cstdlib>
#include <iostream>
#include <string>

using namespace std;

template<typename T>
 class Array {
 public:
  void print(int stop=0,string sep="\n");
   Array(int len)                : len_(len), data_(new T[len]) { }
  ~Array()                          { delete[] data_; }
   int len() const                  { return len_;     }
   const T& operator[](int i) const { return data_[i]; }
         T& operator[](int i)       { return data_[i]; }
   Array(const Array<T>&);
   Array<T>& operator= (const Array<T>&);
 private:
   int len_;
   T*  data_;
 }; 

template<typename T> 
void Array<T>::print(int stop,string sep){
  printf("len is: %d\n",len_);
  for (int i=0;i<len_;i++) 
    printf("%d%s",data_[i],sep.c_str());
     
}

//template <class T>
void multi(int i,Array yes){ //this function
  cout <<"adsf"<<yes.len()<<endl;
}

int main(int argc, char *argv[]){
  Array<int> ai(8);
  for (int i=0;i<ai.len();i++)
    ai[i]=i;
  ai.print(0 ,"\t");

  multi(3,ai);
  return 0;
}

```

How do I define a function that takes a class derived from the Array type?

thanks in advance

---

### Post by dwhitney67 on 2008-08-24
Define your function to receive the parameter as a pointer, or as a reference to the object being passed in.

---

### Post by monkeyking on 2008-08-24
Can you elaborate on the syntax. 
Should I type cast from a void * pointer?

```
//template <class T>
void multi(int i,Array yes){ //this function
  cout <<"adsf"<<yes.len()<<endl;
}

```

---

### Post by dwhitney67 on 2008-08-24
As a pointer:
[PHP]
template <class T>
void multi( int i, Array<T> *a )
{
  std::cout << "adsf " << a->len() << std::endl;
}
...
multi( 3, &ai );
[/PHP]

Using a reference:
[PHP]
template <class T>
void multi( int i, Array<T> &a )
{
  std::cout << "adsf " << a.len() << std::endl;
}
...
multi( 3, ai );
[/PHP]

---

### Post by monkeyking on 2008-08-24
thanks now it will compile,
but I still find it strange that I need to use ref/pointers.

It should seem possible to pass a template object as parameter.
But now it works.

In my example I've overloaded the [] operator.
What is the correct syntax accesing using the pointer parameter passing

/thanks in advance

```

template<class T>
void multi(int i,Array<T> *a){
cout << "length is:"<<a->len()<<endl;
a[5]=3;
}

```

---

### Post by dwhitney67 on 2008-08-24
[edited]
I was wrong.  For now try this:
[php](*a)[5] = 3;[/php]
This also works:
[php]a->operator[]( 5 ) = 3;[/php]

---

### Post by dribeas on 2008-08-25
> **monkeyking said:**
> ```

template<class T>
void multi(int i,Array<T> *a){
cout << "length is:"<<a->len()<<endl;
a[5]=3;
}

```

Probably for completeness dwhitney67 offered both allowed syntaxes, one with pointer another with reference. If you stick to references (they are more natural for coding) this code will work directly:
```

template <typename T>
class Array 
{
   ...
   template <typename U>
   void multi( int i, Array<U> & a )
   {
      cout << "length is: " << a.len() << endl;
      a[ 5 ] = 3;
   }

```

At least syntax-wise. Now on the design issues... what are you trying to achieve with the code? As it is, it is a templated method that does not use the object for anything, but changes the Array<> passed as reference. It seems as if it could be either a free templated function or else a method of Array<T> that does not receive an Array<> --uses implicit this.

Note that I changed the syntax a little: if you are defining a member function of a template on parameter T, then if the method is not templated 'template' keyword does not need to be specified. If the method is templated is because you want o add another type to the genericity and you should give it a different name U. Else internal T (now U) will shade external T (initial T).

   David

---

### Post by dwhitney67 on 2008-08-25
I thought a little more about the exercise posted by the OP, and with the comments produced by Dribeas, I wonder if the solution below would be better?  A class, called Array, is a subclass of an STL vector.
[PHP]
#include <vector>
#include <iostream>


template< class T >
class Array : public std::vector<T>
{
  public:
    // constructor
    Array( size_t capacity = 0 ) : std::vector<T>(capacity) {}

    // add other constructors if necessary...

    // destructor
    ~Array() {}

    // print method similar to that in the OP
    void print( int stop = 0, std::string sep = "\t" )
    {
      std::cout << "len is: " << this->size() << std::endl;

      const size_t last = (stop == 0 ? this->size() : stop );

      for ( size_t i = 0; i < last; ++i )
      {
        std::cout << (*this)[i] << sep;
      }
      std::cout << std::endl;
    }

    // friend function to assist with printing Array attributes
    template< typename U >
    friend std::ostream & operator<<( std::ostream &os, const Array<U> &a )
    {
      os << "len is: " << a.size() << std::endl;

      for ( size_t i = 0; i < a.size(); ++i )
      {
        os << a[i] << "\t";
      }

      return os;
    }

    template< typename U >
    friend void multi( size_t index, Array<U> &a )
    {
      std::cout << "length is: " << a.size() << std::endl;
      a[5] = 3000;
    }
};


int main()
{
  Array<int> ai(8);

  for ( size_t i = 0; i < ai.size(); ++i )
  {
    ai[i] = i;
  }
  ai.print( 0, "\t" );             // print array

  multi( 3, ai );                  // manipulate the array ai at index 3
  std::cout << ai << std::endl;    // print changes

  ai.push_back( 10 );              // add a new element
  std::cout << ai << std::endl;    // print changes

  return 0;
}
[/PHP]

P.S.  The for-loops used in the code above could be simplified by using the STL for_each() algorithm, however for clarity, I elected to use the [] operator.

Since Array does not have any additional member data, the need to define a copy contructor or an assignment operator= was not necessary since these are already offered by the STL vector.

---

### Post by hod139 on 2008-08-25
It's not safe to extend from STL containers.  The writers wanted to maintain compatibility with C as much as possible when writing the STL, so there are no virtual functions.  Most important being the destructors are not virtual.

---

### Post by dwhitney67 on 2008-08-25
Then in such case, perhaps the OP should just use an STL vector without reinventing the wheel with the Array class.

I think the only unique functionality presented was the print() method; this can be defined as a function that is called by for_each, or conversely print() can display the length (as is currently done) and then use for_each to call another method.

In conclusion, I think that the Array class is not necessary; unless it is being designed for learning purposes or the OP is restricted to Embedded-C++ (unlikely).

---

### Post by monkeyking on 2008-08-25
> **dribeas said:**
> ...

At least syntax-wise. Now on the design issues... what are you trying to achieve with the code?...

   David

Actually I'm just trying to get learn the syntax and so forth. :)

But thanks you have all been very helpfull.
I still find it ackward though, that it is not possible to pass a templated class as a val, but only as a ref/pointer.

---

### Post by dwhitney67 on 2008-08-26
> **monkeyking said:**
> ...
I still find it ackward though, that it is not possible to pass a templated class as a val, but only as a ref/pointer.
That's not true; you can pass a templated object by value.  Here's a simple example:
[PHP]#include <iostream>

template< class T >
class Foo
{
  public:
    Foo( T value ) : m_value(value) {}

    ~Foo() {}

    void setValue( T value ) { m_value = value; }

    T getValue() const { return m_value; }

    template< typename U >
    friend std::ostream & operator<<( std::ostream &os, const Foo<U> &foo )
    {
      os << foo.m_value;
      return os;
    }

  private:
    T m_value;
};

template< typename U >
void function( Foo<U> foo )
{
  foo.setValue( 10 );
  std::cout << "value is now 10... " << foo << std::endl;
}

int main()
{
  Foo<int> f(5);
  std::cout << "value is originally 5... " << f << std::endl;
  function( f );
  std::cout << "value should still be 5... " << f << std::endl;
  return 0;
}[/PHP]

---

### Post by dribeas on 2008-08-26
> **dwhitney67 said:**
> 
[PHP]
template< class T >
class Array : public std::vector<T>
[/PHP]


I agree that it is better just using std::vector. Now some comments... On STL derivation. It is true that STL containers are not meant to be derived, and thus have no virtual methods/destructors. The problem with it is that an Array<T> cannot be destroyed thought a std::vector<T> pointer (where virtual destructor would be called. This means that to be on the safe side you should not use public inheritance, but you can use private inheritance and write Array<T> as a façade around vector facilities.

Not that it is worth the time. If you only want to provide a print method you can implement it as a free function. Which brings us to this code:

> **dwhitney67 said:**
> 
[PHP]{
    // friend function to assist with printing Array attributes
    template< typename U >
    friend std::ostream & operator<<( std::ostream &os, const Array<U> &a );
    template< typename U >
    friend void multi( size_t index, Array<U> &a );
};[/PHP]


There are a couple of issues here. First, friendship is the strongest relation in C++, and should be avoided. In this case, only public operations are used, so there is no reason to use friendship.

It is usual to provide a virtual print/dump method (not free function) in classes that are designed to be extended with operator<< being just a call to that method. This allows to polymorphic insertion into streams.

operator<< could, and possibly should be implemented as a call to print, as it will reduce code, and any changes to print will automatically be applied to operator<<.

```

class Base {
public:
	virtual void print( ostream& o ) { o << "Base"; }
};
class D : public X {
public:
	virtual void print( ostream& o ) { o << "Derived"; }
};
ostream& operator<<( ostream& o, Base const & x)
{
	x.print( o );
	return o;
}
{
	Base *b = new Derived();
	cout << *b; // will print "Derived"
		// If print were not virtual "Base" would be printed
}

```

If the class is not meant to be extended, print can be omitted and only operator<< implemented as a free function.

> **dwhitney67 said:**
> 
P.S. The for-loops used in the code above could be simplified by using the STL for_each() algorithm, however for clarity, I elected to use the [] operator.


It is better to use iterators (whether with for_each or in a handmade loop):
```

	for ( typename std::vector<T>::iterator it = begin();
		it != end(); ++it )
	{
		ostr << *it << sep; // with sep defined
	}

```

   David

---

### Post by dribeas on 2008-08-26
> **monkeyking said:**
> I still find it ackward though, that it is not possible to pass a templated class as a val, but only as a ref/pointer.

I guess we may be having a naming problem here. The OP asked about passing a class *derived* from, which means inheritance. If you want inheritance and polymorphism you must use references/pointers.

I am getting to think that what you wanted to pass was on instantiation of the template, which is unrelated to inheritance. In that case you don't need to use references, but note that pass-by-value semantics imply making possibly unnecessary copies of the objects, which for Array-s could be expensive.

```

class B { virtual void print() { std::cout << "Base"; } };
class D : public B { virtual void print() { std::cout << "Derived"; } };
void f( B& a ) { a.print(); }
void g( B* a ) { a->print(); }
void h( B a ) { a.print(); }

template <typename T> C {};
template <typename T> void t( C<T> ) { ... }

int main()
{
	D d;
	f( d ); // reference: "Derived"
	g( d ); // pointer:  "Derived"
	h( d ); // value: "Base", also a copy of d 'sliced' to B type is created

	C<int> ci; // instantiation for int
	t( ci ); // Allowed: pass by value of instantiation
}

```

Note that if C is a large object, a copy will be created (copy-constructed) during call to t(). For most not trivial classes, it is better to pass const references than values. The language warrants that the method will not modify the contents and at the same time it won't be required to copy objects.

   David

---

### Post by hod139 on 2008-08-26
> **dribeas said:**
> 
There are a couple of issues here. First, friendship is the strongest relation in C++, and should be avoided. In this case, only public operations are used, so there is no reason to use friendship.


Why should friend be avoided?  I agree that it is powerful and should be used correctly, but not avoided.  There are many situations when it can improve data encapsulation (and even slightly speed) and should be the preferred choice.  For example, if you wanted to write a print function for a class using a non-member non-friend function, you must write public interface functions for every field of the class.  Using a friend, you have access to these private members directly, and you do not need to expose them (it also removes the slight overhead of a function call, but that is less important).

For this example, there was a public interface already available, so a non-friend non-member function was possible.  But claiming that it is better to use non-friend non-member functions for operator<< is not true.  For other operators, I prefer using non-member non-friends, but people can (and do) debate this as well.  For the specific case of operator<<, I would actually argue that making it friend function is the preferred way.  It is no worse than non-friend non-member when the data to print already has public interfaces, but is also allows changes to a classes internals to not break the print function.

---

### Post by dribeas on 2008-08-26
> **hod139 said:**
> Why should friend be avoided?  I agree that it is powerful and should be used correctly, but not avoided.  There are many situations when it can improve data encapsulation (and even slightly speed) and should be the preferred choice.  For example, if you wanted to write a print function for a class using a non-member non-friend function, you must write public interface functions for every field of the class.  Using a friend, you have access to these private members directly, and you do not need to expose them (it also removes the slight overhead of a function call, but that is less important).

For this example, there was a public interface already available, so a non-friend non-member function was possible.  But claiming that it is better to use non-friend non-member functions for operator<< is not true.  For other operators, I prefer using non-member non-friends, but people can (and do) debate this as well.  For the specific case of operator<<, I would actually argue that making it friend function is the preferred way.  It is no worse than non-friend non-member when the data to print already has public interfaces, but is also allows changes to a classes internals to not break the print function.

You are completely right. I guess I was not clear enough: whenever it is not required (as it was with this case), it should be avoided as it raises coupling and is intrusive. That is in this example, it can and thus should be avoided.

The general rule is that you should always use the weakest relation you can in your designs. If you need friendship use it. If you need inheritance use it. If you can manage with aggregation or use, it will be better. If aggregation suffices, then avoid inheritance, if use is enough, don't add friendship.

Many good designs cannot be properly implemented without frienship. Last example I used in this forum was that of shared_ptr/weak_ptr in boost libraries. Those to classes (templates, indeed some internal implementation class) are unrelated (inheritance-wise) but they need access to private members of the other. Any design that does not use friendship would require publishing inner data and thus break encapsulation, as you have pointed.

Thanks for bringing this up so that I can try to get it right :)

   David

---

