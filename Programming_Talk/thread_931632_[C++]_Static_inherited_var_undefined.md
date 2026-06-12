---
title: "[C++] Static inherited var undefined"
date: 2008-09-27
forum: Programming Talk
---

### Post by Danikaze on 2008-09-27
Hello.

I have a code like this:

```
class A {
    ...
  protected:
    static int var;
    ...
}
int A::var;


class B : public A {
  ...
  void method() {
    ...
    var = whatever;
    ...
  }
}
```

It compiles, but the linker says...
undefined reference to A::var

where's the problem? :confused:

thanks in advance :)

---

### Post by dribeas on 2008-09-27
> **Danikaze said:**
> 
It compiles, but the linker says...
undefined reference to A::var

where's the problem? :confused:

When you declare an static variable in a class you are only stating that the variable is defined somewhere, but you are not defining it.

```

// a.h
class A
{
   static int s_;
};

// a.cpp
#include "a.h"

int A::s_; // definition here

```

This has nothing to do with inheritance.

---

### Post by Danikaze on 2008-09-27
Yeah I know, but I don't know why I have that error... :S 
And I don't know how to solve it T_T

I even tried changin order of objects while linking... but it didn't work!

---

### Post by dribeas on 2008-09-27
> **Danikaze said:**
> Yeah I know, but I don't know why I have that error... :S 
And I don't know how to solve it T_T

I even tried changin order of objects while linking... but it didn't work!

Is the code really like what you posted? I copied and compiled (removing ellipsis) into a test.cpp file, added an empty main() and it compiled perfectly.

From the compiler error you posted, my assumption is that you are not compiling the file with the real definition (int A::var; ) or you are not linking that file in the executable.

---

### Post by Danikaze on 2008-09-27
> **dribeas said:**
> Is the code really like what you posted? I copied and compiled (removing ellipsis) into a test.cpp file, added an empty main() and it compiled perfectly.

From the compiler error you posted, my assumption is that you are not compiling the file with the real definition (int A::var; ) or you are not linking that file in the executable.

That's why I'm asking for help: because it's too weird... :S

The real code is like that, and I have other classes in that way too, but with no problem... :confused:

---

### Post by dwhitney67 on 2008-09-27
I've seen weird before too.  Try compiling with a clean slate; that is, remove all of your object files before re-attempting to compile again.

P.S.  Though not required, I personally like to preface my static variables with the namespace or the class name.  For example, A::var (when used in class B).

---

### Post by Danikaze on 2008-09-27
> **dwhitney67 said:**
> I've seen weird before too.  Try compiling with a clean slate; that is, remove all of your object files before re-attempting to compile again.

P.S.  Though not required, I personally like to preface my static variables with the namespace or the class name.  For example, A::var (when used in class B).

I'm trying right now to make it from the start.
And yes, to access static vars you need to use classname::varname.

---

### Post by Danikaze on 2008-09-27
I think I got it... 

---header file:---
```
class A {
 public:
  ..
  static int var;
  ..
}
```

---cpp file---
```

int A::var
...

```

---main file---
```
extern int A::var
...
```

but is like a pain to declare that vars extern in every file that access them...
there isn't another way, like in java?

---

### Post by dwhitney67 on 2008-09-27
The "extern" statement in the main.cpp is not required.  That is a C thing, not C++.

A.h:
[PHP]class A
{
  protected:
    A();

    static int val;
};[/PHP]

A.cpp:
[php]
#include "A.h"

int A::val = 0;

A::A()
{
}[/PHP]

B.h:
[PHP]
#include "A.h"

class B : public A
{
  public:
    B();
    void setValue( int value );
};[/PHP]

B.cpp:
[PHP]
#include "B.h"

B::B()
{
}

void B::setValue( int value )
{
  A::val = value;   // note, A:: not required, but nice to see
}[/PHP]

Main.cpp
[PHP]#include "B.h"

int main()
{
  B bee;
  bee.setValue( 10 );

  A::val = 20;   // error, cannot do... A::val is a protected member of class A

  ...

  return 0;
}[/PHP]

To compile:
```
g++ A.cpp B.cpp Main.cpp
```

---

### Post by Danikaze on 2008-09-28
> **dwhitney67 said:**
> The "extern" statement in the main.cpp is not required.  That is a C thing, not C++.

A.h:
[PHP]class A
{
  protected:
    A();

    static int val;
};[/PHP]

A.cpp:
[php]
#include "A.h"

int A::val = 0;

A::A()
{
}[/PHP]

B.h:
[PHP]
#include "A.h"

class B : public A
{
  public:
    B();
    void setValue( int value );
};[/PHP]

B.cpp:
[PHP]
#include "B.h"

B::B()
{
}

void B::setValue( int value )
{
  A::val = value;   // note, A:: not required, but nice to see
}[/PHP]

Main.cpp
[PHP]#include "B.h"

