---
title: "Another c++ programming problem"
date: 2007-07-23
forum: Programming Talk
---

### Post by babyboss on 2007-07-23
Hello, this is another c++ program that comes from the book, and I still got some compiling error

There are three files in this program: personType.h, personType.cpp, testPerson.cpp

I got the following error when I compiled it:
personType.h:8: error: ‘string’ has not been declared
personType.h:8: error: ‘string’ has not been declared
personType.h:10: error: ‘string’ has not been declared
personType.h:10: error: ‘string’ has not been declared
personType.h:12: error: expected `)' before ‘first’
personType.h:15: error: ‘string’ does not name a type
personType.h:16: error: ‘string’ does not name a type
testPerson.cpp: In function ‘int main()’:
testPerson.cpp:11: error: no matching function for call to ‘personType::personType(std::string&, std::string&)’
personType.h:4: note: candidates are: personType::personType()
personType.h:4: note:                 personType::personType(const personType&)

personType.h:
#include<string>

class personType
{
	public:
		void print() const;

		void setName(string first, string last);

		void getName(string& first, string& last);

		personType(string first="", string last="");

	private:
		string firstName;
		string lastName;
};


personTypeImp.cpp:
#include<iostream>
#include<string>
#include "personType.h"

using namespace std;

void personType::print() const
{
	cout<<firstName<<""<<lastName;
}

void personType::setName(string first, string last)
{
	firstName=first;
	lastName=last;
}

void personType::getName(string& first, string& last)
{
	first = firstName;
	last = lastName;
}

personType::personType(string first, string last)
{
	firstName = first;
	lastName = last;
}


testPerson.cpp:

#include<iostream>
#include<string>
#include "personType.h"


using namespace std;

int main() {
	string first = "kkkk";
	string last = "pppp";
	personType myself(first, last);
	myself.print();
}

---

### Post by LaRoza on 2007-07-23
Perhaps you should resolve your first program you posted. And use the code tags!

(The same error is made in your first post)

---

### Post by rahul.gupta on 2007-07-23
perhaps adding the using namespace statement in the .h file will help
alternatively, you could prepend "std::" to string in the header file

---

### Post by aks44 on 2007-07-23
> **rahul.gupta said:**
> perhaps adding the using namespace statement in the .h file will help
alternatively, you could prepend "std::" to string in the header file

Never, ever **use namespace std;** in a header file!
This *will* sonner or later cause name conflicts.

I'm not an advocate of putting it in a cpp file either as it clutters the global namespace, but at least it's kinda safe to do so.

---

### Post by babyboss on 2007-07-23
personType.h
```

#include<string>
#include<iostream>

class personType
{
	public:
		void print() const;

		void setName(string first, string last);

		void getName(string& first, string& last);

		personType(string first="", string last="");

	private:
		string firstName;
		string lastName;
};

```

personTypeImp.cpp
```

#include<iostream>
#include<string>
#include "personType.h"

using namespace std;

void personType::print() const
{
	cout<<firstName<<""<<lastName;
}

void personType::setName(string first, string last)
{
	firstName=first;
	lastName=last;
}

void personType::getName(string& first, string& last)
{
	first = firstName;
	last = lastName;
}

personType::personType(string first, string last)
{
	firstName = first;
	lastName = last;
}

```

testPerson.cpp
```

#include<iostream>
#include<string>
#include "personType.h"


using namespace std;

int main() {
	
	string first = "kkkk";
	string last = "pppp";
	personType myself(first, last);
	myself.print();
	myself.setName("BBB", "ZZZ");
	myself.print();
}

```

---

### Post by babyboss on 2007-07-23
for my previous c++ programming problem, i resolved by using the following command to compile:

g++ clockTypeImp.cpp testClock.cpp -o testClock

for this one, when i tried to use the same command to compile, I still have some compile error:

personType.h:9: error: ‘string’ has not been declared
personType.h:9: error: ‘string’ has not been declared
personType.h:11: error: ‘string’ has not been declared
personType.h:11: error: ‘string’ has not been declared
personType.h:16: error: ‘string’ does not name a type
personType.h:17: error: ‘string’ does not name a type
testPerson.cpp: In function ‘int main()’:
testPerson.cpp:13: error: no matching function for call to ‘personType::setName(std::string&, std::string&)’
personType.h:9: note: candidates are: void personType::setName(int, int)
personType.h:9: error: ‘string’ has not been declared
personType.h:9: error: ‘string’ has not been declared
personType.h:11: error: ‘string’ has not been declared
personType.h:11: error: ‘string’ has not been declared
personType.h:16: error: ‘string’ does not name a type
personType.h:17: error: ‘string’ does not name a type
personTypeImp.cpp: In member function ‘void personType::print() const’:
personTypeImp.cpp:9: error: ‘firstName’ was not declared in this scope
personTypeImp.cpp:9: error: ‘lastName’ was not declared in this scope
personTypeImp.cpp: At global scope:
personTypeImp.cpp:12: error: prototype for ‘void personType::setName(std::string, std::string)’ does not match any in class ‘personType’
personType.h:9: error: candidate is: void personType::setName(int, int)
personTypeImp.cpp: In member function ‘void personType::setName(std::string, std::string)’:
personTypeImp.cpp:14: error: ‘firstName’ was not declared in this scope
personTypeImp.cpp:15: error: ‘lastName’ was not declared in this scope
personTypeImp.cpp: At global scope:
personTypeImp.cpp:18: error: prototype for ‘void personType::getName(std::string&, std::string&)’ does not match any in class ‘personType’
personType.h:11: error: candidate is: void personType::getName(int&, int&)
personTypeImp.cpp: In member function ‘void personType::getName(std::string&, std::string&)’:
personTypeImp.cpp:20: error: ‘firstName’ was not declared in this scope
personTypeImp.cpp:21: error: ‘lastName’ was not declared in this scope

---

### Post by babyboss on 2007-07-23
I don't really understand why that the compiler keeps telling me that string is not declare when I already include string library.

---

### Post by babyboss on 2007-07-23
Also, I already declare firstName and lastName as private in my header file, why does the compiler tell me that they are not declare either?

---

### Post by hod139 on 2007-07-23
In your header file you need to prefix the type string with std:: since the name string is protected in the std namespace.  Replace all occurrences of string with std::string.

---

### Post by babyboss on 2007-07-23
Great! it works perfectly now. thanks a lot!

---

