---
title: "C++, comparing pointers."
date: 2011-03-04
forum: Programming Talk
---

### Post by cgroza on 2011-03-04
Hello everyone. I started to do a limited container just to test my skills after finishing the chapter about iterators in the book "The C++ programming language". 

So my "container" basically uses a vector(by default, can be specified as a template argument) to hold its elements. I made this whole thing just to try to implement iterators for it.

Here is the container class code:
```

#include <iostream>
#include <vector>
using namespace std;

template <class T, class C> class Vec {
private:
     typedef T val_type;

     C vec;
     struct ends {
          val_type* first;
          val_type* last;
     };

     ends extrem;

public:
     template<class V = val_type>
     class iterator {
     private:
          V* it;
     public:
          iterator(val_type* a):it(a) {
          }

          void operator=(val_type* a) {
               it=a;
          }

          void operator++() {
               ++it;
          }
          val_type& operator*()const {
               return *it;
          }
          bool operator<(val_type* y) {
               return it < y;
          }
     };

     Vec(const int nr):vec(nr) {
          extrem.first = &vec[0];
          extrem.last = &vec[-1];

     }

     val_type* end() const {
          return extrem.last;
     }

     val_type* begin() const {
          return extrem.first;
     }

     void push_back(const val_type& a) {
          vec.push_back(a);
          extrem.first = &vec[0];
          extrem.first = &vec[-1];
     }

     val_type& operator[](int x) {
          return vec.at(x);
     }

     int size() {
          return vec.size();
     }

};
```And here is my main:

```
int main()
{
     Vec<int, vector<int> > test(10);
     Vec<int, vector<int > >::iterator<int> p = test.begin();


     for(int j = 0 ; j < test.size() ; j++) {
          test[j] = j;
     }

     int i = 0;
     while (i<test.size()) {
          cout<<*p;
          ++p;
          i++;
     }
}
```With this main function, the thing prints out all the elements using my iterator.
The problem is that I want to do the loop with while(p<test.end()){...} like in the book, but the < operator returns something bad and the loop goes crazy and segfaults.
This is the < operator:
```
          
bool operator<(val_type* y) {
               return it < y;
          }
```Any ideas why? I am I doing something wrong?

---

### Post by GeneralZod on 2011-03-04
This seems highly dubious:

> 
```

          extrem.last = &vec[-1];


```


---

### Post by cgroza on 2011-03-04
> **GeneralZod said:**
> This seems highly dubious:
More explanation please?

---

### Post by PaulM1985 on 2011-03-04
You seem to be saying the last position is the one before the first.

Paul

---

### Post by cgroza on 2011-03-04
> **PaulM1985 said:**
> You seem to be saying the last position is the one before the first.

Paul
OK, I think that I was thinking python. In python -1 is the last position for an array. :D
EDIT: Great, it works. Now lets do a google on python mistakes in C++ :D.

---

### Post by Vox754 on 2011-03-04
> **GeneralZod said:**
> This seems highly dubious:

```

>>> a = ["first", 1, 2, 3, "last"]
>>> print(a)
['first', 1, 2, 3, 'last']
>>> print(a[0])
first
>>> print(a[-1])
last

```

It works in Python!

I wonder why it doesn't work in C++?

---

### Post by cgroza on 2011-03-04
> **Vox754 said:**
> ```

>>> a = ["first", 1, 2, 3, "last"]
>>> print(a)
['first', 1, 2, 3, 'last']
>>> print(a[0])
first
>>> print(a[-1])
last

```It works in Python!

I wonder why it doesn't work in C++?

Different languages, maybe it is because of the vector, let me try for a built in array.
EDIT: It does not, just spits some random data.

---

### Post by Vox754 on 2011-03-04
> **cgroza said:**
> Different languages, maybe it is because of the vector, let me try for a built in array.
EDIT: It does not, just spits some random data.

You were supposed to read my witty remark before realizing your mistake. Otherwise my post makes no sense.

---

