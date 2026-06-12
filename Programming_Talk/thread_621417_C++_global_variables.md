---
title: "C++: global variables"
date: 2007-11-23
forum: Programming Talk
---

### Post by Rij on 2007-11-23
Hello,

I am struggling with a proper technique to use global variables in C++. I want to move away from the the C-style externs. I learnt static does the job, but is frowned upon. So, I need your help.

Ok, I want to maintain a global map and a couple of methods to operate on it. I decided not to make this a class since there will be just one instance of it that will be used by my other "threads".

So I have defined this:
```
#ifndef _global_
#define _global_
#include <map>
#include "module.h"

namespace Global {
  std::map<char, C_module*> ref_table;
  void some_operation() {
   }
}
#endif
```

Now, I have a base class called module defined as follows:

```
#ifndef module_h
#define module_h

//----------------------------------------------------------------------------

class C_module {
public:
    C_module();
    virtual ~C_module();
    virtual void push(Message *m) = 0;
};
//----------------------------------------------------------------------------

#endif
```

The idea is to create several derived classes from module, each running in a thread and asynchronously accessing Global.ref_table. One such, is the receiver class defined as follows:


```


#ifndef receive_h
#define receive_h

#include "global.h"
#include "module.h"
#include "common.h"

class C_receive : public C_module {

public:

    C_receive();
    ~C_receive();

	void operator()();
	void push(Message *);
};
#endif
//----------------------------------------------------------------------------

#include "receive.h"

C_receive::C_receive() {
}

C_receive::~C_receive() {
}

void C_receive::operator()() {
	cout << "I'm thread\n";
}

void C_receive::push(Message *m) {
}

//----------------------------------------------------------------------------
```

Then I have my main like this:

```
#include <boost/thread/thread.hpp>
#include "receive.h"

int main(int argc, char* argv[]) {
	C_receive receive; // Line 1
	boost::thread t1(receive); // Line 2
	t1.join();
	return 0;
}
```

This code compiles but while linking gives me this error:

ld: fatal: symbol `Global::ref_table' is multiply-defined:
        (file main.o type=OBJT; file receive.o type=OBJT);

How could this be when I have used #define in global.h?

I also have a thread specific question. I want to run receive as a thread. Boost.thread accepts a function object as an argument. Is a class considered a function object? Also, the thread constructor will not accept a pointer for example, boost::thread t1(new C_receive())

Any solutions around this?

Thanks, Rij

---

### Post by aks44 on 2007-11-23
> **Rij said:**
> I am struggling with a proper technique to use global variables in C++. I want to move away from the the C-style externs. I learnt static does the job, but is frowned upon. So, I need your help.

*Global variables* are what is really frowned upon. :p

> **Rij said:**
> This code compiles but while linking gives me this error:

ld: fatal: symbol `Global::ref_table' is multiply-defined:
        (file main.o type=OBJT; file receive.o type=OBJT);

How could this be when I have used #define in global.h?

Just a few hints...
- how do you define a variable?
- how do you declare a variable?
- what is a translation unit?
;)


> **Rij said:**
> Is a class considered a function object?
A class is NOT an object. A class is a "blueprint" for making objects. An instance of a class (ie. an object) can be a function object though depending on how the class is written.


> **Rij said:**
> Also, the thread constructor will not accept a pointer for example, boost::thread t1(new C_receive())

Any solutions around this?
Pass an object or a reference...



Your whole design is pretty unclear to me. What is the point of Global::ref_table? Is it supposed to be a "repository" of C_module objects so that you can dynamically allocate them, and access/free them later? If so, why should it be a global variable anyway? More info on what you want to do (and I really DON'T mean HOW you want to do it) would be welcome.


Also, don't forget that concurrent programming needs synchronization (I haven't seen any in your snippets).

---

### Post by Rij on 2007-11-23
Ok, I'll explain my objectives. 

My system has N independednt modules, and I want them to run as independent threads. Lets assume N=3 and the modules are A, B and C. They should be able to pass messages to each other. The messages are stored in a private data space (of the receiver) by the sender (by using a public method). The receiving thread, when notified, will wake up and process it.

