---
title: "[SOLVED] C++: How to pass a functor as a parameter?"
date: 2008-10-17
forum: Programming Talk
---

### Post by dwhitney67 on 2008-10-17
I know how to declare/implement a C++ functor object, but how does one declare a constructor method (in another class) that will accept a functor object as a parameter?

---

### Post by Lux Perpetua on 2008-10-17
Assuming the functors in consideration aren't of a fixed type, something like this may work:

```
#include <iostream>

using namespace std;

struct functor {
    int a;
    void operator () () const {
        cout << a << endl;
    }
};

class myclass {
public:
    template <typename F> myclass(const F & f) {
        f();
    }
};

int main(int argc, char **argv) {
    functor f = {5};
    myclass c(f);

    return 0;
}
```I like that because the call to functor::operator() will resolve at compile time. This isn't the only way to answer your question, so if this doesn't satisfy you, be more specific.

---

### Post by dwhitney67 on 2008-10-17
Thanks Lux Perpetua, however what I need is a class that can hold the functor, and that provides for delayed (as in later) execution.

So in essence I need to know how to store the functor reference.

I believe, but I cannot confirm, that the Boost thread library does something similar when constructing a thread.

For instance:
[php]
...

Functor f;

// define a thread
boost::thread* t1 = new boost::thread(f);

// create thread group and add thread(s)
boost::thread_group threads;
threads.add_thread(t1);

// Run thread(s)
threads.join_all();     // this is where the functor object is executed

...
[/php]
Now how do you surmise boost::thread() is "holding" onto that functor object?  The other thing that perplexes me is that boost::thread does not appear to be templated, but for all I know it is (similar to your example); but then how is it holding that functor?

---

### Post by dwhitney67 on 2008-10-18
Well, after doing a little research, I determined that it is possible to implement a class to hold a functor object, however I really never found out how.  :)

So I threw in the towel, and decided it would be more efficient and appropriate to use boost's function0.

So, I came up with the following:
[php]
#include <boost/function.hpp>
#include <iostream>

class MyFunctor
{
  public:
    void operator()(void)
    {
      std::cout << "MyFunctor is in action." << std::endl;
    }
};

class FunctorHolder
{
  public:
    FunctorHolder(const boost::function0<void>& functor)
      : m_functor(functor)
    {}

    void call() { m_functor(); }

  private:
    boost::function0 m_functor;
};

int main()
{
  MyFunctor mf;

  FunctorHolder fh(mf);

  fh.call();

  return 0;
}
[/php]

I'm moving on to bigger/better things.  This thread will be marked as solved.  Thanks Lux Perpetua for the effort/assistance you provided earlier.

---

### Post by Lux Perpetua on 2008-10-18
Hmmm. I'm not an expert on boost threads, but I did have a look at this: [http://www.boost.org/doc/libs/1_36_0/doc/html/thread/thread_management.html#thread.thread_management.thread](http://www.boost.org/doc/libs/1_36_0/doc/html/thread/thread_management.html#thread.thread_management.thread)

You're right: the thread class itself is not templated. However, the constructor is templated, and apparently the implementation copies the function object. I tried to produce the same functionality with an example. It's not pretty, and it has a lot of indirection, but here is *a* solution: ```
#include <iostream>

using namespace std;

struct myfunctor {
    int a;
    void operator () () const {
        cout << a << endl;
    }
};

class functor {
public:
    virtual void operator () () = 0;
    virtual ~functor() { }
};

template <typename F>
class functor_wrapper : public functor {
    F * p;
public:
    functor_wrapper(const F & f) {
        p = new F(f);
    }
    void operator () () {
        p->operator () ();
    }

    ~functor_wrapper() {
        delete p;
    }
};

class myclass {
    functor * p;
public:
    template <typename F>
    myclass(const F & f) { 
        p = new functor_wrapper<F>(f);
    }

    void test() {
        cout << "test..." << endl;
        p->operator() ();
    }

    ~myclass() {
        delete p;
    }
};

int main(int argc, char **argv) {
    myfunctor f = {5};
    myclass c(f);

    c.test();

    return 0;
}
```There should be a better way to do this, but I can't think of it off the top of my head. Note that you can simplify this a lot if you can make your functors themselves inherit from a common base class.

