---
title: "C++ Returning pointers from functions problem."
date: 2010-03-04
forum: Programming Talk
---

### Post by Swerve1000 on 2010-03-04
Hi,

I have been wrestling with this program all day and am looking for some help.

I have never separated a program up before into separate files (main.cpp, base.h and base.cpp).

What I'm trying to do is call a function from main() and have that function return a pointer to a new object.

Once the pointer has been returned, I'm trying to push it into the std::list.

The problem I've been having is this compile error:

> illegal call of non-static member function

I have wrote a simple version of my program which reproduces the same problem:

**main.cpp :**
```

#include <iostream>
#include <list>
#include <string>
#include "base.h"
using namespace std;

int main()
{
	typedef list<Base *>BaseList;

	do{
		char choice;
		cout << "a) Create then add a base class pointer into the list" << endl;
		cin >> choice;
		cin.ignore();

		switch(choice)
		{
		case 'a':
			{
				//Create an object and return a pointer to that object
				//(I will be making many of these objects)
				Base::ReturnPtrToANewBaseClassObject();

				//push the returned pointer onto the std::list
				BaseList.push_back( ptr );

				cout << "Object now pushed onto list" << endl;
				break;
			}
		default:
			{
				cout << "You made an invalid choice" << endl;
				break;
			}
		}
	}
	while(true);

	system("pause");
}

```

**base.h :**
```

#ifndef BASE_H
#define BASE_H

#include <iostream>
#include <string>
using namespace std;

class Base
{
public:
	//constructor
	Base(string mystring);

	//Member Functions:
	Base * ReturnPtrToANewBaseClassObject();//Create an object and return a pointer to it

private:

protected:

	//Data Members common to all objects (abstract base class):
	string _mystring;

};
#endif

```

**base.cpp :**
```

#pragma once

#include <iostream>
#include <string>
#include "base.h"


//Base class contructor

Base::Base(string mystring)
{
	_mystring = mystring;
}

//Base class function
Base * ReturnPtrToANewBaseClassObject()
{
	//Build an object, and then return a pointer to that object
	//Wthin main() the pointer will be be pushed into the std:list

	string mystring;
	cout << "Value? " << endl;
	getline (cin, mystring);

	//Get a pointer to the new object
	Base *ptr = new Base(mystring);

	//return the pointer to main()
	return (ptr);
}

```

Here is what Visual Studio reports when I try to build:

> 
------ Build started: Project: myproject, Configuration: Debug Win32 ------
Compiling...
main.cpp
c:\main.cpp(22) : error C2352: 'Base::ReturnPtrToANewBaseClassObject' : illegal call of non-static member function
c:\base.h(15) : see declaration of 'Base::ReturnPtrToANewBaseClassObject'
c:\main.cpp(25) : error C2143: syntax error : missing ';' before '.'
c:\main.cpp(25) : error C2143: syntax error : missing ';' before '.'
Build log was saved at "file://c:\Debug\BuildLog.htm"
myproject - 3 error(s), 0 warning(s)
========== Build: 0 succeeded, 1 failed, 0 up-to-date, 0 skipped ==========


I have a very similar program working when I use a single main.cpp file, but I want to stop using single files, and this problem has really been holding me back.

Hope you guys and gals can help me with this.

Thanks very much!!!

---

### Post by Some Penguin on 2010-03-04
Looked at your code for a few seconds and two things that struck me:

(1) You have a comment that indicates that the next line returns blah blah blah, but you don't actually do anything with the return value.  This is probably wrong.

(2) You're calling 'push_back' on a type, not an object.  This, again, is probably wrong.

---

### Post by Swerve1000 on 2010-03-04
Hi Some Penguin,
thanks very much :)

Are you referring to this line? :

```

//push the returned pointer onto the std::list
BaseList.push_back( ptr );

```

ptr is a base class pointer and I'm trying to insert it into the std::list after it has been returned from the function ReturnPtrToANewBaseClassObject()

---

### Post by Some Penguin on 2010-03-04
I covered that.  You're NOT using the return value.  You're not even storing it anywhere.

---

### Post by DougB1958 on 2010-03-04
...but your error is exactly what the compiler says it is: Base::ReturnPtrToANewBaseClassObject is declared as an ordinary member function in the Base class, and so you need a Base object in which to call it. You never create such an object in main, instead you call Base::ReturnPtrToANewBaseClassObject as if it were a static method of the Base class (i.e., what the compiler is complaining about). Since it seems convoluted to have to create an instance of the Base class in order to call the function that makes instances of Base, the solution is probably to declare ReturnPtrToANewBaseClassObject to be a static function in class Base:

[PHP]
class Base {
    ...
    static Base * ReturnPtrToANewBaseClassObject();
    ...
};
[/PHP]

(But SomePenguin is right too, you aren't doing anything with the value ReturnPtrToANewBaseClassObject returns either)

---

### Post by WitchCraft on 2010-03-05
Member function pointers ?

See here:
[http://www.uluga.ubuntuforums.org/showthread.php?p=6321657](http://www.uluga.ubuntuforums.org/showthread.php?p=6321657)

---

### Post by dribeas on 2010-03-05
> **WitchCraft said:**
> Member function pointers ?

See here:
[http://www.uluga.ubuntuforums.org/showthread.php?p=6321657](http://www.uluga.ubuntuforums.org/showthread.php?p=6321657)

I think it is more of a member function that returns a pointer than a member function pointer. From the context of the conversation I am not too sure the OP is ready to go into member-function-pointers yet :)

---

