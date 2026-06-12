---
title: "template specialization"
date: 2010-12-28
forum: Programming Talk
---

### Post by JakeFrederix on 2010-12-28
Hi,

I'm having the following problem;
I'd like to implement serialization for a template class.
To do this, I want every method/function to stay the same, and add 2 extra methods that will write the object to stream, or read the object from a stream depending on the class of parameter T.

In attachment is the class I wish to serialize.
The problem lies in the methods read and write, because the fields of the original class are not defined there.

Kind regards,
Jake

---

### Post by dwhitney67 on 2010-12-28
You cannot separate the template code definition (ie. implementation) from the template declaration.

In other words, the contents of the .cpp file need to be included within the .h file (not the other way around).  Or, as most folks do, they develop the implementation code within the header file itself, thus obviating the need to have two files.

I've taken the liberty to reformat your code to have a more professional look to it.  I've also redefined the methods necessary to serialize and deserialize your data, although I could not implement them entirely since I'm not sure what data you want written out or what the format is of the data you want to read in.

Please provide some hints if you wish for further input on how to read/write your class object.

```

#ifndef TRANSITION_METRIC_H
#define TRANSITION_METRIC_H

#include <iostream>
#include <map>
#include <vector>

template <typename T>
class TransitionMetric
{
public:
   TransitionMetric();
   ~TransitionMetric();

   void train(const T* t, const size_t n);
   void train(const std::vector<T>& t);      // preferable to passing an array

   double chance(const T* t, const size_t n);
   double chance(const std::vector<T>& t);   // preferable to passing an array

   template <typename TT>
   friend std::ostream& operator<<(std::ostream& os, const TransitionMetric<TT>& tm);

   template <typename TT>
   friend std::istream& operator>>(std::istream& is, TransitionMetric<TT>& tm);

private:
   double transition(const T& t0, const T& t1);
   double floor_dest(const T& sour);
   double floor_sour(const T& dest);
   double floor();

   std::map<T, std::map<T, int> > transitions;
   std::map<T, int>               transitions_totals;
};


template <typename T>
TransitionMetric<T>::TransitionMetric()
{
}


template <typename T>
TransitionMetric<T>::~TransitionMetric()
{
   // Not Necessary!
   transitions.clear();
   transitions_totals.clear();
}


template <typename T>
void TransitionMetric<T>::train(const T* t, const size_t n)
{
   std::vector<T> tmp(t, t + n);
   train(tmp);
}


template <typename T>
void TransitionMetric<T>::train(const std::vector<T>& t)
{
   for (int i = 0; i < t.size() - 1; ++i)
   {
      T curr = t[i];
      T next = t[i + 1];

      // put key in map if not already present
      if (transitions.find(curr) == transitions.end())
      {
         transitions.insert(std::make_pair<T, std::map<T, int> >(curr, std::map<T, int>()));
         transitions_totals.insert(std::make_pair<T, int>(curr, 0));
      }

      if (transitions.find(curr)->second.find(next) == transitions.find(curr)->second.end())
      {
         transitions.find(curr)->second.insert(std::make_pair<T, int>(next, 0));
      }

      // update maps
      transitions.find(curr)->second.find(next)->second++;
      transitions_totals.find(curr)->second++;
   }
}


template <typename T>
double TransitionMetric<T>::chance(const T* t, const size_t n)
{
   std::vector<T> tmp(t, t + n);
   return chance(tmp);
}


template <typename T>
double TransitionMetric<T>::chance(const std::vector<T>& t)
{
    double retval = 1;

    for (int i = 0; i < t.size() - 1; ++i)
    {
      retval *= transition(t[i], t[i + 1]);
    }

    return retval;
}


template <typename T>
double TransitionMetric<T>::transition(const T& t0, const T& t1)
{
   // try finding exact chance at transition
   if (transitions.find(t0) != transitions.end())
   {
      if (transitions.find(t0)->second.find(t1) != transitions.find(t0)->second.end())
      {
         return (double)transitions.find(t0)->second.find(t1)->second / (double)transitions_totals.find(t0)->second;
      }
   }

   // flooring
   double d0 = floor_dest(t0);

   if (d0 > -1)
   {
      return d0;
   }

   d0 = floor_sour(t1);

   if (d0 > -1)
   {
      return d0;
   }

   return floor();
}


template <typename T>
double TransitionMetric<T>::floor_dest(const T& sour)
{
   typename std::map<T, int>::iterator it;

   double min = -1;

   if (transitions.find(sour) != transitions.end())
   {
      for (it = transitions.find(sour)->second.begin(); it != transitions.find(sour)->second.end(); it++)
      {
         if (it->second < min || min == -1)
         {
            min = it->second;
         }
      }
   }

   return min / (double)transitions_totals.find(sour)->second;
}


template <typename T>
double TransitionMetric<T>::floor_sour(const T& dest)
{
   typename std::map<T, std::map<T, int> >::iterator it;

   double min = -1;

   for (it = transitions.begin(); it != transitions.end(); it++)
   {
      if (it->second.find(dest) != it->second.end())
      {
         double d0 = (double)it->second.find(dest)->second / (double)transitions_totals->find(it->first);

         if (d0 < min || min == -1)
         {
            min = d0;
         }
      }
   }

   return min;
}


template <typename T>
double TransitionMetric<T>::floor()
{
   typename std::map<T, std::map<T, int> >::iterator it0;

   int min = -1;

   for (it0 = transitions.begin(); it0 != transitions.end(); it0++)
   {
      typename std::map<T, int>::iterator it1;

      for (it1 = it0->second.begin(); it1 != it0->second.end(); it1++)
      {
         double d0 = (double)it1->second / (double)transitions_totals.find(it0->first)->second;

         if (d0 < min || min == -1)
         {
            min = d0;
         }
      }
   }

   return min;
}


template <typename TT>
std::ostream& operator<<(std::ostream& os, const TransitionMetric<TT>& tm)
{
   return os;
}


template <typename TT>
std::istream& operator>>(std::istream& is, TransitionMetric<TT>& tm)
{
   return is;
}

#endif

```

