---
title: "C++ template argument using user defined class"
date: 2010-12-30
forum: Programming Talk
---

### Post by nitro_n2o on 2010-12-30
Hello all, 

I'm wondering is it possible to create a class and use it as a template argument. For example 


class Hello {
 public: 
   void sayHello() { printf("hello\n"); }
};


template <class T, Hello const &hello> 
class Monkey {
public: 
   T data; 
   void go() { hello.sayHello(); }
};

int main()
{
  const Hello hello; 
  Monkey<double, hello> monkey; 
  monkey.go(); 

  return 0;
}


is this something doable in C++?

Thanks a lot

---

### Post by MadCow108 on 2010-12-30
yes you can do this
it is called policy based design and is sometimes a very elegant solution for certain problems.

your Monkey class must either derive from the policy Hello or have it as a data member.

here is a similar example to your code (but with correct syntax ;) ):
[http://en.wikipedia.org/wiki/Policy-based_design#Simple_example](http://en.wikipedia.org/wiki/Policy-based_design#Simple_example)

for more elaborate examples see this book:
[http://erdani.com/book/main.html](http://erdani.com/book/main.html)

---

### Post by worksofcraft on 2010-12-30
> **MadCow108 said:**
> yes you can do this
it is called policy based design and is sometimes a very elegant solution for certain problems.

your Monkey class must either derive from the policy Hello or have it as a data member.

here is a similar example to your code (but with correct syntax ;) ):
[http://en.wikipedia.org/wiki/Policy-based_design#Simple_example](http://en.wikipedia.org/wiki/Policy-based_design#Simple_example)

for more elaborate examples see this book:
[http://erdani.com/book/main.html](http://erdani.com/book/main.html)

Oh nice one :)
I had never heard of doing it like this. It's a lot neater than the multiple inheritance I normally use for this kind of thing :guitar:

---

### Post by nitro_n2o on 2010-12-30
This is really nice I didn't know about this one either. 

Thanks a lot :)

---

### Post by nvteighen on 2010-12-31
To the original question, about using a user defined class as argument of a template:

You can't do it that way because templates are just to allow you to factor out types from several implementations that only differ from the types you use as template arguments. It's just a type-based and type-restricted macro.

---

### Post by MadCow108 on 2010-12-31
> **nvteighen said:**
> To the original question, about using a user defined class as argument of a template:

You can't do it that way because templates are just to allow you to factor out types from several implementations that only differ from the types you use as template arguments. It's just a type-based and type-restricted macro.

a class is a compile-time defined type, so you can do it.
But you can't use objects (which are created at runtime).

---

### Post by nitro_n2o on 2010-12-31
it might work with a struct, so if i change things around a little bit and do 

struct Hello
{
  public:
    void sayHello() const { printf("Hello\n"); }
};


template <Hello const &hello>
class Monkey {
  public:
    void go() { hello.sayHello(); }
};

int main()
{
  extern const Hello h;
  Monkey<h> m;
  m.go();

  return 0;
}

The code will compile, but the linker will fail. It seems odd that you can use functions or function pointers as template arguments. It will be very convenient in my opinion to have a collection of functions stored in a class or struct as a template argument that can operate on the internal data of the class. That is, instead of parameterizing the template with a bunch of functions, you just pass it a single class or struct that has all the necessary functions. Even better, the class definition serves as an interface for users to define their own implementation of some key functions, while the main algorithm is clean and remains generic

---

### Post by MadCow108 on 2010-12-31
that is exactly what policy based design can do.
You just use it wrong, you don't use functions or objects as template arguments (as stated by nvteighen) you cannot do such things. Templates are static constructs.
Instead you wrap your function into a type by adding it to a class and deriving/composing users from it.
```

// struct == class with default public access
struct Hello
{
  void sayHello() const { printf("Hello\n"); }
};
struct Hi
{
  void sayHello() const { printf("Hi\n"); }
};


template <typename T>
  class Monkey : public T {
  public:
  void go() { T::sayHello(); }
};


int main(int argc, const char *argv[])
{
  Monkey<Hello> m;
  m.go();
  Monkey<Hi> m2;
  m2.go();
  return 0;
}

```

you can do a similar things by using callbacks:
```

class Callback {
  public:
  virtual void operator()() const = 0;
};

class cHello : public Callback {
  public:
  void operator()() const { printf("Hello\n"); }
};
class cHi : public Callback {
  public:
  void operator()() const { printf("Hi\n"); }
};

class Monkey2 {
  public:
  Monkey2() : hello_callback(new cHello()) {}
  Monkey2(Callback * callback) : hello_callback(callback) {}
  
  //this can also be a normal function pointer, but then they can't have state
  const Callback * hello_callback;

  void go() { (*hello_callback)(); }
};


int main(int argc, const char *argv[])
{
  Monkey2 m = Monkey2();
  m.go();
  Monkey2 m2 = Monkey2(new cHi());
  m2.go();
  return 0;
}


```

---

### Post by nitro_n2o on 2010-12-31
Wonderful! that makes more sense! I like the policy design better, it is more elegant 

Thanks a lot madcow :) 


