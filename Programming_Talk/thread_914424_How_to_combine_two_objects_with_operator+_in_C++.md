---
title: "How to combine two objects with operator+ in C++"
date: 2008-09-08
forum: Programming Talk
---

### Post by RavUn on 2008-09-08
I've been trying to figure this out for a while...

I have two objects and I need to write a function for operator+ so the two can be combined.

I created a header file and have:
```
		friend bag operator+ (const bag first, const bag& other);
```
and I have my class file with:
```
bag operator+ (const bag& first, const bag& other)
{
	return //logic?
}

```

I tried return (first + other) but that gave a segmentation fault... I tried a few other things then changed it back to return (first + other) and now it's not compiling.

What would be the logic to combine two objects?  Each object just has a vector storing characters (kinda like a string....) and I just need to figure out how to append the second vector onto the first vector.  Since the function is a friend I cannot just copy the vector since it's declared private in the header file.

We've had 4 class periods on C++ and I haven't figured this out yet.  If all else fails I'm just going to use a String, but I think the professor wanted us to use vectors.  

Would I want to copy the vectors then use the insert method?  But, how would I return that as a bag object and not as a vector object?


Here's the full source code for the class file
```

//Assignment 1

#include "bag.h"
#include <iostream>

using std::cout;
using std::endl;



bag::bag()
{
	charvect.resize(0);
}

bag::bag(int size)
{
	charvect.resize(size);
}

int bag::num_items()
{
	return charvect.size();
}

void bag::empty()
{
	charvect.resize(0);
}

void bag::remove()
{
	if (charvect.size() > 0)
	{
		charvect.pop_back();
	}
	else 
	{
		cout << "There are no items to remove" << endl;
	}
}

void bag::add(char c)
{
	charvect.push_back(c);
}

int bag::count_items(char c)
{
	int count = 0;
	for (int i = 0; i < (int) charvect.size(); i++)
	{
		if (charvect[i] == c)
		{
			count++;
		}
	}

	return count;
}

bag bag::copy()
{
	vector<char> temp = charvect;
	return 
}

bag operator+ (const bag& first, const bag& other)
{
	//return blah....
}

/*istream& operator>> (istream& stream, bag& item)
{
	
}

ostream& operator<< (ostream& stream, bag& item)
{
    for (unsigned int i = 0; i < item.size(); i++)
    	stream << (int)item [i];
    return stream;
}
*/
```

---

### Post by dwhitney67 on 2008-09-08
I have no idea what you want to add together, but the method signature (declaration) you desire should be something like:
[PHP]friend Bag operator+( const Bag &bag, const Bag &other )
{
  return Bag( bag.someField + other.someField );
}

...

Bag b1;
Bag b2;

Bag b3 = b1 + b2;[/PHP]

There are other combinations that you may want to explore (e.g. operator+=).  For this method:
[PHP]Bag & operator+=( const Bag &other )
{
  this->someField += other.someField;
  return *this;
}[/PHP]

---

### Post by RavUn on 2008-09-08
I try this and get an error:
[php]
vector<char> bag::get_items()
{
	return charvect;
}

void bag::set_items(vector<char> new_vect)
{
	charvect.assign(new_vect.begin(), new_vect.end());
} 

friend bag operator+ (const bag& first, const bag& second)
{
	
  return bag( first.set_items(first.get_items) + second.set_items(second.get_items) );

}[/php]

```
bag.cpp:87: error: no matching function for call to ‘bag::set_items(<unresolved overloaded function type>) const’
bag.cpp:70: note: candidates are: void bag::set_items(std::vector<char, std::allocator<char> >)
bag.cpp:87: error: no matching function for call to ‘bag::set_items(<unresolved overloaded function type>) const’
bag.cpp:70: note: candidates are: void bag::set_items(std::vector<char, std::allocator<char> >)

```

I'm pretty sure I'm coding the set_items() function wrong (I was trying to avoid doing it a longer way with for loops).  I've been at this for a while, I think I'm going to give my mind a rest and try again.  Thanks for your reply.

---

### Post by Buttink on 2008-09-08
ummm im confused how this is supposed to work but dont you want something more like this?

[PHP]vector<char> bag::get_items()
{
    return charvect;
}

void bag::set_items(vector<char> new_vect)
{
    charvect.assign(new_vect.begin(), new_vect.end());
}  // Does not return a value

friend bag operator+ (const bag& first, const bag& second)
{
    
  return bag( first.get_items + second.get_items );

} // note you may want to actual destory the 2 bags when you add but i have no idea what this is for[/PHP]

---

### Post by dwhitney67 on 2008-09-08
RavUn

I think that you are misinterpreting concepts related to "const" objects, set/get accessors, and the access privileges of a "friend" method.

