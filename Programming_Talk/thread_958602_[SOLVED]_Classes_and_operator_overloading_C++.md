---
title: "[SOLVED] Classes and operator overloading C++"
date: 2008-10-25
forum: Programming Talk
---

### Post by jspolen on 2008-10-25
Hi I have a problem with a class I named Person that is in the file Person.cpp
```

#include <iostream>
#include <string>
#include "Person.h"

Person::Person( int s, const string & n )
	: ssn( s ), name( n )
	{ }
		
const string & Person::getname( ) const 
	{ return name; }
			
int Person::getSsn( ) const 
	{ return ssn; }
			
void Person::print( ostream & out = cout ) const 
	{ out << "[ " << ssn << ", " << name << " ]"; }
			
bool Person::equals( const Person & rhs ) const 
	{ return ssn == rhs.ssn; }
			
bool Person::operator==( const Person & rhs ) const 
	{ return equals( rhs ); }


```

The header file is Person.h and looks like this
```

#ifndef PERSON_H
#define PERSON_H

class Person
{
	public:
		Person( int s, const string & n = "" );		
		const string & getname( ) const;		
		int getSsn( ) const;		
		void print( ostream & out = cout )const;	
		bool equals( const Person & rhs ) const;	
		bool operator==( const Person & rhs ) const;
					
	private:
		const int ssn;
		string name;
};
#endif


```

I compile it with the command *g++ -c Person.cpp -o Person.o* and get message

[PHP]
In file included from Person.cpp:3:
Person.h:7: error: expected ‘,’ or ‘...’ before ‘&’ token
Person.h:7: error: ISO C++ forbids declaration of ‘string’ with no type
Person.h:8: error: ISO C++ forbids declaration of ‘string’ with no type
Person.h:8: error: expected ‘;’ before ‘&’ token
Person.h:10: error: ‘ostream’ has not been declared
Person.h:16: error: ‘string’ does not name a type
Person.h:10: error: ‘cout’ was not declared in this scope
Person.cpp:5: error: expected ‘,’ or ‘...’ before ‘&’ token
Person.cpp:5: error: ISO C++ forbids declaration of ‘string’ with no type
Person.cpp: In constructor ‘Person::Person(int, int)’:
Person.cpp:6: error: class ‘Person’ does not have any field named ‘name’
Person.cpp:6: error: ‘n’ was not declared in this scope
Person.cpp: At global scope:
Person.cpp:9: error: expected initializer before ‘&’ token
Person.cpp:15: error: variable or field ‘print’ declared void
Person.cpp:15: error: ‘ostream’ was not declared in this scope
Person.cpp:15: error: ‘out’ was not declared in this scope
Person.cpp:15: error: ‘cout’ was not declared in this scope

[/PHP]

I'm new to C++ and just followed an example in my book and modified it, does anybody know what I'm doing wrong?

---

### Post by jspolen on 2008-10-25
Solved it myself

changed the line

```
void Person::print( ostream & out = cout ) const 

```

in the Person.cpp file to

```
void Person::print( ostream & out ) const 

```

and added ```
#include <string>
using namespace std;
``` in the header file.

---

### Post by Flynn555 on 2008-10-25
> **jspolen said:**
> 
void Person::print( ostream & out = cout ) const 



:lolflag:

---

