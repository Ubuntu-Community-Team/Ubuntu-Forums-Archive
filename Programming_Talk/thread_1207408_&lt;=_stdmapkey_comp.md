---
title: "&lt;= std::map::key_comp"
date: 2009-07-08
forum: Programming Talk
---

### Post by monkeyking on 2009-07-08
Can someone verify that if I need to check for smaller than an equality between 2 keys in a map::key_comp, then I need to use the key_comp twice.
And as such, it will be better to write a seperate function for the '<=', when knowing the explict intricacies of the compare function

[PHP]
std::map::key_comp cmp;

//smaller
return(comp(a,b))

//smaller or equal
return(comp(a,b)||(!comp(a,b)&&!comp(b,a)))

[/PHP]

---

### Post by dwhitney67 on 2009-07-08
I don't quite understand what you are asking?  Perhaps you can rephrase the question.

Also, with respect to the code you posted, you need to specify the Key-type and Value-type when declaring your key_compare object.  Something like:
```

std::map<int, std::string>              mymap;
std::map<int, std::string>::key_compare kcomp = mymap.key_comp();

```
This will provide you with the same comparator function used to initialize the map.  By default, the less<Key> function is used when initializing a map, unless another is provided.

Here's are two examples of defining your own:
```

#include <map>
#include <string>

template <typename T>
struct MyComp
{
   bool operator()(const T& key1, const T& key2) const { return key1 < key2; }
};

bool fncomp(const int key1, const int key2) { return key1 < key2; }

int main ()
{
  typedef bool(*CompFunc)(const int, const int);

  CompFunc fn_ptr = fncomp;

  std::map<int, std::string, MyComp<int> > mymap1;
  std::map<int, std::string, CompFunc>     mymap2(fn_ptr);

  std::map<int, std::string, MyComp<int> >::key_compare mycomp1 = mymap1.key_comp();
  std::map<int, std::string, CompFunc>::key_compare     mycomp2 = mymap2.key_comp();
}

```

---

### Post by monkeyking on 2009-07-08
Sorry for not being clear enough.

I already have a working map, that inserts and finds perfectly.

My key is a custom struct, so is the value, my compare function is also custom.
Thats why I didn't bother to type in the full example.

But given your example.
How would you use the 'mymap.key_comp()' method, to check if 2 keys are equal.

I think 2 method calls are nescerray to accomplish this.

---

### Post by dwhitney67 on 2009-07-08
It would be helpful to know what type of Key you are using.

Second, the key_comp always compares two Keys, an "lhs" and an "rhs", or key1 and key2 as I put it (in an earlier example).

A map can only have one type of key object defined.  Is your key an std:: pair with two values?

---

