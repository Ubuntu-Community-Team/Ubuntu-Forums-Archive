---
title: "If there's syntax errors in your C or C++ program, it means you did something wrong"
date: 2010-03-19
forum: Programming Talk
---

### Post by Kenny_Strawn on 2010-03-19
I have had plenty of errors in some compilations of C++ programs in the past, in part because I was trying to do things C++ couldn't. I have virtually eliminated them lately, but still have a long way to go.

For instance, here is what I learned from other members here:

```

#include <iostream>
#include <cmath>
#include <cstring>

using namespace std;

class cube
{
    struct Point1
    {
        int Left;
        int Top;
        int Rear;
    };
    
    struct Point2
    {
        int Right;
        int Bottom;
        int Front;
    };
};

```

As you can see, this is a new revision of the C++ program [here]('https://launchpad.net/gtk2-module-cube') that hasn't been pushed to yet. You'll find that I changed a struct to a class with two nested structs - something C++ prefers over a plain struct, even though C++ will accept it otherwise. What this is supposed to define is basic 3D window geometry, as in something similar to the "Rect" struct in Microsoft Windows, but 3D instead of 2D.

I also thank the many members of LQ.org for helping me to debug some of my programs.

Errors are not fun. In some cases, GCC does not even explain them, and neither does G++. It can take quite some getting used to, and even I messed up. Don't let errors get you down. Maybe you can PM me and I could research the errors, but don't give up.

For example, I tried using 128-bit hexadecimal values in C++, but it only supports up to 32-bit. As such, I needed to use string values, and assign them to "lowerBound" and "upperBound" variables. Man, I really learned my lesson right there.

As I said above: PM me when you come to a frustrating error, and I will Google it.

Regards,

-Kenny

---

### Post by dribeas on 2010-03-20
I don't seem to follow your post or where you want to get to. If the code does not compile you clearly did something wrong: you did not adhere to the syntax of the language. That does not by any means that the design is right or wrong or that if there are no syntax errors the implementation will be correct.

Also I do not understand the whole thing about the class/struct issues you face. A class and a struct are exactly the same thing, with the single difference that access is public by default in structs and private in classes. That is:

```

class d : b1, public b2 {
   int x;
public:
   int y;
};
// equivalent to:
struct d : private b1, b2 {
private:
   int x;
public:
   int y;
};

```

Finally, I don't know how you came to the class you show in the opening post, but unless you have a really good reason for not doing it, I would simplify the design:

```

struct point {
   int x,y,z;
};
struct cube {
   point position, dimensions;
};

```

About the help that the compiler provides when it encounters errors, I bet it tries to do its best, but the c++ language is quite complex to parse. If you don´t mind spending $50 you might want to take a look at [comeau]("http://www.comeaucomputing.com") compiler, which I believe has better error messages than gcc/g++, in many cases telling you not only where the error is but also why it is an error. Anyway you will get used to understanding the error messages and what might have caused them.

---

### Post by Queue29 on 2010-03-20
```

class cube
{
    struct Point1
    {
        int Left;
        int Top;
        int Rear;
    };
    
    struct Point2
    {
        int Right;
        int Bottom;
        int Front;
    };
};

```

What the heck kind of coordinate system are you using? A Point struct/class should contain x,y, and z values. Each instance of a Point will set those values appropriately. 
Having "Top","Left","Rear","Right","Bottom",Front" values is.. nonsensical. Learn something about the [Cartesian Coordinate]("http://en.wikipedia.org/wiki/Cartesian_coordinate_system") system before you go any further. 

Also
> As I said above: PM me when you come to a frustrating error, and I will Google it.

```
some.cpp: In function ‘std::ofstream& operator<<(std::ofstream&, const EmployeeType&)’:
something.cpp:138: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/lib/gcc/x86_64/4.1.2/../../../../include/c++/4.1.2/bits/ostream.tcc:183: note: candidate 1: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(int) [with _CharT = char, _Traits = std::char_traits<char>]
something.cpp:136: note: candidate 2: std::ofstream& operator<<(std::ofstream&, const EmployeeType&)
something.cpp:141: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/lib/gcc/x86_64/4.1.2/../../../../include/c++/4.1.2/bits/ostream.tcc:361: note: candidate 1: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(double) [with _CharT = char, _Traits = std::char_traits<char>]
something.cpp:136: note: candidate 2: std::ofstream& operator<<(std::ofstream&, const EmployeeType&)
something.cpp:142: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/lib/gcc/x86_64/4.1.2/../../../../include/c++/4.1.2/bits/ostream.tcc:628: note: candidate 1: std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, char) [with _Traits = std::char_traits<char>]
something.cpp:136: note: candidate 2: std::ofstream& operator<<(std::ofstream&, const EmployeeType&)
```

