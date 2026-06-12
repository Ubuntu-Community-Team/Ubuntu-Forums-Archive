---
title: "header problems in g++ (new to c++)"
date: 2011-04-03
forum: Programming Talk
---

### Post by jebsector on 2011-04-03
I have the following header file:

```

#include <string>
#include <vector>

#ifndef SOMECLASS_H
#define SOMECLASS_H

class someclass {
   private: 
      string var1;
      string var2;
      vector<string> mycoll;
   public:
      someclass();
      ~someclass();
      void updateVar1(string val);
      void updateVar2(string val);
      void addToVector(string val);
};

#endif

```

Then I have code for someclass as follows:

```

#include "someclass.h"

someclass::someclass() {}
someclass::~someclass() {}
void someclass::updateVar1(string val) {
   var1 = val;
}
void someclass::updateVar2(string val) {
   var2 = val;
}
void someclass::addToVector(string val) {
   //etc..
}

```

The problem I'm having just with this code is with g++, the includes in the header file are there but when i reference string and vector in the header file it doesn't get recognized by the compiler.

Also, if I don't want memory leaks, is simply assigning a new value on top of an existing string ok?

And, let's say i had an array of strings for var2, and i created it using the new operator.  in updateVar2 would i then need to first delete the array and then call new again to replace it; or what is the correct way to overwrite an existing object?

Thanks,

---

### Post by MadCow108 on 2011-04-03
> **jebsector said:**
> I have the following header file:

The problem I'm having just with this code is with g++, the includes in the header file are there but when i reference string and vector in the header file it doesn't get recognized by the compiler.

