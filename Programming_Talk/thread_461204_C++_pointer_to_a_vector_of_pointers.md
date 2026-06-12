---
title: "C++ pointer to a vector of pointers?"
date: 2007-06-01
forum: Programming Talk
---

### Post by Yendor on 2007-06-01
I'm trying to create a class that has a pointer to a vector of pointers to an object on the freestore.  100's of these vectors of pointers will exist, so I'm trying to create them on the freestore, but I can't find how to access the objects functions.

From what I understand, this should create a pointer to a vector of pointers to an object:
```
vector<object*>* connections;
```

Then I fill this vector:
```
object* oneObject = new object;
connections->push_back(oneObject);
```

Everything seems to be working fine up to this point.  Then I get errors trying to initialize this object:
```
connections[index]->Initialize(index);
```
gives:
> base operand of '->' has non-pointer type ...
and:
```
connections[index].Initialize(index);
```
gives:
> ... has no member named 'Initialize'

I've searched google extensively, but can't seem to figure this out.  Am I going about this all wrong?  Is the problem with the way I create the vector, fill the vector, how I'm calling the object's Initialize() function, or somewhere else?

---

### Post by WW on 2007-06-01
Since connections is not a vector, but a pointer to a vector, you must first dereference connections to use the brackets:
```

    (*connections)[0]->Initialize(index);

```

Be sure that you have first initialized connections to point to a vector before using it:
```

    connections = new vector<object *>;

```

---

### Post by Yendor on 2007-06-01
Thank you so much WW, worked like a charm.  I have a lot yet to learn, thinking I need to tackle simpler projects, just never been one to take the intelligent route ;)

---

### Post by aks44 on 2007-06-01
> **Yendor said:**
> Thank you so much WW, worked like a charm.  I have a lot yet to learn, thinking I need to tackle simpler projects, just never been one to take the intelligent route ;)
If you're new to C++ (as your question seems to suggest), I'd suggest you *immediately* forget about pointers. C++ is not plain old C, and pointers are a very rare thing around here.

FWIW, last time I checked (I was trying to explain a member of our GUI team why pointers are bad), we had like 15-20 new's in our 250kloc server and not a single delete (ah, the joys of smart pointers), even though almost all data is allocated on the heap.

The Standard Library, and boost to some extent, are things you must absolutely learn & master. Mainly, the standard containers and boost's smart pointer classes will allow you to easily write error-free code, and concentrate on the real problems : algorithms and architecture.

---

### Post by Yendor on 2007-06-02
Thank you for your thoughtful advice aks44.

I am slowly working my way through studying the Standard Library, with a lot of research currently going into containers.  I haven't heard much about boost, and will definitely look into it ... thank you.

I'm curious to know though, forgetting about pointers ... as in, use boost's smart pointers instead?  Or simply drop them entirely?  You mentioned almost all data being allocated on the Heap; isn't this what pointers do? or is there another way to store the data on the Heap? (or am I taking that way out of context?)

---

### Post by aks44 on 2007-06-05
> **Yendor said:**
> I'm curious to know though, forgetting about pointers ... as in, use boost's smart pointers instead?  Or simply drop them entirely?  You mentioned almost all data being allocated on the Heap; isn't this what pointers do? or is there another way to store the data on the Heap? (or am I taking that way out of context?)

Sorry for the confusion, I should have written *raw* pointers.

Indeed you are right, the only way to use the heap is to use pointers. However, you should NEVER manage them directly ("à la C").

Standard containers do allocate their memory on the heap, but quite often you also need very specific memory management that isn't provided by the standard library. Boost's wide range of smart pointers sometimes (often) do the trick, but for the rest you must write your own wrappers.

Most resource management (not only memory, but also files etc) should be done using the RAII idiom (Resource Acquisition Is Initialization). RAII relies on the fact that whenever an object goes out of scope due to normal program flow or to exceptions, it's destructor (where you put the cleanup code) is automagically called.

The key benefits of RAII being that, if done correctly, your code is fully exception-safe, and no resource leaks can arise, whatever path your program takes at runtime.

std::auto_ptr is the most basic incarnation of that idiom. Search the web for more details and examples.

Hope this helps a bit. :)

---

### Post by Yendor on 2007-06-07
> **aks44 said:**
> Standard containers do allocate their memory on the heap,
<snip>
Hope this helps a bit. :)

This solves my initial issue ... it would seem there is no reason for setting up a pointer to a vector of pointers, since the vector is on the heap to begin with.  Thank you.  And, thank you for your other advise also ... it has definitely helped guide my self-studies in a very positive direction.

---

