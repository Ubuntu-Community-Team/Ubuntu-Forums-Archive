---
title: "multithreading and C++ in linux"
date: 2008-10-09
forum: Programming Talk
---

### Post by StOoZ on 2008-10-09
Hi,
I came a cross a problem , where multi-threading needs to take place (plz dont try to tell me that there are better ways...).
now , I know I can use pthread , which belongs to the linux API (?) , should I go with it , or look for a proper C++ threads libary?

are there any drawbacks in using pthread (since its written in C) in a C++ code?

---

### Post by dribeas on 2008-10-09
> **StOoZ said:**
> Hi,
I came a cross a problem , where multi-threading needs to take place (plz dont try to tell me that there are better ways...).
now , I know I can use pthread , which belongs to the linux API (?) , should I go with it , or look for a proper C++ threads libary?

are there any drawbacks in using pthread (since its written in C) in a C++ code?

I would recommend using one of the (portable) c++ libraries. I would go for boost::thread, some people recommend POCO, I use ACE (due to our dependency to TAO, that uses ACE internally) but I am considering moving to boost.

Most of these libs are wrappers around pthread --simple proof that you can use pthread directly-- but present it in a more C++ style. The drawback that using pthread directly has is that you will probably end up reinventing a C++ / class wrapper, and chances are you won't do it better than others did before.

---

### Post by StOoZ on 2008-10-09
I see , but what if my app doesnt need to be portable , will be used only under linux?

---

### Post by dribeas on 2008-10-09
> **StOoZ said:**
> I see , but what if my app doesnt need to be portable , will be used only under linux?

Same advice. Using the libs give you the extra portability advantage, but the main reason is not rewritting yet another-yet to be tested object wrapper around pthreads. That without considering the time spent in providing your own interface to pthread.

---

### Post by snova on 2008-10-09
C code works just fine from C++, assuming the headers are properly done. They usually are, including pthread.h. You don't need a C++ wrapper unless you think it'll be easier to use.

But if you're certain that portability isn't an issue, pthreads isn't the lowest level interface. You can always use Linux-specific functions such as fork(). In some cases, it might even be easier/simpler.

---

### Post by dribeas on 2008-10-09
> **snova said:**
> But if you're certain that portability isn't an issue, pthreads isn't the lowest level interface. You can always use Linux-specific functions such as fork(). In some cases, it might even be easier/simpler.

System call fork creates a processes, which are [different]("http://en.wikipedia.org/wiki/Multi-threading#Threads_compared_with_processes") to threads.

Whether you should or should not use a C++ thread library can end up in and endless discussion, so I will stop it just here. Below I provide three samples of code, with boost::thread, ACE and pthreads. With each of the libs three threads are created, one that calls a free function (pthread specialty), one that calls a member method that requires no arguments and another that calls a member method with an argument. The class X is assumed to be thread safe (there won't be a problem in creating various threads that work with the same instance). Now, it is up to you to decide. Disclaimer: I don't use pthreads, I used them time ago but that was long ago, so I cannot say that the pthread code is the best that can be done, but I don't think you could do it much simpler.

I previously posted an example of boost thread usage [here]("http://ubuntuforums.org/showthread.php?t=201776#4"), which I am copying (and updating with blue) below. As you can see it is simple and clean. You implement your algorithms/logic and then create a thread that will run them.
```

[COLOR="Blue"]#include <boost/bind.hpp>
#include <boost/thread.hpp>
[/COLOR]class X {
public: 
   void run();
   void complexOperation( int limit );
};

[COLOR="Blue"]void f();[/COLOR]

X x;
boost::thread thr1( boost::bind( &X::run, &x ) );
boost::thread thr2( boost::bind( &X::complexOperation, &x, 30 ) );
boost::thread thr3( boost::bind( &X::complexOperation, &x, 100 ) );
[COLOR="Blue"]boost::thread thr4( f );[/COLOR]
... // while threads work in background
thr1.join();
thr2.join();
thr3.join();
[COLOR="Blue"]thr4.join();[/COLOR]
```

With ACE it is a little more intrusive as to create threads you must inherit from a common base and then call activate() creating the new thread that will call a virtual svc method:
```

void f();
class Worker : public ACE_Task_Base
{
public:
	Worker( int limit ) : limit_( limit ) {}

	int svc()
	{
		run(); // same implementation as above, or:
*//		complexOperation( limit_ );* // or:
*//		f();*
	}	// thread dies when it exits svc method
	
	void run();
	void complexOperation( int limit );
private:
	int limit_;
};

int main() 
{
	Worker w(10);
	w.activate(); // creates thread that calls svc
	// ... 
	w.wait();
}

```

Note that as the signature of svc is fixed in the library, if you need to pass arguments to the method you will need to provide them either in the constructor or any other method of the class before you call activate().

Equivalent pthread code would be:

```

void f();
class X
{
public:
	X( int limit ) : limit_( limit ) {}
	int limit() const { return limit_; }

	void run();
	void complexOperation( int limit );
private:
	int limit_;
};
void proxy1( void * x )
{
	X* xptr = static_cast<X*>(x);
	xptr->run();
}
struct PData2
{
	X * xptr;
	int limit;
};
void proxy2( void * x )
{
	PData2* ptr = static_cast<PData2>( x );
	ptr->xptr->complexOperation( ptr->limit );
}
void proxy3( void * x )
{
	X * xptr= static_cast<X*>(x);
	xptr->complexOperation( ptr->limit() );
}
int main()
{
	X x(10);
	pthread_t thr[4];
	pthread_create( &thr[0], 0, proxy1, static_cast<void*>(&x) );
	
	PData2 d; d.xptr = &x; d.limit = 10;
	pthread_create( &thr[1], 0, proxy2, static_cast<void*>(&d) );

	pthread_create( &thr[2], 0, proxy3, static_cast<void*>(&d) );

	pthread_create( &thr[3], 0, f, 0 );

	for ( int i = 0; i < 3; ++i )
	{
		pthread_join( thr[i], 0 );
	}
}

```

You can see that calling a member function with pthread requires creating a free function (an static method would suffice) that takes the instance as argument and calls the method. If you want to provide arguments to the method you have to pass the arguments to the class beforehand (as in the ACE example, not replicated here) or else create a struct to hold both the pointer and the arguments and pass it to the proxy function.

For simple uses, where you call a free function boost and pthread solutions yield similar user code. If you just want to create a new class with a method then boost and ACE solutions are quite similar. Overall (in my opinion) boost yields the clearer simpler user code with the greater flexibility (when combined as above with boost::bind).

---

### Post by snova on 2008-10-09
Oops. Thanks for that.

Well, I'm pretty sure there's a low-level syscall for threading.

Oh! It's clone(). The manpage doesn't make it look easy, either...

I suggest sticking with pthreads, they're even somewhat portable (being POSIX). Or, if you're using a library such as Qt, use whatever facilities it provides instead, since it'll generally provide extra features useful in that particular library.

---

