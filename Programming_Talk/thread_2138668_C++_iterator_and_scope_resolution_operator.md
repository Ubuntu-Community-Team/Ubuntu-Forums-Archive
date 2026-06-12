---
title: "C++ iterator and scope resolution operator"
date: 2013-04-24
forum: Programming Talk
---

### Post by cybo on 2013-04-24
I have't coded a lot in C++ and when I did the coding that I have done was pretty simple. To remedy the situation I decided to read more about it, so I decided to search for C++ tutorials. I bumped onto an MIT OpenCourseware website for C++,[http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-096-introduction-to-c-january-iap-2011](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-096-introduction-to-c-january-iap-2011)

One of the lectures has the following piece of code:

```
set<int>::iterator it;
```

I understand what it means (create an iterator over a set of integers) but I can't see how would one implement it in the set class. Is iterator a constructor, a function or something else?
I know if I have a templated class with a method, the code would look something like this:
```

template <typename T>
class MyClass {
  public:
    T myMethod(T a) {return a;}
};
int main(void) {
  MyClass<int> myObj;
  int a = 10;
  int b = myObj.myMethod(a);
  return 0;
}

```

But how would the code look like for the returning of an instance of an iterator, i.e for
```
set<int>::iterator it;
```

Any help is appreciated.

---

### Post by dwhitney67 on 2013-04-25
> **cybo said:**
> 
One of the lectures has the following piece of code:
```
set<int>::iterator it;
```

The code above is merely a declaration of an iterator to a set of int values; it is not presently assigned a value.

Think of an iterator a merely being a pointer (but actually a more complex class object).  It can be assigned to reference a particular element in a group of data.  When a forward iterator (similar to your example) is incremented, it references either the next element or is at the end of the group of data.  A reverse iterator is also typically provided for STL constructs.

In your simple class example, an iterator would not be necessary because it does not hold any data.  In fact, it is quite rare for one to implement an iterator, because the STL provides it already for the various classes it offers.

When I developed my own List class, without using STL, my iterator class appears as the following:
```

    class ListIterator
    {
      public:
        typedef T iterator_category;

        ListIterator(Node* head) : m_node(head) {}

        ListIterator(const ListIterator& it) : m_node(it.m_node) {}

        bool operator==(const ListIterator& other) const { return m_node == other.m_node; }
        bool operator!=(const ListIterator& other) const { return m_node != other.m_node; }

        void operator++() const // goto the next element
        {
          assert(m_node != 0);
          m_node = m_node->m_next;
        }

        void operator--() const // goto the previous element
        {
          assert(m_node != 0);
          m_node = m_node->m_prev;
        }

        const T& operator*() const // access the current element
        {
          assert(m_node != 0);
          return m_node->m_elem;
        }

        T& operator*() // access the current element
        {
          assert(m_node != 0);
          return m_node->m_elem;
        }

    private:
        friend class List<T>;
        mutable Node* m_node;
    };

```

Usage of the List would be something like:
```

nonstd::List<int> myList;

myList.push_front(10);
myList.push_front(3);
myList.push_front(6);

myList.sort();

for (nonstd::List<int>::iterator it = myList.begin(); it != myList.end(); ++it)
{
    std::cout << *it << std::endl;
}

```

---

### Post by cybo on 2013-04-25
> **dwhitney67 said:**
> The code above is merely a declaration of an iterator to a set of int values; it is not presently assigned a value.

Think of an iterator a merely being a pointer (but actually a more complex class object).  It can be assigned to reference a particular element in a group of data.  When a forward iterator (similar to your example) is incremented, it references either the next element or is at the end of the group of data.  A reverse iterator is also typically provided for STL constructs.

In your simple class example, an iterator would not be necessary because it does not hold any data.  In fact, it is quite rare for one to implement an iterator, because the STL provides it already for the various classes it offers.

When I developed my own List class, without using STL, my iterator class appears as the following:
```

    class ListIterator
    {
      public:
        typedef T iterator_category;

        ListIterator(Node* head) : m_node(head) {}

        ListIterator(const ListIterator& it) : m_node(it.m_node) {}

        bool operator==(const ListIterator& other) const { return m_node == other.m_node; }
        bool operator!=(const ListIterator& other) const { return m_node != other.m_node; }

        void operator++() const // goto the next element
        {
          assert(m_node != 0);
          m_node = m_node->m_next;
        }

        void operator--() const // goto the previous element
        {
          assert(m_node != 0);
          m_node = m_node->m_prev;
        }

        const T& operator*() const // access the current element
        {
          assert(m_node != 0);
          return m_node->m_elem;
        }

        T& operator*() // access the current element
        {
          assert(m_node != 0);
          return m_node->m_elem;
        }

    private:
        friend class List<T>;
        mutable Node* m_node;
    };

```

Usage of the List would be something like:
```

nonstd::List<int> myList;

myList.push_front(10);
myList.push_front(3);
myList.push_front(6);

myList.sort();

for (nonstd::List<int>::iterator it = myList.begin(); it != myList.end(); ++it)
{
    std::cout << *it << std::endl;
}

```

Thanks. I think I got it. I did more googling and found a page that explains iterators pretty well, even how do define one. Here it is [http://www.cs.northwestern.edu/~riesbeck/programming/c++/stl-iterator-define.html](http://www.cs.northwestern.edu/~riesbeck/programming/c++/stl-iterator-define.html)

---

