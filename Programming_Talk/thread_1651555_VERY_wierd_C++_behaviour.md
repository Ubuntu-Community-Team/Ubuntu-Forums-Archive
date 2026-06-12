---
title: "VERY wierd C++ behaviour"
date: 2010-12-23
forum: Programming Talk
---

### Post by PaulM1985 on 2010-12-23
Hi all

This problem is something I have found while using Windows and Visual Studio, so I accept that this is not the correct forum, but since I know you people are good I was hoping this is a C++ problem, rather than something windows based.

I originally had a CircularPatternProcedure class which inherited from a ComponentProcedure class.  Since I am going to add another type of circular procedure I have added an abstract CircularProcedure class, which inherits from the ComponentProcedure.  CircularPatternProcedure now inherits from CircularProcedure.

CircularPatternProcedure had a function "bool GetFeatures(List &list) const" which took a list and added the features to it, returning true if features existed.

I moved GetFeatures to the abstract class, since I want to use polymorphism.  I have labelled GetFeatures as virtual in both the abstract CircularProcedure class and the concrete CircularPatternProcedure class.

Here is my problem:
If I do
```

SomeOtherClass::SomeMethod(const CircularProcedure &circProc)
{
   List list;
   if (circProc.GetFeatures(list)) {
      ...
   }
}

```
The call on GetFeatures correctly calls the code on the CircularPatternProcedure, however when I do:
```

CircularPatternProcedure::Build()
{
   List list;
   if (GetFeatures(list)) {
      ...
   }

   ...
}

```

The call doesn't actually go to the GetFeatures function, it goes off to execute some other function in a different class ("Type Geometry2d::GetType() const", if you were wondering.)

Has anyone come across this before, and does anyone have any idea how to fix this?  Is this likely to be a compiler/OS specific problem and this forum is completely the wrong place for such a question?

I am afraid this is actual work stuff, so I can't post real code, I can only give an example of what I am doing.

Paul

---

### Post by MadCow108 on 2010-12-23
it actually calls a wrong function? did you test that with a debugger?
This in my experience indicates an abi conflict in a shared library, but this should not happen in this case.
but you can still try to relink all code and try again.

you could also try:
```

if (this->GetFeatures(list)) {

```
or (unlikely to help according to your description)
```

if ((GetFeatures(list))) {

```

---

### Post by PaulM1985 on 2010-12-23
> **MadCow108 said:**
> it actually calls a wrong function? did you test that with a debugger?


Yep, actually calls the wrong function.  I am stepping through the code with the debugger and when I step into the function in the first case it goes in and executes correctly and in the second case it goes to some wierd function in a different class.  I have already tried using Clean and Build on the entire solution and still get the same problem.

I will have a go of the "this->" and let you know what I find.

Paul

---

### Post by dwhitney67 on 2010-12-23
> **PaulM1985 said:**
> 
I am afraid this is actual work stuff, so I can't post real code, I can only give an example of what I am doing.

Paul

I'm afraid I do not exactly follow all that you described earlier; is it possible for you to correct the following code that I threw together based on my interpretation of your description.  Btw, the code below works as expected.
```

#include <iostream>

class ComponentProcedure
{
public:
   ComponentProcedure() {}
   ~ComponentProcedure() {}
};

class CircularProcedure : public ComponentProcedure
{
public:
   CircularProcedure() {}
   virtual ~CircularProcedure() {}

   virtual void getFeatures() const = 0;
};

class CircularPatternProcedure : public CircularProcedure
{
public:
   CircularPatternProcedure() {}
   virtual ~CircularPatternProcedure() {}

   void getFeatures() const { std::cout << "In CircularPatternProcedure::getFeatures()." << std::endl; }

   void build() { getFeatures(); }
};

class SomeOtherClass
{
public:
   SomeOtherClass() {}

   void someMethod(const CircularProcedure& circProc)
   {
      circProc.getFeatures();
   }
};

int main()
{
   CircularPatternProcedure cpp;
   cpp.build();

   SomeOtherClass soc;
   soc.someMethod(cpp);
}

```


P.S.  Is it possible that some other area within your code is trampling on the memory region where your CircularPatternProcedure object has been stored?

---

### Post by PaulM1985 on 2010-12-23
Thanks for the code sample dwhitney
I checked my code but that is the same thing that I am doing.  There must be something corrupting the memory somewhere else that I do not know about.

MadCow108, I tried you suggestion, but unfortunately that did not work either.

---

### Post by PaulM1985 on 2010-12-23
Another thing I have thought of that <may> be relevant, these classes are just an access layer.  The overall parent class just has a pointer to an entity and it is this entity that all derived classes make calls on.

So I can't think how the memory problem would apply since all of the derived classes would have the same size as the parent.  So adding a class to split the hierarchy would not make any difference to corrupt memory issues would it?

Sorry for not mentioning it sooner.

Paul

---

### Post by dwhitney67 on 2010-12-23
I was not trying to imply that the memory is being trampled on by your code re-factoring.  It could be affected by code that is in "left field".  I've seen anomalies like you describe in previous projects I've supported.

Look for areas in your entire application where memory is written to; there is probably something that is corrupting the heap (or stack).

Another alternative is to copy/paste pieces of your code into another project to see at what point the new code breaks.  It's tedious, but you might find this approach easier than hunting for an area where memory is being corrupted.

---

### Post by Arndt on 2010-12-23
Have you tried 'valgrind'?

---

### Post by PaulM1985 on 2010-12-23
> **dwhitney67 said:**
> I was not trying to imply that the memory is being trampled on by your code re-factoring.  It could be affected by code that is in "left field".

Winner from the left field.

The problem is because the call is done on a class which is an instance of something else higher up in the hierarchy (there is alot more of a tree than my original posts, I thought the problem was something trivial that I was doing wrong).  The way it is designed is that the virtual functions are defined on the data entity layer and these make calls onto non-virtual methods on the appropriate derived class on the access layer that the entity requires.  

I think this worked ok originally because none of the access layer classes had member variables and the only virtual functions existed in the top level base class.

The virtual functions where not defined in the higher up class so when the code was reaching the calls it was being sent off to strange memory areas.

Thanks for the help.

Paul

---

