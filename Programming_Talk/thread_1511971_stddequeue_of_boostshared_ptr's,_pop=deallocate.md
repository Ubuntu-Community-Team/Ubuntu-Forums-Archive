---
title: "std::dequeue of boost::shared_ptr's, pop=deallocate?"
date: 2010-06-17
forum: Programming Talk
---

### Post by FalFire on 2010-06-17
Hi,

In my current project I am making a class that checks for events from the underlying windowing system, converts them to objects of my own Event class, and stores them in an event queue. This class is part of the interface of my shared library, and one of it's functions, getEvent(), should return the first event in the queue and remove that event from the queue. 

I am trying to use smart pointers here, boost::shared_ptr's to be exact, but I am having trouble getting those to work with the std::dequeue I use for the event queue. What I want is the function getEvent() to return a smart pointer to the first Event object in the queue, with which the user of my class can do anything he wants. The smart pointer then takes care of the deallocation of the memory when needed. However, I understand that the std::dequeue calls the destructor of the object it pops, which would mean that my Event object would be deallocated before the user can do anything with it. Is this true? If yes, then how do I accomplish what I want? Should I use the pointer container of the boost library?

---

### Post by MadCow108 on 2010-06-17
the resource held by a shared pointer is only deleted when all references to it are gone.
So if still you have a reference to your object (.e.g. received by a top before the pop) your object will not be deleted by the pop:

```

// pseudocode, boost::shared_ptr is a reference counted pointer
{
  ReferenceCountedPtr a = queue.top(); // reference counter increased by one to e.g. 2.
  if (a->fine)
    queue.pop(); // ReferenceCountedPtr destructor called = reference counter decreased to 1, nothing else
  dostuff(a); // object pointed to by a is still in existence
} // a gets deleted: reference counter decreased to 0 => object pointed to gets deleted

```

---

### Post by FalFire on 2010-06-17
Hi,

May I ask where you found those functions of the smart_ptr? I cannot find them in the reference at [http://www.boost.org/doc/libs/1_43_0/libs/smart_ptr/shared_ptr.htm#Members](http://www.boost.org/doc/libs/1_43_0/libs/smart_ptr/shared_ptr.htm#Members)? And, now that I think about it, doesn't the dequeue dynamically allocate a copy of the smart_ptr, raising it's use count to 2?

EDIT: but then, if that's the case, does dequeue.clear() properly free the memory? Now I am confused...

---

### Post by MadCow108 on 2010-06-17
above was just pseudocode.

yes adding a shared_ptr to the queue will raise its reference count by one.
The queue will only contain and handle the pointers, not the objects itseld.
It will only delete its the objects saved in it (the shared_ptr) by calling its destructor.
The queue does not care what that destructor does.

In case of the shared_ptr (a reference counted pointer) it only decreases the reference count (each copy/construction on the other hand increase the count by one).
Only if it reaches zero the destructor really deletes its object.

```

// again pseudocode
deque<shared_ptr> queue;
{
  shared_ptr a(new int(0)); // construction: reference count: 1
  shared_ptr b = a; // shallow copy: reference count: 2
  queue.push_back(a); // shallow copy: reference count 3;
  queue.push_back(b); // shallow copy: reference count 4;
} // a, b get deleted -> reference count: 2 (the references in the queue)
queue.pop() // reference count:1
{
  shared_ptr c = queue.top(); // shallow copy: reference count: 2
} // c deleted -> reference count: 1
queue.clear() // reference count: 0 now finally the integer gets deleted, (has nothing to with clear per se, another pop would have done the same)

another example:
http://www.boost.org/doc/libs/1_43_0/libs/smart_ptr/example/shared_ptr_example.cpp

```

this is the niceness of smart pointers, you don't really have to care about deallocation or dangling pointers.
As long as you do not have any new's outside of shared_ptr you cannot have "real" memory leaks (logical leaks are of course still possible) and all shared pointers are always valid on use.
smart pointers are an essential part of the RAII idiom:
[http://en.wikipedia.org/wiki/Resource_Acquisition_Is_Initialization](http://en.wikipedia.org/wiki/Resource_Acquisition_Is_Initialization)

---

