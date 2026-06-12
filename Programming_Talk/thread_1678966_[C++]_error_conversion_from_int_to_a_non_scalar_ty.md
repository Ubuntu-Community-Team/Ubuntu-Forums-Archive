---
title: "[C++] error: conversion from int to a non scalar type"
date: 2011-01-31
forum: Programming Talk
---

### Post by erotavlas on 2011-01-31
Hi all,
I have a problem with the following code inside a class. I have copied it from a book of a C++ course. The error is on the if statement-> error: conversion from "int" to a non scalar type "std::multimap<std::vector<std::string, std::allocator<std::string> >, float, std::less<std::vector<std::string, std::allocator<std::string> > >, std::allocator<std::pair<const std::vector<std::string, std::allocator<std::string> >, float> > >' requested|.
How can I correct it?

```

std::multimap<std::vector<std::string>, Value> GetMap (const std::string&name) const
    {

std::map<std::string, std::multimap<std::vector<std::string>, Value> >::const_iterator it = Map.find(name);

     if (it == Map.end())
         return NULL;

return it->second;

```

Thank you

---

### Post by Zugzwang on 2011-01-31
Technically, you can't. You described a function that returns a "std::multimap<std::vector<std::string>, Value>". However, NULL is not a multimap but you are still trying to return it. Now what you can do is to return an empty multimap. But strictly speaking that is not the same and might not be the intended meaning of that function. Thus, depending on the environment from which your function is called, returning "std::multimap<std::vector<std::string>, Value>()" instead of NULL *might* be an acceptable fix.

---

### Post by erotavlas on 2011-01-31
Thank you, with your suggestion it works. An other question, is your tip safely?i.e. is a good programming tip?

---

### Post by Zugzwang on 2011-01-31
> **erotavlas said:**
> Thank you, with your suggestion it works. An other question, is your tip safely?i.e. is a good programming tip?

No, certainly not. As already written, whether returning just a newly made multimap or not may or maybe acceptable, depending on the situation in which the function is applied. Typically, one would rather return some kind of iterator type, which contains information on whether the element has been found or not, and a reference to the object found. If you want to prevent modifying the multimap from outside (which you do by copying it instead of returning a reference or pointer to the object found), you would rather give a const reference or pointer to the object found. Here's a way that uses pairs, where the first element returned is information whether the element has been found and if yes, the second one gives a reference (warning: not tested and might have to be slightly changed):

```

std::pair<bool, std::multimap<std::vector<std::string>, Value> const&>GetMap (const std::string&name) const {
        std::map<std::string, std::multimap<std::vector<std::string>, Value> >::const_iterator it = Map.find(name);

        return std::pair<bool, std::multimap<std::vector<std::string>, Value> const&>(it!=Map.end();it->second);
}

```

But actually, your class having something like a "GetMap" function is already an indication for not-so-clean OOP design of the overall project.

---

