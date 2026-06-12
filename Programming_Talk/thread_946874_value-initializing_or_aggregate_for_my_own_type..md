---
title: "value-initializing or aggregate for my own type."
date: 2008-10-13
forum: Programming Talk
---

### Post by monkeyking on 2008-10-13
Is it possible to define aggregate/value-initialization,
for my own class.

Like in basic array declaration
[PHP]int var[3] = {3,2,1}[/PHP]

If I have a very basic class like,

[PHP]
class ary{
  int *m_data;
  int m_len;
public:
  get(int a);
  set(int b);
};
[/PHP]

Would it be possible to initialize this like a basic array.

thanks in advance.

---

### Post by dribeas on 2008-10-13
> **monkeyking said:**
> Would it be possible to initialize this like a basic array.

thanks in advance.

You can provide your own constructor. The syntax will not be the same, but it will initialize members:

```

class Test
{
public:
	Test( int the_int, double the_double ) 
		: m_int( the_int ), m_double( the_double ) 
	{}

private:
	int m_int;
	double m_double;
};

int main()
{
	Test test( 5, 5.5 );
}

```

Not that it seems what you want from your snippet. It seems as yet-another beginner implementation of array/dynamic_array/vector, in which case you might want to receive only the size in the constructor and acquire the memory yourself.

```

class YetAnotherArrayOfInts
{
public:
	explicit YetAnotherArrayOfInts( size_t size = 0 )
		: size_( size ), data_( new int[size] )
	{}

	~YetAnotherArrayOfInts()
	{
		delete []data_;
	}
private:
	size_t size_;
	int * data_;
};

```

---

### Post by jimi_hendrix on 2008-10-13
your syntax suggests you are using C++ so i will use C++ for the example

[PHP]ary myAry[3];[/PHP]

edit: got there too slow...

---

### Post by snova on 2008-10-13
If what you wanted was something like

[PHP]ary AnArray[3] = { 1, 2, 42 };[/PHP]

Then I'm 99% certain that that's impossible. It might be possible with the next standard, though.

---

### Post by monkeyking on 2008-10-13
Thanks for your responses,
but this is not really what I'm talking about,
I'm talking about aggregates which is part of the standard.

Thats section 8.5.1 [decl.init.aggr] of the c++ standard.


But thanks for your adviceces.

---

### Post by dribeas on 2008-10-14
> **monkeyking said:**
> Thats section 8.5.1 [decl.init.aggr] of the c++ standard.


> ```

class ary{
  int *m_data;
  int m_len;
public:
  get(int a);
  set(int b);
};  

```

Your class (besides being ill defined as get and set must have return values) is not an aggregate.

*(8.5.1 par 1): An aggregate is an array or a class (clause 9) with no user-declared constructors (12.1), **no private or protected non-static data members** (clause 11), no base classes (clause 10) and no virtual functions (10.3).*

Your class example has two private non-static data members. That is what made me think that you were trying to do was more in the line of providing a constructor.

Example of an aggregate that can be initialized with an initializer-clause:
```

#include <iostream>
#include <ostream>

class test // [*]
{
public:
   int m_a;
   int m_b;

   // member function for the sake of it
   std::ostream& print( std::ostream& o );
};

// more common to see (but exactly the same) as
// struct test
// {
//    int m_a;
//    int m_b;
//    std::ostream& print( std::ostream& o );
// };

std::ostream& test::print( std::ostream& o )
{ 
   return o << "test( " << m_a << ", " << m_b << " )";
}

int main()
{
   test t = { 5, 7 };

   t.print( std::cout );
}

```

In general, I would avoid having public member attributes and I would provide constructors. Note that initialization clauses are not verified by the compiler to have exactly the same amount of arguments as the class:

```

int main()
{
   test t = { 5 }; // compiler ok, maybe forgot second argument?
}

```

If the number of parameters is smaller than the class defined attributes then value initialization will be performed for the rest of data members (m_b will get 0). In this simple class it is easy to detect, but if you had, say 5 members, forgetting one can go undetected.

With a constructor you can force the compiler into checking the number of arguments (if you want) or you can get the same effect if you so desire:

```

class Test1
{
public:
   Test1( int a, int b ) : a_( a ), b_( b ) {} 
private:
   int a_, b_;
};
class Test2
{
public:
   Test2( int a, int b = 0 ) : a_( a ), b_( b ) {}
private:
   int a_, b_;
};

int main()
{
   Test1 test( 1, 2 ); // ok
   Test1 test( 1 ); // error, need 2 arguments
   Test2 test2( 1 ); // ok, same as test2( 1, 0 )
}

```

Even if more verbose than above, Test2 has the same behavior than you would get with aggregate initialization, but with Test1 the compiler will help you if you forgot an argument.

---