That is broadly the objective. Since I am also trying to learn C++ principles, I want the whole design to be as loosely coupled as possible. So I want the receiver to obtain the reference to the sender dynamically.

Thanks for the heads up on synch. I will implement it once I have a basic structure in place. :)

---

### Post by dwhitney67 on 2007-11-23
Just so you are aware, when designing a multi-threaded application, all threads share the same program space.  Thus if you were to declare a global variable (btw, indicative of a bad design), then your all your threads, including the main thread, will have access to such.

You should concern yourself with protecting this variable from multiple "concurrent" accesses.  If you only have one CPU, then only one thread is executing at any given moment.  However, that does not mean a thread's critical section will run to completion.  It could be interrupted (by the CPU) so that other processes or another thread can run.  You need to ensure that data within the global variable is not accessed by more than one thread at a time.

I recently posted some code in another post concerning the Boost libraries.  You should look at that.  The only thing, as I was reminded, is that in the code I posted, the STL queue is not thread-safe.  I should have wrapped that object into a class that protects the queue with a pthread-mutex or Boost equivalent.

Anothed tidbit... always start the consumer thread before the producer is started.  And lastly, if you want to learn C++, skip the notion of multi-threading until you are fluent in C++.

---

### Post by aks44 on 2007-11-23
Again, global variables is a form of tight coupling. I guess you'd be better off passing the registry as a constructor argument and storing the reference, something along those lines:

```
class Registry
{
  // wrapper around your std::map
  // it should handle the synchronization itself
  // so its clients don't have to bother about it
};


class C_module
{
private:
  Registry& m_registry;
public:
  C_module(Registry& registry)
    : m_registry(registry)
  {
    m_registry.register(*this);
  }
  ~C_module()
  {
    m_registry.unregister(*this);
  }
};
```


This way you don't have to make your map global, it can perfectly be a local (stack) variable.

If you have a fixed number of modules, better allocate them statically too (ie. on the stack). This will save you many headaches.

You may want to factorize the threading code into C_command so that your derived modules have little or no management to do. Or perhaps have a separate class (which operates on a single C_command) handle that responsibility?

Also, modules should *not* talk to each other directly IMHO, the Registry should act as a mediator between them.

//-------------------------------------------------------------------------------------

From the top of my head, my best guess would be:
- class Registry: contains a list of AsyncOperation, handles all synchronization and acts as a mediator between all modules
- class AsyncOperation: handles the registration & threading details, bound at construction-time to a specific CommandInterface (and Registry, as shown above), could be a template class which also takes care of module instantiation
- class CommandInterface: abstract class that your modules will inherit of (the only concrete methods needed are a constructor to hook back to the Registry and/or AsyncOperation, and a virtual destructor)


This should result in something as simple as:

```
int main()
{
  Registry registry;
  AsyncOperation<SomeModule> someModule(registry);
  AsyncOperation<OtherModule> otherModule(registry);
  registry.run(); // launches all threads and joins them
  return 0;
}
```


Now if you *need* dynamic allocation, a factory would be the way to go:

```
int main()
{
  Registry registry;
  AsyncOperation<SomeModule>::create(registry);
  AsyncOperation<OtherModule>::create(registry);
  registry.run(); // launches all threads, joins them, and cleans up
  return 0;
}
```


Depending on your needs you may have to adjust the design, but I guess you get the big picture...



EDIT: dwhitney67's advices are quite worthy, especially the last one ("*if you want to learn C++, skip the notion of multi-threading until you are fluent in C++.*")... ;)

---

### Post by monkeyking on 2007-11-23
> **aks44 said:**
> *Global variables* are what is really frowned upon. :p

Actually I never understood why everybody hates global variabels.
I started my programming abilities in the functional programming world like mosml and haskell.

In these languages, no global variabels are possible. And it was annoying passing a variabel throug 8 different function calls, just for using it in the last.

So are there any really good reasons, for not using them?

I can understand arguments like "code is difficult to understand and debug...", but are there any effiency gains?

---

### Post by aks44 on 2007-11-23
> **monkeyking said:**
> Actually I never understood why everybody hates global variabels.

