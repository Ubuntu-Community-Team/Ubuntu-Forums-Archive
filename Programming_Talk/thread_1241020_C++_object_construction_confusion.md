---
title: "C++ object construction confusion"
date: 2009-08-15
forum: Programming Talk
---

### Post by Volt9000 on 2009-08-15
I thought I completely understood constructors, but now this has thrown me for a loop.

I have a class which has a constructor that requires a parameter. Now I have another class that uses this first class, but I've only declared it, I haven't actually created it.

So I have something like this

```

class Foo
{
  public:
    Foo(int a);
};

class Bar
{
  private:
    Foo myfoo;
};

```

But this won't work, because the compiler complains there is no matching function call to Foo::Foo(), referring to the private member in class Bar. I understand exactly what it's saying, except I haven't created myfoo yet; I've only declared its existence.

I figured it would complain if I tried creating myfoo thusly

```

myfoo = new Foo();

```

but that is not the case.
Is there any way around this? Will I have to create an parameter-less empty, dummy constructor just to keep the compiler quiet?

---

### Post by veda87 on 2009-08-15
u have to go with the concept of inheritence.... I am not very good at explaining things... But try this code...
```
class Foo
{
  public:
    Foo(int a);
};

class Bar(Foo)
{
  private:
    Foo myfoo;
};

```
This will work....

---

### Post by scourge on 2009-08-15
> Will I have to create an parameter-less empty, dummy constructor just to keep the compiler quiet?

No, Foo doesn't need a default constructor. But you must create a constructor for Bar that initializes the Foo object:
```

class Bar
{
  public:
    Bar() : myfoo(0) {}
  private:
    Foo myfoo;
};

```
I'm initializing myfoo with a value of 0 in the example.


> u have to go with the concept of inheritence.... I am not very good at explaining things... But try this code...

This case has nothing to do with inheritance, composition works just fine. And your code isn't valid C++ either.

---

### Post by slaiyer on 2009-08-16
like scourge said, you will have to initialize the foo object. since the constructor of Foo requires an interger. Therefore you will need to do:

```
class Foo
{
  public:
    Foo(int a);
};

class Bar
{
  private:
    Foo myfoo(0);
};
```

---

### Post by mkrahmeh on 2009-08-16
am not quite good in c++, but isn't there supposed to be a default constructor for any class you create ? i mean, even if an instant of foo is created without parameters, the default constructor has to work !!

besides, to the best of my recollection, the constructor of foo wont be invoked, that is, an instant of foo wont be created unless an instant of the containing class (bar) is created, so i guess something else is missing here

---

### Post by MadCow108 on 2009-08-16
default constructors are only declared when only if no other constructor is provided
in this case there was a constructor declared so it does not create the default Foo() constructor which again is needed because Bar tries to initialise Foo with no arguments.

---

### Post by mkrahmeh on 2009-08-16
i see, but that is the case when an instant of bar is created, right ?

---

### Post by dwhitney67 on 2009-08-16
> **slaiyer said:**
> ...
class Bar
{
  private:
    Foo myfoo(0);
};[/CODE]

What you have above won't compile.  The approach presented by scourge in an earlier post is the only way I know how to initialize the Foo object.

Of course, the implementation does not need to be embedded within the class declaration; it can be done outside.
```

class Bar
{
public:
   Bar();
private:
   Foo myFoo;
};

Bar::Bar() : myFoo(0) {}

```

---

### Post by dribeas on 2009-08-16
Unlike managed languages (Java/C#) where you only work with references, in C++ you work with real objects (unlike you explictly ask for it). In Java, when you write 'MyClass c' you are not creating an instance of MyClass, but rather declaring a reference. When you write the exact same code in C++ you are actually creating the object. References are achieved in C++ by the use of pointers. But that is another question the fact is that in C++ you are actually creating a local instance of MyClass in the call above.

Now, about constructors in generarl. There is some confusion about constructors. I will try to state a couple of terms so that the discussion will be clearer:

A *default constructor* is a constructor that takes no arguments or a constructor that taking any number of arguments has default values for all of them.

```

struct A {
   A() {}
};
struct B {
   B( int a = 1, double b = 1.0 ) {}
};

```

A class can have only one default constructor (else constructing an object with the default constructor will be ambiguous, but can have any number of constructors with unambigous signatures.

```

struct C{
   C() {}
   C( int a ) {} // a cannot have a default value
   C( double b ) {}
};

```

A constructor is *user provided* when the programmer has explicitly written it (as in all examples above. When a class has no user provided constructors, the compiler will generate a default constructor. Compiler generated constructors are called *implicitly defined*. 

```

struct D {
}; // implicitly defined D() {}

```

A constructor that takes only a reference (constant or not, volatile or not) is a *copy constructor*.

```

struct E {
   E( E & rhs ) {}
};
struct F {
   F( F const & rhs ) {}
};

```

Copy constructor are special in a couple of ways, the first of which is the fact that if there is no user provided copy constructor the compiler will implicitly define a copy constructor for the user. In all the examples above from A to D, the compiler generates an implicitly defined copy constructor. The other important detail is that the copy constructor should have no side effects other than actually creating a new object that is semantically equivalent to the passed in argument. This is important as the compiler can elide making some copies as an optimization (in particular RVO - Return Value Optimization)

The rules of what the implicitly defined default constructor do are quite a few. For common classes, the implicitly defined constructor will call the default constructor (implicit or not) of all the attributes.

```

struct G {
   G( int ) {} // there is a constructor, so no default constructor is generated by the compiler
};
class H {
public:
// implicitly defined constructor is equivalent to:
//  H() : g() {}  <- error, G has no default constructor

private:
   G g;
};

```

Which is the error the OP had. Now, there are two ways of correcting it, that basically depend on the design and the domain that is being modeled. If G can be default constructed (it make sense to create objects of type G what take no arguments, and is feasible [G does not contain references]) then you can provide a default constructor for G. If it does not make sense, or if it cannot be done, then you must provide a constructor in H that calls the G constructor with the appropriate arguments:

```

struct G1 {
   G1( int x = 0 ) {} // option 1: provide default values to the arguments
};
struct G2 {
   G2( int x ) {}
   G2() {}             // option 2: provide a default constructor
};
class H1or2 {
public:
   G1 g1;
   G2 g2;
};
class H3 {
public:
   H3() : g( 0 ) {} // option 3: provide a default constructor in H that injects
                            // parameters in the initializer list
private:
   G g;
};

```

Also note that implicitly defined default constructors will not initialize POD attributes.

```

class I { // implicitly defined default constructor
private:
   int data;           // will be uninitialized
   std::string str; // will call the user provided default constructor
};

```

P.S: To slaiyer and veda87: please, if you do not know the answer, before stating something incorrect as an answer take a few seconds and try to compile it. This will keep the number of misleading answers to a limit.

---

### Post by Volt9000 on 2009-08-17
Thanks for your replies everyone, this clears things up for me a bit. :)

---

