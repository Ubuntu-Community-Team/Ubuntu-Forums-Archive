---
title: "Any way to lookup key by value - C++ STL Map?"
date: 2009-07-07
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-07-07
I am using a C++ STL Map and I need to lookup both value by key and key by value.  Anyone know how to do this in constant time via STL container?  (I know it's possible to get constant time lookup for the value by key search and then find the key in linear time by iterating through the map and checking each key / value pair.)

---

### Post by Simian Man on 2009-07-07
I don't believe so.  Describe your problem though, there's likely a better solution that having to do this at all.

---

### Post by dwhitney67 on 2009-07-07
To find the value, if it exists, use the find() method.  For example:
```

std::map<int, std::string> MyMap;

MyMap.insert(std::pair(0, "zero"));
MyMap.insert(std::pair(1, "one"));
MyMap.insert(std::pair(2, "two"));
...

// Now find 'value' associated with key '1'
//
std::map<int, std::string>::const_iterator it = MyMap.find(1);

std::string value = it->second;

```

To find the key using a value, will require you do perform a linear search of the map.  To do this, you iterate from the begin() to the end().

```

std::map<int, std::string>::const_iterator it;
int key = -1;

for (it = MyMap.begin(); it != MyMap.end(); ++it)
{
   if (it->second == value)
   {
      key = it->first;
      break;
   }
}

```

---

### Post by Roptaty on 2009-07-07
What about using two maps? One with the key as the key, and another one with the value as the key.

---

### Post by SNYP40A1 on 2009-07-10
> **dwhitney67 said:**
> To find the value, if it exists, use the find() method.  For example:
```

std::map<int, std::string> MyMap;

MyMap.insert(std::pair(0, "zero"));
MyMap.insert(std::pair(1, "one"));
MyMap.insert(std::pair(2, "two"));
...

// Now find 'value' associated with key '1'
//
std::map<int, std::string>::const_iterator it = MyMap.find(1);

std::string value = it->second;

```

To find the key using a value, will require you do perform a linear search of the map.  To do this, you iterate from the begin() to the end().

```

std::map<int, std::string>::const_iterator it;
int key = -1;

for (it = MyMap.begin(); it != MyMap.end(); ++it)
{
   if (it->second == value)
   {
      key = it->first;
      break;
   }
}

```

dwhitney67, that's what I described above...I hoped the avoid the linear search one the value -> key lookup, so I ended up using 2 maps as Roptaty suggested.  Guess it's a simple space / time tradeoff.

---

### Post by Zugzwang on 2009-07-12
> **SNYP40A1 said:**
> Guess it's a simple space / time tradeoff.

Note that this also doesn't give you "constant time" lookup as described as being wanted in your first post! It is actually a "O(log n)" lookup rather than a "O(1)" lookup. You *might* want to consider "std::tr1::unodered_map"s for faster lookup if that is suitable for your application. Then you will however have to write suitable hash functions. Note that depending on the application, it might be fine to stick with the "regular" maps.

---

### Post by kknd on 2009-07-12
> **Roptaty said:**
> What about using two maps? One with the key as the key, and another one with the value as the key.

I think that's the optimal way too.

---

### Post by issih on 2009-07-12
Depends what you are doing, and how dynamic the key/value pairings are, but you might benefit from extending the value object to hold a pointer to the key object, and ensure that you set the key value held on a given value when the pair are added to the map.

ideally you should extend the map definition and override the addition methods to make this foolproof.

Hope that helps

---

### Post by monkeyking on 2009-07-12
> **issih said:**
> Depends what you are doing, and how dynamic the key/value pairings are, but you might benefit from extending the value object to hold a pointer to the key object, and ensure that you set the key value held on a given value when the pair are added to the map.

ideally you should extend the map definition and override the addition methods to make this foolproof.

Hope that helps

Yes, this is a good approch

---

### Post by logoff on 2012-03-07
Boost bidirectional map could be a solution ([boost::bimap]("http://www.boost.org/doc/libs/1_46_1/libs/bimap/doc/html/index.html"))

---

### Post by howefield on 2012-03-07
Back to sleep, old thread...

Closed.

---