int main()
{
  B bee;
  bee.setValue( 10 );

  A::val = 20;   // error, cannot do... A::val is a protected member of class A

  ...

  return 0;
}[/PHP]

To compile:
```
g++ A.cpp B.cpp Main.cpp
```

Yes, it worked as it supossed to do... but I don't know why in my project it doesn't work...
Gotta check it better then... :S

thanks anyway.

I'll post here if I find what I have, so maybe others have the same problem...

---

### Post by dwhitney67 on 2008-09-28
> **dwhitney67 said:**
> The "extern" statement in the main.cpp is not required.  That is a C thing, not C++.
...
Btw, this is not always true.  There are cases where one would need to "import" C functions or header files into a C++ file, and thus an extern clause would be needed.

For example:

Main.cpp:
[PHP]extern "C"
{
  #include "C_HeaderFile.h"
  #include <stdio.h>

  void function( int value )
  {
    printf( "value = %d\n", value );
  }
}
[/PHP]

---

### Post by Danikaze on 2008-09-28
I've found where my problem were...

I have used C quite a while, but I'm new with C++

All my .cpp and .hpp files where with *extern"C" {* thing

this is

.cpp:
```
#ifdef __cplusplus
extern "C" {
#endif
	file body
#ifdef __cplusplus
}
#endif
```

.hpp:
```
#ifndef __FILENAME_HPP__
#define __FILENAME_HPP__
#ifdef __cplusplus
extern "C" {
#endif
	file body
#ifdef __cplusplus
}
#endif
#endif // __FILENAME_HPP__
```

I removed every *extern "C"* { and it worked...

I'm lying if I say I fully understand *extern *uses... :P

---

### Post by dribeas on 2008-09-28
> **dwhitney67 said:**
> Btw, this is not always true.  There are cases where one would need to "import" C functions or header files into a C++ file, and thus an extern clause would be needed.

Moreover, it is still valid C++ (as long as your principles consider valid declaring global vars):
```

// x.h
extern int x;

// x.cpp
int x;

// a.cpp
#include "x.h"
// ...
   x = 5; // valid, it is declared in x.h

// main.cpp
#include "x.h"
int main()
{
}

//compile
g++ -o exe main.cpp a.cpp

```

If the extern keyword was not used, then both a.o and main.o compilation units will have their own 'x' variable, and the linker will sadly complain. That, again, if you want to use raw global variables. Even if it is valid code, it is a hardly recommended use case.

---

### Post by Danikaze on 2008-09-28
> **dribeas said:**
> 
If the extern keyword was not used, then both a.o and main.o compilation units will have their own 'x' variable, and the linker will sadly complain. That, again, if you want to use raw global variables. Even if it is valid code, it is a hardly recommended use case.

So, it's better not to have global vars, but having functions grouped in classes, with static vars?

help.hpp:
```
class help {
  static var foo;

  static void f1();
  static void f2();
}
```

is better than

help.hpp:
```

extern var foo;
void f1();
void f2();

```
:confused:

---

### Post by dribeas on 2008-09-28
> **Danikaze said:**
> ```
class help {
  static var foo;
public: // added here
  static void f1();
  static void f2();
}
```

It is not the nicest paradigm, but if you must have something close to a global in your design (singleton, as an example, even if they are considered evil not just as much as globals :)), then the code above is much better than a plain global variable.

Global variables can be accessed, and worst changed, from anywhere in the code. In the code above foo can only be accessed or changed from within help class, which makes your code less error prone. Now, even if there is just one instance of that variable, modifications of the variable are under help class' control, and your class can keep any invariants on the variable. Note that if the static class variable is public, that is just as bad as a global.

This is not a good design, but for the sake of discussion, consider a vector holding a set of values for which you want to keep max and min values. If you have globals, chances are that at some point in time user code will update the vector and forget to update min/max. With a static variable that can be taken care of.

```

class MinMaxVector
{
public:
   static void addElement( int value ) {
   {
      data_.push_back( value );
      if ( value > max_ ) max_ = value;
      if ( value < min_ ) min_ = value;
   }
   static int maxValue() { return max_; }
   static int minValue() { return min_; }
private:
   static std::vector<int> data_;
   static int min_;
   static int max_;
};

```

That is NOT good design, just an example for discussion, it should probably be implemented as non-static methods/attributes but this allows for discussion.

If data_, min_, and max_ where public, user code could add elements to data_ without updating min_ and max_, or it could intentionally or by mistake change the values of the variables.

```

// With globals/public static vars:
// Somewhere else in the code:
if ( min_ = 0 ) // meant min_ == 0 but everyone has a bad day
{
   // ...
}

```

Now you can run tests where min_ should never get to 0 but it does, and you'll have quite a lot of fun searching through your whole code base (globals can be changed everywhere) to detect the error, and that subtle difference from == to = is not so visible anyway...

---

