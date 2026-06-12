---
title: "Array of functions pointers... C++ compile error."
date: 2008-12-18
forum: Programming Talk
---

### Post by iharrold on 2008-12-18
I am trying to assign an array of function pointers to the same location as an enum so that I can simply call the array with the enum position to go to the correct function without having to do alot of if/else statements or switches.

I am using the Poco Library. The array of function pointers are defined as:
```

Poco::Logger*            m_pfilelogger; 
void (* m_pfilefuncarray[9])(const std::string &);
```

And I am trying to assign a function to the position via:
```
void cLogger::setupfunctiontable()
{
    if(m_pfilelogger && m_pfcconsole)
    {
        m_pfilefuncarray[Message::PRIO_FATAL] = &(m_pfilelogger->fatal);
        
    }
}
```

According to the [Poco::logger ]("http://pocoproject.org/poco/docs/Poco.Logger.html")class definition fatal is defined as:
```

void fatal( const std::string & msg );

and 

bool fatal() const;

```

obviously I want the first option.  My compile error is:
../src/Main_App/Logger/Logger_setupfunctiontable.cpp: In member function &#8216;void ProWrite::cLogger::setupfunctiontable()&#8217;:
../src/Main_App/Logger/Logger_setupfunctiontable.cpp:9: error: no matches converting function &#8216;fatal&#8217; to type &#8216;void (*)(const struct std::string&)&#8217;
/Libraries/IA32/include/Poco/Logger.h:379: error: candidates are: void Poco::Logger::fatal(const std::string&)
/Libraries/IA32/include/Poco/Logger.h:433: error:                 bool Poco::Logger::fatal() const
make: *** [src/Main_App/Logger/Logger_setupfunctiontable.o] Error 1

Any help would be greatly appreciated.  Thanks!

---

### Post by bapoumba on 2008-12-18
Moved to PT.
(hoping this is not for a class assignment..).

---

### Post by tyfius on 2008-12-18
> **bapoumba said:**
> Moved to PT.
(hoping this is not for a class assignment..).[Off Topic]Is that so bad? Even if it is homework the OP at least made an effort and provided some examples. If you want to forbid any homework related stuff, even if it's well explained and documented, you'd be better off closing this section of the forums because there is no way to tell if something is a homework assignment or not.[/Off Topic]

OP: try removing the & sign when you assign and see if that helps.

---

### Post by bapoumba on 2008-12-18
> **tyfius said:**
> [Off Topic]Is that so bad? Even if it is homework the OP at least made an effort and provided some examples. If you want to forbid any homework related stuff, even if it's well explained and documented, you'd be better off closing this section of the forums because there is no way to tell if something is a homework assignment or not.[/Off Topic]

No it is not so bad. That is why I put the remark as a note. But we do not allow plain and simple homework questions, and asking for hints is fine.
The thread is still open, as you can see :)

---

### Post by dwhitney67 on 2008-12-18
> **iharrold said:**
> I am trying to assign an array of function pointers to the same location as an enum so that I can simply call the array with the enum position to go to the correct function without having to do alot of if/else statements or switches.

I am using the Poco Library. The array of function pointers are defined as:
```

Poco::Logger*            m_pfilelogger; 
void (* m_pfilefuncarray[9])(const std::string &);
```

And I am trying to assign a function to the position via:
```
void cLogger::setupfunctiontable()
{
    if(m_pfilelogger && m_pfcconsole)
    {
        m_pfilefuncarray[Message::PRIO_FATAL] = &(m_pfilelogger->fatal);
        
    }
}
```

According to the [Poco::logger ]("http://pocoproject.org/poco/docs/Poco.Logger.html")class definition fatal is defined as:
```

void fatal( const std::string & msg );

and 

bool fatal() const;

```

obviously I want the first option.  My compile error is:
../src/Main_App/Logger/Logger_setupfunctiontable.cpp: In member function ‘void ProWrite::cLogger::setupfunctiontable()’:
../src/Main_App/Logger/Logger_setupfunctiontable.cpp:9: error: no matches converting function ‘fatal’ to type ‘void (*)(const struct std::string&)’
/Libraries/IA32/include/Poco/Logger.h:379: error: candidates are: void Poco::Logger::fatal(const std::string&)
/Libraries/IA32/include/Poco/Logger.h:433: error:                 bool Poco::Logger::fatal() const
make: *** [src/Main_App/Logger/Logger_setupfunctiontable.o] Error 1

Any help would be greatly appreciated.  Thanks!

To the best of my knowledge, you will not be able to store the address of the 'fatal' method as you are attempting.

What are you attempting to set up anyways?  An array of callback methods?

In C++, one way to setup a callback, is to use an instance of the object, and the address of the method you are interested in storing.

