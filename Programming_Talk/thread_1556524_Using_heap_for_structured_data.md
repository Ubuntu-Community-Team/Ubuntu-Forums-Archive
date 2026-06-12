---
title: "Using heap for structured data"
date: 2010-08-19
forum: Programming Talk
---

### Post by davoudi on 2010-08-19
I read about the algorithm class and how heap can nicely works as priority queue. My problem is that the heap just can handle unstructured data like a vector of integer, double etc. My problem is that I have a structured data, the simplest form contains two set of number, the first one is the ID (an integer) and the second one is a double defines the priority. For example, I need to know the ID of a data with highest priority rather than the priority itself. I read a little about boost library and tuple but I don't know how to feed a vector of tuple into a heap and extract the data from it. Any help would be very appreciated.

---

### Post by dwhitney67 on 2010-08-19
Unstructured?

If you have two pieces of data, group them together into a struct.

As for storing them in the heap, allocate space to store them.  If you want a specialized container, whether from the STL or home-made, then use such.

I'm not quite following why you seem to think there is some issue using the heap.

---

### Post by davoudi on 2010-08-19
> **dwhitney67 said:**
> Unstructured?

If you have two pieces of data, group them together into a struct.

As for storing them in the heap, allocate space to store them.  If you want a specialized container, whether from the STL or home-made, then use such.

I'm not quite following why you seem to think there is some issue using the heap.

 I read about the algorithm class here :[http://www.cplusplus.com/reference/algorithm/](http://www.cplusplus.com/reference/algorithm/).
I really like the way that make_heap, push_heap, etc work. In all examples there, they use heap to deal with unstructured data, like a vector of integer. So I don't know how to use those methods for the structured data.

---

### Post by smartbei on 2010-08-19
I believe what the OP means is that he has some data that is to be sorted according to some score, such that he can access the data in the order specified by the score.

For example, in python:
```

>>> heap = []
>>> heapq.heappush(heap, (27, "should_be_third"))
>>> heapq.heappush(heap, (15, "should_be_second"))
>>> heapq.heappush(heap, (4, "should_be_first"))
>>> heapq.heappush(heap, (79, "should_be_fourth"))
>>> heapq.heappop(heap)
(4, 'should_be_first')
>>> heapq.heappop(heap)
(15, 'should_be_second')
>>> heapq.heappop(heap)
(27, 'should_be_third')
>>> heapq.heappop(heap)
(79, 'should_be_fourth')
>>> heapq.heappop(heap)

```

Or, for code that works in cpp using STL:
```

#include <iostream>
#include <queue>
using namespace std;


struct mydata
{
    // This class just holds an int as data (could be an index, etc.)
    // you can change it to hold whatever you want and it should still work as intended.
    unsigned int m_score;
    unsigned int m_data;

    // This function is the key - it returns the comparison.
    bool operator<(const mydata & other) const {
        return m_score < other.m_score;
    };

    mydata(unsigned int score, unsigned int data) : m_score(score), m_data(data) {};
};

int main()
{
    priority_queue<mydata> Q;

    Q.push(mydata(27, 1001));
    Q.push(mydata(9919, 100001));
    Q.push(mydata(4, 101));
    Q.push(mydata(999, 10001));

    cout << Q.top().m_data << endl; Q.pop();
    cout << Q.top().m_data << endl; Q.pop();
    cout << Q.top().m_data << endl; Q.pop();
    cout << Q.top().m_data << endl; Q.pop();

    return 0;
}

```

---

### Post by MadCow108 on 2010-08-19
> **davoudi said:**
> I read about the algorithm class here :[http://www.cplusplus.com/reference/algorithm/](http://www.cplusplus.com/reference/algorithm/).
I really like the way that make_heap, push_heap, etc work. In all examples there, they use heap to deal with unstructured data, like a vector of integer. So I don't know how to use those methods for the structured data.

c++ is templated language, the algorithms and containers work with any (static) type you wish, no matter how complex
you just have to provide the appropriate operators

```

#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;

class Data {
  public:
    Data(int ID_, double prio_) : ID(ID_), priority(prio_) {}
    int ID;
    double priority;
    // used by default
    bool operator<(const Data & that) const {
      // this can be as complicated as you wish, but it should have no side effects
      return this->priority < that.priority;
    }
};

// used when requested, binary_function is optional, but allows using adaptors
struct DataCmp : public binary_function<Data, Data, bool> {
  bool operator()(const Data & a, const Data & b) const {
    return a.priority >=b.priority;
  }

}; 

int main(int argc, const char *argv[])
{
  vector<Data> d;
  d.push_back(Data(1, 0.5));
  d.push_back(Data(2, 1.5));
  d.push_back(Data(3, 0.1));
  // use default
  make_heap(d.begin(), d.end());
  cout << "front " << d.front().ID << endl;
  pop_heap(d.begin(), d.end());
  d.pop_back();
  cout << "next " << d.front().ID << endl;
  pop_heap(d.begin(), d.end());
  d.pop_back();
  cout << "next " << d.front().ID << endl;
  d.pop_back();

  // use non default operator
  d.push_back(Data(1, 0.5));
  d.push_back(Data(2, 1.5));
  d.push_back(Data(3, 0.1));
  make_heap(d.begin(), d.end(), DataCmp());
  cout << "front " << d.front().ID << endl;
  pop_heap(d.begin(), d.end(), DataCmp());
  d.pop_back();
  cout << "next " << d.front().ID << endl;
  pop_heap(d.begin(), d.end(), DataCmp());
  d.pop_back();
  cout << "next " << d.front().ID << endl;
  return 0;
}


```

---

### Post by davoudi on 2010-08-19
Thanks a lot for your input. I got the idea from your example.

---