Rather than answer your problem with specifics (because it may be a homework assignment?), I have attached a simple example that defines a class object that contains a vector of integers and an operator+ friend method.
[PHP]#include <vector>
#include <iostream>

class Bag
{
  public:
    // handy-dandy typedef
    typedef std::vector<int> Data;

    // no-arg constructor
    Bag() {}

    // constructor that accepts a Data (vector) parameter
    Bag( const Data &data )
    {
      m_data = data;
    }

    // accessor to insert values into Data object
    void insertValue( int value )
    {
      m_data.push_back( value );
    }

    friend Bag operator+( const Bag &first, const Bag &second )
    {
      // create temporary vector; initialize with data from the
      // 'first' Bag
      Data temp( first.m_data.begin(), first.m_data.end() );

      // insert the data from the 'second' Bag at the end of the
      // temporary vector
      temp.insert( temp.end(), second.m_data.begin(), second.m_data.end() );

      // construct new Bag that is pre-initialized with data
      return Bag( temp );
    }

    // handy-dandy method for displaying contents of a Bag object
    friend std::ostream & operator<< ( std::ostream &os, const Bag &bag )
    {
      for ( std::vector<int>::const_iterator it = bag.m_data.begin(); it != bag.m_data.end(); ++it )
      {
        os << (*it) << " ";
      }
      return os;
    }

  private:
    Data m_data;
};

int main()
{
  // setup two Bags
  Bag b1;
  Bag b2;

  b1.insertValue( 10 );
  b1.insertValue( 20 );
  b1.insertValue( 30 );

  b2.insertValue( 40 );
  b2.insertValue( 50 );
  b2.insertValue( 60 );

  // test operator+() method
  Bag b3 = b1 + b2;

  // display results
  std::cout << "b1 = " << b1 << std::endl;
  std::cout << "b2 = " << b2 << std::endl;
  std::cout << "b3 = " << b3 << std::endl;

  return 0;
}[/PHP]

---

### Post by monkeyking on 2008-09-09
> **dwhitney67 said:**
> 
[PHP]friend Bag operator+( const Bag &bag, const Bag &other )
[/PHP]

There are other combinations that you may want to explore (e.g. operator+=).  For this method:
[PHP]Bag & operator+=( const Bag &other )[/PHP]


I'm a little confused about the different signatures for overloaded  operators
[PHP]myClass operator+(const myClass other)
vs
myClass operator+ (const myClass first,const myClass second)
[/PHP]

---

### Post by dwhitney67 on 2008-09-09
First of all, I would recommend that the methods accept the "myClass" object by reference; otherwise you are creating a copy of the object(s) upon calling the method, which is wasteful.

As far as the differences between the two methods, the first will act upon the "first" object (aka 'this'), whereas the second method (which should be declared as a friend method) treats both the 'first' and 'second' object as constants, and thus will need to create a new object.

Here's a code example that you can play with to see the subtle differences between the two methods.  Just comment-in the first operator+() to see the differences.
[PHP]#include <iostream>


class Foo
{
  public:
    Foo( int value ) : m_value(value)
    {
      std::cout << "1-arg constructor called." << std::endl;
    }

    Foo( const Foo &other ) : m_value(other.m_value)
    {
      std::cout << "copy-constructor called." << std::endl;
    }

/*
    Foo operator+( const Foo &other )
    {
      std::cout << "operator+( 1-arg ) called." << std::endl;

      m_value += other.m_value;
      return *this;
    }
*/

    friend Foo operator+( const Foo &first, const Foo &second )
    {
      std::cout << "operator+( 2-arg ) called." << std::endl;

      return Foo( first.m_value + second.m_value );
    }

    friend std::ostream & operator<<( std::ostream &os, const Foo &foo )
    {
      os << foo.m_value;
      return os;
    }

  private:
    int m_value;
};

int main()
{
  Foo f1 = Foo(10);
  Foo f2 = Foo(20);

  std::cout << "f1 = " << f1 << std::endl;
  std::cout << "f2 = " << f2 << std::endl;

  f1 + f2;

  std::cout << "f1 = " << f1 << std::endl;

  Foo f3 = f1 + f2;

  std::cout << "f1 = " << f1 << std::endl;
  std::cout << "f3 = " << f3 << std::endl;

  return 0;
}[/PHP]

P.S.  To avoid modifying the principal object (this) in the 1-arg operator+() method, the method could be implemented as the following to return a newly created object with the values of 'this' and 'other' summed together.  This is probably are better implementation, and what I suggested earlier would perhaps be best for the implementation of the operator+=() method.
[PHP]
Foo operator+( const Foo &other )
{
  std::cout << "operator+( 1-arg ) called." << std::endl;

  return Foo( this->m_value + other.m_value );
}
[/PHP]

---

