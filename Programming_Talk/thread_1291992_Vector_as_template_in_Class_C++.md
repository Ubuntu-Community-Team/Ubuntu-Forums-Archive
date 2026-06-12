---
title: "Vector as template in Class C++"
date: 2009-10-15
forum: Programming Talk
---

### Post by adalmiina on 2009-10-15
I have to do library program by using **vector**. I haven't never use vector and I want to get help. I have to use class library, libraryitem, book and cd and also have borrow class. Methdos could be that borrow can borrow book, reserve book and find book and so on.
It's possible to use **vector** such **as template** ?
Have I create **vector to class** or how...? Could **vector **be so **untyped** that it takes all kind of things suchs as int variables, string and float types.
 
 Could **vector** be in class or should it be** out of class** ?
Please.. .help me.. I need  more knowledge.

---

### Post by dwhitney67 on 2009-10-15
This seems like a homework (class assignment) issue.

You should be able to read up on vector at this location:
[http://www.cplusplus.com/reference/stl/vector/](http://www.cplusplus.com/reference/stl/vector/)

Consider bookmarking the main page that provides an index to all STL containers:
[http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)

---

### Post by adalmiina on 2009-10-15
Thanks about links.
 
It's not always so easy for beginner to study yourself and understand all new things.
But I'm happy that you answer!!
 
How I get things to vector, what user has written to console? 
I mean cin>>number; 
How I put these to vector? 
 
[SIZE=2]vector.push_back(Base(16)); //Base is class so I put number 16
But how from instream?
 
It's possible to create template from vector, which could handle different kind of data?
[http://www.parashift.com/c++-faq-lite/templates.html#faq-35.18](http://www.parashift.com/c++-faq-lite/templates.html#faq-35.18)
[/SIZE]

---

### Post by MadCow108 on 2009-10-15
a Standard **Template** Library (STL) vector is already a template, like most other stuff of the STL.
and you can also use it in other templates:
```

template<typename T>
class stuff {
	private:
	vector<T> data;
};

```
here's a good tutorial for vectors:
[http://www.codeguru.com/cpp/cpp/cpp_mfc/stl/article.php/c4027/](http://www.codeguru.com/cpp/cpp/cpp_mfc/stl/article.php/c4027/)

adding a int to a vector:
```

vector<int> numbers;
int num = 14;
numbers.push_back(16);
numbers.push_back(num);

```

---

### Post by adalmiina on 2009-10-15
Thanks lots!!
```
 
#include <vector>
#include <iostream>
#include <string>
#include "person.hpp"
 
std::vector <person> My;
//person is class
 
int main(){
double age;
std::string name;
 
for(int a = 0; a < 3; a++){
std::[cout]("http://www.opengroup.org/onlinepubs/009695399/functions/cout.html") << "Name is" << std::endl;
std::cin >> name;
 
std::[cout]("http://www.opengroup.org/onlinepubs/009695399/functions/cout.html") << "Give age" << std::endl;
std::cin >> age;
 
My.push_back(Person(name, age));
}
 
return EXIT_SUCCESS;
}
 

``` 
How I could get name and age from vector?
How I could find certain name from vector and edit ?
 
 
If I have many classess, should I declarate the vector to base class?
 
How uses the class whic doesn't inherits base class? Like person is usual class but have composition relation.
 
Could the base class be abstract if its vectors type?
If I get data from vektor, how I check the type in code?
 
Sorry, I have many questions... 
Are vectors easy for you??

---

### Post by dwhitney67 on 2009-10-15
Consider the following:
```

#include <vector>
#include <string>
#include <stdexcept>
#include <iostream>
#include <iterator>


class Person
{
public:
   Person(const std::string& name, const unsigned int age)
      : myName(name),
        myAge(age)
   {
   }

   std::string  getName() const { return myName; }
   unsigned int getAge()  const { return myAge; }

   friend std::ostream& operator<<(std::ostream& os, const Person& p)
   {
      os << "Name: " << p.myName << ", Age: " << p.myAge;
      return os;
   }

private:
   std::string  myName;
   unsigned int myAge;
};

template <typename T>
class GenericContainer
{
public:
   GenericContainer()
   {
   }

   void addItem(const T& item)
   {
      myStorage.push_back(item);
   }

   T getItem(size_t index) const
   {
      if (index >= myStorage.size())
      {
         throw std::range_error("Index is out of range!");
      }

      return myStorage[index];
   }

   friend std::ostream& operator<<(std::ostream& os, const GenericContainer<T>& gc)
   {
      std::copy(gc.myStorage.begin(), gc.myStorage.end(), std::ostream_iterator<T>(os, "\n"));
      return os;
   }

private:
   std::vector<T> myStorage;
};

int main()
{
   GenericContainer<Person> gc;

   gc.addItem(Person("Huey",  10));
   gc.addItem(Person("Louie", 20));
   gc.addItem(Person("Duey",  30));

   std::cout << gc << std::endl;

   try {
      std::cout << gc.getItem(0).getName() << " ..... "
                << gc.getItem(0).getAge()  << std::endl;

      // ...

      // this will throw an exception...
      //
      std::cout << gc.getItem(3).getName() << " ..... "
                << gc.getItem(3).getAge()  << std::endl;
   }
   catch (std::exception& e) {
      std::cerr << "Exception Caught: " << e.what() << std::endl;
      return 1;
   }
}

```

---

### Post by MadCow108 on 2009-10-15
to find something in a vector use the find and find_if algorithms:
[http://www.cplusplus.com/reference/algorithm/find_if/](http://www.cplusplus.com/reference/algorithm/find_if/)
[http://www.cplusplus.com/reference/algorithm/find/](http://www.cplusplus.com/reference/algorithm/find/)

and have a look at the STL map which could be useful in your project.

also you should not derive from STL containers. You can, but it is error-prone if done wrong.
STL is all generic so there is usually no need to do that anyway.

---

### Post by adalmiina on 2009-10-16
Wow..... you are guru.. I'm sunny .. Thanks lotss!!
 
I learn more about code and links are good area...
But I have to ask yet, Have I know right way this code ...because I want really understand what my code do. I add some comments and could you write me  what they really mean ?
 
```

class Person
{
public:
//constructor, 2 get parameters
   Person(const std::string& name, const unsigned int age)
      : myName(name),
        myAge(age)
   {
    }

// std::ostream& os,  is os  reference to ostream that I could cout something ?
// is Person& p  usual reference to person class  ?

   friend std::ostream& operator<<(std::ostream& os, const Person& p)
   {
      os << "Name: " << p.myName << ", Age: " << p.myAge;
      return os;
   }

};

// You create generic container

template <typename T>
class GenericContainer
{
public:
   GenericContainer()
   {
   }

   void addItem(const T& item) //const T& item does it mean that I can put all kind of data. Its generic
   {
      myStorage.push_back(item);
   }

   T getItem(size_t index) const
   {
      if (index >= myStorage.size())
      {
         throw std::range_error("Index is out of range!");
      }

      return myStorage[index];
   }

//ostream& os, const GenericContainer<T>& gc  ??

   friend std::ostream& operator<<(std::ostream& os, const GenericContainer<T>& gc)
   {
      std::copy(gc.myStorage.begin(), gc.myStorage.end(), std::ostream_iterator<T>(os, "\n"));
      return os;
   }


```
 
 
Could you tell if  my comments in code are true or could say better.
For example :
ostream& operator<<(std::ostream& os, const Person& p)
ostream& os, const GenericContainer<T>& gc
I 'm not sure could I think that & is reference ...?

---

### Post by dwhitney67 on 2009-10-16
The '&' symbols in the code do indeed refer to a reference.

The friend methods are not "part" of the class, and thus require that a reference to a class object be given as a parameter.  The friend-ship relationship allows for the method to access all member data and functions of the class object.

Please bear in mind that the code I provided was merely an outlandish attempt to show you how vector is used; the GenericContainer class is superfluous.  You can easily use vector as:
```

class Person
{
};

class Animal
{
};

class Shape
{
};

std::vector<Person> personVec;
std::vector<Animal> animalVec;
std::vector<Shape>  shapeVec;

// etc

```

As it was pointed out in an earlier post, most containers in the STL are designed as template classes.  Thus you can use them to store any object you wish.

Note:  Some containers requires that your class object have declarations/implementation for copy-constructor and assignment-operator (ie operator=()).

---

### Post by adalmiina on 2009-10-16
These things are not easy for me, I'm beginner, but I want to learn..
 
```

std::vector <person> My;
//person is class
 
int main(){
double age;
std::string name;
 
for(int a = 0; a < 3; a++){
std_::_[[COLOR=#444444]cout[/COLOR]]("http://www.opengroup.org/onlinepubs/009695399/functions/cout.html")_ << "Name is" << std::endl;_
_std::cin >> name;_
 
_std::_[[COLOR=#444444]cout[/COLOR]]("http://www.opengroup.org/onlinepubs/009695399/functions/cout.html") << "Give age" << std::endl;
std::cin >> age;
 
My.push_back(Person(name, age));
}

```
 
If this add name and age to Person class : 
```
My.push_back(Person(name, age));
```
 
I try the same by you fine code... it doesn't success..
 
```


int
[LEFT]main()
[LEFT]{
GenericContainer <Person> gc;[/LEFT]
 
[LEFT]cout <<"Give name:";
cin>>name;
cout <<"Give age:";
cin>>age;[/LEFT]
 
[LEFT]gc.addItem(Person(name, age));[/LEFT]
gc.addItem(Person("Hue", 10));

```
I have used myname and name ... but problem is other..
[SIZE=2]error: `name' undeclared (first use this function)[/SIZE]
[SIZE=2]error: `age' undeclared (first use this function)[/SIZE]
[SIZE=2]If I add Person or gc.name doesn't work..[/SIZE]
 
[SIZE=2]I want to use you code if I understand those things.. [/SIZE]
 
 
[/LEFT]

---

### Post by MadCow108 on 2009-10-16
you forgot this:
double age;
std::string name;

---

### Post by adalmiina on 2009-10-16
I have to ask again.
```

//----main.cpp----*/
 
#include<vector>
#include<string>
#include<stdexcept>
#include<iostream>
#include<iterator>
#include"Person.h"
 
[LEFT]using namespace std;[/LEFT]
 void SetPerson(string name, unsignedint age);
 
int main()
{
   void SetPerson(string name, unsignedint age);
[LEFT]   return 0;
}[/LEFT]
 
[LEFT]/*-------Person.h -------*/[/LEFT]
class Person
{
   public:
[LEFT]        Person(const string& name, const unsignedint age);
        void SetPerson(string name, unsignedint age);[/LEFT]
/*-------Person.cpp -------*/
 
[LEFT]void Person::SetPerson(string name, unsignedint age)[/LEFT]
{
   GenericContainer <Person> gc;

[LEFT]   cout <<"Give name:";
[LEFT]   cin>>name;
   cout <<"Give age:";
   cin>>age; [/LEFT]
[/LEFT]

 
[LEFT]   gc.addItem(Person(name, age));[/LEFT]
    cout << gc.getItem(0).getName() << " ..... "<< gc.getItem(0).getAge() << std::endl;

```
 
[LEFT][SIZE=2][SIZE=2][SIZE=2]It doesn't give error but do nothing.[/SIZE][/SIZE][/SIZE][SIZE=2]
[SIZE=2][SIZE=2]How I could set name and age to Person if I have to use Person.h and Person.cpp files and also main.cpp ?[/SIZE][/SIZE][/LEFT]
 
[/SIZE]

---

### Post by dwhitney67 on 2009-10-16
You have got to get yourself a proper tutorial for learning the C++ language.  You should not rely on a forum for this.

As for your code, there are syntax errors in it (or you have posted incomplete code).  Please correct these first... then reply again if you still have errors.

Some hints...

1.  You need to declare all variables (MadCow indicated this earlier).

2.  You cannot call a non-static class method unless you instantiate an object through which to call it.  You have an error in the main() function with respect to this.

3.  At this point in your C++ development studies, I would refrain from creating multiple files for your code.  Just use one file for everything.  Once you have mastered this, then move onto other experiments.

P.S.  The basic ordering for constructs in your file should be...

a.  Include header file(s)
b.  Declare class(es)
c.  Implement class method(s)
d.  Declare and implement main() function.

---