Global variables are Evil(tm) because they increase coupling, which strongly reduces code modularity, reusability and maintainability.

---

### Post by LaRoza on 2007-11-23
> **monkeyking said:**
> Actually I never understood why everybody hates global variabels.

So are there any really good reasons, for not using them?

I can understand arguments like "code is difficult to understand and debug...", but are there any effiency gains?

Hate is not an issue, the bugs they create are.

Use them, use them a lot, and any less than trivial program will get more buggy.

Yes, when a local variable goes out of scope, the memory is freed. Global variables are always there, and taking up memory and can be changed by any action.

If a variable is being passed to every (or almost every) function, having a global will save memory by avoiding the copying of that variable for every function. In C (and other languages) using references fixes this problem, so global variables aren't needed.

---

### Post by DavidBell on 2007-11-23
I don't think they are so bad as long as they are used with a bit of caution. I often define a global something like **gvSysData** that has various constants etc that are used a lot in the program but don't change much in themselves. 

Usually I do it as a class that might have some general functions as well. If you are doing this it's best to design the class so it is just as happy being instanced locally as it is globally, that way some of the reuse issues are not so bad.

I also have a couple of macros I use occasionally for setting up a file globals.h, doesn't always work brilliantly but helps sometimes

```

// you include globals.h in any .cpp where you need the variables
// but you define BCGLOBALMODULE in only one .cpp file

//then in globals.h something like

#ifdef BCGLOBALMODULE

	#define BCGLOBALVARIABLE(gTYPE, gNAME)	gTYPE gNAME;

	#define BCGLOBALVARIABLE_INIT(gTYPE, gNAME, gVALUE)	gTYPE, gNAME = gVALUE;

#else

	#define BCGLOBALVARIABLE(gTYPE, gNAME)	extern gTYPE, gNAME;

	#define BCGLOBALVARIABLE_INIT(gTYPE, gNAME, gVALUE)	extern gTYPE, gNAME;

#endif

BCGLOBALVARIABLE (bcAppData, gvAppData);

BCGLOBALVARIABLE_INIT (long, gvWhatever, 0);

// BCGLOBALVARIABLE_INIT works for simple classes too, 
// but more complicated ones you have to do manually

// etc


```

You don't ever really need globals I think, I just think they are convenient sometimes.

DB

---

### Post by dwhitney67 on 2007-11-23
Globals may be convenient, but their use strays from OOD.  Period.  I should further add, that if you take an OOD and implement it in C++, globals can be used... but its a bad idea.  In Java, you would be up the creek.


P.S.  My manager at work and your are two of a kind... you like to use prefix notation for your variable names.  Ugly!!!

---

### Post by tonyhawz on 2007-11-23
there is a design pattern for something like "global variables" , it is called Singleton
its basically a class that only will have one instance. 
The constructor is a private method and you will have the getInstance() method that will return the only instance of the class (it will create it if its not there and it will return it if no one used getInstance() before)
That class will have a static attribute in which store the only instance.

I hope it helps

---

### Post by dwhitney67 on 2007-11-23
You are right.  There is such a construct as a singleton object; however it is not intended to be the "kitchen sink" where you throw everything into it.

---

### Post by aks44 on 2007-11-23
There is yet another thing to keep in mind.