Have fun with that..

---

### Post by dribeas on 2010-03-20
> **Queue29 said:**
> 
```
some.cpp: In function ‘std::ofstream& operator<<(std::ofstream&, const EmployeeType&)’:
something.cpp:138: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/lib/gcc/x86_64/4.1.2/../../../../include/c++/4.1.2/bits/ostream.tcc:183: note: candidate 1: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(int) [with _CharT = char, _Traits = std::char_traits<char>]
something.cpp:136: note: candidate 2: std::ofstream& operator<<(std::ofstream&, const EmployeeType&)
something.cpp:141: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/lib/gcc/x86_64/4.1.2/../../../../include/c++/4.1.2/bits/ostream.tcc:361: note: candidate 1: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(double) [with _CharT = char, _Traits = std::char_traits<char>]
something.cpp:136: note: candidate 2: std::ofstream& operator<<(std::ofstream&, const EmployeeType&)
something.cpp:142: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/lib/gcc/x86_64/4.1.2/../../../../include/c++/4.1.2/bits/ostream.tcc:628: note: candidate 1: std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, char) [with _Traits = std::char_traits<char>]
something.cpp:136: note: candidate 2: std::ofstream& operator<<(std::ofstream&, const EmployeeType&)
```

Have fun with that..

That´s what happens when you sprinkle code for implicit conversions here and there...

---

### Post by CptPicard on 2010-03-20
> **Queue29 said:**
> 
What the heck kind of coordinate system are you using?

It does make some kind of sense actually. Consider a 3D box and the planes that make up its sides -- theoretically the first point could be the one at the "back upper left" corner and the second point at the "front lower right" corner.

But, of course I am not saying that it makes any *real* sense. Kenny is just very... creative... :)

---

### Post by nvteighen on 2010-03-20
Ugh...

```

class Point
{
public:
    int left, top, rear;
};

class Cube
{
public:
    Point point_1, point_2;
};

int main(void)
{
    // Stub main() to make compilation as executable possible...

    return 0;
}

```

Of course, a struct would be just fine as no methods have been defined yet. Please notice how none of your #include's is actually necessary up to this point...

But a data structure without any actions somehow associated is useless... A structure or class (I'm slowly starting to think structs' and classes' limits aren't that easy to define) is not only what it is, but also what it does.

I again recommend you to look up at Python, get how classes work in general (Python makes it much easier to grasp the general concepts of OOP) and then revisit C++.

---

### Post by lisati on 2010-03-20
> **nvteighen said:**
> But a data structure without any actions somehow associated is useless... 

As I understand it, a struct doesn't have to have a method included as part of its definition - historically, C didn't support having actions as part of the struct definition. It might not be technically accurate, but I like to think of one use of the "struct" as roughly analogous to a "record" in traditional file-based programming.

---

### Post by falconindy on 2010-03-20
A lack of syntax errors doesn't mean you did something right.

```
#include <stdio.h>
int main(void) {
  char* p;
  printf("%s\n", p);
  return 0;
}
```

---

### Post by nvteighen on 2010-03-20
> **lisati said:**
> As I understand it, a struct doesn't have to have a method included as part of its definition - historically, C didn't support having actions as part of the struct definition. It might not be technically accurate, but I like to think of one use of the "struct" as roughly analogous to a "record" in traditional file-based programming.

Ok, formally structs aren't classes. 

But, though they don't have methods in their definitions, structs end up being used as classes, as data structures with actions associated as their own and that define what they conceptually are. Maybe what I'm referring to is not a programming idea but another science's... :P

The formal differences, like e.g. classes constituting a namespace (whereas structs need naming conventions in order to not produce conflicts) don't defeat the fact that both can be used as simulation of objects containing information and having a set of actions associated to them... The same goes for the record ("dictionary" in Python-lingo, "%hash" in Perl-lingo) and whatever data structure that works as a mean of combination in such way that the resulting combination is placed functionally at the same level as the language's basic types.

In other words, whatever that is able to make a bunch of data be treated as a single opaque entity having some operations that can manipulate it (the same as + can manipulate int's in C or C++... one could think + as an integer's method, and so do Python, Java, Common Lisp, etc.) is pretty much the same concept of "object". The differences of struct and class are much more language- and implementation-dependent, IMO, rather than conceptual.