---

### Post by dwhitney67 on 2008-10-18
Thanks again Lux Perpetua...

The code definitely is not pretty, but nevertheless it was what I sought in the first place.

It would seem that the abstract class was the key to it all.  Without it, it would not have been possible to generically store, and call, the no-arg functor in the 'functor_wrapper'.

I guess a similar concept would have to be followed if one wants to implement 1-arg, 2-arg, etc functor handlers.

---

### Post by dribeas on 2008-10-20
> **dwhitney67 said:**
> 
So in essence I need to know how to store the functor reference.

I believe, but I cannot confirm, that the Boost thread library does something similar when constructing a thread.


Boost::Thread is templated. Not really if you look at the headers, but the effect is the same. Constructor is templated on the type of the argument (functor) and internally instantiates a templated class on that same type:

```

    struct xtime;
    class BOOST_THREAD_DECL thread
    {
//...
        template<typename F>
        struct thread_data:
            detail::thread_data_base
        {
            F f;

            thread_data(F f_):
                f(f_)
            {}
            thread_data(detail::thread_move_t<F> f_):
                f(f_)
            {}

            void run()
            {
                f();
            }
        };
//...
    public:
//...
        template <class F>
        explicit thread(F f):
            thread_info(new thread_data<F>(f))
        {
            start_thread();
        }
//...
    }

```

Now you see, thread class is not a template, but the constructor creates a thread_data<F> templated on the type of the functor. Note that the implementation of the functor holder makes a copy of the functor. There are some specializations on the other hand for boost::reference_holder so that you can avoid the functor copies and get a truly shared object.

Anyway, I recommend using already provided classes as boost::function (the generic boost::function<void ()> better than the more specific boost::function0<void>). Even if reading the code is always interesting.

---

### Post by DanIngold on 2008-11-05
I have a similar problem of passing a functor as a parameter, and used the ideas in this thread as a starting point.  They seem unnecessarily complex with the double indirection, however, and leave some other polymorphism issues unresolved.  This is an attempt to simplify and generalize.  

To recap the problem, it appears impossible to call a virtual operator() method on a functor, through an abstract base class.  In my case, I wanted to create a runtime-selectable BinOp to use with std::accumulate.  The issue seems to be that in this case (at least) operator() must be resolvable at compile time, which a virtual call by definition is not.  

The solution is to embed the functor in a non-virtual wrapper, whose operator() method *is* resolvable at compile time.  Since the code below defines a BinOp, it has template parameters that the original example, which defined a void, parameter-less method, could omit.  
 
```

// Here is the functor ABC, in this case a BinOp.  Note that it 
// defines the operator() as virtual, which is necessary to get a
// run-time selectable concrete instantiation of some particular
// BinaryFunctor, like the SumFunctor defined later in this
// example. 

template < typename T1, typename T2 >
class BinaryFunctor
{
public:
    typedef CountedPtr< BinaryFunctor >     Ptr;

    virtual T1  operator() ( T1 value1, T2 value2 ) const = 0;

    virtual ~BinaryFunctor()                    { }
};


// The wrapper is non-virtual, which allows its operator() to be
// resolved at compile-time.  The wrapper defines a reference-
// counted pointer to the ABC, which at run-time holds a reference
// to the desired concrete functor.  When this wrapper's 
// non-virtual (and compile-time resolvable) operator() is called 
// at run-time, it makes a virtual call to the concrete functor's 
// operator().  

template < typename T1, typename T2 >
class BinaryFunctorWrapper
{
public:
    BinaryFunctorWrapper( BinaryFunctor< T1, T2 > * functor ) :
        pFunctor_( functor )
    {
    }

    T1  operator() ( T1 value1, T2 value2 )          
    {
        return pFunctor_-> operator()( value1, value2 );
    }

private:
    BinaryFunctor< T1, T2 > :: Ptr      pFunctor_;
};


// The concrete functor class, in this example a simple summer.

class SumFunctor : public BinaryFunctor< double, double >
{
public:
    double   operator() ( double value, double obj ) const
    {
        return value + obj;
    }
};


// The server class, which uses an run-time defined functor.

class Server
{
public:
    // The parameters and return type of the functor must be
    // defined at run-time, which this typedef just simplifies the
    // declaration of.  The operator() of the concrete functor
    // must match this signature, and can be of any class derived
    // from BinaryFunctor.  

    typedef BinaryFunctorWrapper< double, double >    ValueFunctor;

    Server( const ValueFunctor & valueFunctor ) :
        valueFunctor_( valueFunctor )               { }

private:
    ValueFunctor    valueFunctor_;
}; 


int main( int argc, char ** argv )
{
    Server   s( Server::ValueFunctor( new SumFunctor ) );

    // call some method in s that uses the functor...
}

```