you are missing the std:: namespace for the strings and vectors (don't use using namespace in a header, bad style)

> 
Also, if I don't want memory leaks, is simply assigning a new value on top of an existing string ok?

And, let's say i had an array of strings for var2, and i created it using the new operator.  in updateVar2 would i then need to first delete the array and then call new again to replace it; or what is the correct way to overwrite an existing object?

yes simply assigning will not create memory leaks and you would have to delete/new when it would be an array.
but avoid new/delete where ever possible, just use vectors instead of old C-style arrays

---

### Post by jebsector on 2011-04-03
So then the code in the header becomes:

```

#include <string>
#include <vector>

#ifndef SOMECLASS_H
#define SOMECLASS_H

class someclass {
   private: 
      std::string var1;
      std::string var2;
      std::vector<std::string> mycoll;
   public:
      someclass();
      ~someclass();
      void updateVar1(std::string val);
      void updateVar2(std::string val);
      void addToVector(std::string val);
};

#endif

```

And that compiled the header file, but then the source file doesn't pick up the includes from the header, and so in the .cpp file it doesn't recognize string and vector.  

Do I need to move header includes from the std namespace to the source file?  And, it seems to work when i include the header of some class that i create within a project..

..I tried moving the includes from the standard library over to the source file, and it seems to work like that using the std namespace.  Then includes in the header file that i use like #include "someclass.h" seem to work fine.  Is that how it is supposed to be?

Thanks,

---

### Post by cgroza on 2011-04-03
You still need to use  std:: in the source file, are you saying you can't access the member variables or just the vector class?

---

### Post by jebsector on 2011-04-03
ok, i don't know what happened.  I just moved the includes back to the header file and it compiled without having to include string or vector in the .cpp file.  I just have the using std namespace and it seems to work.  

Sorry - this is my first time doing these things.  To make sure, when I include a library in a header, i then need to use that namespace in the .cpp file.  So say i'm using boost - and for whatever reason i include the boost headers in the .h file.  Then in the .cpp file to use the boost objects i just prefix it with the namespace?

Thanks,

---

### Post by cgroza on 2011-04-03
> **jebsector said:**
> ok, i don't know what happened.  I just moved the includes back to the header file and it compiled without having to include string or vector in the .cpp file.  I just have the using std namespace and it seems to work.  

Sorry - this is my first time doing these things.  To make sure, when I include a library in a header, i then need to use that namespace in the .cpp file.  So say i'm using boost - and for whatever reason i include the boost headers in the .h file.  Then in the .cpp file to use the boost objects i just prefix it with the namespace?

Thanks,
Namespace rules apply everywhere. You either put using directives, either namespace resolution operator ::.

---

### Post by dazman19 on 2011-04-04
using namespace std;

you can make your own namespaces in your header file.

#include "a3.h" //this is in the main .cpp file
using namespace A;

header file a3.h has multiple namespaces.

#include <iostream>
#include <string>
namespace A {
  void displayInfo() {
  std::cout << "----------------------------------------" << std::endl;
  } // I have used explicit call to std namespace here.
}
namespace B {	
   using namespace std; //required for cout to be called without using namespace operator '::'
class Date { //stores a date. (DD/MM/YYYY) as integers.
	public:
		Date() {};
		Date(int d, int m, int y);
		~Date(){};
		void print_nz(void);
		void print_text(void);
		void add(int days);
		Date operator+(const int &b);
		//ostream& operator<<(ostream& output, const Date &d);
	private:
		int day;
		int month;
		int year;
	};

Date::Date(int d, int m, int y) { //constructor (checking for valid date) - if the date is not valid the variables inside the object will be undefined.
	if (d > 0 && d < 32) {
		day = d;
	}
	if (m > 0 && m < 13) {
		month = m;
	}
	if (1899 > 0 && y < 3000) {
		year = y;
	}
}

void Date::print_nz(void) { //print date in the standard NZ format DD/MM/YYYY 
	std::cout<<day<<"/"<<month<<"/"<<year;
}

ostream& operator<<(ostream& output, Date &d) { //overloaded << operator when working with Date class.
	d.print_text();
	return output;
}

Date Date::operator+(const int &b) { //overloaded operator + to add and integer of days to the date.
	Date calculateddate(day, month, year);
	calculateddate.add(b);
	return calculateddate;
}

---

### Post by dwhitney67 on 2011-04-04
> **jebsector said:**
> So then the code in the header becomes:


Try something like this instead:

```

#ifndef SOMECLASS_H
#define SOMECLASS_H

[B]#include <string>
#include <vector>
[/B]
class SomeClass {
   public:
      SomeClass();
      ~SomeClass();
      void updateVar1(**const std::string&** val);
      void updateVar2(**const std::string&** val);
      void addToVector(**const std::string&** val);

   private: 
      std::string var1;
      std::string var2;
      std::vector<std::string> mycoll;
};

#endif

```

If you want to avoid excessive copying of objects (and hence avoid CPU and memory usage), pass objects by reference.  Indicate whether you do not plan to modify them using the 'const' designator.

Btw, I see a lot of developers defining the 'private' section of a class first.  This is kind of silly since it will be the 'public' (or 'protected') interfaces that will be of most interest to someone (or you) when using the class.

In SomeClass.cpp:
```

#include "SomeClass.h"


SomeClass::SomeClass()
{
}

...

void
SomeClass::addToVector(const std::string& val)
{
   ...
}

```
Unless you have a dying need to use a "using namespace" directive, I would avoid it.  The code above is too trivial to warrant its use.

I would master the basics of C++ (by perusing the following [tutorial]("http://www.cplusplus.com/doc/tutorial/")) before delving into Boost.

---

### Post by muteXe on 2011-04-04
> 
Btw, I see a lot of developers defining the 'private' section of a class first. This is kind of silly since it will be the 'public' (or 'protected') interfaces that will be of most interest to someone (or you) when using the class.


I don't have a choice. My company's coding standards mandate we have to do it like this.  Weird, i know...

---

### Post by cgroza on 2011-04-04
That is not so important unless you have more than 50 members or functions. My classes never go bigger than 20.

---

