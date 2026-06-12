---
title: "[C++] STL map and iterator"
date: 2012-03-15
forum: Programming Talk
---

### Post by erotavlas on 2012-03-15
Hi,

I have a question about the map and the iterator. For instance if I have a map<string, vector<int> > myMap to insert an element I can do this
```

map<string, vector<int> >::iterator it = myMap.find(name);

    if (it != myMap.end())
    {
        it->second.push_back(integer);
        myMap[name] = it->second;
    }

    else
    {
        vector<int> temp;
        temp.push_back(integer);
        myMap[domainName] = temp;
    }

```
while with a map of map as this map<string, map <string, int> > myMap  
```

    map<string, map <string, int> >::const_iterator it = myMap.find(name);
 
    if(it != myMap.end())
    {
        map <string, int>::const_iterator jt = it->second.find(name2);

        if (jt != it->second.end())
            return false;
        
        map <string, int> temp = it->second;
        temp[name2] = integer;
        myMap[name] = temp;
    }
        
    else
    {
        map <string, int> temp;
        temp[name2] = integer; 
        myMap[name] = temp;        
    }


```
Is it correct? Or I can do it in best way (avoid copying)?

Thank you

---

### Post by MadCow108 on 2012-03-15
the map instert and [] operators have the property of inserting the entry if its not found (after constructing it with the default constructor), so you can do this:

```
  map<string, vector<int> > vmap;
  vmap["a"].push_back(1);
  vmap["a"].push_back(1);
  vmap["b"].push_back(1);

  map<string, map<string, int> > mmap;
  mmap["a"]["a"] = 5;
  mmap["a"]["b"] = 3;
  mmap["b"]["a"] = 3;
  pair<map<string,int>::iterator,bool> ret = mmap["a"].insert(pair<string, int>("a", 4));
  return ret.second


```
[http://www.cplusplus.com/reference/stl/map/insert/](http://www.cplusplus.com/reference/stl/map/insert/)

---

### Post by kingtaurus on 2012-03-15
> **MadCow108 said:**
> the map instert and [] operators have the property of inserting the entry if its not found (after constructing it with the default constructor), so you can do this:

```
  map<string, vector<int> > vmap;
  vmap["a"].push_back(1);
  vmap["a"].push_back(1);
  vmap["b"].push_back(1);

  map<string, map<string, int> > mmap;
  mmap["a"]["a"] = 5;
  mmap["a"]["b"] = 3;
  mmap["b"]["a"] = 3;
  pair<map<string,int>::iterator,bool> ret = mmap["a"].insert(pair<string, int>("a", 4));
  return ret.second


```
[http://www.cplusplus.com/reference/stl/map/insert/](http://www.cplusplus.com/reference/stl/map/insert/)

A few points:
(1) careful with double maps (because mmap["a"]["b"] is not equivalent to mmap["b"]["a"]); it might be better to use 
```

std::map<std::pair<std::string, std::string> >, int>

``` 
(i.e. a single map with key being a pair of strings).
(2) don't use mmap as identifier (its a call in a POSIX operating systems; the compiler shouldn't get confused, but be careful)
(3) you can't use operator[] where the map has been declared const (or is const reference); thus to use an element in the map you have to use const_iterator, find, lower_bound, or upper_bound)
(4) if you want to iterate over elements consider investigating the C++ standard library's for_each or BOOST's foreach

Cheers

---