The simplification here (such as it is) is that Server calls the non-virtual operator() in the wrapper -- no further indirection is needed, unlike *myclass* in the previous example.  Since the wrapper is concrete, it can be instantiated directly in Server and need not be a reference.  By using a reference-counted pointer to the concrete functor, the wrapper releases its storage when the wrapper is destroyed.  (I didn't define the reference-counted pointer here, though both Boost and Josuttis provide examples.)  

The wrapper is passed a pointer to the concrete functor, rather than a reference, because it knows only the ABC type.  It cannot allocate a *new* copy of the ABC, and if it knew which concrete functor were being used, it would no longer be general. 

I hope this long-winded explanation gives a simpler and more general example.  Thanks!

--Dan

---

### Post by dribeas on 2008-11-06
> **DanIngold said:**
> I have a similar problem of passing a functor as a parameter, and used the ideas in this thread as a starting point.  They seem unnecessarily complex with the double indirection, however, and leave some other polymorphism issues unresolved.  This is an attempt to simplify and generalize.

Before discussing the pros and cons of the code you present, I must start stating that you are providing a specific solution to just a subset of the initial problem: that of the functors for which you can implement an inheritance relationship. And I am not discussing the cases where you do not want to use inheritance for other issues.

This restricts the set of 'functors' that you can use in your system. You cannot use function pointers, or binding libraries like boost::bind or boost::lamda::bind to reuse an existing class implementation. Nor can you use boost::lambda to generate unnamed functor types to use in your code, or functor libraries like boost::function. I don't know your experience or whether this rings a bell or not, so I will provide an example:

Given a class X, with a member function f that takes two double arguments and returns a double, with your solution the user must implement a functor wrapper that takes a reference to an object of type X and calls f(a,b) in its operator() implementation. None of those libraries will inherit from your base class. You must provide the adaptor for each and every class/method that you want to call in your Server class.

With the general (and more complex solution above) you can fall back into using the provided libraries with user code similar to this:
```

class X { ... }; // provides method: double f( double, double ) and double g( std::string const &, double, double )
int main()
{
   X x;
   Server s1( boost::bind( &X::f, &x, _1, _2 ) ); // will call method f
   Server s2( boost::bind( &X::g, &x, "hi", _1, _2 ) ); // will call method g, adding a "hi" first parameter during the call
}

```

Compare the simplicity of library built functors like above with the boiler plate code you will need to adapt just the first call:

```

class X_f_adaptor : public functor_base
{
public: 
   X_f_adaptor( X & x ) : x_(x) {}
   double operator()( double a, double b )
   {
      return x_.f( a, b );
   }
private:
   X & x_;
};
class X_g_adaptor : public functor_base // repeat equivalent code for g

```

Now, lets focus on your code sample:

> **DanIngold said:**
> To recap the problem, it appears impossible to call a virtual operator() method on a functor, through an abstract base class.  In my case, I wanted to create a runtime-selectable BinOp to use with std::accumulate.  The issue seems to be that in this case (at least) operator() must be resolvable at compile time, which a virtual call by definition is not.  

This paragraph, and the first after the code make me think that you may have a misunderstanding on how polymorphism works in C++. You cannot access polymorphic behavior through objects of the base class created by copying from a derived class. That is in fact a problem as you will be slicing the original object (keeping only the shared part, with the behavior of the base). To use polymorphism you need either references or pointers.

Virtual functions are always resolved at compile time, the compiler creates a virtual method table for the class, with pointers to the virtual methods. A call to a virtual method is translated into a call to the method pointed by the nth element in the virtual method table. During compilation, the pointer is an unknown variable. When you instantiate an object of a derived class at runtime, the compiler change the virtual method table of the object, so that the pointer goes to the most derived implementation provided. After that happens, during runtime, calls made through the virtual table (all virtual method calls) achieve polymorphic behavior.

This means that you don't need to wrap your functor/or any other bas class to achieve polymorphism, you can just store a pointer (usually in a smart pointer, let it be std::auto_ptr<>, boost::shared_ptr<>...) and you can remove the *Wrapper class from your code.

> **DanIngold said:**
> 
The solution is to embed the functor in a non-virtual wrapper, whose operator() method *is* resolvable at compile time.  Since the code below defines a BinOp, it has template parameters that the original example, which defined a void, parameter-less method, could omit.  


There is no need to embed the fucntor in a wrapper, it can be held by pointer/reference with the same result (changes highlighted in blue):
 
```

[COLOR="Blue"]// This could use a third type parameter as std::binary_function does to hold return type[/COLOR]
template < typename T1, typename T2 >
class BinaryFunctor
{
public:
    virtual T1  operator() ( T1 value1, T2 value2 ) const = 0;
    virtual ~BinaryFunctor()                    { }
};

// The concrete functor class, in this example a simple summer.
class SumFunctor : public BinaryFunctor< double, double >
{
public:
    double   operator() ( double value, double obj ) const
    {
        return value + obj;
    }
};

[COLOR="Blue"]// changed to hold by pointer:[/COLOR]
class Server
{
public:
    typedef BinaryFunctorWrapper< double, double >    ValueFunctor;

    Server( ValueFunctor [COLOR="Blue"]*[/COLOR] valueFunctor ) :
        valueFunctor_( valueFunctor )               { }

private:
    [COLOR="Blue"]std::auto_ptr<ValueFunctor>[/COLOR]    valueFunctor_;
}; 


int main( int argc, char ** argv )
{
    Server   s( new SumFunctor ); [COLOR="Blue"]// removed wrapper[/COLOR]

    // call some method in s that uses the functor...
}

```

> **DanIngold said:**
> The simplification here (such as it is) is that Server calls the non-virtual operator() in the wrapper -- no further indirection is needed, unlike *myclass* in the previous example.  Since the wrapper is concrete, it can be instantiated directly in Server and need not be a reference.

You are still holding by pointer (or reference if you wished), just one level deeper inside the wrapper. The wrapper, that is not even needed, is held by value, but the real functor is still held by pointer.

> **DanIngold said:**
> By using a reference-counted pointer to the concrete functor, the wrapper releases its storage when the wrapper is destroyed.  (I didn't define the reference-counted pointer here, though both Boost and Josuttis provide examples.)

That is a good design choice, pointers should be held inside smart pointers whenever possible. In this case, as only Server has access to the newly created functor you can use a plain std::auto_ptr<> for the task.  

> **DanIngold said:**
> The wrapper is passed a pointer to the concrete functor, rather than a reference, because it knows only the ABC type.  It cannot allocate a *new* copy of the ABC, and if it knew which concrete functor were being used, it would no longer be general.

Anything you can do with a pointer can be done with a reference. You are problably talking about holding the instance (and not a reference) of the functor.

> **DanIngold said:**
> I hope this long-winded explanation gives a simpler and more general example.  Thanks!

--Dan

While I disagree that your solution is more general --it is not-- it is a good step and source for discussion of the implications of design choices.

---

### Post by DanIngold on 2008-12-01
Actually, yes, I was "providing a specific solution" -- that is, a simplification of the proposed solution to the original question:

> **dwhitney67 said:**
> ...how does one declare a constructor method (in another class) that will accept a functor object as a parameter? 

The solution proposed by Lux Perpetua was, in my opinion, more complex than necessary, due to its use of double indirection.  The solution I proposed achieves the same functionality, somewhat more simply.  

It's not clear that your earlier response actually suggests a solution, though you do allude to one.  Your solution in the response to my post is certainly clever, however, although perhaps more general than what dwhitney67 asks.

---