---

### Post by JakeFrederix on 2010-12-29
You haven't solved my problem I'm afraid.
1) I wanted a separate .h and .cpp file (otherwise I would not have created them separately)
2) Your code does not show template specialization, which is what I asked for.
3) I clearly indictated that the methods I use for serialization are 'read' and 'write'. And these have vanished in your code.

On the note of my code not being professional;
1) At university, we were always expected to separate declaration and implementation.
2) Using my IDE, it generates both a .h and .cpp file automatically when I ask it to make a new class.

I am not being (intentionally) mean. Just letting you know that your solution is not what I'm after.

Kind regards,
Jake

---

### Post by Lootbox on 2010-12-29
As far as I know, if you provide a specialization of a template class, you need to provide the entire interface (not just the two new methods), because as far as the compiler is concerned, it's an entirely separate type. This makes sense since you could theoretically want to eliminate some of the methods in the specialized version.

Your first option is to have egregious code duplication:

```
#include <iostream>
#include <map>

template <typename T>
class transition_metric {
public:
    transition_metric();
    void train(T* t, int n);
    double chance(T* t, int n);
    ~transition_metric();

private:
    double transition(T t0, T t1);
    double floor_sour(T dest);
    double floor_dest(T sour);
    double floor();
    std::map<T, std::map<T, int> > transitions;
    std::map<T, int> transitions_totals;
};

template <>
class transition_metric<int> {
public:
    transition_metric();
    void train(int* t, int n);
    double chance(int* t, int n);
    ~transition_metric();

    void read(std::istream* in);
    void write(std::ostream* out);

private:
    double transition(int t0, int t1);
    double floor_sour(int dest);
    double floor_dest(int sour);
    double floor();
    std::map<int, std::map<int, int> > transitions;
    std::map<int, int> transitions_totals;
};
```

...but that's a horrendous solution. This much code duplication (especially since you have to repeat method implementations as well) means an impossible-to-maintain program. A better solution would be to inherit from a base class to factor out shared components of interface and implementation. Simplified example:

