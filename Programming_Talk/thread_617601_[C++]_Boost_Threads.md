---
title: "[C++] Boost Threads"
date: 2007-11-19
forum: Programming Talk
---

### Post by iharrold on 2007-11-19
I am trying to create a class that contains a std::list and a boost::thread.  I would like the thread maintenance function to be a class function and assign that function in the class constructor as such:
```
#include <list>
#include "frameobject.h"
#include <boost/thread/thread.hpp>

void hello();

class commandqueue
{
public:
    commandqueue();
    ~commandqueue();
    
private:
    void listmaintance();
    boost::thread* thrd;
    std::list<frameobject>* m_commandqueue;    
};

commandqueue::commandqueue()
{
    std::cout<<"Command Queue constructor called"<<std::endl;
    thrd = new boost::thread(&commandqueue::listmaintance);
    if(thrd != NULL)
    {
        thrd->join();
    }
    else
    {
        std::cout<<"Unable to allocate command thread\n";
    }
    
    m_commandqueue = new std::list<frameobject>;
    if(m_commandqueue == NULL)
    {
        std::cout<<"Unable to allocate command queue\n";
    }
};

commandqueue::~commandqueue()
{
    std::cout<<"Command Queue destructor called"<<std::endl;
    delete thrd;
    delete m_commandqueue;
};
      
void commandqueue::listmaintance()
{
  std::cout <<"Hello world, I'm a thread!"<< std::endl;
  //list maintance functionality
};
```

Is this even possible?  Is there a better approach to this?

I get the following errors:
> /usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/iharrold/UXC'
mkdir -p build/Debug/GNU-Linux-x86
g++ -lboost_thread   -c -g3 -gdwarf-2 -o build/Debug/GNU-Linux-x86/uxcmain.o uxcmain.cc
/usr/include/boost/function/function_template.hpp: In member function ‘bool boost::detail::function::basic_vtable0<R, Allocator>::assign_to(F, boost::detail::function::function_buffer&) [with F = void (commandqueue::*)(), R = void, Allocator = std::allocator<boost::function_base>]’:
/usr/include/boost/function/function_template.hpp:656:   instantiated from ‘void boost::function0<R, Allocator>::assign_to(Functor) [with Functor = void (commandqueue::*)(), R = void, Allocator = std::allocator<boost::function_base>]’
/usr/include/boost/function/function_template.hpp:513:   instantiated from ‘boost::function0<R, Allocator>::function0(Functor, typename boost::enable_if_c<boost::type_traits::ice_not<boost::is_integral<Functor>::value>::value, int>::type) [with Functor = void (commandqueue::*)(), R = void, Allocator = std::allocator<boost::function_base>]’
commandqueue.h:32:   instantiated from here
/usr/include/boost/function/function_template.hpp:284: error: no matching function for call to ‘boost::detail::function::basic_vtable0<void, std::allocator<boost::function_base> >::assign_to(void (commandqueue::*&)(), boost::detail::function::function_buffer&, boost::detail::function::member_ptr_tag)’
/usr/include/boost/function/function_template.hpp: In member function ‘void boost::detail::function::basic_vtable0<R, Allocator>::init(F) [with F = void (commandqueue::*)(), R = void, Allocator = std::allocator<boost::function_base>]’:
/usr/include/boost/function/function_template.hpp:277:   instantiated from ‘boost::detail::function::basic_vtable0<R, Allocator>::basic_vtable0(F) [with F = void (commandqueue::*)(), R = void, Allocator = std::allocator<boost::function_base>]’
/usr/include/boost/function/function_template.hpp:655:   instantiated from ‘void boost::function0<R, Allocator>::assign_to(Functor) [with Functor = void (commandqueue::*)(), R = void, Allocator = std::allocator<boost::function_base>]’
/usr/include/boost/function/function_template.hpp:513:   instantiated from ‘boost::function0<R, Allocator>::function0(Functor, typename boost::enable_if_c<boost::type_traits::ice_not<boost::is_integral<Functor>::value>::value, int>::type) [with Functor = void (commandqueue::*)(), R = void, Allocator = std::allocator<boost::function_base>]’
commandqueue.h:32:   instantiated from here
/usr/include/boost/function/function_template.hpp:298: error: no matching function for call to ‘boost::detail::function::basic_vtable0<void, std::allocator<boost::function_base> >::init(void (commandqueue::*&)(), boost::detail::function::member_ptr_tag)’
make[1]: *** [build/Debug/GNU-Linux-x86/uxcmain.o] Error 1
make[1]: Leaving directory `/home/iharrold/UXC'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.

---

### Post by c174 on 2007-11-19
Have a look at this thread, might help you

[http://ubuntuforums.org/showthread.php?t=615952]("http://ubuntuforums.org/showthread.php?t=615952")

---

### Post by aks44 on 2007-11-19
First off, this is C++ not C. **new** can (and will) throw, so better be prepared.
Anyway from your snippet you don't seem to need any dynamic allocation... *IF* you really do need dynamic allocation, use smart pointers (boost::scoped_ptr or std::auto_ptr) instead of raw, unguarded pointers.

Also, the boost::thread constructor takes a boost functor as a parameter (**const boost::function<void (void)>&**), see Boost.Functions (optionally using boost::bind) for the exact syntax. I very seldom use those so I guess you're better off on your own.


```
#include <list>
#include "frameobject.h"
#include <boost/thread/thread.hpp>

