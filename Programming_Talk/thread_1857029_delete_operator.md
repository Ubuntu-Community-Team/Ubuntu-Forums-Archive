---
title: "delete operator"
date: 2011-10-09
forum: Programming Talk
---

### Post by leg on 2011-10-09
I am confusing myself here so I thought I would ask. does there need to be a corresponding delete for every object created with new. Specifically I am thinking of a situation where I have a pointer to a vector which contains pointers to objects. The vector is created using new and then a loop creates the objects it contains with new. Can I just use delete on the vectors pointer and that releases all the memory or do I need to loop through the vector using delete on each item?

---

### Post by MadCow108 on 2011-10-09
you need to loop through the vector and delete each entry.
When a vector gets deleted it calls the destructor of all entries in it. As pointers are just basic number type with no destructor, it will only delete the pointer and not the object pointed to.

To get some automatic memory handling with pointers in standard containers use smart pointers, like boosts' shared_ptr
[http://www.boost.org/doc/libs/1_47_0/libs/smart_ptr/shared_ptr.htm](http://www.boost.org/doc/libs/1_47_0/libs/smart_ptr/shared_ptr.htm)

Compared to normal pointers smart pointers are objects with a destructor capable of handling deallocation when the smart pointer gets deleted (in the case of shared_ptr via reference counting).

---

### Post by nvteighen on 2011-10-09
Basic rule:

For each *new* you write, you have to write its corresponding *delete*.

The reason behind this is easy. Being a statically compiled language, C++ is uncapable of doing automatic heap allocation. If something is allocated without resorting to *new*, then it is stored at the stack and therefore doesn't need to be deallocated manually.

Of course, it could happen that you use a third-party library that defines a class called A, which in turn dynamically allocates internal stuff and fails to deallocating them. In that case, you have no way to solve the leak (unless you modify the source code or the leaking memory happens to be a public member...) and it wouldn't be your fault.

---

### Post by MadCow108 on 2011-10-09
> **nvteighen said:**
> Basic rule:

For each *new* you write, you have to write its corresponding *delete*.

unless you transfer ownership of the object to a different object which will delete it.
This is exactly what e.g. shared_ptr does:
```

#include <boost/shared_ptr.hpp>
int main(int argc, const char *argv[]) {
  boost::shared_ptr<int> a(new int);
  return 0; // a goes out of scope, its destructor delete's int, no memory leak
}

```

---

### Post by leg on 2011-10-09
Thank you that was very helpful. I did think I had to but thought that just deleting the vector might be enough. I suppose this is the kind of confusion I should expect having learnt Java first.

---

### Post by ofnuts on 2011-10-09
> **leg said:**
> Thank you that was very helpful. I did think I had to but thought that just deleting the vector might be enough. I suppose this is the kind of confusion I should expect having learnt Java first.In Java deleting the vector doesn't delete the objects either... they could be referenced elsewhere. But you don't have to deal with object destruction, this is handled by the garbage collector.

---

### Post by leg on 2011-10-10
> **ofnuts said:**
> In Java deleting the vector doesn't delete the objects either... they could be referenced elsewhere. But you don't have to deal with object destruction, this is handled by the garbage collector.

Could yes but if not then they are hanging and would be deleted for you.

---

### Post by nvteighen on 2011-10-10
> **MadCow108 said:**
> unless you transfer ownership of the object to a different object which will delete it.
This is exactly what e.g. shared_ptr does:
```

#include <boost/shared_ptr.hpp>
int main(int argc, const char *argv[]) {
  boost::shared_ptr<int> a(new int);
  return 0; // a goes out of scope, its destructor delete's int, no memory leak
}

```

Very true; I forgot about that.

---

