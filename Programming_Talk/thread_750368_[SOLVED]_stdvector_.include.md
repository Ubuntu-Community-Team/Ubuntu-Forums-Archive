---
title: "[SOLVED] std::vector .include?"
date: 2008-04-09
forum: Programming Talk
---

### Post by Zeotronic on 2008-04-09
C++: I'm sure this will be answered rather quickly, but it seems that I do not understand how to properly use .insert, of std::vector. I have a vector array of unsigned longs and I'm trying to insert a value into it something like this:
```
longarray.insert(0,1000);
```
However, I get the following error:
> main.cpp:991: error: no matching function for call to &#8216;std::vector<long unsigned int, std::allocator<long unsigned int> >::insert(long unsigned int, long unsigned int&, long unsigned int&)&#8217;
I have a site ([www.cplusplus.com](www.cplusplus.com)) that I use to find coding examples for things like this, but I cannot derive from it's example the proper method of useage. How do I use .insert?

Edit: I see I made a typo on the thread's title...

---

### Post by WW on 2008-04-09
The first argument to insert() must be an iterator, not an integer.  Take a look at the example: [http://www.cplusplus.com/reference/stl/vector/insert.html](http://www.cplusplus.com/reference/stl/vector/insert.html).

Something like this:
```

    vector<long>::iterator it;
    .
    .
    .
    it = longarray.begin();
    longarray.insert(it,1000);

```

---

### Post by heikaman on 2008-04-09
or you can use push_back()

```

vec.push_back(1000);

```

---

### Post by Zeotronic on 2008-04-09
> or you can use push_back()
Sure... if you want to write to the END of the array!

Edit:
I'm not quite clear on how to use an iterator... or even what it is.

---

### Post by aks44 on 2008-04-09
> **Zeotronic said:**
> I'm not quite clear on how to use an iterator... or even what it is.

Think of an iterator as an object that represents a *_position in a sequence_*, and that allows you to either
- get/set the value at that position,
- or, move somewhere else.


Using vectors (random access containers), you can just use the plain old "index" idiom:

```
for (size_t i = 0; i < vect.size(); ++i)
{
  // do something with vect[i]
};
```


but if you switch to other kinds of containers (eg. lists) you can't do that anymore. The typical idiom for solving that is to use those so-called iterators:

```
for (std::list<int>::iterator i = lst.begin(); i != lst.end(); ++i)
{
  // do something with (*i) OR with i itself
};
```


Back to vectors: since they are barely more than an encapsulation of dynamically allocated arrays, it is very straightforward to convert iterator loops to plain old pointer loops...

```
for (std::vector<int>::iterator i = vect.begin(); i != vect.end(); ++i)
{
  // ...
};
```

is (more or less) equivalent to:

```
int arr[ARR_SIZE];
for (int* i = arr; i != (arr + ARR_SIZE); ++i)
{
  // ...
};
```


But again, the iterator abstraction is more than that, as it also works on chained lists, dequeues and any other container.

Some containers (slist = single-linked list) only provide forward iterators (that you can only increment).
Doubly-linked lists provide sequential iterators (that you can both increment and decrement).
Vectors provide random-access iterators (sequential iterators that can also "jump" anywhere in the sequence without additional cost).


The good part about iterators is that this abstraction also allows you to use "reverse" iterators (doesn't work for forward-only iterators though):

```
for (std::list<int>::reverse_iterator i = lst.rbegin(); i != lst.rend(); ++i)
{
  // walk lst in reverse order...
};
```


One more thing to keep in mind (that speaks in favour of iterators) is that you usually barely need random iterators. Most of the time you'll just need to traverse a container in order (whether begin -> end or end -> begin).




Hmm proofreading my post I'm not sure whether I actually made a clear explanation... but hopefully you'll be able to extract some useful info from it. :)

---

