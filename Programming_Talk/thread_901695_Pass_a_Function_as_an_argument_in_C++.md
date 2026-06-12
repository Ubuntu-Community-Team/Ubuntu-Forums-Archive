---
title: "Pass a Function as an argument in C++"
date: 2008-08-26
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-08-26
can you show me an example of it?

---

### Post by StOoZ on 2008-08-26
you can use a function pointer...

void func(int (*p)(int)) {}

this function takes an argument of a function that takes an int , and return an int...
for example:

int sxt(int k) {...}

func(sxt);

---

### Post by dwhitney67 on 2008-08-26
You can also try "functor" objects.

Example:
[PHP]#include <iostream>

class Echo
{
  public:
    int operator()(int value )
    {
      return value;
    }
};

class MultiplyByTwo
{
  public:
    int operator()(int value )
    {
      return value*2;
    }
};

template< typename F >
void function( F f, int value )
{
 std::cout << "value = " << f(5) << std::endl;
}

int main()
{
  Echo          echo;
  MultiplyByTwo mult;

  function( echo, 5 );
  function( mult, 5 );

  return 0;
}[/PHP]

---

### Post by dribeas on 2008-08-26
> **dwhitney67 said:**
> You can also try "functor" objects.


+1

Also consider using libraries: boost::function (functors), boost::bind (creating functors bound to existing functions/methods) to remove some of the hassle of creating the functors. I am really fond of boost::signals combined with boost::bind and boost::function :)

   David

---

