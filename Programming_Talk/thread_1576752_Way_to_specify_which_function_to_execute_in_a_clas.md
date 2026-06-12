---
title: "Way to specify which function to execute in a class?"
date: 2010-09-17
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-09-17
Sorry for the poor subject title...not sure how else to phrase my question...

**Language:** C++, although I'm mixing C++ and Java below...

**Short Version:** I have the name of a function that I want to execute stored in a string.  How can I execute the function (which is located within the same class)?

**Long Version:**

I have an extended class with several functions.  The class looks like this:

class Tests extends BaseTest
{
      void runTest1();
      void runTest2();
      void RunTest3();
}

The BaseTest class looks like this:

class BaseTest
{
     virtual void initialize();
     virtual void execute();
     virtual void cleanup();
      void helperFunction1();
      void helperFunction2();
      ...
}

These test classes are actually run on a tester.  Every test in the list implements the baseTest class above.  The tester simply calls initialize(), then execute(), then cleanup() for every test in the list.  I am trying to make test setup easier for other people in my group who don't know much about programming.  I developed a bunch of helper functions as shown above in the baseTest class.  It would be nice if each other member of my group only had to add a void runTestX(); to the Tests class above and not have to worry about implementing the entire class.  The methods cannot be static due to tester requirements.  So the Tests class above will need to over-ride the execute() method of the BaseTest class.  For any given test, only one of the RunTestX() methods will need to be called.  However, the only function that will be called by the tester when it's time to execute will be the execute() method.  What's  a clean way to make the execute() method of Tests (which is the only function that will ever be directly called by the tester) execute the desired RunTestX() function?  I could so something like:

void Tests::setFunctionNametoExecute(String name)
{
     this.name = name;
}

void Tests::execute()
{
     if(name.equals("Test 1")) runTest1();
     else if(name.equals("Test 2")) runTest2();
     ...
}

But having to update the execute() function every time a new test is added is somewhat tedious, but I guess that could be a last resort.  Is there a better way?

---

### Post by Tony Flury on 2010-09-17
From what i know of C/C++ you cannot at run time convert a string into an executable R value (i.e a language statement), this is mainly due to the fact that by the time your code executes the "name" of your functions and methods are no longer recorded - what the machince sees is addresses and assembled jump statements.

The only conceivable way you might get this to work would be to build a table to enable you to translate strings into pointers - but that is not going to be nice I don't think. 

If you are trying to build a tester - do it another way.

---

### Post by Some Penguin on 2010-09-17
You could require that the functions be named or commented in a specific way and then write a program to produce the corresponding test code.  That would be far simpler than building shared libraries and then using libld's dlopen() and dlsym() , for instance.

---

### Post by simeon87 on 2010-09-17
You seem to be reinventing test suites though; for Java you could use JUnit instead unless there's a reason why you need a custum testing framework.

---

### Post by lisati on 2010-09-17
It almost sounds like a candidate for a [switch statement]("http://en.wikipedia.org/wiki/Switch_statement") or similar inside a wrapper function/class that chooses the most appropriate section of code to call.

---

### Post by Some Penguin on 2010-09-18
True about reinvention.