```
#include <iostream>

/*
 * Common base class:
 */

template<typename T> class Base {
public:
    Base(const T& value);
    void say_hi() const;

protected:
    T field;
};

template<typename T>
Base<T>::Base(const T& value) : field(value) {
    // empty constructor
}

// Shared implementation of say_hi:
template<typename T>
void Base<T>::say_hi() const {
    std::cout << "Hello, " << field << std::endl;
}


/*
 * Generic derived template class:
 * (no need to repeat interface declarations)
 */

template<typename T> class Foo : public Base<T> {
public:
    Foo(const T& value);
};

template<typename T>
Foo<T>::Foo(const T& value) : Base<T>(value) {
    // empty constructor
}

/*
 * Specialization over <int> type:
 * (we'll add a say_bye method here)
 */

template<> class Foo<int> : public Base<int> {
public:
    Foo(int value);
    void say_bye() const; // add a method
};

Foo<int>::Foo(int value) : Base<int>(value) {
    // empty constructor
}

void Foo<int>::say_bye() const {
    std::cout << "Goodbye, " << field << std::endl;
}


int main(int argc, char** argv) {
    Foo<char> f_char('a');
    f_char.say_hi(); // prints "Hello, a"
    
    Foo<int> f_int(17);
    f_int.say_hi();  // prints "Hello, 17"
    f_int.say_bye(); // prints "Goodbye, 17"

    return 0;
}
```
You can also add a virtual destructor and a pure-virtual function to Base to be safe, in case you end up using the class polymorphically. That's not necessary if you never actually refer to a Base<T> object, pointer, or reference.

dwhitney67 is correct, though - you should put the method implementations in the same .h file, or in a .cpp file and then #include the .cpp at the end of the .h. Most compilers require template definitions during compilation, not during linking as is the case with non-template classes and functions. I'm not sure how universal this is across different build environments, but it's the case with g++ and you may as well avoid locking your code into a single compiler.

---

### Post by dwhitney67 on 2010-12-29
> **JakeFrederix said:**
> You haven't solved my problem I'm afraid.
1) I wanted a separate .h and .cpp file (otherwise I would not have created them separately)

I wasn't fabricating out of thin air the need to incorporate the template implemenation within the header file; this is a requisite for C++.  Perhaps you are new to C++?

> **JakeFrederix said:**
> 
2) Your code does not show template specialization, which is what I asked for.

I offered an alternative; if you do not like it, then take your homework assignment elsewhere.

> **JakeFrederix said:**
> 
3) I clearly indictated that the methods I use for serialization are 'read' and 'write'. And these have vanished in your code.

As indicated, you can take your homework problem elsewhere; however, if you (err, your instructor) insist, then
```

#ifndef TRANSITION_METRIC_H
#define TRANSITION_METRIC_H

...

template <typename T>
class TransitionMetric
{
public:
   ...

   bool read(std::istream& is);
   void write(std::ostream& os) const;

private:
   ...
};

template <typename T>
bool TransitionMetric<T>::read(std::istream& is)
{
   return false;
}

template <typename T>
void TransitionMetric<T>::write(std::ostream& os) const
{
}

#endif

```

> **JakeFrederix said:**
> 
On the note of my code not being professional;

I did not mean to imply anything about your code; I merely formatted to the style expected by each of the companies I have worked at for the last 11 years where I developed in C++.

> **JakeFrederix said:**
> 
1) At university, we were always expected to separate declaration and implementation.

Something tells me that you either skipped the class wrt templates, or were asleep in the back of the classroom.

> **JakeFrederix said:**
> 
2) Using my IDE, it generates both a .h and .cpp file automatically when I ask it to make a new class.

Always a mistake for a beginner; that is, using an IDE.  But that is merely my opinion.

> **JakeFrederix said:**
> 
I am not being (intentionally) mean. Just letting you know that your solution is not what I'm after.

I know that; nor was I.  I was merely indicating to you how the class would have been implemented in the "real world", not in academia.

---

### Post by worksofcraft on 2010-12-29
At a first glance, the only data fields in your templates are two std::map containers, that use type T as a key, so to serialize and deserialize the class you need to be able to save streams of data from which you can reconstitute the maps.

In other words, your as yet unidentified class, T, MUST have a serialization interface and then all you have to do is iterate over the maps to serialize/deserialize their contents by calling read and write methods of class T.

If a type is supplied that doesn't have them, then you will get a compile time error.

Remember that templates are more like macros that get expanded at compile time. You can't create a compiled object file containing template class implementation.

---

