---
title: "[C++] Accessing Member Values from Static Member Function"
date: 2010-05-26
forum: Programming Talk
---

### Post by dodle on 2010-05-26
Is there a way to access the value of a member variable from within a static member function?
[php]class MyClass
  public:
    MyClass();
    ~MyClass();
    static void *Print();
  private:
    string hello;
};

MyClass::MyClass()
{
    hello = "Hello World";
}

...

void *MyClass::Print()
{
    cout << hello << endl; // Trying to access data stored in "hello" variable
}[/php]

The tutorials that I have read say that static functions can only access static members.  Here's one of the tutorials: [http://msdn.microsoft.com/en-us/library/yyh8hetw.aspx](http://msdn.microsoft.com/en-us/library/yyh8hetw.aspx)

So I would have to declare my member variable like this:
[php]class MyClass
  public:
    MyClass();
    ~MyClass();
    static void *Print();
  private:
    static string hello;
};

string MyClass::hello = "Hello World";[/php]

But I want to be able to change the value of "hello" from within the class.  I have tried the following two methods that don't work:
[php]MyClass::MyClass()
{
    string MyClass::hello = "Hello World";
}[/php]

[php]int SetString()
{
    string MyClass::hello = "Hello World";
}

MyClass::MyClass()
{
    SetString();
}[/php]

But both return this error:
```
error: invalid use of qualified-name ‘MyClass::hello’
```

---

### Post by MadCow108 on 2010-05-26
replace:
int SetString() {
string MyClass::hello = "Hello World";
}

with:
int SetString() {
hello = "...";
}

note that static means, all objects of MyClass will share the same hello variable.

---

### Post by dodle on 2010-05-26
I get this error:
```
In function &#8216;int SetString()&#8217;:
error: &#8216;hello&#8217; was not declared in this scope
```

[php]class MyClass
{
  public:
    MyClass();
    ~MyClass();
  private:
    static string hello;
};

int SetString()
{
    hello = "Hello World";
}

MyClass::MyClass()
{
    SetString();
    cout << hello << endl;
}[/php]

[quote=MadCow108]note that static means, all objects of MyClass will share the same hello variable.[/quote]

Okay, let me see if I understand:  Let's say I create two instances of "MyClass", called "test1" and "test2", and change the value of "hello" to "Goodbye World" from "test1".  When I access "hello" from "test2", it will still retain the value "Goodbye World"?

---

### Post by MadCow108 on 2010-05-26
> **dodle said:**
> I get this error:
```
In function &#8216;int SetString()&#8217;:
error: &#8216;hello&#8217; was not declared in this scope
```

setstring must be a member of MyClass, I overlooked that. It can also be static.
You can also set it in the constructor or any other member function directly.
You just had a syntax error. A static variable behaves just like a normal variable in the class (except that its shared).You do not need the same syntax you used to define it.


> 
Okay, let me see if I understand:  Let's say I create two instances of "MyClass", called "test1" and "test2", and change the value of "hello" to "Goodbye World" from "test1".  When I access "hello" from "test2", it will still retain the value "Goodbye World"?

yes, it will even remain so when you delete the objects test1 and test2 (unless the destructors explicitly change it again). hello only gets deleted when the program ends.
static member variables are kind of class scoped global variables.

---

### Post by dwhitney67 on 2010-05-26
> **dodle said:**
> Is there a way to access the value of a member variable from within a static member function?


The only way to access a non-static member data from within a class's static method is to have an instance of the class object where the member data is defined.

```

class Foo
{
   Foo(int v) : myValue(v) {}

   static void printData(Foo& f)
   {
      std::cout << f.myValue << std::endl;
   }

private:
   int myValue;
};

int main()
{
   Foo f(5);
   Foo::printData(f);
}

```
If you need to use static methods and member data in your class(es), make sure it is for a good reason.  Too many static declarations can be indicative of a poor design.

---

### Post by dodle on 2010-05-26
I must no be understanding MadCow, I still get errors:
[php]class MyClass
{
  public:
    MyClass();
    ~MyClass();
    void SetString();
  private:
    static string hello;
};

MyClass::MyClass()
{
    SetString();
    cout << hello << endl;
}

MyClass::~MyClass()
{
}

void MyClass::SetString()
{
    hello = "Hello World";
}[/php]

Error:
```
In function `MyClass::SetString()':
(.text+0x129): undefined reference to `MyClass::hello'
In function `MyClass::MyClass()':
(.text+0x143): undefined reference to `MyClass::hello'
In function `MyClass::MyClass()':
(.text+0x1af): undefined reference to `MyClass::hello'
collect2: ld returned 1 exit status
```

---

### Post by dwhitney67 on 2010-05-26
Somewhere in  your code, you must initialize the static data member.  Perhaps in your main module, or in MyClass.cpp, add the following _outside_ of the class declaration:
```

class MyClass
{
...
private:
   static std::string hello;
};

...

// initialize static data member(s)
//
std::string MyClass::hello;

```
Then when you call SetString(), the 'hello' variable will be set to "Hello World".

---

### Post by dodle on 2010-05-26
Thank you dhwhitney, thank you both.... for being patient with a newbie :)

[php]#include <iostream>
using namespace std;

class MyClass
{
  public:
    MyClass();
    ~MyClass();
    void SetString();
  private:
    static string hello;
};

string MyClass::hello("Hello World");

MyClass::MyClass()
{
    SetString();
    cout << hello << endl;
}

MyClass::~MyClass()
{
}

void MyClass::SetString()
{
    hello = "Hello World";
}

int main()
{
    MyClass test;
    return 0;
}[/php]

---

### Post by dribeas on 2010-05-29
Most answers jump into solutions, I believe that you better know the problem. 

The problem you are facing is that statics are part of the class, but non-static members belong to each instance of the class. 

```

MyClass myObject, another;
myObject.non_static_foo();
MyClass::static_bar();

```

When you call 'non_static_foo' in the example, you are calling it with a particular instance 'myObject', so it can access all of that instance state, and also all of the class' state. On the other hand, when you call 'static_bar' you are calling an operation on the class itself. The class can access it's own state (statics), but it does not have an instance from which to get the state. What 'hello' attribute would you like printed? The one in 'myObject' or the one in 'another'?

To make things a little harder to read, the language allows you to write 'myObject.static_bar()', but that is still calling a method of the class.

---

