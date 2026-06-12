---
title: "thread safety of std::map"
date: 2009-07-16
forum: Programming Talk
---

### Post by monkeyking on 2009-07-16
Hi I'm considering pthreading my application, I've used pthread in the past and feel comfortable with this in c context.

Now I've got a std::map<int,VALS> where VALS is a struct consisting of all the data that I need for my computation.

This means that I can create 'map.size()' threads that can run in parallele without any problems. 

Each thread should update a value 'RES' in the the VALS struct so my question is,

Since I dont modify the other VALS in the std::map do I need to mutex the modification  of RES?

Thanks in advance

---

### Post by smartbei on 2009-07-16
Since in many implementations of the STL a map is actually a red black tree (see [http://en.wikipedia.org/wiki/Red-black_tree](http://en.wikipedia.org/wiki/Red-black_tree)) I do not think it would be wise to allow non-thread-safe access to the data structure. Alternatively, if the key is an integer, why not use a vector - assuming the size of the vector doesn't change during the thread's runtime, there should be no problem with multiple threads accessing different parts of it.

---

### Post by dwhitney67 on 2009-07-16
You would not need a mutex for the map if you are updating a VALS object that is held by reference (or a pointer).

Only if you plan for your threads to modify the map itself, then you would you need a mutex.

Here's an example where only the contents of the map are examined (not modified), but they could easily be modified without impact to the map:
```

#include <boost/thread.hpp>
#include <map>
#include <iostream>

struct VALS
{
   int value1;
   int value2;
   int value3;
};

class MyThread
{
public:
   MyThread(VALS& vals) : m_vals(vals) {}

   void operator()()
   {
      // here, it is possible to access and/or modify the
      // m_vals contents.
      //
      std::cout << "values = " << m_vals.value1 << ", "
                               << m_vals.value2 << ", "
                               << m_vals.value3
                               << std::endl;
   }

private:
   VALS& m_vals;
};

int main()
{
   using namespace std;

   map<int, VALS> myMap;
   VALS           val1 = {0,1,2};
   VALS           val2 = {3,4,5};
   VALS           val3 = {6,7,8};

   myMap.insert(make_pair(0, val1));
   myMap.insert(make_pair(1, val2));
   myMap.insert(make_pair(2, val3));

   MyThread t0(myMap.find(0)->second);
   MyThread t1(myMap.find(1)->second);
   MyThread t2(myMap.find(2)->second);

   boost::thread_group threads;

   threads.add_thread(new boost::thread(t0));
   threads.add_thread(new boost::thread(t1));
   threads.add_thread(new boost::thread(t2));

   threads.join_all();
}

```
In conclusion, without a mutex, do not modify the map container (ie. do not remove or insert elements), but modifying its contents is ok.

---

### Post by smartbei on 2009-07-16
dwhitney67 has it right - I was assuming that the threads might want to delete/add that certain VALS to the map. On second read however, it appears that the OP meant only to edit them, so there should be a problem.

---

### Post by monkeyking on 2009-07-17
Thanks ppl,
it does indeed seem like you are correct dwhitney.

---

