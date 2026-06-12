---
title: "c++ initializing std library class members"
date: 2011-05-24
forum: Programming Talk
---

### Post by akvino on 2011-05-24
I have a situation where I have to make sure to reset std library members in a class. I tried to search C++ standard about std::libarary initialization, yet I failed to find what I was looking for.

1) If you define std::string as your class member in the Header file, do you initialize it? Constructor will be called when you call the member - but does the standard require intialization in a constructor?

Sampl Header File:
[PHP]
SomeFile.h
#include <iostream>
#include <string>


class Custom
{
public:
Custom();
~Custom();
std::string m_string;

};


SomeFile.cpp
Custom::Custom()
{
   m_string.clear(); //clearing the string - calling string constructor

}

OR

Custom::SomeMethod()
{
  m_string.append("test");
}

[/PHP]

---

### Post by PaulM1985 on 2011-05-24
If you don't do anything in your constructor, it will call the default constructor of std::string, which will initialise your variable to an empty string.  See here for constructors for std::string:  [http://www.cplusplus.com/reference/string/string/string/](http://www.cplusplus.com/reference/string/string/string/)

Paul

---

### Post by Simian Man on 2011-05-24
If you don't call any constructor yourself, the default one will be called.  In the case of std::string, this will just set the string to "".  If you *do* want to call a constructor yourself, just use an initializer list in youir constructor:

```

class Custom {
  public:
    Custom( ) : a("Hello"), c("HelloThere", 5), b(10, 'X') {
      /* other stuff */
    }

  private:
    std::string a, b, c;
};

```

---

### Post by dwhitney67 on 2011-05-24
> **akvino said:**
> 
```

Custom::Custom()
{
   m_string.clear();
}

```

By the time the string is cleared above, it has *already* been constructed.  See Simian Man's post to learn how to construct the member data.

---

### Post by akvino on 2011-05-25
> **dwhitney67 said:**
> By the time the string is cleared above, it has *already* been constructed.  See Simian Man's post to learn how to construct the member data.

Got it. 
The question was intialization related, but it has been answered.

---

### Post by Blackbug on 2011-05-26
> If you define std::string as your class member in the Header file, do you initialize it?
 
you never explicitly initialize anythin within header file.
The initialization will take place whenever the constructor of your class will be called.
and all member variables should be initialized over there, even those member variables which you don't want to initialize.
Its to avoid any undefined behavior at runtime..and I hope everyone knows how worse is undefiend behavior...
 
for example:
 
 
```

// header file
 
class MyClass
{
public:
 MyClass( int id, int salary, m_department );
private:
  int m_id;
  int m_salary;
  int m_sum;
  string m_department;
  string m_cid; // say we are concatenating character in front of integer m_id according to department 'C' for computer science and all.
};

```
 
 
```

// cpp file
 
MyClass::MyClass( int id, int salary, string department )
: m_id( id ),
  m_salary(salary),
  m_sum(0),
  m_department( department ),
  m_cid() // default constructor will be invoked
{
}

```

---

