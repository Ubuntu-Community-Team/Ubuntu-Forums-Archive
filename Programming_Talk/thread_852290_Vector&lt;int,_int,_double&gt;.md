---
title: "Vector&lt;int, int, double&gt; ?"
date: 2008-07-07
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-07-07
I need a data structure to store a list of 2 ints and a double which I then need to sort.  I am wondering which data structure I should use for optimal efficiency.  The test will involve inserting a few thousand entries, sorting the entries by the first integer only, then printing (traversing the list in sorted order and printing the results).  The test will be run over and over again, clearing the list after each print.  I was thinking that the best way to do this (most efficient, but still somewhat simple / clean) is to do something like this:

struct datastruct {
   int val1;
   int val2;
   double val3;
};

List<datastruct> datalist;

void insertEntry(int first, int second, double third)
{
    datastruct ds1;
    ds1.val1 = first;
    ds1.val2 = second;
    ds1.val3 = third;
    datalist.push_back(ds1);
}

void sortdatastruct()
{
   datalist.sort();
}

Then there would be another function to clear the list and also print the list.  

Other questions:
Since I am filling and then emptying the list for each test, and this will happen many, many times, will the allocated memory be retained (results cleared, but memory still claimed) between each dump and fill?  It would be wasteful for the list to allocate memory as it is filling up, then need more memory, realloc a few times, then on clear free the memory, then as the list fills again, alloc, then realloc...etc.  I am hoping that the memory allocated is not returned after clear in order to avoid allocating it again as the list is filled on the next iteration.

Does anyone see a better data structure for this task?  I only care about sorting by the first integer, the second integer and double can be unsorted, in any order.  There will not be any duplicates in the list.

---

### Post by SNYP40A1 on 2008-07-07
I used list and vector interchangeably in the previous post.  Indexing is not important, so a list would work.

---

### Post by gnusci on 2008-07-07
The structure is fine for your purpose, I assume you will use STL so there shouldn't be memory problems if you **clear** the List before to fill it again.

---

### Post by tanderson on 2008-07-08
Would a multimap using your conditional integer as your key work?

---

### Post by Zugzwang on 2008-07-08
There is no need to build your own data structure, the boost library already contains tuples. So you could do something like
[PHP]
#include <list>
#include "boost/tuple/tuple.hpp"

int main() {
    std::list<boost::tuple<int,int,double> > datalist;
    datalist.push_back(boost::tuple<int,int,double>(1,2,3.4));
}
[/PHP]

There's even a comparison operator provided, but you might want to provide your own in order to sort only for the first item (instead of doing it lexicographically) 

For more details, look [here]("http://www.boost.org/doc/libs/1_35_0/libs/tuple/doc/tuple_users_guide.html"). And don't forget to install the "libboost-dev" package if you choose to use this solution.

---

### Post by dwhitney67 on 2008-07-08
You can use an STL map if you want the data sorted after each insert.  This can be costly in terms of time.  Or you can use an STL list as in your example; insert all data at the end of the list (very quick btw!), and when done with all the inserts, then sort the list.

I have pasted two examples below, both using the STL list.  The second example uses the Boost tuple as Zugzwang suggested.  Either way, they both yield the same results.  Note that I did not test either with a large pool of data.

Example1:
[PHP]#include <iostream>
#include <list>


struct Data
{
  Data( int v1, int v2, double v3 )
  {
    val1 = v1;
    val2 = v2;
    val3 = v3;
  }

  bool operator<( const Data &other ) const
  {
    return this->val1 < other.val1;
  }

  friend std::ostream & operator<<( std::ostream &os, const Data &ds )
  {
    os << ds.val1 << ", " << ds.val2 << ", " << ds.val3;

    return os;
  }

  int    val1;
  int    val2;
  double val3;
};


class DataList
{
  public:
    DataList() {}
    ~DataList() {}

    void insertEntry( Data ds )
    {
      m_datalist.push_back( ds );
    }

    void sortEntries()
    {
      m_datalist.sort();
    }

    friend std::ostream & operator<<( std::ostream &os, const DataList &dl )
    {
      for ( DL_Iterator it = dl.m_datalist.begin(); it != dl.m_datalist.end(); ++it )
      {
        os << *it << std::endl;
      }

      return os;
    }

