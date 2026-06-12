---
title: "C++ array initialization question"
date: 2009-11-12
forum: Programming Talk
---

### Post by jdunn on 2009-11-12
Help!  I need to initialize multidimensional arrays within the body of a class so they'll be global for the entire class but I can't set the array size until I read the value in as a string from a text file and convert it to integer.  How do I get around this problem?

---

### Post by dwhitney67 on 2009-11-12
> **jdunn said:**
> Help!  I need to initialize multidimensional arrays within the body of a class so they'll be global for the entire class but I can't set the array size until I read the value in as a string from a text file and convert it to integer.  How do I get around this problem?

Use the STL vector, or TR1 (or Boost) array class.

P.S.  If you insist on using C-style arrays, then...
```

class Foo
{
public:
  Foo()
  {
     // read some size-value from external source (really though, should be passed as a parameter)
     // ...

     array = new DataType*[someSize];

     for (size_t i = 0; i < someSize; ++i) {
        array[i] = new DataType[someSize];
     }
  }

  virtual ~Foo() {
     // de-allocate array
  }

private:
   DataType** array;
};

```
Change DataType to be the actual type of data required for your array.

---

### Post by jdunn on 2009-11-12
I'm kind of lost on what's going on in this foo code

Is there just a way to pass a parameter from main() to the class I'm calling?

---

### Post by jdunn on 2009-11-12
Never mind.  I understand the foo code a better now and it helped.  I implemented something similar in my program and it does what I wanted.  I'm not very experienced with passing pointers to multidimensional arrays as arguments to methods.

:popcorn:

---

