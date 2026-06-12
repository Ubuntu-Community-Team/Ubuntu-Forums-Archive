---
title: "pthreads in classes - C++"
date: 2008-04-16
forum: Programming Talk
---

### Post by zenkaon on 2008-04-16
Hello all, I have decided to be adventurous and get into using threads so as to fully use my quad-core machine.

I have been looking at some example code and can get it to run. :)
The examples are limited however and I would like to allow one of my classes to manage the threading. Here is a rather simple piece of code that won't compile:

> #include <pthread.h>
#include <iostream>
using namespace std;

class g{

public:	
	g();
	~g();

	void* th_a(void* arg);
	void* th_b(void* arg);
};

g::g(){
   const int THREADS = 2;
   pthread_t thread[THREADS];
   int args[THREADS];

if(pthread_create(&thread[0], 0, th_a ,&args[0])){cerr<<"Bugged up thread"<<endl;exit(1);}
if(pthread_create(&thread[1], 0, th_b ,&args[1])){cerr<<"Bugged up thread"<<endl;exit(1);}	


	cout << "Now we are waiting for all to finish:" << endl;
for (int i = 0; i < THREADS; ++i) {
	int* resultp;
	if (pthread_join(thread[i], (void**) &resultp)) {
	cerr << "pthread_join failed, aborting!\n" << endl;
	exit(1);
	}
	cout << "Thread " << i << " finished. Got "
	<< *resultp << " as return value." << endl;
	}	
	
}

g::~g(){}

void* g::th_a(void* arg){
   	int number = *((int*) arg);
	for(int a=0;a<1000;++a){cout<<"Thread A "<<a<<endl;}
	return arg;
}

void* g::th_b(void* arg){
   	int number = *((int*) arg);
	for(int a=0;a<1000;++a){cout<<"Thread B "<<a<<endl;}
	return arg;
}

int main(){ 
	g* go=new g;
	delete go;
	return EXIT_SUCCESS;
}

The error I get is:
> -bash-3.00$ g++ -o go class.cpp -lpthread
class.cpp: In constructor `g::g()':
class.cpp:20: no matches converting function `th_a' to type `void*(*)(void*)'
class.cpp:11: candidates are: void* g::th_a(void*)
class.cpp:21: no matches converting function `th_b' to type `void*(*)(void*)'
class.cpp:12: candidates are: void* g::th_b(void*)


So it's a problem with the member functions I want to use for each of the threads. When I do this outside of a class environment, the code compiles and runs as you would expect.

Does anybody know what I'm doing wrong? I realise that I don't know how to define the member functions properly. Do you?

Cheers

---

### Post by heikaman on 2008-04-16
You're trying to use a member function as a call-back function of a thread.

First, you reference a member function with the scope resolution operator "::" like this:
[PHP]
 g::th_a
[/PHP]

Hence the errors :
[PHP]
class.cpp:11: candidates are: void* g::th_a(void*)
class.cpp:12: candidates are: void* g::th_b(void*)
[/PHP]

Second, this won't work because you can't use a member function as a call-back function of a thread. :) it's just not allowed.

Hence the errors:
[PHP]
class.cpp:20: no matches converting function 'th_a' to type 'void*(*)(void*)'
class.cpp:21: no matches converting function 'th_b' to type 'void*(*)(void*)'
[/PHP]

But there's a work around, you use another function like a proxy, like this:

[PHP]
class FooClass{
	friend void* proxy_function(void*);
private:	
	void create_thread();
	void thread_function();
};

void* proxy_function(void* foo_ptr){
	static_cast<FooClass*>(foo_ptr)->thread_function();
}

void FooClass::create_thread(){
	pthread_t thread;
	thread=pthread_create(&thread, NULL, proxy_function, this);
}
[/PHP]

---

### Post by WW on 2008-04-16
zenkaon: Instead of using the **quote** tag, use either **code** or **php** around your code.  These use a monospace font and preserve the indentation.

---

