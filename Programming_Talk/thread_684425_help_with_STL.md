---
title: "help with STL"
date: 2008-02-01
forum: Programming Talk
---

### Post by arielsegal on 2008-02-01
Hi,
I need to maintain a list of pairs of two elements of type string. One string serves as a key, so I'll be able to access the element with it, but I also need to be able to access the element by an index, which is the place of the element in the array.
I thought of using the STL types map and vector. The map will hold the key and the other field, and the vector will be a list of key strings by order.
To access an element by index, first get the key from the vector by the index, then use the key to access the map.
I'm sure there is a better way, but I don't know enough STL to think of such a way.
Does anyone know a better way?

---

### Post by hod139 on 2008-02-01
You need to be more specific with your goals.  For example, a vector of string pairs will satisfy your requirements.
```

std::vector< std::pair< std::string, std::string > > stringVec.

```
Accessing an element by the index is constant time O(1).
Accessing the element by the first string will require iterating over the elements: linear time O(n) where n is the number of elements in the list.

Your method of using two data structures is more complicated and uses more memory, but you gain:
Lookup by index is still constant .
Lookup by key is now log(n)  (std::maps are stored as red-black trees not hashtables)
However, you have to be careful because now you have to maintain the relationship between the two structures.  A map must have unique elements, a vector does not.

Some other thoughts, 
Why do you need to lookup by both index and key?
If you really do need to lookup by both index and key, which will you use more frequently?
Why are you using strings as the keys, string comparisons will be slower than some primitive type?
Deletions from a vector are very expensive.

---

### Post by aks44 on 2008-02-01
In addition to hod's very good advices, I may add that (depending on your usage pattern) you may want to keep that container ordered (according to your key) so that you can use a binary search for your lookups. This assumes a container that supports random access.

std::deque may also be a better container than a vector, insertions and deletions will be way cheaper than with a vector and it doesn't have much more overhead when accessing items.

---