void hello();

class commandqueue
{
public:
    commandqueue();
    ~commandqueue();
    
private:
    void listmaintance();
    std::list<frameobject> m_commandqueue; // should be constructed before the thread
    // and destructed after the thread, hence the reordering
    boost::thread thrd;
};

commandqueue::commandqueue()
    : m_commandqueue(),
      thrd(/* provide a wrapper functor to listmaintenance */)
{
    std::cout<<"Command Queue constructor called"<<std::endl;
    thrd.join();
}

commandqueue::~commandqueue()
{
    std::cout<<"Command Queue destructor called"<<std::endl;
};
      
void commandqueue::listmaintance()
{
  std::cout <<"Hello world, I'm a thread!"<< std::endl;
  //list maintance functionality
};
```

---

### Post by c174 on 2007-11-19
@aks44:
I think the point in your code, where you put "/* provide a wrapper functor to listmaintenance */" is what is giving iharrold problems.

@iharrold:
You can ask for more help if you need it :) Did my previous post help anything?

---

### Post by aks44 on 2007-11-19
> **c174 said:**
> @aks44:
I think the point in your code, where you put "/* provide a wrapper functor to listmaintenance */" is what is giving iharrold problems.

I know. The thing is:
- in my post I made a point about something that was not asked (good RAII style),
- I gave to the OP all the information needed to find the relevant boost documentation by him/herself
- I am not willing to read those docs myself and "spoon-feed" the OP, even more when you know that I won't use this knowledge anytime soon...


So maybe my previous post was not *the* (predigested, as you seem to suggest?) answer the OP was expecting, but I'd bet it is indeed a step in the good direction.

Give a man a fish, etc etc... ;)

---

### Post by c174 on 2007-11-19
If I had the predigested answer I would give it :) But I agree that giving a fish etc is in general also very useful.

iharrold:
try to put "static" in front of "void listmaintance();" in the class definition. Pointers to member-functions are not allowed - unless the member is static.

I guess you want a new thread for each instance of "commandqueue"? It can be done, but the solution is more elaborate than the code you have now (for example let the static member function include another list and a switch)

---

### Post by iharrold on 2007-11-20
Thank you AKS and c174,  I really appreciate the feed back.  Putting static in front of the class function solved it and from a cursory run, seems to work.  Otherwise, I was thinking of overloading the () operator as shown in the example c174 linked too.  And in this example:
```
#include <boost/thread/thread.hpp>
#include <boost/thread/xtime.hpp>
#include <iostream>

struct thread_alarm
{
   thread_alarm(int secs) : m_secs(secs) { }
   void operator()()
   {
       boost::xtime xt;
       boost::xtime_get(&xt, boost::TIME_UTC);
       xt.sec += m_secs;

       boost::thread::sleep(xt);

       std::cout << "alarm sounded..." << std::endl;
   }

   int m_secs;
};

