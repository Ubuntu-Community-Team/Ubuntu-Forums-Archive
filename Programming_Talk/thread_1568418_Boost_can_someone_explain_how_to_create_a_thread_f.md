---
title: "Boost: can someone explain how to create a thread for a class function?"
date: 2010-09-05
forum: Programming Talk
---

### Post by Swiftslide on 2010-09-05
I'm just learning boost and multithreading in general. In my project I have a class called "HarbourMaster" (it is a boat simulation), which needs to create three threads of functions that belong to it. The functions are named "passTime()", "checkLoadingBays()" and "checkUnloadingBays()".

I have tried to create these threads in several ways. The first is following the syntax provided in my reference material:


[INDENT]boost::thread timeThread(&passTime);
boost::thread lBaysThread(&checkLoadingBays);
boost::thread uBaysThread(&checkUnloadingBays);
[/INDENT] 
But the references seemingly don't apply for class functions; I get the following errors, once for each thread:

[INDENT][I]ISO  C++ forbids taking the address of an unqualified or parenthesized  non-static member function to form a pointer to member function.  Say  ‘&HarbourMaster::passTime’
  [/I][/INDENT] [INDENT]   [I]ISO C++ forbids taking the address of an unqualified or parenthesized  non-static member function to form a pointer to member function.  Say  ‘&HarbourMaster::checkLoadingBays’
ISO C++ forbids taking the address of an unqualified or parenthesized  non-static member function to form a pointer to member function.  Say  ‘&HarbourMaster::checkUnloadingBays[/I]’ 
  
 [/INDENT] 
So despite all my past experiences with the C++ compiler I decide to follow its advice:

[INDENT]boost::thread timeThread(&HarbourMaster::passTime);
boost::thread lBaysThread(&HarbourMaster::checkLoadingBays);
boost::thread uBaysThread(&HarbourMaster::checkUnloadingBays);
[/INDENT]  
 Of course, I get another error - though only one this time:

[INDENT][I]In file included from /usr/include/boost/thread/thread.hpp:22,
/usr/include/boost/thread/detail/thread.hpp:56: error: must use ‘.*’ or  ‘->*’ to call pointer-to-member function in  ‘((boost::detail::thread_data<void  (HarbourMaster::*)()>*)this)->boost::detail::thread_data<void  (HarbourMaster::*)()>::f (...)’, e.g. ‘(... ->*  ((boost::detail::thread_data<void  (HarbourMaster::*)()>*)this)->boost::detail::thread_data<void  (HarbourMaster::*)()>::f) (...)’[/I]
[/INDENT] 
I tried understanding this, but failed miserably. So I started messing  around trying random ways of writing the statement, looking at the  error, and trying to figure out what random way to try next. I've been  trying for forty-five minutes now and decided that it's rather  pointless. Could anyone please tell me how I'm supposed to create a thread? I would love you forever, but in a totally non-invasive way.

Thanks

---

### Post by dwhitney67 on 2010-09-05
Your thread class needs to be defined as a functor (function object).

For example:
```

class MyThread
{
public:
   MyThread() {}

   void operator()(void)
   {
      // do whatever here
   }
};

```

Then in your main thread:
```

MyThread mt1;
MyThread mt2;

boost::thread* bt1 = new boost::thread(mt1);
boost::thread* bt2 = new boost::thread(mt2);

boost::thread_group threads;
threads.add_thread(bt1);
threads.add_thread(bt2);

threads.join_all();

```
Of course, there are other spins on boost threads; thus far I have only experimented with code similar to what I have shown above.

---

### Post by dribeas on 2010-09-08
The boost threading library is designed to be quite flexible when used in combination with boost::bind. I cannot really point what the best solution would be without more knowledge of your domain, but here are a couple of the things that you can do with boost::thread.

You can create a thread that will execute a free function or a static member function of a class by passing the pointer to function directly to boost::thread:

```

void foo();
struct bar {
   static void foo();
   void g();
};
int main() {
   boost::thread thr1( &foo );
   boost::thread thr2( &bar::foo );
// boost::thread thr3( &bar::g ); [1]
}

```