Global objects (or static ones? can't remember right now) are constructed upon first use. In multithreaded context, the construction of those global objects can be subject to race conditions, because C++ doesn't have built-in knowledge of concurrency. Such behaviour is simply not reliable, and there is barely anything one can do to prevent or work around it.
The singleton pattern is also broken in this case, for the same reasons.


AFAIK there is only one compiler that can handle a multithreaded singleton in a correct (yet non-standard) way: MSVC 8.0 thanks to its volatile keyword that is guaranteed to place the necessary memory barriers around the sensitive instructions. Unfortunately, even though it is a neat feature, one shouldn't rely on it because of the vendor lock in involved with a non-standard feature.

---

### Post by DavidBell on 2007-11-23
> **dwhitney67 said:**
> Globals may be convenient, but their use strays from OOD.  Period. ...
P.S.  My manager at work and your are two of a kind... you like to use prefix notation for your variable names.  Ugly!!!

I guess I use OOD as far as it suits me. My global classes tend be highly portable. Their clients may be more or less portable depending on what I judge to be their likelyhood of being re-used elsewhere. But my programs are just me, maybe I would be stricter if I was part of a group.

I don't go for the full hungarian notation thing, my prefixes are just two letters - first tells me the scope (global, file, member, local, argument, temp) second tells me if it is a variable, pointer or smartpointer. Just helps me remember a little bit with tidying up and so forth.

DB

---

### Post by dwhitney67 on 2007-11-23
> **aks44 said:**
> There is yet another thing to keep in mind.

Global objects (or static ones? can't remember right now) are constructed upon first use. In multithreaded context, the construction of those global objects can be subject to race conditions, because C++ doesn't have built-in knowledge of concurrency. Such behaviour is simply not reliable, and there is barely anything one can do to prevent or work around it.
The singleton pattern is also broken in this case, for the same reasons.

Have you verified this?

I have books that show the "traditional" way of implementing a singleton, where a pointer to the "self" object is declared private and initialized within a module.

For simplistic simpleton objects, this is an alternate approach:

```
class Singleton
{
  public:
    static Singleton& self()
    {
      static Singleton theInstance;
      return theInstance;
    }
    ...
};
```

This obviates the need to initialize a static pointer within a module, whether it be the implementation of a thread class or otherwise.

---

### Post by aks44 on 2007-11-24
> **dwhitney67 said:**
> Have you verified this?
Here are the results for the simple example you gave:
```
#include <iostream>

class Singleton
{
private:
  Singleton()
  {
    std::cout << "Singleton::Singleton()" << std::endl;
  }

public:
  static Singleton& getInstance()
  {
    static Singleton singleton;
    std::cout << "Singleton::getInstance()" << std::endl;
    return singleton;
  }

  void foo()
  {
    std::cout << "Singleton::foo()" << std::endl;
  }
};

int main()
{
  std::cout << "main()" << std::endl;
  Singleton::getInstance().foo();
  return 0;
}
``````
$ ./test
main()
Singleton::Singleton()
Singleton::getInstance()
Singleton::foo()
```

Clearly it wouldn't work well if subject to race conditions.

//-------------------------------------------------------------------------

Using a static variable initialized in the module:
```
#include <iostream>

class Singleton
{
private:
  static Singleton singleton;

  Singleton()
  {
    std::cout << "Singleton::Singleton()" << std::endl;
  }

public:
  static Singleton& getInstance()
  {
    std::cout << "Singleton::getInstance()" << std::endl;
    return Singleton::singleton;
  }

  void foo()
  {
    std::cout << "Singleton::foo()" << std::endl;
  }
};

Singleton Singleton::singleton;

int main()
{
  std::cout << "main()" << std::endl;
  Singleton::getInstance().foo();
  return 0;
}
``````
$ ./test
Singleton::Singleton()
main()
Singleton::getInstance()
Singleton::foo()
```

This would work, since the variable is constructed before entering main(). The thing that bothers me is that this code is subject to the C++ static initialization (dis)order problem (ie. there is no guarantee about the order in which the translation units will be initialized, leading to problems if a global variable depends on a global variable in another unit).
I tried with a pointer initialized in the module, and it works the same.

//-------------------------------------------------------------------------

After clearing the things up and searching more info, it appears that the behaviour I had in mind was a messy mix of local static variables and of the double-checked-lock idiom (which is broken in C++).

Proof is: when I don't use things for a long time, I tend to forget the details. :oops:

---

### Post by dwhitney67 on 2007-11-24
> **aks44 said:**
> Here are the results for the simple example you gave:
```
#include <iostream>

class Singleton
{
private:
  Singleton()
  {
    std::cout << "Singleton::Singleton()" << std::endl;
  }

public:
  static Singleton& getInstance()
  {
    static Singleton singleton;
    std::cout << "Singleton::getInstance()" << std::endl;
    return singleton;
  }

  void foo()
  {
    std::cout << "Singleton::foo()" << std::endl;
  }
};

int main()
{
  std::cout << "main()" << std::endl;
  Singleton::getInstance().foo();
  return 0;
}
``````
$ ./test
main()
Singleton::Singleton()
Singleton::getInstance()
Singleton::foo()
```

Clearly it wouldn't work well if subject to race conditions.

Can you explain how you feel this is "clearly" an example where a race condition would cause a problem?

I've used this technique on two separate projects that have employed multi-threaded applications, and never once was there a problem.  On the first project, the system had 4 CPUs, the second project only one CPU.

I'm not saying that your 2nd technique is worse, in fact it may be better, however unless I see proof that the first technique is flawed, I wouldn't knock it down.

Btw, it never prudent to use cout directly within a multi-threaded application.  It is not thread safe, and thus cannot be guaranteed to run to completion.

---

### Post by aks44 on 2007-11-24
> **dwhitney67 said:**
> Can you explain how you feel this is "clearly" an example where a race condition would cause a problem?
In this case, the object is constructed the first time it is used, after the program is started. If it may be used by several threads at once, there is no guarantee (as far as the standard goes) that the object can be correctly constructed under race conditions. I know that g++ by default ensures thread-safe construction of static variables (which can be disabled with -fno-threadsafe-statics), *but again this is _not_ C++ but a _vendor-specific_ feature one should not rely on if the program has to be even remotely portable*.


```
void getInstance()
{
  static Foo bar;
  // do stuff
}
```

In single-threaded context, calling getInstance() internally does something like:
- check if bar is constructed
- if not constructed, construct it
- do stuff

But if getInstance() gets called by several threads "at the same time", a race condition can happen between steps 1 & 2, and the static object would probably get corrupted by multiple concurrent constructions.

The only way to make that code truly thread safe is to ensure (ie. by calling getInstance() once) that the static object is fully constructed *before* starting multiple threads that may call getInstance().


> **dwhitney67 said:**
> I've used this technique on two separate projects that have employed multi-threaded applications, and never once was there a problem.  On the first project, the system had 4 CPUs, the second project only one CPU.
If you were using g++, you benefited from the feature I mentioned which makes static initializations thread safe.
If not, you either ensured the static object was constructed before going multi-threaded, or you were very unlucky not to have stumbled upon this case and have a bug lying somewhere.


> **dwhitney67 said:**
> I'm not saying that your 2nd technique is worse, in fact it may be better,
The second technique is indeed better, since the static objects get constructed *before* main() is executed. The only problem being that static initialization order is not specified in C++, so better not depend on a specific construction order for your program's correctness or else you're screwed.


> **dwhitney67 said:**
> Btw, it never prudent to use cout directly within a multi-threaded application.  It is not thread safe, and thus cannot be guaranteed to run to completion.
+1

---

### Post by Rij on 2007-11-24
Thanks everyone for some great discussion. While on the subject of static variables, I had a question. I realize static variables need to be defined before they can be used. What is the code to initialize a STL container, for example vector?

---

### Post by dempl_dempl on 2007-11-24
> **dwhitney67 said:**
> You are right.  There is such a construct as a singleton object; however it is not intended to be the "kitchen sink" where you throw everything into it.

Actually, you're wrong. 

In this particular case (thread) Singleton looks just like a solution.
Mayers Singleton , to be exact.

---

### Post by LaRoza on 2007-11-24
Post editing due to issue being resolved.

---

### Post by dempl_dempl on 2007-11-24
> **LaRoza said:**
> I think there more to a language than knowing who Alexandrescu is. 

Is a lack of knowledge in one area a reason to remove the "rights" of others? Everyone, including those he we do not discuss has a right to post on the forum as long as the code of conduct is followed, which are on the verge of breaching.

Please amend the post.

You were right, got little bit carried away :)   . Fixed .  It's 2 a.m here :)

---

### Post by LaRoza on 2007-11-24
> **dempl_dempl said:**
> You were right, got little bit carried away :)   . Fixed .  It's 2 a.m here :)

