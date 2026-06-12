---
title: "can a class member function be used as a thread routine?"
date: 2007-11-17
forum: Programming Talk
---

### Post by ibne.fazil on 2007-11-17
:cry::cry:Hello

I have to make a udp server in c++ to service multiple clients at a time.
For this i would create a thread for each arriving client using pthread_create() function. Can i use a class member function as a thread routine?

I tried it but it using g++ but it gave an error saying cannot convert 'CServer::' to 'void *(*)(void *)' 

Please help me on this!

I also tried to use an external function 'void * handler(void *)'which i defined in the header file of the class but when i compiled 'g++ -o k CServer.o main.o' it returned an error saying multiple definitions of 'handler(void *)'  :cry:

---

### Post by CptPicard on 2007-11-17
Seeing some code might help people help you... but off the top of my head, if using straight raw class member (static, in Java terms?) function doesn't work, you might just as well try wrapping the call by something that *does* work, that is, make your own wrapper function for the express purpose of calling YourClass::memberFunction().

---

### Post by DavidBell on 2007-11-17
> **ibne.fazil said:**
> Can i use a class member function as a thread routine?

Well, assuming pthread is the same as windows threads, the answer is no, because member functions have a hidden pointer to *this* prepended to start of their arguments, so the function signature doesn't match correctly.

However, at least in windows, you can get around it by declaring the member function as *static* which gets rid of the hidden *this*. (Cast the void* argument to *this* to get to member data if you need to).

HTH DB

---

### Post by ibne.fazil on 2007-11-17
I tried to use a wrapper function, but it dint work. My implementation was like this...

---------------------------------------------------------------------------
// Server.h

class CServer
{
          
};
CServer *obj;
void* Wrapper(void *arg)
{
         obj->HandleClient(arg);
         // HandleClient(void*) is the function that i want use as thread  
         //routine
}
---------------------------------------------------------------------------
// Server.cpp
#include "Server.h"

CServer::CServer()
{
         obj->this;
}
int HandleClient(void *arg)
{

}
----------------------------------------------------------------------------
// main.cpp

#include "Server.h"

int main(void)
{
       CServer s;
       ...
}

-----------------------------------------------------------------------------
Following two commands run fine...
g++ -c -I. Server.cpp
g++ -c -I. main.cpp

But when I put
g++ -o k -lpthread Server.o main.o

compiler gives an error, multiple definitions of function Wrapper(void*)

Please help me how can I remove this problem?
Thanx for ur answer...

Umar

---

### Post by dumbsnake on 2007-11-17
You must nest the functions you wish to use inside a class...  In general:

```

class myClass {

};

```

But mainly, I don't think you have ever written a working program in C++...  YOu might want to learn the language first a bit.  I'd recommend a book, but I might not be the best person to do that.  I believe there are several threads on the forums that will help you get started with C++.  Best of Luck.

---

### Post by ibne.fazil on 2007-11-17
oh yes i really need to learn it first... but the thing is, as it is clear, we cannot use a class member function as a thread routine, we have no other way than to make a wrapper function, which could be of course global. Therefore i wrote Wrapper(void) function with such intentions. 

Please tell me if this is not the correct way of writing a wrapper function, then what it is? I am sure it wouldnt be nested inside the class!

---

### Post by dumbsnake on 2007-11-17
Most thread libraries (if they take a function pointer) will want it to be of type int (*)(void *) which translates to a function like:

```

int new_thread_function(void *){
  // do whatever here
}

```

Then you pass the address of the function with whatever parameters you want in the void * argument as follows:

```

void *params;

(myclass *&)params = new myclass(9000, somevariable, "put", "your", "parameters", "here");

create_thread(&new_thread_function, params);

```

---

### Post by aks44 on 2007-11-18
> **ibne.fazil said:**
> ```
// Server.h

class CServer
{
          
};
CServer *obj;
void* Wrapper(void *arg)
{
         obj->HandleClient(arg);
         // HandleClient(void*) is the function that i want use as thread  
         //routine
}
---------------------------------------------------------------------------
// Server.cpp
#include "Server.h"

CServer::CServer()
{
         obj->this;
}
int HandleClient(void *arg)
{

}
----------------------------------------------------------------------------
// main.cpp

#include "Server.h"

int main(void)
{
       CServer s;
       ...
}
```

[...]

compiler gives an error, multiple definitions of function Wrapper(void*)

There is a rule in C++ :  the **One Definition Rule**. It means that a function or variable can be **defined** only once in the whole program, however you can **declare** it numerous times.

**declare** = make the prototype available (typically in headers)
**define** = make the implementation available (typically in units aka .cpp)


In your code, the definition of Wrapper() is in Server.h, which gets included by both Server.cpp and main.cpp.
As a result, Wrapper() is defined in *both* units, hence the "multiple definitions" error. Move the definition to either .cpp, and in the .h replace it by a declaration, and all will be fine.


You don't have a problem with pthreads, only a problem of _*basic*_ C++ syntax (not to mention the numerous other errors in the code you provided). I would strongly suggest that before messing with multithreading, you learn how C++ really works, otherwise you *will* screw up badly. Concurrent programming is a very advanced topic, definitely not for beginners. Just my 0.02...

---

### Post by uljanow on 2007-11-18
```
#include <cstdlib>
#include <pthread.h>

class foo {
	pthread_t tid;

	static void* run(void*)
	{
		// do something
		return NULL;
	}
public:
	void run()
	{
		if (pthread_create(&tid, NULL, foo::run, this))
			exit(-1);
	}
	void* join() 
	{
		void* ret;
		if (pthread_join(tid, &ret))
			exit(-1);
		return ret;
	}
};

int main()
{
	foo f;
	f.run();
	f.join();
}
```Here is an example. The real thread function is static. A better way would be to define an abstract class Runnable and let foo derive from that class (like in java).

---