### Post by JakeFrederix on 2010-12-29
I've already graduated you know. So it's not a homework question.
Also, calling g++ *.cpp works perfectly even if you split implementation and declaration.

I'm not exactly new to c++. It's just that these tricky details aren't something I come across often.

Also, my use of an IDE is not because I am unable to write my own code. It's because it makes it easy to do things that would otherwise be strenuous.
Such as globally renaming a method for example. (I am bound to get a whole stack of critique from the avid users of the CLI.)

Kind regards,
Jake

---

### Post by dwhitney67 on 2010-12-29
Foo.h:
```

#ifndef FOO_H
#define FOO_H

template <typename T>
class Foo
{
public:
   Foo();
};

#endif

```

Foo.cpp:
```

#include "Foo.h"

template <typename T>
Foo<T>::Foo()
{
}

```

Main.cpp:
```

#include "Foo.h"

int main()
{
   Foo<int> foo;
}

```

Building the code:
```

g++ Foo.cpp Main.cpp

```

Errors that are generated:
```

/tmp/ccCe1Pe3.o: In function `main':
Main.cpp:(.text+0x11): undefined reference to `Foo<int>::Foo()'
collect2: ld returned 1 exit status

```

> **JakeFrederix said:**
> 
Also, calling g++ *.cpp works perfectly even if you split implementation and declaration.

Would you care to explain why the code above did not compile?  Or would it be just easier to revise your statement above?


Regards.

---

### Post by JakeFrederix on 2010-12-30
foo.h

```

#ifndef FOO_H
#define    FOO_H

#include <string>

class foo {
public:
    foo();
    foo(const foo& orig);
    void foodo();
    ~foo();
private:
    std::string message;
};

#endif    /* FOO_H */

```foo.cpp

```

#include "foo.h"
#include <iostream>

foo::foo() {
    message = "Hello world";
}

foo::foo(const foo& orig) {
    message = orig.message;
}
void foo::foodo(){
    std::cout << message << std::endl;
}
foo::~foo() {
}

```main.cpp

```

#include <cstdlib>
#include "foo.h"

using namespace std;

int main(int argc, char** argv) {

    foo* f = new foo();
    f->foodo();
    return 0;
}

```compiles perfectly
produces a file called 'a.out'
and calling ./a.out prints "Hello World"

So now, instead of trying to disprove every single statement I make, could you put some effort into actually solving my problem. Because what you're doing is rather irritating.

---

### Post by GeneralZod on 2010-12-30
> **JakeFrederix said:**
> foo.h

```

#ifndef FOO_H
#define    FOO_H

#include <string>

class foo {
public:
    foo();
    foo(const foo& orig);
    void foodo();
    ~foo();
private:
    std::string message;
};

#endif    /* FOO_H */

```foo.cpp

```

#include "foo.h"
#include <iostream>

foo::foo() {
    message = "Hello world";
}

foo::foo(const foo& orig) {
    message = orig.message;
}
void foo::foodo(){
    std::cout << message << std::endl;
}
foo::~foo() {
}

```main.cpp

```

#include <cstdlib>
#include "foo.h"

using namespace std;

int main(int argc, char** argv) {

    foo* f = new foo();
    f->foodo();
    return 0;
}

```compiles perfectly
produces a file called 'a.out'
and calling ./a.out prints "Hello World"


That's not a template class, though.

---

### Post by JakeFrederix on 2010-12-30
In attachment are foo.h, foo.cpp and main.cpp
with foo a template class.

In case of a template class, include both foo.h and foo.cpp in main.cpp
And it will compile.

And I can only assume that the next reply will be somewhat along the lines of "if you have to include both files, then why not put all code in 1 file?"

You could give people the .h, and they would know what objects of your class do, and without the .cpp, they don't know how it's done. (Great in an industrial context.)

Kind regards,
Jake

---

### Post by dwhitney67 on 2010-12-30
> **JakeFrederix said:**
> In attachment are foo.h, foo.cpp and main.cpp
with foo a template class.

In case of a template class, include both foo.h and foo.cpp in main.cpp
And it will compile.

Not using the "g++ *.cpp" you indicated earlier!

> **JakeFrederix said:**
> 
And I can only assume that the next reply will be somewhat along the lines of "if you have to include both files, then why not put all code in 1 file?"