The reason that you cannot pass a non-static member function is that non-static member functions are applied to an object, and you are not giving such an object to the boost::thread (nor you can directly).

You can pass in a functor to the thread and the boost thread will execute it (as in dwhitney67) answer:

```

struct functor {
   void operator()();
}; 
int main() {
   boost::thread thr( functor() );
}

```

Or you can use boost::bind to create a functor that adapt interfaces for you if you have some code that you want to call already written:

```

struct test {
   static void f( int );
   void g();
};
void f( double );
int main() {
   test t;
   boost::thread thr1( boost::bind( &test::f, 5 ) );   // run test::f( 5 )
   boost::thread thr2( boost::bind( &test::g, &t ) ); // run t.g()
   boost::thread thr3( boost::bind( &f, 10.5 );         // run f( 10.5 )
}

```

The boost::bind library basically creates a function object with one signature and then forwards the call to the binded element by injecting the extra arguments you provided in the bind call.

---

### Post by alatnet on 2010-09-09
I've havent had any luck with boost::thread but i did find resources on this problem.
The problem is that when you are passing a "class" method to boost::thread(), it doesnt like this cus the class method is also passing "this" as an extra argument to the additional arguments.

What i mean is that say you have a class method foo:
```
void foo() {}
```
you see that method foo has no arguments.  this isnt true for class methods because "this" is a hidden argument, so what you are really getting is:
```
void foo(class this) {}
```

To bypass this, create a static class method that accepts a "void *" argument and call that method within the static method:
```
void foo() {}
static void fooCaller(void *args){
  class* c = (class*)args;
  c->foo();
}
```

Then all you have to do is this:
```
class* c = new class();
boost::thread(class::fooCaller,(void*)c)
```

Please note that i dont know how to pass args to boost::thread so look up that and basicly do what i have above and it should work as expected.

---

### Post by dwhitney67 on 2010-09-09
You do not need to pass the object, whether it be the class or another object, as a void pointer.  Passing as itself would suffice; for example:
```

static void fooCaller(Class* c)
{
  c->foo();
}

```

---

### Post by alatnet on 2010-09-09
> **dwhitney67 said:**
> You do not need to pass the object, whether it be the class or another object, as a void pointer.  Passing as itself would suffice; for example:
```

static void fooCaller(Class* c)
{
  c->foo();
}

```
I guess... But isn't the function prototype in the form of "void (prototype*)(void *)" that has to be passed as the first argument to boost::thread()?

---

### Post by dwhitney67 on 2010-09-09
> **alatnet said:**
> I guess... But isn't the function prototype in the form of "void (prototype*)(void *)" that has to be passed as the first argument to boost::thread()?

The boost::thread constructor documentation can be referenced here:
[http://www.boost.org/doc/libs/1_38_0/doc/html/thread/thread_management.html#thread.thread_management.thread](http://www.boost.org/doc/libs/1_38_0/doc/html/thread/thread_management.html#thread.thread_management.thread)

Note the third constructor, that accepts a templated typename object (ie. class F), and additional args (ie. class A1, etc).

---

### Post by dribeas on 2010-09-09
> **alatnet said:**
> 
To bypass this, create a static class method that accepts a "void *" argument and call that method within the static method:
```
void foo() {}
static void fooCaller(void *args){
  class* c = (class*)args;
  c->foo();
}
```

Then all you have to do is this:
```
class* c = new class();
boost::thread(class::fooCaller,(void*)c)
```

Please note that i dont know how to pass args to boost::thread so look up that and basicly do what i have above and it should work as expected.

Or much simpler:
```

type obj;
boost::thread thr( boost::bind( &type::method, &obj ) );

```
No need to create the dispatcher static method manually.

---

### Post by alatnet on 2010-09-09
> **dwhitney67 said:**
> The boost::thread constructor documentation can be referenced here:
[http://www.boost.org/doc/libs/1_38_0/doc/html/thread/thread_management.html#thread.thread_management.thread](http://www.boost.org/doc/libs/1_38_0/doc/html/thread/thread_management.html#thread.thread_management.thread)

Note the third constructor, that accepts a templated typename object (ie. class F), and additional args (ie. class A1, etc).
Ah. ok.

---

