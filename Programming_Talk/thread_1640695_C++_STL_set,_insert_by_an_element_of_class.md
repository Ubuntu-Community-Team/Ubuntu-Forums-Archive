---
title: "C++ STL set, insert by an element of class"
date: 2010-12-08
forum: Programming Talk
---

### Post by AlGorism on 2010-12-08
Hi.
I implemented a class like this: 

class term {
 public:
string name;
int *p;
}

I will keep terms with set STL. Then, I want to sort the elements by their names. However, I don't know how to use insert(); because, the examples don't show if I can sort by name.
I want to know if I can sort objects by an attribute of that class? Here is name?

---

### Post by Zugzwang on 2010-12-08
The stl set class by default uses the comparator of a class to sort its elements. So you can simply define it to have it sorted after "name" as follows:

[PHP]
#include <iostream>
#include <set>

using namespace std;

class term {
public:
    string name;
    int p;

    term(string _name, int _p) : name(_name), p(_p) {};
    bool operator< (const term& b) const {
        return name < b.name;
    }
};

int main(int argv, char **args) {
    std::set<term> data;
    data.insert(term("hello",4));
    data.insert(term("test",1));
    data.insert(term("anywhere",2));
    data.insert(term("two-fold",7));
    data.insert(term("nothing",42));
    for (std::set<term>::const_iterator it = data.begin();it!=data.end();it++) {
        std::cout << it->name << ", " << it->p << std::endl;
    }
}
[/PHP]

Output:
```

me@my-computer:/tmp$ g++ test.cpp
me@my-computer:/tmp$ ./a.out 
anywhere, 2
hello, 4
nothing, 42
test, 1
two-fold, 7

```

Note the code is a little bit untypical for C++ as there are no getters in the "term" class.

EDIT: Also look here: [http://stackoverflow.com/questions/1114856/stdset-with-user-defined-type-how-to-ensure-no-duplicates](http://stackoverflow.com/questions/1114856/stdset-with-user-defined-type-how-to-ensure-no-duplicates) - Apparently, in the C++ standard it is stated that (25.3:3) "For the algorithms to work correctly, comp (the comparator) has to induce a strict weak ordering on the values". Thus, duplicate names in the set might cause problems.

---

### Post by AlGorism on 2010-12-08
Thanks, I thought that but I wasn't sure. Now it works very well.

For adding duplicate names: I tried now, and it doesn't add to set the duplicated one. 
Also, if you try to use find(), you can do it by this way:

For instance, finding "test":
[PHP]
it=data.find(term("test",0));
std::cout << it->name << ", " << it->p << std::endl;[/PHP]Output should be like this:

```
test, 1
```

---

### Post by Zugzwang on 2010-12-09
> **AlGorism said:**
> For adding duplicate names: I tried now, and it doesn't add to set the duplicated one. 


Ok, but apparently, this is undefined behaviour. Somewhere in the link that I've provided you, there's a link to an example where this behaviour breaks. You should definitely try avoiding having undefined behaviour in your program.

BTW: Do you know maps? These have defined behaviour with respect to duplicates. If you want to sort only by the name, these might be precisely what you want.

---

### Post by dwhitney67 on 2010-12-09
> **Zugzwang said:**
> Ok, but apparently, this is undefined behaviour. Somewhere in the link that I've provided you, there's a link to an example where this behaviour breaks. You should definitely try avoiding having undefined behaviour in your program.

BTW: Do you know maps? These have defined behaviour with respect to duplicates. If you want to sort only by the name, these might be precisely what you want.

I do not see it as undefined behaviour; it is clearly documented [here]("http://www.cplusplus.com/reference/stl/set/") that an STL set cannot store duplicate values.  If you wish to store duplicate values, then use an STL multiset.

P.S.  With an STL map, one has the same issue.  Duplicate values cannot be stored using the same key.  To store multiple values using the same key, one can use the STL multimap.

---

### Post by Zugzwang on 2010-12-09
> **dwhitney67 said:**
> P.S.  With an STL map, one has the same issue.  Duplicate values cannot be stored using the same key.  To store multiple values using the same key, one can use the STL multimap.

Ah, ok, it looks like I misinterpreted "strict weak ordering" - apparently, strict weak orders do not have to be total orders. I was referring to [this post]("http://stackoverflow.com/posts/1123118/revisions"), but that one is, making a closer look, about something different. Also, the behaviour of calling "insert()" on an element which is already in the set seems to be well-defined. So you are right - there shouldn't be any problems.

---

### Post by AlGorism on 2010-12-17
Hi again. 
I figured out how.

A compare class should be implemented to keep complex classes via set. Here is an example:
[http://anwarmamat.blogspot.com/2008/02/cstl-set-example.html](http://anwarmamat.blogspot.com/2008/02/cstl-set-example.html)

---

### Post by dwhitney67 on 2010-12-17
> **AlGorism said:**
> Hi again. 
I figured out how.

A compare class should be implemented to keep complex classes via set. Here is an example:
[http://anwarmamat.blogspot.com/2008/02/cstl-set-example.html](http://anwarmamat.blogspot.com/2008/02/cstl-set-example.html)

Great, you found out another way, however as indicated earlier, you could avoid the additional comparator-class by merely implementing a comparator-function within your 'term' class.  Refer to Zugswang's post for how to do this.

P.S.  It is more commonplace to see one implement the "bool operator<(...) const" method within a class, than to see one implement a class comparator.  I personally do not agree with Anwar Mamat's suggestion.

---

### Post by AlGorism on 2010-12-29
> **dwhitney67 said:**
> 
P.S.  It is more commonplace to see one implement the "bool operator<(...) const" method within a class, than to see one implement a class comparator.  I personally do not agree with Anwar Mamat's suggestion.

Can you tell me why?

---

### Post by MadCow108 on 2010-12-29
it depends on the kind of class and the data is contains.
If it has a single natural ordering it makes more sense to implement it in the class.
E.g. an integer class, there is only one way to compare integers, so we can associate the comparison with the data by implementing a < operator in the class.

If you have a aggregate data type which can be compared in many different ways and none of the ways is significantly more important than others it is not advantageous to add one as special by implementing it in the < operator (but it also does little harm)
In this case comparison functors makes more sense.
just remember to derive your functors from binary_function to be able to use the STL adaptors.
[http://www.cplusplus.com/reference/std/functional/binary_function/](http://www.cplusplus.com/reference/std/functional/binary_function/)

---

### Post by Lootbox on 2010-12-29
If you want to store multiple entries with the same name in a std::set, you can also refine your comparison operator to differentiate based on an additional field:

```
bool operator<(const term& other) const {
    // Order by name first:
    if (name != other.name) {
        return name < other.name;
    }

    // If names are the same, order by p:
    return p < other.p;
}
```
This would allow you to store term("Hello", 5) and term("Hello", 6) as different entries in the same std::set.

I would also personally avoid using a comparison functor for an example as simple as this. It requires a good amount of boiler-plate to accomplish the same functionality.

As MadCow explained, however, if you have a need for multiple ways to compare and sort your term objects (i.e. by string only, by string first and then by int, etc.), then you'll have to supply those as separate comparators. A functor would also be more appropriate if you wanted to access additional data inside the function without resorting to global data.

---

### Post by AlGorism on 2010-12-30
Thanks people. I had really useful information.

---