int main(int argc, char* argv[])
{
   int secs = 5;
   std::cout << "setting alarm for 5 seconds..." << std::endl;
   thread_alarm alarm(secs);
   boost::thread thrd(alarm);
   thrd.join();
}
```

Though, I must admit I don't fully understand the mechanism of why the struct and operator overload works like it does.  I assume the operator overload overides the construction of the alarm[struct] as it is being sent to the boost::thread utility function.  Or is it happening after the Join as part of the join"()"?  Thus the calling of the join "()" invokes the "()" operator which maintains the thread [in this case waiting for 5 seconds].


I'll more than likely have more issues later, since it has been nearly 4 years since I was coding last and I'm re-acquainting myself with it.

---

### Post by iharrold on 2007-11-20
So, I was experimenting in the "threadmaintance()" function by checking a boolean:
```
void commandq::commandqueue::listmaintance()
{
    while (!m_bisdestruct)
    {
        std::cout <<"Hello world, I'm a thread!"<< std::endl;
        sleep_seconds(1);
    }
  //list maintance functionality
};
```

sleep_seconds is just a wrapper around some boost thread sleep functionality to make it easier to use.  Anyways, I get the error:

> commandqueue.h: In static member function &#8216;static void commandq::commandqueue::listmaintance()&#8217;:
commandqueue.h:30: error: invalid use of member &#8216;commandq::commandqueue::m_bisdestruct&#8217; in static member function
commandqueue.cc:21: error: from this location

So slimply putting "static" didn't solve the problem, but merely hid the problem... atleast not allowing the functionality that I want because a "static" function can only access static variables or enums, etc..  I am hoping that someone can explain to me what I am missing here.  Particularly with the mechanism I posted in reply #7.

---

### Post by smartbei on 2007-11-20
Static member functions can only access static members - makes sense if you think about it. Just declare m_bisdestruct static and you should be good to go.

---

### Post by iharrold on 2007-11-20
> **smartbei said:**
> Static member functions can only access static members - makes sense if you think about it. Just declare m_bisdestruct static and you should be good to go.

Thanks smartbei, but I feel simply declaring everything as static is a band-aid approach.  There has to be a more oop approach to this that I am just not getting.

Edit:
So I was reading around the Boost library info and found this nugget:
> explicit thread(const boost::function0<void>& threadfunc);

Effects: 	Starts a new thread of execution and constructs a thread object representing it. Copies threadfunc (which in turn copies the function object wrapped by threadfunc) to an internal location which persists for the lifetime of the new thread of execution. **Calls operator() on the copy of the threadfunc function object in the new thread of execution.**
Postconditions: 	*this is joinable.
Throws: 	boost::thread_resource_error if a new thread of execution cannot be started.

So I feel I am getting closer with this code:
```
commandqueue::commandqueue() :
        m_commandqueue(),
        thrd(&commandqueue::listmaintance(this)),
        m_bisdestruct(false)    
{
    std::cout<<"Command Queue constructor called"<<std::endl;
    thrd.join();
};

void commandqueue::listmaintance(void * pThis)
{
    std::cout <<"Hello world, I'm a thread!"<< std::endl;
    commandqueue* pt = (commandqueue*)pThis;
    pt->workerfunction();
    //list maintance functionality
};

void commandqueue::workerfunction()
{
    while (!m_bisdestruct)
    {
        std::cout <<"Hello world, I'm a thread!"<< std::endl;
        sleep_seconds(1);
    }
  //list maintance functionality
};
```

What I am trying to do is pass in the reference to "this" to the thread maintance function and then immediatly call out to another commandqueue function that is non-static.  I get the following error however:
> commandqueue.cc: In constructor &#8216;commandq::commandqueue::commandqueue()&#8217;:
commandqueue.cc:11: error: invalid lvalue in unary &#8216;&&#8217;

so it appears that I cannot pass in "this".  But I am still confused on the () operator mechanism.

---

### Post by dwhitney67 on 2007-11-20
iHarold -

Here's an example I wrote a year ago when I was dabbling around with Boost threads.

main.cpp:
```
#include "Producer.h"
#include "Consumer.h"
#include <boost/thread/thread.hpp>


