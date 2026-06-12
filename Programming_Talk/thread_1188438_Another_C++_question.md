---
title: "Another C++ question"
date: 2009-06-15
forum: Programming Talk
---

### Post by Mirge on 2009-06-15
Just as an example, I created:

/home/mike/projects/test/

This directory includes:

main.cpp
animal.h
animal.cpp

animal.h contains the class declaration... animal.cpp contains the class definition I guess you'd say (it defines the class methods). main.cpp makes use of the class.

How would I compile that? I'm not used to separating code into multiple files. Normally I'd just g++ -o main main.cpp.... or as Geany is configured: g++ -Wall -g -o "main" "main.cpp"

---

### Post by Cyanidepoison on 2009-06-15
```

g++ -c animal.cpp
g++ -o main main.cpp animal.o

```

---

### Post by Mirge on 2009-06-15
Thanks! Ran into a compiling error though..

```

mike@mike-kubuntu:~/projects/test$ g++ -c animal.cpp
animal.cpp: In member function ‘void Animal::SetAge(int)’:
animal.cpp:16: error: request for member ‘age’ in ‘this’, which is of non-class type ‘Animal* const’
animal.cpp: In member function ‘int Animal::GetAge()’:
animal.cpp:21: error: request for member ‘age’ in ‘this’, which is of non-class type ‘Animal* const’
animal.cpp: In member function ‘void Animal::SetWeight(double)’:
animal.cpp:26: error: request for member ‘weight’ in ‘this’, which is of non-class type ‘Animal* const’
animal.cpp: At global scope:
animal.cpp:29: error: prototype for ‘double Animal::GetWeight()’ does not match any in class ‘Animal’
animal.h:14: error: candidate is: int Animal::GetWeight()

```

animal.cpp:
```

#include <iostream>
#include "animal.h"

Animal::Animal()
{
    // do nothing for now
}

Animal::~Animal()
{
    // do nothing for now
}

void Animal::SetAge(int age)
{
    this.age = age;
}

int Animal::GetAge()
{
    return this.age;
}

void Animal::SetWeight(double weight)
{
    this.weight = weight;
}

double Animal::GetWeight()
{
    return this.weight;
}

```

---

### Post by Mirge on 2009-06-15
Oops, I didn't notice until I pasted it here...

replaced this.FOO
with this->FOO

---

### Post by Cyanidepoison on 2009-06-15
That's how I do it in C,  I just guessed it would be the same in C++.

I guess I was wrong.

---

### Post by SledgeHammer_999 on 2009-06-15
or you could use 
[quote] g++ main.cpp animal.cpp -o main[/code]

On your problem. "this" is a **pointer** to the current instance of your class. A pointer to a class is **dereferenced** with **->** and not with a .(dot).
If you don't know what I am talking about read [this](http://www.cplusplus.com/doc/tutorial/pointers/)

---

### Post by Cyanidepoison on 2009-06-15
The only downside to one-lining it is that you have to compile EVERY source file whether or not it changed.  If you do it by compiling each source file once and then just combining all the resulting object files, you only need to recompile the separate source files when they change.

---

### Post by Mirge on 2009-06-15
> **Cyanidepoison said:**
> That's how I do it in C,  I just guessed it would be the same in C++.

I guess I was wrong.

No no, you were correct. The errors I had posted were syntactical errors, which I resolved using -> instead of . (dot).

---

### Post by Can+~ on 2009-06-15
> **Cyanidepoison said:**
> The only downside to one-lining it is that you have to compile EVERY source file whether or not it changed.  If you do it by compiling each source file once and then just combining all the resulting object files, you only need to recompile the separate source files when they change.

Or you could write a makefile.

---

### Post by Cyanidepoison on 2009-06-15
I thought that was obvious for anything more than a couple of source files.

---

### Post by SledgeHammer_999 on 2009-06-15
> **Mirge said:**
> No no, you were correct. The errors I had posted were syntactical errors, which I resolved using -> instead of . (dot).

Although in many cases you don't need to do a this->
Example:
You can easily change this:
[php]
int Animal::GetAge()
{
    return this->age;
}
[/php]

to this:
[php]
int Animal::GetAge()
{
    return age;
}
[/php]

---

### Post by Mirge on 2009-06-15
Thanks. Is there any advantage to using either method? Or just preference?

---

### Post by SledgeHammer_999 on 2009-06-16
As far as I know there isn't any advantage in the compiled code. You just write less code :p

---

### Post by Habbit on 2009-06-16
I've known people who put "this->" (actually "this.", as he was a Java programmer) in every single member variable/method reference. While useful to disambiguate member and local variables (for example in property getters/setters), there is usually no point in prepending "this->", other than to explicitly signify that you are accessing an instance member. The compiled code does not change in the slightest, as the pointer-dereference implied by this-> is automatically added even if you don't write it.

---

### Post by CanadianBac0n77 on 2009-06-16
Do you or Have you ever thought about using [Netbeans]("http://www.netbeans.org/")?

---

### Post by Mirge on 2009-06-16
Using Code::Blocks and Geany atm. Geany is my favorite editor for all things non-C/C++. Is NetBeans better than Code::Blocks?

---

### Post by Mirge on 2009-06-16
Tried NetBeans, uninstalling it now... slow, bulky, don't like the look of the IDE, and "New File" -> "Main C++ File" included stdlib.h by default? Lotta small things like that irritated me enough to uninstall.. sticking with Code::Blocks for now.

---

### Post by jacensolo on 2009-06-17
> **Habbit said:**
> I've known people who put "this->" (actually "this.", as he was a Java programmer) in every single member variable/method reference. While useful to disambiguate member and local variables (for example in property getters/setters), there is usually no point in prepending "this->", other than to explicitly signify that you are accessing an instance member. The compiled code does not change in the slightest, as the pointer-dereference implied by this-> is automatically added even if you don't write it.

I find that I do this also. I think I do it partly to distinguish he differences between members and locals, but I think it might have carried over from python's "self" even though I started learning c++ before Python.

---