That's what I wanted to say :P

---

### Post by dwhitney67 on 2010-03-20
There is nothing different between a struct and a class, other than the "public"-ness of the attributes/methods as described earlier by Dribeas.

These two constructs are equivalent:
```

struct Example
{
// by default, these are public
//
   Example(int value) : myValue(value) {}   // constructor

   int getValue() const { return myValue; }

// must be explicit to denote member data that is private
private:
   int myValue;
};

```

```

class Example
{
// no access designator defined here; thus everything below is
// private, unless indicated otherwise.
//
   int myValue;

public:
   Example(int value) : myValue(value) {}   // constructor

   int getValue() const { return myValue; }
};

```

structs can have destructors, (pure) virtual methods, and they can also be used in inheritance constructs.

---

### Post by Simon17 on 2010-03-20
nvteighen, what the hell are you blabbering about?

---

### Post by CptPicard on 2010-03-20
> **Simon17 said:**
> nvteighen, what the hell are you blabbering about?

He's a linguist; it affects his brain you see.. ;)

I guess what he's after is that the class specifically is a means to get a user-extensible type system that has inheritance relationships and a way to specify actions (methods) associated with the particular types; and structs are at least generally understood more as pure data-records. Except that they actually *do* work as classes, as well. :)

---

### Post by grayrainbow on 2010-03-21
> **Queue29 said:**
> ```

class cube
{
    struct Point1
    {
        int Left;
        int Top;
        int Rear;
    };
    
    struct Point2
    {
        int Right;
        int Bottom;
        int Front;
    };
};

```

What the heck kind of coordinate system are you using? A Point struct/class should contain x,y, and z values. Each instance of a Point will set those values appropriately. 
Having "Top","Left","Rear","Right","Bottom",Front" values is.. nonsensical. Learn something about the [Cartesian Coordinate]("http://en.wikipedia.org/wiki/Cartesian_coordinate_system") system before you go any further. 

Also


```
some.cpp: In function &#8216;std::ofstream& operator<<(std::ofstream&, const EmployeeType&)&#8217;:
something.cpp:138: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/lib/gcc/x86_64/4.1.2/../../../../include/c++/4.1.2/bits/ostream.tcc:183: note: candidate 1: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(int) [with _CharT = char, _Traits = std::char_traits<char>]
something.cpp:136: note: candidate 2: std::ofstream& operator<<(std::ofstream&, const EmployeeType&)
something.cpp:141: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/lib/gcc/x86_64/4.1.2/../../../../include/c++/4.1.2/bits/ostream.tcc:361: note: candidate 1: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(double) [with _CharT = char, _Traits = std::char_traits<char>]
something.cpp:136: note: candidate 2: std::ofstream& operator<<(std::ofstream&, const EmployeeType&)
something.cpp:142: error: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
/usr/lib/gcc/x86_64/4.1.2/../../../../include/c++/4.1.2/bits/ostream.tcc:628: note: candidate 1: std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, char) [with _Traits = std::char_traits<char>]
something.cpp:136: note: candidate 2: std::ofstream& operator<<(std::ofstream&, const EmployeeType&)
```

Have fun with that..
It kinda make sense for beginning. Well, when you take the fact that one point and one size do exactly same as this "class cube"(which as all POD should be struct btw)...and the fact that 3D is done quite differently then 2D(people usually use linear algebra and GPU for 3D)...yea, learn the math :)
Anyway, apart from some nonsenses in the OP example the idea of this thread is kinda good - learn the language, and why things are as they are in the language(well, there's always some exceptions to not bother much with, if one is not REAL C++ fan, namespace resolution rules for example :D ).

P.S. And always try abuse as much as you can with "const" keyword.

Edit: actually you'll need quaternion for proper representation.

---

### Post by nvteighen on 2010-03-21
> **Simon17 said:**
> nvteighen, what the hell are you blabbering about?

After reading this thread, I'm not sure... :P

> **CptPicard said:**
> 
I guess what he's after is that the class specifically is a means to get a user-extensible type system that has inheritance relationships and a way to specify actions (methods) associated with the particular types; and structs are at least generally understood more as pure data-records. Except that they actually *do* work as classes, as well. :)

Oh...! ;)

Ok, what I wanted to say is that whatever data construct that somehow defines a set of data as a single unified new data type and has a set of actions defined with respect to that, that's something that can be used as an object because an object (in programming) is something that has some propierties and does some actions.

That's why the conceptual difference between a struct and a class is near to none, if not none.

---

