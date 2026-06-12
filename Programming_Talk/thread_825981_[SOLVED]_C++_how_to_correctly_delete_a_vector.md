---
title: "[SOLVED] C++ how to correctly delete a vector?"
date: 2008-06-11
forum: Programming Talk
---

### Post by xlinuks on 2008-06-11
Hi,
I have an std:vector that contains pointers to objects.
So, say the pointer to my vector is called pMyVector, what does
this do:
```

vector<SomeObject*> *pMyVector = new vector<SomeObject*>();

pMyVector->add( new SomeObject() );
pMyVector->add( new SomeObject() );
//and so on

//what does the following line do?
delete pMyVector;

```

Is it correct that it?:
1) Calls vector's clear() method to delete the objects, and since there are only pointers to objects it only deletes the pointers but the objects themselves stay in memory.
2) Destroys the vector.

If not please let me know how to correctly delete the vector and the data it contains to avoid memory leaks.

---

### Post by geirha on 2008-06-11
For each "new" you do, you should do a "delete" to free it. You are correct on both 1 and 2. You'll need to iterate your vector, and run delete on each element, before you delete the vector itself.

Try running your program with [valgrind](apt:valgrind). ```
valgrind ./a.out
``` It should tell you if you have memory leeks and other useful info, like how much memory has been allocated.

---

### Post by xlinuks on 2008-06-11
I see now, thanks a lot!

---

### Post by Jessehk on 2008-06-11
The code you have now is wrong in two ways.

1) For the most part, you won't want to create a pointer to a container (like a std::vector for example), but just an instance. Thus, instead of:

```

std::vector<int> *numbers = new std::vector<int>();

```

You'd want something like this:
```

std::vector<int> numbers;

```

2) Storing raw pointers in standard containers is AFAIK, never a good idea. If you really need to store resources that have to be allocated by **new**, your best bet is a boost::shared_ptr. The Boost documentation for that is [here](http://www.boost.org/doc/libs/1_35_0/libs/smart_ptr/shared_ptr.htm).

This is a contrived example:
```

#include <iostream>
#include <vector>

#include <boost/shared_ptr.hpp>

class Foo {
    int bar_;
public:
    explicit Foo( int bar ) :
        bar_( bar ) {}

    int bar() const { return bar_; }
};

Foo *factory( int bar ) {
    Foo *result = new Foo( bar );

    return result;
}

// typedef to make the name shorter. It gets cumbersome
// otherwise.
typedef std::vector<boost::shared_ptr<Foo> > FooList;

int main() {
    FooList foos;

    for ( int i = 0; i < 10; i++ )
        foos.push_back( boost::shared_ptr<Foo>( factory( i + 1 ) ) );

    FooList::const_iterator iter = foos.begin();
    for ( ; iter != foos.end(); iter++ )
        std::cout << (*iter)->bar() << std::endl;
}

```

---