I know the feeling [noparse]:-)[/noparse] I have spend the last two nights (early mornings) on UF, and things often slip out.

---

### Post by dwhitney67 on 2007-11-24
> **Rij said:**
> Thanks everyone for some great discussion. While on the subject of static variables, I had a question. I realize static variables need to be defined before they can be used. What is the code to initialize a STL container, for example vector?

Header file:
```
#ifndef FOO_H
#define FOO_H

#include <vector>

class Foo
{
  public:
    // ...

  private:
    static std::vector< int > MyVector;
};

#endif
```

Implementation file:
```
#include "Foo.h"

std::vector< int > Foo::MyVector;

// ...
```

---

### Post by dwhitney67 on 2007-11-24
> **dempl_dempl said:**
> Actually, you're wrong. 

In this particular case (thread) Singleton looks just like a solution.
Mayers Singleton , to be exact.

Huh?  What am I wrong about?  Yes, I am aware that a Singleton object is a viable design pattern.  What I was saying that its use should not be abused to hold global variables; this would indicate a poor design that warrants refactoring.

A Singleton object should be used to model a one-of-a-kind object within a system, one where there would not need to be more than one instance.  I recommend you read this book... "Design Patterns" by Gamma, Helm, Johnson, and Vlissides.

---

### Post by the_unforgiven on 2007-11-25
> **aks44 said:**
> In this case, the object is constructed the first time it is used, after the program is started. If it may be used by several threads at once, there is no guarantee (as far as the standard goes) that the object can be correctly constructed under race conditions. I know that g++ by default ensures thread-safe construction of static variables (which can be disabled with -fno-threadsafe-statics), *but again this is _not_ C++ but a _vendor-specific_ feature one should not rely on if the program has to be even remotely portable*.


