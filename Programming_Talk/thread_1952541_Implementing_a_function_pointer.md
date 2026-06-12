---
title: "Implementing a function pointer"
date: 2012-04-04
forum: Programming Talk
---

### Post by alfa_80 on 2012-04-04
I'm trying to implement a function pointer in C++ with object-oriented paradigm in mind. However, I didn't get it working. It complaints somehow when I call  *functionPointer.implement(10, 100, &FunctionPointer::sub)*.

```

#include <iostream>

class FunctionPointer
{
private:
  int a;
  int b;

public:
  FunctionPointer();
  ~FunctionPointer();

  double add(int a, int b){return a+b;}
  double sub(int a, int b){return a-b;}
  double mul(int a, int b){return a*b;}
  double div(int a, int b){return a/b;}
  void implement(int a, int b, double(*func)(int, int));

};

FunctionPointer::FunctionPointer()
{

}

FunctionPointer::~FunctionPointer()
{

}

void FunctionPointer::implement(int a, int b, double(*func)(int, int))
{
  double result;
  result = func(a, b);
  std::cout << "result = " << result << std::endl;
}


int main()
{
  std::cout << "hello" << std::endl;

  FunctionPointer functionPointer;
  functionPointer.implement(10, 100, &FunctionPointer::sub);

  return 0;

}

```Any idea how to fix it. Thanks in advance.

---

### Post by GeneralZod on 2012-04-04
Make add, sub, div, mul and implement static.

```

#include <iostream>

class FunctionPointer
{
private:
  int a;
  int b;

public:
  FunctionPointer();
  ~FunctionPointer();

  static double add(int a, int b){return a+b;}
  static double sub(int a, int b){return a-b;}
  static double mul(int a, int b){return a*b;}
  static double div(int a, int b){return a/b;}
  static void implement(int a, int b, double(*func)(int, int));

};

FunctionPointer::FunctionPointer()
{

}

FunctionPointer::~FunctionPointer()
{

}

void FunctionPointer::implement(int a, int b, double(*func)(int, int))
{
  double result;
  result = func(a, b);
  std::cout << "result = " << result << std::endl;
}


int main()
{
  std::cout << "hello" << std::endl;

  FunctionPointer::implement(10, 100, &FunctionPointer::sub);

  return 0;

}

```

---

### Post by alfa_80 on 2012-04-04
> **GeneralZod said:**
> Make add, sub, div and mul static.

Why those methods should be made/declared static? I didn't get it.

---

### Post by GeneralZod on 2012-04-04
> **alfa_80 said:**
> Why those methods should be made/declared static? I didn't get it.

Because otherwise they are *member functions* which are not interchangable with ordinary functions.

See e.g.

[http://www.parashift.com/c++-faq-lite/pointers-to-members.html#faq-33.6](http://www.parashift.com/c++-faq-lite/pointers-to-members.html#faq-33.6)

---

### Post by alfa_80 on 2012-04-04
> **GeneralZod said:**
> Because otherwise they are *member functions* which are not interchangable with ordinary functions.

See e.g.

[http://www.parashift.com/c++-faq-lite/pointers-to-members.html#faq-33.6](http://www.parashift.com/c++-faq-lite/pointers-to-members.html#faq-33.6)


Thanks a lot for the great explanation.

---

### Post by dwhitney67 on 2012-04-04
> **alfa_80 said:**
> 
Any idea how to fix it. Thanks in advance.

One option available to you is to employ the "boost" C++ library.  For example:
```

#include <boost/bind.hpp>
#include <string>
#include <sstream>
#include <iostream>

struct X
{
    int add(int a, int b) { return a + b; }
    int sub(int a, int b) { return a - b; }
    int mul(int a, int b) { return a * b; }
    int div(int a, int b) { return a / b; }
    int err(int a, int b) { throw int(-1); }
};


int main()
{
    // Gather input from the user (note, there is no error checking)
    //
    std::string input;
    char        op;
    int         num1, num2;

    std::cout << "Enter first number: ";
    std::getline(std::cin, input);
    std::istringstream iss(input);
    iss >> num1;

    std::cout << "Enter an operator (ie. +, -, *, or /): ";
    std::getline(std::cin, input);
    op = input[0];

    std::cout << "Enter second number: ";
    std::getline(std::cin, input);
    iss.clear();
    iss.str(input);
    iss >> num2;


    // Setup pointer to desired function based on what the user inputted.
    //
    int (X::*func)(int, int);

    switch (op)
    {
        case '+' : func = &X::add; break;
        case '-' : func = &X::sub; break;
        case '*' : func = &X::mul; break;
        case '/' : func = &X::div; break;
        default  : func = &X::err; break;
    }


    // Instantiate an object of type X
    //
    X x;


    // We bind function 'func' to be callable using a reference to
    // our object 'x' (thus obviating the need to make the class
    // functions static), and this function will accept two parameters,
    // those being _1 and _2.  We then call the function, passing num1
    // and num2, and then save our result.
    //
    int result = boost::bind(func, boost::ref(x), _1, _2)(num1, num2);

    std::cout << result << std::endl;
}

```

---