You can, however, use a function as a template argument

#include <iostream>
using namespace std;

template <void sayHello()> 
class Monkey {
  public: 
    void go() { sayHello(); }
};


void sayHello() { 
  cout << "Hello\n";
}

int main()
{
  Monkey<sayHello> m; 
  m.go(); 

  return 0;
}

but the policy design is probably more elegant I think

---

### Post by nvteighen on 2011-01-01
Ok, yeah, and you can do this too:
```

/* Compiled using:
 *
 * g++ -Wall -Wextra -pedantic -std=c++98
 *
 * Forced to use the C++ 98 Standard to avoid any GNU extension slip in.
 */

#include <cstdio> // No, I barely stand iostream. I'm sorry, std::cout fans.

template <int my_int>
int silly(void)
{
    return my_int;
}

int main(void)
{
    int hey = silly<4>();
    int huh = silly<6>();

    (void)printf("hey is %d\nhuh is %d", hey, huh);

    return 0;
}

```

I really flipped out when I saw this could compile... and more when I tried with the -std=c++98 option... So this is standard C++, guys...

But, you know that passing objects (even those known at compile-time), is usually done by passing them as arguments to functions, not to templates. Well, the snippet above works, yes... but you know at what cost? Increasing the executable size (the same code is generated for each template instantiation) and increasing the time it takes to compile your code (which is also a resource you have to manage). 

Ok, the effect of my snippet is no different than the one of an inlined function. It may be an interesting runtime optimization technique or not (depending on how well compilers optimize templated code)... I don't deny it can bring some advantages. But it doesn't make really much sense: there's **inline**, templates are meant for metaprogramming (which this is not)...

Giving this a second thought, maybe the biggest disadvantage this has is that it confuses people. Some people think that as long as the code works, you have the right to write weird, hard-to-understand code. Well, yes, as long as you keep the code to yourself and understand it. But if you're going to work with other people, you have to write code that those also understand... And I bet using templates this way isn't something you see in normal contexts... If I had to use it this way, I'd place a comment to explain why I'm not passing the stuff at runtime (and the explanation should be really good).

P.S.: Oh, great, the FQA beat me:
[http://yosefk.com/c++fqa/templates.html#fqa-35.2](http://yosefk.com/c++fqa/templates.html#fqa-35.2)

---

### Post by worksofcraft on 2011-01-01
> **nvteighen said:**
> ...
P.S.: Oh, great, the FQA beat me:
[http://yosefk.com/c++fqa/templates.html#fqa-35.2](http://yosefk.com/c++fqa/templates.html#fqa-35.2)

^^
hadn't seen FQA before.
I had a giggle reading some of the "stupid thing #x" type comments... coming back to brave new C++ world after 15 years absence I experienced similar insights :D

---

