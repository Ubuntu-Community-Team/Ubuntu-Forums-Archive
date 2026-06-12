---
title: "C++ Template issues"
date: 2009-04-11
forum: Programming Talk
---

### Post by gaten on 2009-04-11
OK, I'm at my wits end here, and I'm hoping someone here can end my nightmare of template coding.

I'm trying to create a very basic memory manager. The idea is this: I will have some basic objects, let's say a Box, which is derived from a Node class. To create a box, you would do the following:
```

MemoryManager mem;
Box *box1 = mem(new Box(x, y, z));

```etc. My problem is the MemoryManager class, shown below:

```
/*
 * MemoryManager.h
 *
 *  Created on: Apr 10, 2009
 *      Author: gaten
 */

#ifndef MEMORYMANAGER_H_
#define MEMORYMANAGER_H_

#include <vector>
using namespace std;

template <class T>
class MemoryManager
{
    public:
        MemoryManager();
        ~MemoryManager();

        T* create(T *object);

        void deletes(T *object);

        void garbageCollection();

        int getTotalObject();
        int getDeadObjects();
        int getAliveObjects();

    private:
            std::vector<T> objectList;
            std::vector<bool> deleteList;
            int aliveObjects, deadObjects, totalObjects;
};

template <class T>
MemoryManager<T>::MemoryManger()
{
    aliveObjects = 0;
    deadObjects = 0;
    totalObjects = 0;
}

template <class T>
MemoryManager<T>::~MemoryManager()
{
    // delete everything
    vector<Object>::iterator it;

    for (it = objectList.begin();
            it != objectList.end(); it++ )
        delete it;
}

template <class T>
Object* MemoryManager<T>::create(Object *object)
{
    objectList.push_back(&object);
    deleteList.push_back(false);

    aliveObjects++;
    totalObjects++;

    return &objectList.back();
}

template <class T>
void template <class T>::deletes(Object *object)
{
    // delete object
    deadObjects++;
    aliveObjects--;

    // make object to be deleted
}

template <class T>
void template <class T>::garbageCollection()
{
    int pos = 0;

    vector<bool>::iterator it;

    for (it = deleteList.begin(); it < deleteList.end();
        it++, pos++ )
    {
        if (it)
        {
            Object* temp = objectList.at(pos);
            delete temp;
            objectList.erase(pos);
        }
    }
}

int MemoryManager::getTotalObject() { return objectList.size(); }
int MemoryManager::getDeadObjects() { return deadObjects; }
int MemoryManager::getAliveObjects() { return aliveObjects; }

#endif /* MEMORYMANAGER_H_ */

```These are the errors I get:
```
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"main.d" -MT"main.d" -o"main.o" "../main.cpp"
In file included from ../main.cpp:8:
../MemoryManager.h:38: error: ISO C++ forbids declaration of ‘MemoryManger’ with no type
../MemoryManager.h:38: error: no ‘int MemoryManager<T>::MemoryManger()’ member function declared in class ‘MemoryManager<T>’
../MemoryManager.h: In destructor ‘MemoryManager<T>::~MemoryManager()’:
../MemoryManager.h:49: error: ‘Object’ was not declared in this scope
../MemoryManager.h:49: error: template argument 1 is invalid
../MemoryManager.h:49: error: template argument 2 is invalid
../MemoryManager.h:49: error: expected initializer before ‘it’
../MemoryManager.h:51: error: ‘it’ was not declared in this scope
../MemoryManager.h: At global scope:
../MemoryManager.h:57: error: expected constructor, destructor, or type conversion before ‘*’ token
../MemoryManager.h:69: error: expected unqualified-id before ‘template’
../MemoryManager.h:79: error: expected unqualified-id before ‘template’
../MemoryManager.h:97: error: ‘template<class T> class MemoryManager’ used without template parameters
../MemoryManager.h: In function ‘int getTotalObject()’:
../MemoryManager.h:97: error: ‘objectList’ was not declared in this scope
../MemoryManager.h: At global scope:
../MemoryManager.h:98: error: ‘template<class T> class MemoryManager’ used without template parameters
../MemoryManager.h: In function ‘int getDeadObjects()’:
../MemoryManager.h:98: error: ‘deadObjects’ was not declared in this scope
../MemoryManager.h: At global scope:
../MemoryManager.h:99: error: ‘template<class T> class MemoryManager’ used without template parameters
../MemoryManager.h: In function ‘int getAliveObjects()’:
../MemoryManager.h:99: error: ‘aliveObjects’ was not declared in this scope
../main.cpp: In function ‘int main()’:
../main.cpp:18: error: request for member ‘create’ in ‘mem’, which is of non-class type ‘MemoryManager<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >*’
make: *** [main.o] Error 1
```The problems start on line 38 (MemoryManager<T>::MemoryManger()) and I also get a 'syntax error' from my IDE (eclipse w/ CDT) on line 37 (template <class T>), which I just simply do not understand. Any help would be appreciated!

