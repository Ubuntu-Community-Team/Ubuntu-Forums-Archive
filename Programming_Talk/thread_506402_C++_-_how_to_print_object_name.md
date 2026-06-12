---
title: "C++ - how to print object name?"
date: 2007-07-21
forum: Programming Talk
---

### Post by Torajima on 2007-07-21
Is this possible in c++?

Say, i've got class Person, and I just created object Joe.

Right now, I'm doing something like:

Person Joe ("Joe");

And setting "Joe" to a variable such as 'name'. But this seems pretty dumb... the objects name is already Joe, isn't there a way to print it directly?

Printing the 'this' pointer doesn't work:

cout << this; // prints the memory address
cout << *this; // prints an empty string

---

### Post by Modred on 2007-07-21
> And setting "Joe" to a variable such as 'name'. But this seems pretty dumb... the objects name is already Joe, isn't there a way to print it directly?

You could overload the << operator so that passing the object Joe to an output stream will return the string that's inside Joe.name.  It doesn't get the exact functionality you're requesting, but this way it will still print the appropriate name no matter what you call your variable.

For example, consider if you have 5 Person objects in an array.  I doubt you'd want them to output "person[0]", "person[1]", and so on, if that were possible.  But if you overload <<, then you could do something like:

```
for( int i = 0; i < 5 ; i++ ) {
    cout << person[ i ] << endl;
}
```

And because you overloaded << it will output the name you passed in to the constructor.  This is a much more flexible use than trying to pull the name from your object.  So there may be a little redundancy between an object named Joe with an instance variable holding "Joe", but chances are you won't be naming each Person object after the person it contains if you start managing more than one or two of them.

---

### Post by olejorgen on 2007-07-21
C++ does not normally store any runtime typeinfo. But if you'll set a certain compile switch you could use [http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.xlcpp8a.doc/language/ref/the_typeid_operator.htm](http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.xlcpp8a.doc/language/ref/the_typeid_operator.htm)

EDIT: SOrry, I thought you needed the class name.

---

### Post by Wybiral on 2007-07-21
If you just mean using the label in a string, you can make a macro for it...

```

#include <iostream>

#define GET_NAME(n) #n

using namespace std;

int main()
{
    int x = 7;
    cout << x << endl;
    cout << GET_NAME(x) << endl;
    return 0;
}

```

I do this occasionally for debugging info.

---

### Post by Jucato on 2007-07-22
My reply is not really technical, but I think it's worth considering...

> **Torajima said:**
> And setting "Joe" to a variable such as 'name'. But this seems pretty dumb... the objects name is already Joe, isn't there a way to print it directly?

I don't think this is dumb. In fact, I think that it's natural that an object Joe has an *name* attribute, which is equivalent to "Joe". I guess it depends on what other attributes the Person class has. For example, consider:

```

class Person
{
      string name;
      int age;
      string address;
      int birthdate;
};

```

Hope you get my drift. (Hope I'm also correct in theory :P)

---

### Post by Torajima on 2007-07-22
> **Modred said:**
> For example, consider if you have 5 Person objects in an array.  I doubt you'd want them to output "person[0]", "person[1]", and so on, if that were possible.

What is the correct method for declaring/initialzing an array of Person(s)? I've been trying to figure out how to create a random number of objects.

And how do you call their member functions? Is it something like: person[3].setName("Joe")?

---

### Post by Torajima on 2007-07-22
> **Wybiral said:**
> If you just mean using the label in a string, you can make a macro for it...


Thanks, I'll try your suggestion.

---

### Post by aks44 on 2007-07-22
> **Torajima said:**
> What is the correct method for declaring/initialzing an array of Person(s)? I've been trying to figure out how to create a random number of objects.

And how do you call their member functions? Is it something like: person[3].setName("Joe")?

Use a std::vector. Something like :

```
#include <vector>
#include <iostream>

class Person
{
public:
  Person(const std::string& name)
    : m_name(name)
  {
  };
  const std::string& getName() const { return m_name; };
private:
  std::string m_name;
};

int main()
{
  std::vector<Person> persons;

  while (true)
  {
    std::cout << "Enter a person's name: ";
    std::string name;
    std::cin >> name;

    if (name.empty())
      break;

    persons.push_back(Person(name));
  };

  if (persons.empty())
    std::cout << "You didn't enter any name." << std::endl;
  else
  {
    std::cout << "You entered the following names:" << std::endl;

    // Preferred syntax (iterators)
    for (std::vector<Person>::const_iterator i = persons.begin(); i != persons.end(); ++i)
      std::cout << i->getName() << std::endl;

    // Alternate syntax (random access using subscript operator)
    for (size_t i = 0; i < persons.size(); ++i)
      std::cout << persons[i].getName() << std::endl;
  };
}
```

Hope this helps.

---

### Post by hod139 on 2007-07-22
> **Wybiral said:**
> 
```

#define GET_NAME(n) #n

```
This is a neat trick.  Is there a C++ way to do this without having to define a global macro?

---

### Post by shan23 on 2009-01-09
> **olejorgen said:**
> C++ does not normally store any runtime typeinfo. But if you'll set a certain compile switch you could use [http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.xlcpp8a.doc/language/ref/the_typeid_operator.htm](http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.xlcpp8a.doc/language/ref/the_typeid_operator.htm)

EDIT: SOrry, I thought you needed the class name.

I need exactly what u are talking about i.e. how to print the name of a class from within one of its methods....that way, i can use the same command each time no matter what class i'm calling it from....

Unfortunately, the link u have given is broken...could u pls update it ?

---

### Post by Xakiru on 2010-02-07
if you want to print the class name to an object you have to use , we assume that you have a class names point :

point a;
cout << typeid(a).name();


that won't work if you don't include typeinfo.h in some compilators ...
this is a late reply but i beleave that can help other people who are seeking for this information ;)

---

### Post by jsjiang on 2011-07-04
> **shan23 said:**
> I need exactly what u are talking about i.e. how to print the name of a class from within one of its methods....that way, i can use the same command each time no matter what class i'm calling it from....

Unfortunately, the link u have given is broken...could u pls update it ?

It is possible to get the class name from within a class. Try this.

#include <typeinfo>
class {
    string get_class_name() {return typeid(*this).name();}
}

---

### Post by cgroza on 2011-07-04
Uhmm, what's wrong in having a getName method that returns the name attribute?
So you could do:

```

Person person("Joe");
cout << person.getName();
```And the output could be:
```
Joe
```I think that this is the OP really wants.

---

### Post by cgroza on 2011-07-04
> **shan23 said:**
> I need exactly what u are talking about i.e. how to print the name of a class from within one of its methods....that way, i can use the same command each time no matter what class i'm calling it from....

Unfortunately, the link u have given is broken...could u pls update it ?
Maybe polymorphism is what you need.

---

### Post by cirrronimbo on 2012-01-27
I too am wondering if we could really get our hands on the object's ( NOT THE CLASS's which could definitely be done by aforementioned approach of 'typeid(*this).name()') name at runtime (but of-course without assigning it to a separate 'string' or 'char*' ).
Can we ?

---