Here's a drawn-out coding example that you can play with:
[php]
#include <string>
#include <vector>
#include <iostream>

namespace Poco
{
class Logger
{
  public:
    void fatal(const std::string& msg)
    {
      std::cout << msg << std::endl;
    }

    void fatal() const
    {
    }
};
}


template <class T>
class Callback
{
  public:
    typedef void (T::*Function)(const std::string&);

    Callback(T* instancePointer, Function functionPointer)
    {
      m_instance = instancePointer;  // the object that defines the function
      m_function = functionPointer;  // the function
    }

    Callback(const Callback<T> &other)
    {
      m_instance = other.m_instance;
      m_function = other.m_function;
    }

    void execute(const std::string& msg) const
    {
      (m_instance->*m_function)(msg);
    }

  private:
    T *      m_instance;
    Function m_function;
};


struct Handler
{
  Handler(Callback<Poco::Logger> cb)
    : callback(cb)
  {
  }

  Callback<Poco::Logger> callback;
};


int main()
{
  std::vector<Handler> callbacks;

  Poco::Logger* logger = new Poco::Logger();

  callbacks.push_back(Handler(Callback<Poco::Logger>(logger, &Poco::Logger::fatal)));

  callbacks[0].callback.execute("Death becomes us.");

  return 0;
}
[/php]

There are other alternatives available to you, such as the Boost library's bind functions, but I have only used it to bind free-floating functions, not those in a class.  Maybe with luck, **dribeas** will weigh in and assist you with Boost.

---

### Post by Lux Perpetua on 2008-12-18
> **iharrold said:**
> 
```

Poco::Logger*            m_pfilelogger; 
void (* m_pfilefuncarray[9])(const std::string &);
```

And I am trying to assign a function to the position via:
```
void cLogger::setupfunctiontable()
{
    if(m_pfilelogger && m_pfcconsole)
    {
        m_pfilefuncarray[Message::PRIO_FATAL] = &(m_pfilelogger->fatal);
        
    }
}
```You can't do that: C++ doesn't have closures.

---

### Post by iharrold on 2008-12-29
No not a HW assignment.

Though I did solve it.   Or so I believe.

Defined this in the member variable section of the class definition:
```
void (cLogger::* m_pfuncarray[9])(const std::string &, const LOGGERTYPE&);         
```

Then in the constructor called a function to setup the table of member functions

```

cLogger::cLogger() :
        m_pfcconsole(NULL), m_pfcfile(NULL), m_pfcfilechan(NULL),
        m_consolelogger(Poco::Logger::root()), m_filelogger(Poco::Logger::root()), m_mconsolemutex(), 
        m_mfilemutex(), m_pfuncarray()
{
//other code
    setupfunctiontable();
}

```

```
void cLogger::setupfunctiontable()
{
    m_pfuncarray[Message::PRIO_FATAL] = &cLogger::fatal;
    m_pfuncarray[Message::PRIO_CRITICAL] = &cLogger::critical;
    m_pfuncarray[Message::PRIO_ERROR] =&cLogger::error;
    m_pfuncarray[Message::PRIO_WARNING] = &cLogger::warning;
    m_pfuncarray[Message::PRIO_NOTICE] = &cLogger::notice;
    m_pfuncarray[Message::PRIO_INFORMATION] = &cLogger::information;
    m_pfuncarray[Message::PRIO_DEBUG] = &cLogger::debug;
    m_pfuncarray[Message::PRIO_TRACE] = &cLogger::trace;
}
```

I *THINK* this works.  I have alot more debug to do with it.  The Poco Logger function is nice to use ... but a pain to wrap around do the the constructor and = operator's being private.

My reason for doing this was to cheat having to use a switch statement.  If I mapped the function pointer in the same order as Message::PRIO_~ I could just use a lookup table to go to the correct function rather than having to use a switch or worse if/else if structure.

Code became this simple:
```

void cLogger::log(const std::string &in_str, const int & in_priority, 
                  const LOGGERTYPE & in_loc)
{
    
    if((in_priority <= Message::PRIO_TRACE ) &&
        (in_priority >= Message::PRIO_FATAL))
    {
        (this->*m_pfuncarray[in_priority])(in_str,  in_loc);
    }
}

```

---

### Post by dribeas on 2008-12-30
The problem, which is quite common is that free function pointers and member function pointers are not the same. The types differ as with member functions the compiler must provide the implicit 'this' pointer.

The suggestion by @dwhitney67 of using boost::bind does not help by itself, as it will generate a functor of unknown type. You can, nonetheless, combine it with boost::function to define a generic function interface.

Anyway your solution should work as you are now correctly using member function pointers.

---

