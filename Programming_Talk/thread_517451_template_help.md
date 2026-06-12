---
title: "template help"
date: 2007-08-04
forum: Programming Talk
---

### Post by rjfioravanti on 2007-08-04
I have this code in vector.h
```

#ifndef __VECTOR__
#define __VECTOR__

template <class T>
class Vector {

public:
	Vector();
	~Vector();
};

#endif

```

This is vector.cc
```

#include "vector.h"

template <class T>
Vector<T> :: Vector() {
	
} 

template <class T>
Vector<T> :: ~Vector() {

} 

```

In another file I try to use it like this
```

Vector<String> strings;

```

When I compile I get the following error
generate++.cc:102: undefined reference to `Vector<String>::Vector()'
generate++.cc:107: undefined reference to `Vector<String>::~Vector()'


What is wrong?

---

### Post by PandaGoat on 2007-08-04
It is std::string, and you must #include <string>.

Someone's been using Java :P.

---

### Post by rjfioravanti on 2007-08-04
I created my own class called String and am using that

I am just showing a subset of the code but I do have an include statement for my string class

---

### Post by rjfioravanti on 2007-08-04
I think it has something to do with not being able to compile a template source file... am I supposed to define the implementations of my functions in the header? 

I am reading this and it seems like this is the case... [http://www.codeguru.com/forum/showthread.php?t=250284](http://www.codeguru.com/forum/showthread.php?t=250284)

---

### Post by rjfioravanti on 2007-08-04
yeah ok that was the problem

I was doing 

g++ -c vector.cc

I put the cc code into vector.h, then the objects that need it just figure it out, its never compiled apparently

---