int main( int argc, char** argv )
{
  Producer producer( 10 );    // num messages to produce
  Consumer consumer( 5 );     // max idle cycles

  boost::thread* producerThread = new boost::thread( producer );
  boost::thread* consumerThread = new boost::thread( consumer );

  boost::thread_group threads;

  threads.add_thread( consumerThread );
  threads.add_thread( producerThread );

  threads.join_all();  // runs the threads!
}
```

Producer.h:
```
#ifndef PRODUCER_H
#define PRODUCER_H

class Producer
{
  public:
    Producer( int numMessages );

    virtual ~Producer();

    inline int getNumMessages() const
    {
      return numMessages;
    }

    void operator()(void);

  private:
    int numMessages;
};

#endif
```

Producer.cpp:
```
#include "Producer.h"
#include "Consumer.h"
#include "Message.h"

#include <boost/thread/thread.hpp>
#include <boost/thread/xtime.hpp>


Producer::Producer( int numMessages )
{
  this->numMessages = numMessages;
}

Producer::~Producer()
{
}

void
Producer::operator() (void)
{
  boost::xtime xt;
  boost::xtime_get( &xt, boost::TIME_UTC );
  xt.sec++;

  int val1 = 0;
  int val2 = 10;

  while ( numMessages-- )
  {
    Message* msg = new Message( val1++, val2-- );

    Consumer::insertMessage( msg );

    boost::thread::sleep( xt );
    xt.sec++;
  }
}
```

Consumer.h:
```
#ifndef CONSUMER_H
#define CONSUMER_H

#include <queue>

class Message;

typedef std::queue< Message* >  MessageQueue;

class Consumer
{
  public:
    Consumer( int maxIdleCycles );

    virtual ~Consumer();

    void operator() (void);

    static void insertMessage( Message* msg );

  private:
    static MessageQueue incoming;

    int maxIdleCycles;
};

#endif
```

Consumer.cpp:
```
#include "Consumer.h"
#include "Message.h"

#include <boost/thread/thread.hpp>
#include <boost/thread/xtime.hpp>
#include <iostream>

MessageQueue Consumer::incoming;


Consumer::Consumer( int maxIdleCycles )
{
  this->maxIdleCycles = maxIdleCycles;
}

Consumer::~Consumer()
{
}

void
Consumer::operator() (void)
{
  boost::xtime xt;
  boost::xtime_get( &xt, boost::TIME_UTC );
  xt.sec++;

  int idle = 0;

  while ( idle++ < maxIdleCycles )
  {
    if ( incoming.size() > 0 )
    {
      Message* msg = incoming.front();
      incoming.pop();

      std::cout << *msg << std::endl;

      delete msg;

      idle = 0;
    }
    else
    {
      std::cout << "Consumer is idle..." << std::endl;
    }

    boost::thread::sleep( xt );
    xt.sec++;
  }
}

void
Consumer::insertMessage( Message* msg )
{
  incoming.push( msg );
}
```

I've left out Message.h and Message.cpp.  For these, you can substitute your own.

To compile/link:

```
g++ <list all of .cpp files> -lboost_thread-mt -o threadTest
```


Btw, can somebody tell me if the STL queue container is thread-safe or not?

---

### Post by aks44 on 2007-11-21
> **dwhitney67 said:**
> the STL queue container is thread-safe or not?

Nope. C++ (and the whole STL) have not been designed with concurrent programming in mind, so you have to handle the synchronisations yourself.

---

### Post by dwhitney67 on 2007-11-21
Yep, you're correct.  I did a little research into some code used on a former project I supported.  The wrapper class for a priority-queue implementation relied on a wrapper class of the pthread condition, which in turn employs the use of a pthread mutex (of which there is a wrapper class for that).

---

### Post by iharrold on 2007-11-21
Thanks for the examples.  I think I am headed the wrong way in implementing it.  I'll look over the code you provided.  I am just used to grabbing and using pre-digested wrapper classes for easy usage on other projects and now I am developing it all from the ground up after a 4 year heitous.  So I'm trying to get back on the bicycle.  

Could someone please explain how the () operator overload mechanism is being used by the thread in the example you provided?  I don't mean, its what is being called by the thread to do the thread function ... I realize that.  I guess I am asking, how does mechanism occur.  Its probably not a quick and easy answer though and best for me dig around the code for a bit.

I do really appreciate all the help and suggestions everyone has provided to me.

---

### Post by iharrold on 2007-11-26
> **dwhitney67 said:**
> iHarold -

Here's an example I wrote a year ago when I was dabbling around with Boost threads.

Producer.cpp:
```
#include "Producer.h"
#include "Consumer.h"
#include "Message.h"