---

### Post by Habbit on 2009-04-11
First, you are using a non-defined class "Object". If you come from a Java/C# background, you need to understand that there is no "single class hierarchy" in C++, or, in other words, that the hierarchies have no common root. In your case the correct type, according to your parametrization, is "T".

Second, the code you posted for "main" does not seem to match the compiler error. If that's the actual code, you need to specify the template argument for MemoryManager, and actually call "create" instead of invoking an undefined "T* MemoryManager:: operator() (T*)". Could you copy-paste the relevant lines of "main", please?

Third, the implementation of the MemoryManager construction has the wrong name (MemoryManger) and so the compiler thinks it's a member function of the class and wants you to declare a return-value type. Correct the typo.

Fourth, you have some more syntax errors (like using "template <class T>" twice in some functions' implementations). Furthermore, if MemoryManager is parameterized, all its members are, even if they don't directly use T (that goes for the last three functions).

---

### Post by gaten on 2009-04-11
Ugh, those were some silly errors, thanks so much for catching them. I guess I should have put it down for a while and come back, probably would've caught some of em ;)

Now my errors are fewer, but just as confusing to me. Here's the whole thing again:

MemoryManager.h
```
/*
 * MemoryManager.h
 *
 *  Created on: Apr 10, 2009
 *      Author: gaten
 */

#ifndef MEMORYMANAGER_H_
#define MEMORYMANAGER_H_

#include <vector>
using namespace std;

template <class T>
class MemoryManager
{
    public:
        MemoryManager();
        ~MemoryManager();

        T* create(T *object);

        void deletes(T *object);

        void garbageCollection();

        int getTotalObject();
        int getDeadObjects();
        int getAliveObjects();

    private:
            std::vector<T> objectList;
            std::vector<bool> deleteList;
            int aliveObjects, deadObjects, totalObjects;
};

template <class T>
MemoryManager<T>::MemoryManager()
{
    aliveObjects = 0;
    deadObjects = 0;
    totalObjects = 0;
}

template <class T>
MemoryManager<T>::~MemoryManager()
{
    // delete everything

    vector<T>::iterator it;

    for (it = objectList.begin();
            it != objectList.end(); it++ )
        delete it;
}

template <class T>
T* MemoryManager<T>::create(T *object)
{
    objectList.push_back(&object);
    deleteList.push_back(false);

    aliveObjects++;
    totalObjects++;

    return &objectList.back();
}

template <class T>
void MemoryManager<T>::deletes(T *object)
{
    // delete object
    deadObjects++;
    aliveObjects--;

    // make object to be deleted
}

template <class T>
void MemoryManager<T>::garbageCollection()
{
    int pos = 0;

    vector<bool>::iterator it;

    for (it = deleteList.begin(); it < deleteList.end();
        it++, pos++ )
    {
        if (it)
        {
            T* temp = objectList.at(pos);
            delete temp;
            objectList.erase(pos);
        }
    }
}
template <class T>
int MemoryManager<T>::getTotalObject() { return objectList.size(); }

template <class T>
int MemoryManager<T>::getDeadObjects() { return deadObjects; }

template <class T>
int MemoryManager<T>::getAliveObjects() { return aliveObjects; }

#endif /* MEMORYMANAGER_H_ */

```

main.cpp
```
/*
 * main.cpp
 *
 *  Created on: Apr 10, 2009
 *      Author: gaten
 */

#include "MemoryManager.h"
#include <string>
#include <iostream>

using namespace::std;

int main()
{
    MemoryManager<std::string> *mem;

    std::string *hi = mem.create(new std::string("hi"));

    cout << "String: " << *hi;

    delete mem;
}

```

and the errors:
```
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"main.d" -MT"main.d" -o"main.o" "../main.cpp"
In file included from ../main.cpp:8:
../MemoryManager.h: In destructor ‘MemoryManager<T>::~MemoryManager()’:
../MemoryManager.h:50: error: expected `;' before ‘it’
../MemoryManager.h:52: error: ‘it’ was not declared in this scope
../main.cpp: In function ‘int main()’:
../main.cpp:18: error: request for member ‘create’ in ‘mem’, which is of non-class type ‘MemoryManager<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >*’
../MemoryManager.h: In destructor ‘MemoryManager<T>::~MemoryManager() [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]’:
../main.cpp:22:   instantiated from here
../MemoryManager.h:50: error: dependent-name ‘std::vector::iterator’ is parsed as a non-type, but instantiation yields a type
../MemoryManager.h:50: note: say ‘typename std::vector::iterator’ if a type is meant
make: *** [main.o] Error 1
```

As you can see, on line 50, inside the deconstructor, I'm trying to walk through the vector and delete all the elements inside of it, but I can't get the iterator to initialize as a template type. How can I go about doing this?

And in main, I'm having trouble getting my create() function to work. This is supposed to save me memory in my program and prevent memory leaks, so I want all the "new" stuff handled inside this class. 

Is my coding logic right with the pointers and such for this task? I *think* I'm creating a function (create()) that returns a pointer to a memory address of which the data is stored inside a vector inside the manager class. This way I'm using the least amount of memory possible for an object, and can easily move/delete the object when it's no longer needed.

Thanks again for you help.

---

### Post by Idefix82 on 2009-04-11
If I remember my C++ correctly (I used it ages ago) then you are not declaring a MemoryManager object in main, but merely a pointer. A pointer has no member functions. You have to do something like
```

MemoryManager<std::string> *mem = new MemoryManager<std::string>;

```
before you can call create. And then you will have to do
```

mem->create

```
because mem is a pointer. Anybody correct me if I'm wrong.

---

### Post by gaten on 2009-04-11
Idefix82: Yep, you're right. Another silly error caught, thanks :)

Now, the iterator problem remains...

---

### Post by stair314 on 2009-04-11
Change the line to begin with  "typename vector<T>::iterator".

---

### Post by stair314 on 2009-04-11
P.S.
The "delete" keyword only works on pointers. It's like "free()" from C. You can't say "delete it" because "it" is an iterator, not a pointer.
If T is a pointer type, then it would be valid to say "delete *it". That would mean that objectList holds pointers to objects, "it" specifies a member of objectList, and you delete the pointer it identifies.
Since looking at your main.cpp it looks like you're not planning on having T be a pointer type, then what you really want to do, instead of that whole for loop, is
objectList.clear()

---

### Post by stair314 on 2009-04-11
P.P.S.
If you're interested in automated memory management, you might like the idea of a "smart pointer":
[http://en.wikipedia.org/wiki/Smart_pointer](http://en.wikipedia.org/wiki/Smart_pointer)

This way you don't need to manually call a delete method or refer to a memory management object.

---

### Post by dribeas on 2009-04-11
You are trying to tackle a really complex problem. You should start dealing with smaller problems. The simplest memory management code I know of is boost::scoped_ptr. Read about it, download the code and understand it. As it is very limited in scope it will be easy to grasp. Test it, see how it works. Then move to std::auto_ptr, which is also simple and understand the code. Understand each line as all of them are important. Test it.

Then move on to smart pointers in general. Read Alexandrescu's Modern C++ Design chapter on smart pointers. There is a lot of knowledge in that chapter, and I believe that you can find it online. If you find some simple smart pointer library, read the docs, and read the code. If the library has support for weak_ptr then the code will be more complex to read (that is why I do not recommend boost::shared_ptr for a head start).

After understanding some other types of smart pointers (reference counted, as an example) try to implement a reduced, simplified version. 

Dealing with memory management of a single pointer is much simpler than dealing with a class to hold a range of pointers, whether the same or worse, different types.

---

### Post by dribeas on 2009-04-11
Now, that being said, we can discuss your approach. 

The first thing is that as it is, the user must allocate MemoryManager's for each of the types, and she can instantiate as many MemoryManagers as she wishes. The user has to manually determine the type of the element to manage for each of the MemoryManager (MM from here on). Finally, the user must call deletes on the correct MM.

```

int main()
{
   MemoryManager<std::string> mm1;
   MemoryManager<std::string> mm2; // can create more than one
   MemoryManager<int> mm3; // must create a different MM to handle int*

   std::string *str = new std::string(); // I won't comment on the fact of creating an std::string in heap...
   mm1.creates( str ); // records the pointer in mm1
   mm2.deletes( str ); // tries to delete from mm2 !!!
   mm1.garbageCollection(); // str is not freed
   mm2.garbageCollection(); // this may or not free str, depending on implementation. It better not.
}
// mm1 and mm2 go out of scope. At this point if mm2.garbageCollection freed the pointer
// you will get a double free and the application dies,

```

This is not simplifying the live of the user. Garbage collection must be executed by the user at a given time manually, or else all the objects will be left in memory (not leaked, but useless for the user) until the MM goes out of scope and deletes them.

Now compare this with the more idiomatic smart pointer approach:

```

int main()
{
   std::auto_ptr< std::string > str( new std::string() );
   boost::scoped_ptr< std::string > str2( new std::string() );
   boost::shared_ptr< std::string > str3( new std::string() );
}

```

With all types of smart pointers the user must declare that the resource (memory) must be held in a smart pointer and the type, but the code is much more compact and easy to read (no need of the extra memory management objects, the smart pointer replaces the raw pointer). And at the end they will be freed, with the only difference that the deletion will happen when the smart pointer is destroyed (goes out of scope) and cannot be left for a later call to garbageCollection().
You can force early deletion of the object by resetting the smart pointers (which will free the memory).

---

### Post by gaten on 2009-04-11
stair314, dribeas:

Thank you both for your suggestions. The smart pointer seems the best way to go, I just hope it's acceptable for this assignment (this is supposed to be a memory manager for a video game for a class).

I'm reading over those wikipedia entries and the boost stuff, thanks a lot to both of you.

And by the way, the garbageCollection() was going to be run in the glutIdleFunc(), so that it runs the garbage collection when it's idel(ish). 

I'll start redesigning for smart pointers, thanks a bunch. I'll probably be back :P

---

### Post by dwhitney67 on 2009-04-11
I recall working on a satellite program where the use of STL was forbidden (we were relegated to the constraints of Embedded C++).

In an effort to "almost" duplicate what I recall being used (I was not responsible for the Memory Management CSC), I came up with the following... which uses STL queue.  Naturally, one could implement their own queue or perhaps use a message queue (I believe this was done on the satellite program) in lieu of the STL queue.

The whole purpose of the Memory Manager was not to prevent the usage of 'new', but to provide an alternative where memory was "relocated" to a pre-allocated memory pool.

Here's what I threw together with Hard Apple Cider and beer flowing through the veins.  I do not need it to be judged!   :lolflag:

```

#include <queue>
#include <string>
#include <cassert>


template <typename T>
class MemoryManager
{
  public:
    MemoryManager(const size_t poolSize = 100)
    {
      for (size_t i = 0; i < poolSize; ++i)
      {
        m_pool.push(new T);
      }
    }

    ~MemoryManager()
    {
      while (!m_pool.empty())
      {
        T* item = m_pool.front();
        m_pool.pop();
        delete item;
      }
    }

    T* get()
    {
      T* item = 0;

      if (m_pool.size() > 0)
      {
        item = m_pool.front();
        m_pool.pop();
      }

      return item;
    }

    void free(T* obj)
    {
      m_pool.push(obj);
    }

  private:
    std::queue<T*> m_pool;
};


int main()
{
  MemoryManager<int> memMgr(25);

  // Test that memory can be obtained/used/freed
  // Note the use of memory relocation
  int* ptr = new (memMgr.get()) int;
  assert(ptr != 0);
  *ptr = 10;
  assert(*ptr == 10);
  memMgr.free(ptr);

  // Allocate all memory and then test that memory is not infinite
  int* p[25];
  for (int i = 0; i < 25; ++i)
  {
    p[i] = memMgr.get();
    assert(p[i] != 0);
  }

  assert(memMgr.get() == 0);

  for (int i = 0; i < 25; ++i)
  {
    memMgr.free(p[i]);
  }

  // Verify memory is available again...
  ptr = new (memMgr.get()) int;
  assert(ptr != 0);
  memMgr.free(ptr);

  // Ok, use valgrind to verify all memory within MemoryManager is freed
}

```

---

### Post by dribeas on 2009-04-12
If you are asked to implement something in an specific way, then choices are quite limited. Take a look at dwhitney implementation for ideas. The code he posted is more of a memory pool than a garbage collector (your initial approach) though. Creating an easy to use library for memory management is really hard, but you can settle at some intermediate point.

---

### Post by gaten on 2009-04-13
Alright, looks like using the Boost library is allowed, so I'll be going that route. Thanks to you all for the ideas and support, it really helped out. 

Back to the IDE, see you all on the other side of a memory manager :)

---

