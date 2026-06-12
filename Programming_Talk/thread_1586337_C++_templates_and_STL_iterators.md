---
title: "C++ templates and STL iterators"
date: 2010-10-01
forum: Programming Talk
---

### Post by DBQ on 2010-10-01
Hi everyone. I have a question regarding C++ templates and how to use them for STL.

I want to write a function which takes any type of STL container as a parameter.

The code below works fine. 

```

template <class T> void func(T)
{
   cout << T.size(); << endl;
}

int main()
{
 vector<int> vec(100);
 func(vec); 
  return 0;
}

```

However, when I replace "cout << T.size(); << endl;" with 
"T::iterator it = T.begin();", I get this compilation error:

```

error: expected `;' before ‘it’

``` 

How can I fix it?

---

### Post by schauerlich on 2010-10-01
T is a type, not a variable.

```
#include <vector>
#include <iostream>

template <typename T> 
void func(T foo) {
  std::cout << foo.size() << std::endl;
}

int main(void) {
  std::vector<int> vec(100);
  func(vec); 
  return 0;
}

```

Once you've gotten that far, all you have to do is check the error message:
```
foo.cpp: In function &#8216;void func(T)&#8217;:
foo.cpp:6: error: expected `;' before &#8216;it&#8217;
foo.cpp:6: error: &#8216;it&#8217; was not declared in this scope
foo.cpp: In function &#8216;void func(T) [with T = std::vector<int, std::allocator<int> >]&#8217;:
foo.cpp:12:   instantiated from here
foo.cpp:6: error: dependent-name &#8216;T::iterator&#8217; is parsed as a non-type, but instantiation yields a type
**foo.cpp:6: note: say &#8216;typename T::iterator&#8217; if a type is meant**

```
and fix it. Here's an example:

```
#include <vector>
#include <iostream>

template <typename T> 
void func(T foo) {
  for (typename T::iterator it = foo.begin(); it != foo.end(); ++it)
	std::cout << *it << std::endl;
}

int main(void) {
  std::vector<int> vec(10, 10);
  func(vec); 
  return 0;
}

```

---

### Post by worksofcraft on 2010-10-02
It's probably not an issue, but could be if you were working with many different containers types of different object classes...
 
Keep in mind that by using a **template** for your function, the compiler is actually creating **duplicate** code specifically for each and every type that you use with the function.

If you want to have just one function that works on a variety of containers then you would have to create some kind of common base class for them.

---

### Post by dwhitney67 on 2010-10-02
@ the OP and schauerlich -

The function declaration would be better as:
```

template <typename T>
void func(**T&** foo)
{
   ...
}

```
It is better to pass the object by reference to avoid creating a shallow copy of the object being passed as a parameter.

If there is no intent in the function to modify the object that is passed in, then preface the T& with a "const".

As for "genericizing" the function, it obviously will not work for all objects; for example, it would not work if you merely passed an *int* object.  Thus, it might not be worth creating such a function in the first place.

If you want to display the contents of a vector:
```

#include <vector>
#include <iterator>
#include <iostream>
...
std::vector<int> vec;
...
std::copy(vec.begin(), vec.end(), std::ostream_iterator<int>(std::cout, "\n"));

```

---

### Post by schauerlich on 2010-10-03
Yet another reason to love C++... :)

---