#include <boost/thread/thread.hpp>
#include <boost/thread/xtime.hpp>


Producer::Producer( int numMessages )
{
  this->numMessages = numMessages;
}

Producer::~Producer()
{
}

void
Producer::operator() (void)
{
  boost::xtime xt;
  boost::xtime_get( &xt, boost::TIME_UTC );
  xt.sec++;

  int val1 = 0;
  int val2 = 10;

  while ( numMessages-- )
  {
    Message* msg = new Message( val1++, val2-- );

    **Consumer::insertMessage( msg );**

    boost::thread::sleep( xt );
    xt.sec++;
  }
}
``` 


I had a question about the referencing of the Consumer thread from within the Producer thread.  How does the Producer know of Consumer?  Is it through the boost::thread_group?

Also the boost::thread::sleep seems to only allow sleeps in 1 second intervals.  Is there a method to sleep for shorter periods that is non-blocking?  I.e. 8 ms?

---

### Post by dwhitney67 on 2007-11-26
There are probably many ways for the Producer to know.  In my simple example, the Producer just "knows", not by any magic offered by Boost.

I could also have chosen to instantiate the Producer object with a reference to the Consumer object, which might have been a better design.  For example,

```
int main( int argc, char** argv )
{
  Consumer consumer( 5 );               // max idle cycles
  Producer producer( 10, consumer );    // num msgs to produce, and Consumer
  ...
```

Alternatively, I could have perhaps used a more elaborate Register object where the individual threads could register themselves, and thus use the Register object as a "middleman" for directing message traffic, sort of like a telephone operator in the days when manual switch-boards where used.

I'm sure there are other possibilities.  One of the most important aspects of s/w design are to keep things simple; it may sound like obvious advice, but it is amazing how many s/w developers implement the most complex code for something that otherwise should be simple to implement and easy to maintain.

I'm sure you will come up with something appropriate for your design.

As for your second question, I am not sure if Boost offers a high-resolution timer.  You could always implement your own, perhaps relying on select() or nanosleep() for your needs.

---

### Post by iharrold on 2007-11-26
Boost implies that it will offer higher resolution thread timers at a later date.

I do have another problem.  I am experimenting with your method of wrapping the class as a thread... actually using the () operator.  Anyways, the code you provided compiles just fine.  However, my code  errors while linking with:
> g++ -lboost_thread    -o dist/Debug/GNU-Linux-x86/uxc build/Debug/GNU-Linux-x86/uxcmain.o build/Debug/GNU-Linux-x86/frameobject.o build/Debug/GNU-Linux-x86/variabletext.o build/Debug/GNU-Linux-x86/commandqueue.o -L/usr/include/boost/thread 
build/Debug/GNU-Linux-x86/uxcmain.o: In function `main':
**/home/iharrold/UXC/uxcmain.cc:18: undefined reference to `commandq()'**

main.cc
```
#include <iostream>
#include <memory>
#include "commandqueue.h"
#include "frameobject.h"
#include <boost/thread/thread.hpp>

int main(int argc, char* argv[])
{
       CommandQueue commandq();
       
**       boost::thread* commandqueueThread = new boost::thread(commandq);**
       
       boost::thread_group threads;
       
       threads.add_thread(commandqueueThread);
       
       threads.join_all();
        
        return 0;
}
```

commandqueue.h
```
#ifndef _COMMANDQUEUE_H
#define	_COMMANDQUEUE_H

#include <list>
#include "frameobject.h"

typedef std::list<frameo::frameobject*> f_queue;

class CommandQueue
{
public:
    CommandQueue();
    ~CommandQueue();
    
    int getcommandqueuedepth() const
    {
        return m_commandqueue.size();
    }
        
    void operator() (void);
    
    void insertFrame(frameo::frameobject* newFrame);

private:
    void sleep_seconds( unsigned int nSeconds );
    static f_queue m_commandqueue;          
    bool m_bisdestruct;
};

#endif	/* _COMMANDQUEUE_H */
```

commandqueue.cc
```
#include <iostream>
#include <boost/thread/thread.hpp>
#include <boost/thread/xtime.hpp>

f_queue CommandQueue::m_commandqueue;

CommandQueue::CommandQueue() :
        m_bisdestruct(false)    
{
    std::cout<<"Command Queue constructor called"<<std::endl;
};

CommandQueue::~CommandQueue()
{
};

void CommandQueue::operator() (void)
{
    while (!m_bisdestruct)
    {
        if(m_commandqueue.size() > 0)
        {
            // there are objects in the command queue to be processed.
        }
        sleep_seconds(1);
    }
}


void CommandQueue::insertFrame(frameo::frameobject* newFrame)
{
    m_commandqueue.push_back(newFrame);
}

//A wrapper helper function for sleeping a thread for nSeconds seconds.
void CommandQueue::sleep_seconds( unsigned int nSeconds )
{
   boost::xtime xt;
   boost::xtime_get(&xt, boost::TIME_UTC);
   xt.sec += nSeconds; // change xt to next second
   boost::thread::sleep(xt);
} 
```

I am rather perplexed at this vague error.  I thought it was because of the virtual destructor,  But it is not.  Any ideas?

---

### Post by dwhitney67 on 2007-11-26
In the implementation file (the .cpp) for CommandQueue, I do not see that you have included the header file for commandqueue.h.

Could that be the problem?

---

### Post by iharrold on 2007-11-26
> **dwhitney67 said:**
> In the implementation file (the .cpp) for CommandQueue, I do not see that you have included the header file for CommandQueue.h.

Could that be the problem?

Sorry, cut and paste error.  It is there.  Also, if I change the line where I declare > CommandQueue commandq();
to> CommandQueue command1q();

I get the error that "commandq" is out of scope when I try to thread it on line 18.  So it is not an issue of the compiler not finding the object... but something with the initialization of the object perhaps?  or the () operator?  I'm grasping at straws as my code is nearly identical to yours other than the construction and yours compiles just fine.

EDIT:

So I changed main to:
```
CommandQueue commandq();
std::cout<<"depth = "<<commandq.getcommandqueuedepth()<<std::endl; 
```

And i get the error:
```
uxcmain.cc: In function &#8216;int main(int, char**)&#8217;:
uxcmain.cc:18: error: request for member &#8216;getcommandqueuedepth&#8217; in &#8216;commandq&#8217;, which is of non-class type &#8216;CommandQueue ()()&#8217;
make[1]: *** [build/Debug/GNU-Linux-x86/uxcmain.o] Error 1

```

So I do believe it is something with the object creation.  However, if I change the code to this in main with the boost::threads commented out it compiles and runs:
```
CommandQueue* commandq = new CommandQueue();
std::cout<<"depth = "<<commandq->getcommandqueuedepth()<<std::endl;
```

So this got me thinking and I changed the implementation in main too:
```

gint main(int argc, char* argv[])
{
       CommandQueue* commandq = new CommandQueue();
       
       std::cout<<"depth = "<<commandq->getcommandqueuedepth()<<std::endl;
       
       boost::thread* commandqueueThread = new boost::thread(*commandq);
       
       boost::thread_group threads;
       threads.add_thread(commandqueueThread);
       
       threads.join_all();
        
        return 0;
}

```

And it compiles and runs.  But I don't understand why.

---

### Post by dwhitney67 on 2007-11-26
In your main program, change to use the following declaration for commandq:

```
CommandQueue commandq;     // note that the () are not needed.
```

I was able to compile your code, using this command:

```
g++ commandqueue.cpp main.cpp -o cmdq -L/usr/include/boost/thread -lboost_thread
```

Note, I had to comment out the implementation and header files that you did not provide earlier.

---

### Post by iharrold on 2007-11-26
Ahhaha ... that worked aswell.  I think it was because my constructor didn't take in any values so the compiler was confused and calling the () operator versus the constructor perhaps?

---

### Post by aks44 on 2007-11-26
> **iharrold said:**
> Ahhaha ... that worked aswell.  I think it was because my constructor didn't take in any values so the compiler was confused and calling the () operator versus the constructor perhaps?

You're right, the compiler was confusing things, but not what you think...

See what the [C++ FAQ Lite]("http://www.parashift.com/c++-faq-lite/ctors.html#faq-10.2") has to say on that matter. ;)

---

### Post by dwhitney67 on 2007-11-26
iharrold -

I wanted to point out one more thing about your design; first it would be perhaps more appropriate to use STL queue than STL list for the f_queue.  Second, you will need to protect the f_queue when performing insert or retrieve operations; consider using a Boost mutex.  Please note that STL objects, including stream objects (e.g. cout, fstream, etc), are _not_ thread-safe.

P.S.  A *queue* operates on a FIFO basis, whereas a *list* need not be.  You can implement a *list* to behave as a *queue* if you want.

---

### Post by iharrold on 2007-11-26
> **dwhitney67 said:**
> iharrold -

I wanted to point out one more thing about your design; first it would be perhaps more appropriate to use STL queue than STL list for the f_queue.  Second, you will need to protect the f_queue when performing insert or retrieve operations; consider using a Boost mutex.  Please note that STL objects, including stream objects (e.g. cout, fstream, etc), are _not_ thread-safe.

P.S.  A *queue* operates on a FIFO basis, whereas a *list* need not be.  You can implement a *list* to behave as a *queue* if you want.

Good points, however command queue will be a priority queue such that I may push objects at different locations in the queue:
1) At the top (if highest priority)
2) Below the top (if high priority)
3) At the tail (if normal priority)

My intention is that that the Class will maintain and the queue (list).   I think using the list template will be easiest in the long run.

---

### Post by aks44 on 2007-11-26
> **iharrold said:**
> command queue will be a priority queue such that I may push objects at different locations in the queue:

Why reinvent the wheel when you have [std::priority_queue]("http://www.cplusplus.com/reference/stl/priority_queue/")? :p

---

### Post by dwhitney67 on 2007-11-26
It would appear that if one elects to use the priority_queue, then the context of the priority would have to be included _within_ the message being inserted onto the queue.  This may not be desirable.

---

### Post by aks44 on 2007-11-26
As far as I'm concerned, I'd rather throw in a small struct (priority / value / operator<) just for that purpose, rather than reimplementing the priority handling myself. YMMV though.

---

### Post by iharrold on 2007-11-26
> **aks44 said:**
> As far as I'm concerned, I'd rather throw in a small struct (priority / value / operator<) just for that purpose, rather than reimplementing the priority handling myself. YMMV though.

Ya, I just realized there was the priority_queue stl.  I'm going to change my code tomorrow morning to make use of it.    I have been away far too long from coding.

Thanks alot dwhitney67 and aks44 for helping me debug and use the boost::threads.  I really appreciate it.

---

### Post by iharrold on 2007-11-27
Ok, an update and a question on my logic.

So I reimplimented it as a priority queue.
```
typedef std::pair<frameobject, frame_priority> queue_obj;

typedef std::priority_queue<queue_obj, std::vector<queue_obj>, Prioritize> f_queue;
```

with Prioritize being:
```
#ifndef _PRIORITIZE_H
#define	_PRIORITIZE_H

#include "standardtypes.h"

class Prioritize
{
public:
    int operator() (const std::pair<frameobject, frame_priority> &p1,
                               const std::pair<frameobject, frame_priority> &p2)
    {
        if (p2.second == hot)
        {
            return 1;
        }
        else
        {
            return 0;
        }
    }
};


#endif	/* _PRIORITIZE_H */
```

So my question is this, frame_priority is an enum of "hottest, hot, normal".  Hottest is always put at the top no matter what.  Hot is put just below the top and normal is appended to the tail.  I will handle the "hottest" case seperately to ensure it is always ontop.  

However is this logic correct in your oppinion to keep a Hot priority item near the top and to append the normal priority to the bottom?  Or would it be simply:
```
return p1.second < p2.second;
```
Due to the enum being defined as Hottest = 2, Hot = 1, Normal = 0

---

### Post by aks44 on 2007-11-27
First off, your Prioritize::operator() should return a bool, not an int (not that it really matters, the int will be cast back to a bool anyway).

Now, the whole point of the 3rd template argument is to provide a LessThanComparable, which should behave just like operator< does on scalar types.
So yeah, IMO you'd better use < if you are sure that you'll always correctly maintain your enum values ("hottest" priorities always being higher enum values).

---