There's no need to poke any more holes into your suggestions.  You've done enough already. 

> **JakeFrederix said:**
> 
You could give people the .h, and they would know what objects of your class do, and without the .cpp, they don't know how it's done. (Great in an industrial context.)

In the industry, which I am in btw, we include the implementation of the template class within the header file.  Prior to the standardization of C++ (before 1999?), you're technique was acceptable... but no more.  I suggest that you hop on board, and accept the way the compiler works today.

As for your need to serialize your data, you have yet to indicate the requirements of what you need done (I inquired about this earlier).  Do you want the data to be stored as regular text? or do you want it stored in binary?  If binary, will the data be used on other systems that utilize differing CPU architectures?  Consider Big- and Little-Endianess.

As for text files, do you have a particular format that you want?  What if the "T" type that you use for the template is a complex object... have you implemented serializing/deserializing methods for that complex class?

---

### Post by JakeFrederix on 2010-12-30
First google-result for "implementation outside header c++";
[http://www.learncpp.com/cpp-tutorial/89-class-code-and-header-files/](http://www.learncpp.com/cpp-tutorial/89-class-code-and-header-files/)

> 
Traditionally, the class definition is put in a header file of the same  name as the class, and the member functions defined outside of the class  are put in a .cpp file of the same name as the class. 


Article was written in 2007, after the standardization of c++ in 1998.

Kind regards,
Jake

ps: the aforementioned code does compile with the "g++ *.cpp" command on my system. I am not going to go as far as to send screenshots.

---

### Post by SevenMachines on 2010-12-30
I appreciate that its been stated before that, although normally the two would usually be in separate files, template declaration and definition *must* be in the same file. The reasons why templates are different are well explained in, at least what i consider, the first resort of c++ information, cplusplus.com
 [http://www.cplusplus.com/doc/tutorial/templates/](http://www.cplusplus.com/doc/tutorial/templates/)

Note in particular the last section
> **Templates and multiple-file projects**

 From the point of view of the compiler, templates are not normal  functions or classes. They are compiled on demand, meaning that the code  of a template function is not compiled until an instantiation with  specific template arguments is required. At that moment, when an  instantiation is required, the compiler generates a function  specifically for those arguments from the template.

When projects grow it is usual to split the code of a program in  different source code files. In these cases, the interface and  implementation are generally separated. Taking a library of functions as  example, the interface generally consists of declarations of the  prototypes of all the functions that can be called. These are generally  declared in a "header file" with a .h extension, and the implementation  (the definition of these functions) is in an independent file with c++  code.

Because templates are compiled when required, this forces a restriction  for multi-file projects: the implementation (definition) of a template  class or function must be in the same file as its declaration. That  means that we cannot separate the interface in a separate header file,  and that we must include both interface and implementation in any file  that uses the templates.

Since no code is generated until a template is instantiated when  required, compilers are prepared to allow the inclusion more than once  of the same template file with both declarations and definitions in a  project without generating linkage errors.

Hope that clears up the reasons templates are different a little

---

### Post by MadCow108 on 2010-12-30
> **JakeFrederix said:**
> First google-result for "implementation outside header c++";
[http://www.learncpp.com/cpp-tutorial/89-class-code-and-header-files/](http://www.learncpp.com/cpp-tutorial/89-class-code-and-header-files/)

Article was written in 2007, after the standardization of c++ in 1998.

and it does not apply to templates.

> 

ps: the aforementioned code does compile with the "g++ *.cpp" command on my system. I am not going to go as far as to send screenshots.

because you sneaked in a:
#include "foo.cpp"
in main.cpp, which is equivalent to a implementation in a header file
remove that and it will fail.

As stated by many before, you cannot split template definitions and declarations
yet another reliable source if you still do not believe ... :[http://www.parashift.com/c++-faq-lite/templates.html#faq-35.12](http://www.parashift.com/c++-faq-lite/templates.html#faq-35.12)
It can be done to some degree with export. But export does not work as intended and has almost no compiler supporting it, so it will be removed from the standard in c++0x.

---

### Post by nvteighen on 2010-12-30
Let's see.

C++ is a static typed language, meaning that it has to know the types of everything at compile-time, otherwise it won't let you compile your code. More precisely, what C++ needs to know is the **size** each element is going to take in the stack so it can generate the proper ASM code. Also, it's compiled module-wise, so the type checking is done per module, before everything is linked up. This is the main reason why C++ needs header files (well, actually this was inherited from C).

Now. Template classes or template functions are a mechanism that allows you to factor out types from a certain expression. This means that a template is code whose size information isn't deducible from its definition but from its instantiation. In other words, you can't tell how much size will the return value or the argument take in this example:

```

template <typename T>
T something_silly(T something)
{
    return something;
}

```

You can't until you know, for example, that somewhere you execute it as:
```

int my_number = something_silly<int>(7);

```

What this means is that C++ needs the template definition and the template instantiation in the same compilation unit. If in some compilation unit, only the template definition was available, that would be code relying on unknown types (e.g. sizes), something C++ can't do. If there only were template instantiations with no template definition, the result is obvious.

So, you need to place the template in some place where it is available to the compilation unit. If it's a "private" template, put it in the .cpp, but if you intend it to be used by foreign code, I'm sorry, but you have to put in the header file, showing the whole implementation.

(This whole rant is also applicable to the fact that you have to show any class's private members in the header... otherwise, C++ won't be able to correctly calculate how big your objects are)

---

### Post by worksofcraft on 2010-12-30
> **dwhitney67 said:**
> 
As for your need to serialize your data, you have yet to indicate the requirements of what you need done (I inquired about this earlier).  Do you want the data to be stored as regular text? or do you want it stored in binary?  If binary, will the data be used on other systems that utilize differing CPU architectures?  Consider Big- and Little-Endianess.

As for text files, do you have a particular format that you want?  What if the "T" type that you use for the template is a complex object... have you implemented serializing/deserializing methods for that complex class?

Yes this is what I was trying to say also back in post #6:
Your parameter class type T must provides an agreed serialization interface of some sort and also you cannot serialize pointer and reference types.

It seems to me all this debate about programming style is going off track and serves no constructive purpose :confused:

---

### Post by JakeFrederix on 2010-12-30
Back on track then;

Using the modified code  (second post), how do I go from there to serializing the model for ints for instance?
Because, from my point of view it just introduced another parameter TT.

Kind regards,
Jake

---

### Post by dwhitney67 on 2010-12-30
> **JakeFrederix said:**
> Back on track then;

Using the modified code  (second post), how do I go from there to serializing the model for ints for instance?
Because, from my point of view it just introduced another parameter TT.

Kind regards,
Jake

Don't think of TT as being a "new" variable; it is synonymous with T.  A unique type identifier (TT) is required because it is being used with friend functions, which although they are declared within the class, they are not part of such.

Now back to the serialization; this would be the most basic of operations... writing the data out as text data, with a blank space after each key and value.
```

#ifndef TRANSITION_METRIC_H
#define TRANSITION_METRIC_H

#include <iostream>
#include <map>
#include <vector>

template <typename T>
class TransitionMetric
{
public:
   TransitionMetric();
   ~TransitionMetric();

   void train(const T* t, const size_t n);
   void train(const std::vector<T>& t);      // preferable to passing an array

   double chance(const T* t, const size_t n);
   double chance(const std::vector<T>& t);   // preferable to passing an array

   template <typename TT>
   friend std::ostream& operator<<(std::ostream& os, const TransitionMetric<TT>& tm);

   template <typename TT>
   friend std::istream& operator>>(std::istream& is, TransitionMetric<TT>& tm);

private:
   double transition(const T& t0, const T& t1);
   double floor_dest(const T& sour);
   double floor_sour(const T& dest);
   double floor();

   std::map<T, std::map<T, int> > transitions;
   std::map<T, int>               transitions_totals;
};


template <typename T>
TransitionMetric<T>::TransitionMetric()
{
}


template <typename T>
TransitionMetric<T>::~TransitionMetric()
{
   // Not Necessary!
   transitions.clear();
   transitions_totals.clear();
}


template <typename T>
void TransitionMetric<T>::train(const T* t, const size_t n)
{
   typename std::vector<T> tmp(t, t + n);
   train(tmp);
}


template <typename T>
void TransitionMetric<T>::train(const std::vector<T>& t)
{
   for (size_t i = 0; i < t.size() - 1; ++i)
   {
      T curr = t[i];
      T next = t[i + 1];

      // put key in map if not already present
      if (transitions.find(curr) == transitions.end())
      {
         transitions.insert(std::make_pair<T, std::map<T, int> >(curr, std::map<T, int>()));
         transitions_totals.insert(std::make_pair<T, int>(curr, 0));
      }

      if (transitions.find(curr)->second.find(next) == transitions.find(curr)->second.end())
      {
         transitions.find(curr)->second.insert(std::make_pair<T, int>(next, 0));
      }

      // update maps
      transitions.find(curr)->second.find(next)->second++;
      transitions_totals.find(curr)->second++;
   }
}


template <typename T>
double TransitionMetric<T>::chance(const T* t, const size_t n)
{
   typename std::vector<T> tmp(t, t + n);
   return chance(tmp);
}


template <typename T>
double TransitionMetric<T>::chance(const std::vector<T>& t)
{
    double retval = 1;

    for (size_t i = 0; i < t.size() - 1; ++i)
    {
      retval *= transition(t[i], t[i + 1]);
    }

    return retval;
}


template <typename T>
double TransitionMetric<T>::transition(const T& t0, const T& t1)
{
   // try finding exact chance at transition
   if (transitions.find(t0) != transitions.end())
   {
      if (transitions.find(t0)->second.find(t1) != transitions.find(t0)->second.end())
      {
         return (double)transitions.find(t0)->second.find(t1)->second / (double)transitions_totals.find(t0)->second;
      }
   }

   // flooring
   double d0 = floor_dest(t0);

   if (d0 > -1)
   {
      return d0;
   }

   d0 = floor_sour(t1);

   if (d0 > -1)
   {
      return d0;
   }

   return floor();
}


template <typename T>
double TransitionMetric<T>::floor_dest(const T& sour)
{
   typename std::map<T, int>::iterator it;

   double min = -1;

   if (transitions.find(sour) != transitions.end())
   {
      for (it = transitions.find(sour)->second.begin(); it != transitions.find(sour)->second.end(); it++)
      {
         if (it->second < min || min == -1)
         {
            min = it->second;
         }
      }
   }

   return min / (double)transitions_totals.find(sour)->second;
}


template <typename T>
double TransitionMetric<T>::floor_sour(const T& dest)
{
   typename std::map<T, std::map<T, int> >::iterator it;

   double min = -1;

   for (it = transitions.begin(); it != transitions.end(); it++)
   {
      if (it->second.find(dest) != it->second.end())
      {
         double d0 = (double)it->second.find(dest)->second / (double)transitions_totals->find(it->first);

         if (d0 < min || min == -1)
         {
            min = d0;
         }
      }
   }

   return min;
}


template <typename T>
double TransitionMetric<T>::floor()
{
   typename std::map<T, std::map<T, int> >::iterator it0;

   int min = -1;

   for (it0 = transitions.begin(); it0 != transitions.end(); it0++)
   {
      typename std::map<T, int>::iterator it1;

      for (it1 = it0->second.begin(); it1 != it0->second.end(); it1++)
      {
         double d0 = (double)it1->second / (double)transitions_totals.find(it0->first)->second;

         if (d0 < min || min == -1)
         {
            min = d0;
         }
      }
   }

   return min;
}


static const std::string TRAN_VALUE = "tran_value:";
static const std::string TRAN_TOTAL = "tran_total:";


template <typename TT>
std::ostream& operator<<(std::ostream& os, const TransitionMetric<TT>& tm)
{
   typename std::map<TT, std::map<TT, int> >::const_iterator it1 = tm.transitions.begin();

   for (; it1 != tm.transitions.end(); ++it1)
   {
      typename std::map<TT, int>::const_iterator it2 = it1->second.begin();

      os << TRAN_VALUE << " " << it1->first;

      for (; it2 != it1->second.end(); ++it2)
      {
         os << " " << it2->first << " " << it2->second << std::endl;
      }
   }

   typename std::map<TT, int>::const_iterator it3 = tm.transitions_totals.begin();

   for (; it3 != tm.transitions_totals.end(); ++it3)
   {
      os << TRAN_TOTAL << " " << it3->first << " " << it3->second << std::endl;
   }

   return os;
}


template <typename TT>
std::istream& operator>>(std::istream& is, TransitionMetric<TT>& tm)
{
   std::string identifier;
   TT  key1;
   TT  key2;
   int value;

   while (!is.eof())
   {
      is >> identifier;

      if (identifier == TRAN_VALUE)
      {
         is >> key1 >> key2 >> value;

         typename std::map<TT, std::map<TT, int> >::iterator it = tm.transitions.find(key1);

         if (it != tm.transitions.end())
         {
            it->second[key2] = value;
         }
         else
         {
            std::map<TT, int> newMap;

            newMap.insert(std::pair<TT, int>(key2, value));

            tm.transitions[key1] = newMap;
         }
      }
      else if (identifier == TRAN_TOTAL)
      {
         is >> key1 >> value;

         tm.transitions_totals.insert(std::pair<TT, int>(key1, value));
      }
      else
      {
         std::cerr << "Failure parsing input stream." << std::endl;
         break;
      }
   }

   return is;
}

#endif

```

Sample "main" program to test the code above:
```

#include "TransitionMetric.h"
#include <fstream>

int main()
{
   TransitionMetric<int> tm1;
   int trains[] = { 1, 2, 3, 4, 5 };

   tm1.train(trains, 5);

   std::ofstream outFile("data.txt");

   outFile << tm1;

   outFile.close();

   std::ifstream inFile("data.txt");

   TransitionMetric<int> tm2;

   inFile >> tm2;

   inFile.close();

   std::cout << tm1 << "==================\n" << tm2 << std::endl;
}

```

P.S.  More error checking should be performed when ingesting the data from the input stream.

---

### Post by JakeFrederix on 2010-12-30
The problem is that when I read the stream in, I have to know the type of template parameter T.
I have separate methods for writing types like int,double, bool,std::string, ...

And when reading the stream, I would have to know the type of T in order to know how the data should be interpreted.

---

### Post by dwhitney67 on 2010-12-30
There is no way for you to use a templated object without specifying the type you wish to use.  Thus, if you wish to work with different data types (and there's nothing wrong with this), you need the means to distinguish which data type is in a particular data file.

You can decide if you want to name the file such that it identifies this data type, or you can devise some way that you can specify the data type within the file itself.

For choice 1, example filenames could be something like "data_int.txt", "data_double.txt", or "data_string.txt".

For choice 2, you would need to store a string or enumerated value at the beginning of the file which then you can parse to determine the type T to use.  Perhaps defining a "factory" class would also present a convenient option.

Btw, what is this project being used for?

---

### Post by JakeFrederix on 2010-12-30
You don't understand what I meant.

The program will know at runtime (before reading the file) what T is supposed to be.
But I want to store the model  in binary form. So the read method needs to know when it's supposed to read ints, and when it's supposed to read something else for T.

This class can estimate how likely a sequence of T is, given a corpus or T* it was trained on.
It'll be used to build a part of speech tagger.

---

### Post by dwhitney67 on 2010-12-31
> **JakeFrederix said:**
> You don't understand what I meant.

The program will know at runtime (before reading the file) what T is supposed to be.
But I want to store the model  in binary form. So the read method needs to know when it's supposed to read ints, and when it's supposed to read something else for T.

This class can estimate how likely a sequence of T is, given a corpus or T* it was trained on.
It'll be used to build a part of speech tagger.

Change the operator<<() [write] and operator>>() [read] functions to use the write() and read() functions that are available for ostream/istream objects.

For ints, floats, and doubles, something like this will work:
```

const TT& value = ...;

os.write((const char*) *&value*, sizeof(TT));

```
where value is whatever is your data value that you want written.  Reading should be similar.

As for strings, the code above will not work, because sizeof(string) does not make much sense in the context above.

Thus in my opinion, you need to specialized the operator<<() and operator>>() for each data type T that you expect to use.

It is a holiday weekend, and personally I'm tired (err, bored) of working on *your* project.  I think you need to start producing some code yourself, or throw some tokens my way.  :-)   I do not like to work for free, and this project has strayed from being something educational to something that seems more in tune with a money-making venture.

---

