---
title: "[C++] Question about vector and multimap"
date: 2011-01-18
forum: Programming Talk
---

### Post by erotavlas on 2011-01-18
Hi,

I have two question:
1) the first one is about the vector. I have a vector of pointers to a class vector<class1 *> vector1; the class contains a string name that identify it.
```
class class1 {
private:
string name;
}
```
I have to search inside the vector1 to find if an element is already present before insert it. Have I to make a loop and search inside the vector or can I use the find function of algorithm library?
In the second case how can I do? find(vector1.begin(), vector1.end(), name_to_search) is wrong.
 
2) the second question is about a multimap multimap<vector<string>, float> multimap1. I have to search in a multimap1 if an element is already present and in this case I have to search in the set of the values if is present a value (a multimap can have different values for the same key). I know that I need to use multimap1.equal_range(key), how?

```

for (multimap<vector<string>, float>::const_iterator it=multimap1.equal_range(chiave).first; it!=multimap1.equal_range(key).second; ++it)
{
      if (it->second == value)
            std::cout << "found" << std::endl;
}
```
 
thank you

---

### Post by worksofcraft on 2011-01-18
> **erotavlas said:**
> Hi,

I have two question:
1) the first one is about the vector. I have a vector of pointers to a class vector<class1 *> vector1; the class contains a string name that identify it.
```
class class1 {
private:
string name;
}
```
I have to search inside the vector1 to find if an element is already present before insert it. Have I to make a loop and search inside the vector or can I use the find function of algorithm library?
In the second case how can I do? find(vector1.begin(), vector1.end(), name_to_search) is wrong.
 
2) the second question is about a multimap multimap<vector<string>, float> multimap1. I have to search in a multimap1 if an element is already present and in this case I have to search in the set of the values if is present a value (a multimap can have different values for the same key). I know that I need to use multimap1.equal_range(key), how?

```

for (multimap<vector<string>, float>::const_iterator it=multimap1.equal_range(chiave).first; it!=multimap1.equal_range(key).second; ++it)
{
      if (it->second == value)
            std::cout << "found" << std::endl;
}
```
 
thank you

Since your vector is a vector of pointers, by default the find template will be searching for a pointer... not a string inside an object that it points to.

If you want to do that then you must create your own comparator object that takes those two pointers and compares the strings of the objects they point to.

I think you need do same for the multi-map, it depends about what you consider to be equal. Like if your key and floating point values are exactly equal, if the value is within a small error etcetera...

remember that comparing floating point for equality is unreliable due to rounding errors.

---

