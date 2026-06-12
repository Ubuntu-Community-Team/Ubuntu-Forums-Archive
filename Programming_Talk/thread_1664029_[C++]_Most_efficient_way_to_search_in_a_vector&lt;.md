---
title: "[C++] Most efficient way to search in a vector&lt;string&gt;"
date: 2011-01-10
forum: Programming Talk
---

### Post by erotavlas on 2011-01-10
Hi all,

I have to search inside a vector<string>. How can I search in it in efficient way? The vector can't be ordered because the order must remain the same.

Thank

---

### Post by dwhitney67 on 2011-01-10
Well, the vector is basically a "glorified" array.  If the contents of your array are unsorted, then the string you search for could be at the beginning, somewhere in the middle, or at the very end of the vector.

I cannot think of any easy way to search the vector other than iterating one element at a time and then comparing against your target string.  If it were sorted, then you could attempt a binary search.

So your choices are:

1.  Work with the one unsorted vector and search for the target string

2.  Create a sorted copy of the vector, and then attempt a binary search for the target string.

If you go with option 1, you can use the STL find() function:
```

#include <algorithm>
...
std::vector<std::string>::const_iterator it = std::find(vec.begin(), vec.end(), "some string");

if (it != vec.end())
{
   std::cout << "Found '" << *it << "' in the vector." << std::endl;
}

```

---

### Post by thk on 2011-01-10
Do you mean space or time efficient? Energy efficient? These are all different concepts.

You can use an external index, something like

```
map<string, size_t> indx;
```

that maps each string to its position in the vector. If you have duplicate strings you could use

```
map<string, vector<size_t> > indx;
```

or

```
map<string, set<size_t> > indx;
```

These give O(log n) look up. Hash maps will give better performance on average.

---

### Post by MadCow108 on 2011-01-11
> **thk said:**
> Do you mean space or time efficient? Energy efficient? These are all different concepts.

You can use an external index, something like

```
map<string, size_t> indx;
```

that maps each string to its position in the vector. If you have duplicate strings you could use

```
map<string, vector<size_t> > indx;
```

or

```
map<string, set<size_t> > indx;
```

These give O(log n) look up. Hash maps will give better performance on average.

a multimap might be preferable to a map of a container.
[http://www.cplusplus.com/reference/stl/multimap/](http://www.cplusplus.com/reference/stl/multimap/)

---

### Post by erotavlas on 2011-01-11
Thank you for your answers. So there are no efficient ways as searching inside a map.
I have other question: if I have a vector<pair<bool, string> and I want to search inside the second element, how have I to do?

Thank

---

### Post by MadCow108 on 2011-01-11
yes there are more efficient ways, depending on your requirement, e.g. the already mentioned hashtable (=unordered map) or a radix tree, ....
map is O(logN) accumulated and worst case
hash table would be O(1) accumulated and O(N) worst case
radix tree is O(1) worst case but is less versatile than the above (and may have higher constant factor depending on implementation)

for searching in the second element write a custom comparison function, e.g. for the linear find_if using ==
```

template<typename T>
struct equal_second : public unary_function<bool, T> {
  equal_second(const T & c) : search(c) {}
  bool operator()(const T & a) const {
    return a.second == search.second;
  }
  const T & search;
};

..
iterator = find_if(container.begin(), container.end(), equal_second<pairtype>(make_pair(true,"bla")));

```
for maps you need the < binary comparison

---

### Post by dwhitney67 on 2011-01-11
> **erotavlas said:**
> Thank you for your answers. So there are no efficient ways as searching inside a map.
I have other question: if I have a vector<pair<bool, string> and I want to search inside the second element, how have I to do?

Thank

Again, if it is an unsorted vector, you will need to manually iterate through the whole thing.  If you do not know how to do this, then why are using using a vector (and a pair)?  You can read about vectors [here]("http://www.cplusplus.com/reference/stl/vector/").

If the vector is sorted, then you may be able to use one of the Binary Search algorithm functions described [here]("http://www.cplusplus.com/reference/algorithm/").  You would want to use a function in which you can specify your own comparator function that examines the "second" portion of the std::pair value.

---