  private:
    typedef std::list< Data >  DL;
    typedef DL::const_iterator DL_Iterator;

    DL m_datalist;
};


int main()
{
  DataList datalist;

  datalist.insertEntry( Data(3,  6,  9.9) );
  datalist.insertEntry( Data(6, 12, 18.8) );
  datalist.insertEntry( Data(1,  2,  3.3) );

  datalist.sortEntries();

  std::cout << datalist << std::endl;

  return 0;
}[/PHP]
Example 2:
[PHP]#include <iostream>
#include <list>
#include <boost/tuple/tuple.hpp>


typedef boost::tuple< int, int, double > Data;

class CompareData
{
  public:
    bool operator()( const Data &d1, const Data &d2 )
    {
      return d1.get<0>() < d2.get<0>();
    }
};


class DataList
{
  public:
    DataList() {}
    ~DataList() {}

    void insertEntry( Data data )
    {
      m_datalist.push_back( data );
    }

    void sortEntries()
    {
      m_datalist.sort( CompareData() );
    }

    friend std::ostream & operator<<( std::ostream &os, const DataList &dl )
    {
      for ( DL_Iterator it = dl.m_datalist.begin(); it != dl.m_datalist.end(); ++it )
      {
        os << it->get<0>() << ", "
           << it->get<1>() << ", "
           << it->get<2>()
           << std::endl;
      }

      return os;
    }

  private:
    typedef std::list< Data >   DL;
    typedef DL::const_iterator  DL_Iterator;

    DL m_datalist;
};


int main()
{
  DataList datalist;

  datalist.insertEntry( Data(3,  6,  9.9) );
  datalist.insertEntry( Data(6, 12, 18.8) );
  datalist.insertEntry( Data(1,  2,  3.3) );

  datalist.sortEntries();

  std::cout << datalist << std::endl;

  return 0;
}[/PHP]

---

### Post by dribeas on 2008-07-16
[QUOTE=SNYP40A1;5338042The test will involve inserting a few thousand entries, sorting the entries by the first integer only, then printing (traversing the list in sorted order and printing the results).  The test will be run over and over again, clearing the list after each print.

Other questions:
Since I am filling and then emptying the list for each test, and this will happen many, many times, will the allocated memory be retained.

Does anyone see a better data structure for this task?  I only care about sorting by the first integer, the second integer and double can be unsorted, in any order.  There will not be any duplicates in the list.[/QUOTE]

A couple of thoughts: you can hint vector on the size you want to use avoiding unnecessary reallocs/copies:

```
vector<Data> v( 1000 ); // Assure that vectors capacity is at least 1000

```

If you use (as suggested before) v.clear() then vector is marked as empty (v.empty() == true, v.size()==0) but memory will not be released (v.capacity() remains constant through the operation), which seems to be what you want (no new memory/copies will be required until previous capacity is reached). If you needed, on the other hand to release the memory, you would need to do:

```

vector<Data> v( 1000 );
{
   vector<Data> tmp;
   v.swap(tmp); // Exchanges internal data structures
} // tmp is destroyed and memory released

```

This will not clear all memory, but will keep the minimum size that the C++ implementation allows.

About other data structures

std::list, std::map, std::multimap do request and free memory on each insertion and deletion, so if you are concerned on memory allocations you should avoid them.

std::map and std::multimap keep the data ordered in a balanced binary search tree (O(n log n) cost per insertion, data is already ordered), std::sort requires random access iterators, which means that you cannot use it to sort lists, but you need std::list::sort, which is usually implemented as mergesort (O(n log n) complexity).

std::sort has been implemented in different ways in STL implementations, with quicksort being a common choice of implementors, with some variants as SGI's STL using introsort. On the other hand, sorting a vector requires copying data back and forth from different positions in the vector internal data structure, while sorting a list requires only moving pointers arround. That means that for big data structures (not your case, I believe) if the cost of copying superseeds the advantage of the faster sort algorithm sorting a vector could be slower than sorting a list...

Now, go figure... Is it memory allocation/deallocation, sorting, copying data back and forth your higher cost? You should meassure and then decide. I would go for std::vector and std::sort, but that's just intuition.

David Rodríguez Ibeas

---