### Post by zenkaon on 2008-04-16
Thanks for your advice and hack heikaman. The function
```
void* proxy_function(void* foo_ptr)
```
looks like a global to me. Anything could call it. My whole OO philosophy of encapsulated objects with NO globals will be broken. 

Does the call-back function of a pthread have to be global?

If so, are there any other threading implementations that won't make me cry as I wreck my source and style.

WW - that's for the posting tip, hope this is better :)

---

### Post by heikaman on 2008-04-16
> 
The function
```
void* proxy_function(void* foo_ptr)
```
looks like a global to me.

It is global.

> 
Does the call-back function of a pthread have to be global?


Yes, to my knowledge.

> 
If so, are there any other threading implementations that won't make me cry as I wreck my source and style.


The only other solution/impelmentation "That I know of", is using sigc + glibmm threads, but I don't think you need this complexity, anyway, it goes like this:

[PHP]
my_thread=Thread::create(sigc::mem_fun(*this, &FooClass::thread_callback), true);
[/PHP]

Good luck. :)

---

### Post by WW on 2008-04-16
The function can be static.  For example,

**threadobj.h**
[php]
//
// threadobj.h
//

class threader
    {    
    public:
    threader(int *);
    ~threader();
    };
[/php]

**threadobj.cpp**
[php]
//
// threadobj.cpp
//

#include <pthread.h>
#include <iostream>

#include "threadobj.h"

using namespace std;


static void* worker(void* arg)
    {
    int number = *((int *) arg);
    for (int i = 0; i < 3; ++i)
        {
        cout << "worker: arg = " << number << endl;
        sleep(1);
        }
    return arg;
    }
    
threader::threader(int* p)
    {
    pthread_t thread;

    if (pthread_create(&thread, NULL, worker, (void *) p))
        {
        cerr << "Darn it!\n";
        exit(1);
        }
    }

threader::~threader()
    {
    }
[/php]

**threadmain.cpp**
[php]
//
// threadmain.cpp
//

#include <iostream>
#include "threadobj.h"

using namespace std;


int main()
    {
    int m1 = 100;
    int m2 = 200;
    int m3 = 300;
    int m4 = 400;
    cout << "main: creating th1\n";
    threader th1(&m1);
    cout << "main: creating th2\n";
    threader th2(&m2);
    cout << "main: creating th3\n";
    threader th3(&m3);
    cout << "main: creating th4\n";
    threader th4(&m4);
    cout << "main: sleeping...\n";
    sleep(5);
    cout << "main: done.\n";
    return 0;
    }
[/php]

Disclaimer: I haven't experimented much with threads, and I don't know what kind of "recommended practices" there are, if any.  Don't necessarily take this code as a good example of using threads.  I'm sure a more experienced thread programmer could recommend improvements.

---

### Post by dwhitney67 on 2008-04-16
You could also consider using the Boost libraries, thus obviating the need to interface directly with the pthread libraries.

A typical thread object definition could look like:
[PHP]class MyThread
{
  public:
    MyThread() {}

    // Thread main loop
    void operator() (void);
};[/PHP]

The implementation as:
[PHP]MyThread::operator() (void)
{
  // do something here
}[/PHP]

The main thread:
[PHP]#include "MyThread.h"
#include <boost/thread/thread.hpp>

int main( int argc, char **argv )
{
  MyThread mt;

  boost::thread *      myThread = new boost::thread( mt );
  boost::thread_group  threads;

  threads.add_thread( myThread );

  threads.join_all();

  return 0;
}[/PHP]

Compile with something like:
```
g++ MyThread.cpp Main.cpp -lboost_thread-mt
```

---

### Post by heikaman on 2008-04-16
Also openthreads "cross-platform, lightweight C++ thread API" is very good, and 
available in the repository.

here's a link to the documentation:
[http://stderr.org/doc/openthreads-doc/openthreads/annotated.html](http://stderr.org/doc/openthreads-doc/openthreads/annotated.html)

---

