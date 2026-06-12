---
title: "Simplest way to implement hash table in C or C++?"
date: 2012-10-29
forum: Programming Talk
---

### Post by Kdar on 2012-10-29
What is simplest and quickest way to implement hash table in C or C++?

---

### Post by dazman19 on 2012-10-30
What does your tutorial notes say?

having two arrays, one for the key, and one for the value would be a good start.

---

### Post by dwhitney67 on 2012-10-30
> **Kdar said:**
> What is simplest and quickest way to implement hash table in C or C++?

In C++, there's no need to implement the hash table; use an unordered_map instead.

```

#include <string>

#ifndef __GXX_EXPERIMENTAL_CXX0X__
    #include <tr1/unordered_map>
    typedef std::tr1::unordered_map<std::string, std::string> HashMap;
#else
    #include <unordered_map>
    typedef std::unordered_map<std::string, std::string> HashMap;
#endif

int main()
{
    using namespace std;

    HashMap myMap;

    myMap.insert(make_pair<string, string>("Foo", "Bar"));

    // ...
}

```

To use the C++0x version of the unordered_map, compile your code with the following option:  -std=c++0x

---

### Post by Kdar on 2012-11-01
thanks... I will try to use unordered_map...

Do you know what is the difference between map and unordered_map? I heard I could use map as well for hash table.

---

### Post by dwhitney67 on 2012-11-01
> **Kdar said:**
> thanks... I will try to use unordered_map...

Do you know what is the difference between map and unordered_map? I heard I could use map as well for hash table.

The STL map is sorted by key value.

---

### Post by Kdar on 2012-11-01
> **dwhitney67 said:**
> The STL map is sorted by key value.

Can I generate unique key with a hash function or it is only with unordered map?

---

