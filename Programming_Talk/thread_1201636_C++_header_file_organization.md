---
title: "C++ header file organization"
date: 2009-07-01
forum: Programming Talk
---

### Post by swappo1 on 2009-07-01
Hello,

I am having a difficult time with multiple header files.  I am trying to use 1 class per header file to keep things organized.  The problem is that I need some of the information from one class in another class and I am having trouble accessing that information since it is in a different header file.  Here is my example to illustrate my problem:
```
//main.cpp
#include <iostream>
#include <string>
#include <vector>
#include "one.h"
#include "two.h"

using namespace std;

int main()
{
	One one;
	Two two;
	
	two.output();
	
	return 0;
}
..................................................
//one.h
#ifndef ONE_H
#define ONE_H
#include <string>
#include <vector>
using namespace std;

class One
{
	private:
		string s;
		vector<int> v;
	public:
		string set_string();
		vector<int> set_vector();
};

#endif
....................................................
//one.cpp
#include <string>
#include <vector>
#include "one.h"

using namespace std;

string One::set_string()
{
	return s = "This is a string";
}

vector<int> One::set_vector()
{
	v.push_back(1);
	v.push_back(2);
	v.push_back(3);
	
	return v;
}
................................................
//two.h
#ifndef TWO_H
#define TWO_H
#include "one.h"
#include <string>
#include <vector>
using namespace std;

class Two
{
	private:
		string s2;
		vector<int> v2;
	public:
		void get_string();
		void get_vector();
		void output();
};
#endif
.................................................
//two.cpp
#include <iostream>
#include <string>
#include <vector>
#include "two.h"
#include "one.h"
using namespace std;

void Two::get_string()
{
	s2 = one.set_string();
}

void Two::get_vector()
{
	v2 = one.set_vector();
}

void Two::output()
{
	cout << s2 << endl;
	for(int i = 0; i < v2.size(); i++)
		cout << v2[i] << endl;
}
```
Here is the errors I am getting.
> [hopchewer@hopchewer class_ex]$ make
g++ -O2 -Wall -Werror -ansi   -c -o main.o main.cpp
g++ -o class main.o one.cpp two.cpp -lpthread
two.cpp: In member function ‘void Two::get_string()’:
two.cpp:11: error: ‘one’ was not declared in this scope
two.cpp: In member function ‘void Two::get_vector()’:
two.cpp:16: error: ‘one’ was not declared in this scope
make: *** [class] Error 1

The issue is in class Two where I try and access set_string() and set_vector from class one.  Is there a proper way(best practices) to do this that I am missing?

---

### Post by junxuan on 2009-07-01
i notice that your two functions

```
void Two::get_string()
{
	s2 = one.set_string();
}

void Two::get_vector()
{
	v2 = one.set_vector();
}

```

you are accessing the class for the functions which i believe does not work. Instead a "One" object should be created first, and the set_string and set_vector should be used through the object.

You could do it something like that, it might not be the best solution though. Modify your get_string and get_vector to take a "one" object as a argument


```
void Two::get_string(One &oneObject)
{
	s2 = **O**ne.set_string();
}

void Two::get_vector(One &oneObject)
{
	v2 = **O**ne.set_vector();
}

```

and use it like this:
```

#include <iostream>
#include your class etc..

int main(){
    One *newObject = new One;
    Two *twoObject = new Two;
    
    Two.get_string(newObject);
}

```

---

### Post by swappo1 on 2009-07-01
```
#include <iostream>
#include your class etc..

int main(){
    One *newObject = new One;
    Two *twoObject = new Two;
    
    Two.get_string(newObject);
}
```
I am not sure about how to do #include your class etc..  I tried using forward declarations for class One, Two:
```
//main.cpp
#include <iostream>
#include <string>
#include <vector>
#include "one.h"
#include "two.h"
class One;
class Two;

using namespace std;

```
I have the following errors:
> g++ -O2 -Wall -Werror -ansi   -c -o main.o main.cpp
main.cpp: In function ‘int main()’:
main.cpp:17: error: expected unqualified-id before ‘.’ token
cc1plus: warnings being treated as errors
main.cpp:14: error: unused variable ‘newObject’
main.cpp:15: error: unused variable ‘twoObject’
make: *** [main.o] Error 1


---

### Post by dwhitney67 on 2009-07-01
@ OP

junxuan is correct; you cannot access an object 'one' in Two.cpp unless it has been instantiated.  Where that object is instantiated is up to you.  You can consider passing it as a parameter (ie. implying it was instantiated elsewhere), or you could consider making it a class data member of class Two.

The other issues I see with your code are redundant includes for file that you are already including.  For instance, in Two.h, you include One.h... which is fine.  But there is no need to include One.h in Two.cpp.  It will be included via the include for Two.h.

The other issues I see that you should avoid is specifying a "using namespace" directive in any header file.  Also, you should get into the habit of including project header files before system header files.

Consider the following:

One.h:
```

#ifndef ONE_H
#define ONE_H

#include <string>

class One
{
public:
  One(const std::string& str);

  std::string getString() const;

private:
  std::string m_str;
};

#endif

```

One.cpp:
```

#include "One.h"

One::One(const std::string& str) : m_str(str)
{
}

std::string
One::getString() const
{
  return m_str;
}

```

Two.h
```

#ifndef TWO_H
#define TWO_H

#include <string>


// forward declaration
class One;


class Two
{
public:
  Two(One& one);

  std::string getOneString() const;

private:
  One& m_one;
};

#endif

```

Two.cpp:
```

#include "Two.h"
#include "One.h"

Two::Two(One& one) : m_one(one)
{
}

std::string
Two::getOneString() const
{
   return m_one.getString();
}

```

main.cpp:
```

#include "One.h"
#include "Two.h"
#include <iostream>

int main()
{
   One one("Hello World");
   Two two(one);

   std::cout << two.getOneString() << std::endl;
}

```

To build app:
```

g++ main.cpp One.cpp Two.cpp -o myapp

```

---