[http://stackoverflow.com/questions/91683/how-do-you-implement-unit-testing-in-large-scale-c-projects]("http://stackoverflow.com/questions/91683/how-do-you-implement-unit-testing-in-large-scale-c-projects")

---

### Post by worksofcraft on 2010-09-18
It does sound like a candidate for function pointers and a dictionary of strings that map to those pointers. You can use the map container from the standard C++ template library to do all the work for you.

Standard Java is just not up to this though. When programming for the Java VM I wouldn't use anything less than the Pizza language superset and that does include function pointers for Java... [http://pizzacompiler.sourceforge.net/](http://pizzacompiler.sourceforge.net/)

A different and perhaps easier approach is to make the execute method virtual and then derive a distinct tester class for every test function you want. Java could probably manage to associate strings with objects of different classes.

---

### Post by nvteighen on 2010-09-18
> **worksofcraft said:**
> It does sound like a candidate for function pointers and a dictionary of strings that map to those pointers. You can use the map container from the standard C++ template library to do all the work for you.


That'd be just a nicer way to do exactly the same. It doesn't solve the issue of having to update the correlations between string and function.

@OP:
What you want is almost dynamic runtime resolution of symbols... something like Lisp's eval or whatever. Considering that C++ and Java are statically compiled languages, this means, symbols need to be known at compile-time, either you implement a new dynamic interpreter on top of them (no matter how simple, ad hoc and restricted) or I am afraid you won't be able to do this.

And interesting idea would be to use Clojure to extend Java. That'd be actually the same I told you above, but using stuff already done by other people... Maybe you could use the Python API too to extend C++, so that you get the interpreter's power "without" the interpreter running.

---

### Post by Some Penguin on 2010-09-18
Uh, definitely not true for Java.  That's what the reflection API is for.  That's how such things as dependency injection ala the Spring framework works.

Now, it's all kinds of fun when you're talking about overriding and generic methods, and you end up using lots of isAssignableFrom-et-al and catching ClassCastExceptions, but you can certainly ask for methods by name.

---

### Post by dwhitney67 on 2010-09-18
Seems like [CppUnit]("http://sourceforge.net/apps/mediawiki/cppunit/index.php?title=Main_Page") should be considered.

Besides the link above, here's the more practical documentation:
[http://cppunit.sourceforge.net/doc/lastest/cppunit_cookbook.html](http://cppunit.sourceforge.net/doc/lastest/cppunit_cookbook.html)

---

### Post by Reiger on 2010-09-18
Eh if this is about Java, and unit testing then you'd use JUnit.

If it is about mixing Java & C++ and unit testing, I would still use Junit, and do the dynamic method calling on the Java side of the fence where everything is an order of magnitude easier by the simple expedient of being able to annotate methods and lookup the annotations at runtime...

---

### Post by SNYP40A1 on 2010-09-21
Sorry, the original question was not about Unit Testing.  Test refers to code which is run on a Tester to test silicon wafers.  Lanugage is C++, although my code mixed C++ and Java because I am more familiar with Java than C++.  I thought about the function pointer and map approach, really the same as using a switch statement to map strings passed in as parameters to function names.  Seems like the essential problem here is that C++ has no way to get a pointer to a function by the function name.  There's no VM to provide "meta information" (if that's the right name to use) about a given class.

Edit: I am using DLLs and this is being developed on Windows.  There might be a way to get handles to functions in a DLL by name...I think there is according to one of my co-workers.  I suppose I should ask this question on a Windows forum...

---

### Post by dwhitney67 on 2010-09-21
C++ method names are mangled; thus it is hard to summon a method by name.  However, you can map a string to a particular method by setting up the relationship.  For instance:
```

#include <map>
#include <string>
#include <iostream>

void function1(void)
{
   std::cout << "This is function1..." << std::endl;
}

void function2(void)
{
   std::cout << "This is function2..." << std::endl;
}

int main()
{
   typedef void (*Function)();
   typedef std::map<std::string, Function> FunctionMap;

   FunctionMap fm;

   fm.insert(std::make_pair<std::string, Function>("function1", function1));
   fm.insert(std::make_pair<std::string, Function>("function2", function2));

   // here we call function2() by "name"
   fm["function2"]();
}

```

Here's another way, using Boost's bind(), which I must confess I'm not 100% familiar with (perhaps Dribeas could provide a better example):
```

#include <map>
#include <string>
#include <iostream>
#include <boost/function.hpp>
#include <boost/bind.hpp>

class MyClass
{
public:
   MyClass(int val) : value(val) {}

   void function1(void)
   {
      std::cout << "This is function1 w/ access to value = " << value << std::endl;
   }

   void function2(void)
   {
      std::cout << "This is function2 w/ access to value = " << value << std::endl;
   }

private:
   int value;
};

int main()
{
   typedef boost::function<void()>         Function;
   typedef std::map<std::string, Function> FunctionMap;

   FunctionMap fm;
   MyClass     mc(10);

   fm.insert(std::make_pair<std::string, Function>("function1", boost::bind(&MyClass::function1, &mc)));
   fm.insert(std::make_pair<std::string, Function>("function2", boost::bind(&MyClass::function2, &mc)));

   fm["function2"]();
}

```

---