```
void getInstance()
{
  static Foo bar;
  // do stuff
}
```

In single-threaded context, calling getInstance() internally does something like:
- check if bar is constructed
- if not constructed, construct it
- do stuff

But if getInstance() gets called by several threads "at the same time", a race condition can happen between steps 1 & 2, and the static object would probably get corrupted by multiple concurrent constructions.

The only way to make that code truly thread safe is to ensure (ie. by calling getInstance() once) that the static object is fully constructed *before* starting multiple threads that may call getInstance().



If you were using g++, you benefited from the feature I mentioned which makes static initializations thread safe.
If not, you either ensured the static object was constructed before going multi-threaded, or you were very unlucky not to have stumbled upon this case and have a bug lying somewhere.



The second technique is indeed better, since the static objects get constructed *before* main() is executed. The only problem being that static initialization order is not specified in C++, so better not depend on a specific construction order for your program's correctness or else you're screwed.



+1

IIUC, a singleton in a multi-threaded code is more like a shared data structure. So, wouldn't it make sense to protect it with a lock/mutex?
So, even getInstance() can be written in such way that it tries to acquire the lock first and then initialize the static object completely.

Or, I could be completely wrong - please feel free to correct me :p

---

### Post by aks44 on 2007-11-25
> **the_unforgiven said:**
> IIUC, a singleton in a multi-threaded code is more like a shared data structure. So, wouldn't it make sense to protect it with a lock/mutex?
So, even getInstance() can be written in such way that it tries to acquire the lock first and then initialize the static object completely.

Access to the object may indeed need to be synchronized (or may not, if it is a constant object).

But access to the pointer (or reference) by no means needs to be synchronized. If it was, you'd end up with a costly (and useless) mutex acquisition every time you access that pointer/reference. The *_only_* thing that needs to be synchronized as far as getInstance() goes, is the construction itself of the object.

BTW this is the whole point of the double-checked-locking idiom (as originally intended): requiring a lock *only* during the object's construction. Unfortunately, for [various reasons]("http://www.ddj.com/184405726") this pattern is not thread safe.


As far as standard C++ goes, the only way to make a singleton thread safe in a portable yet efficient way is to ensure that the singleton object is already constructed _*before*_ it may be used by multiple threads. Once the object is fully constructed, the pointer won't be changed so it can handle concurrent reads without any need for synchronization.

---

