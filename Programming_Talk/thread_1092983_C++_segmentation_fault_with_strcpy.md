---
title: "C++ segmentation fault with strcpy"
date: 2009-03-11
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2009-03-11
Hey All

I've got this code that's causing a segmentation fault:
```

name = "alphaUpper" + length; // length is a previously defined string
char wName1[name.length()];
strcpy (wName1, name.c_str());

```
This is my first time working with strcpy in C++, so if anyone has any insight as to what I'm doing that's causing the segmentation fault, I'd really appreciate it.
Thanks.

---

### Post by eye208 on 2009-03-11
name.length() does not include the string delimiter. strcpy() will cause a buffer overflow on the stack, possibly overwriting the function's return address and causing the segfault.

---

### Post by the_real_fourthdimension on 2009-03-11
> **eye208 said:**
> name.length() does not include the string delimiter. strcpy() will cause a buffer overflow on the stack, possibly overwriting the function's return address and causing the segfault.

Thanks.  I thought it might be something like that, so I changed the code to this, but I'm still having issues:
```

char * wName;
name = "alphaLower" + length;
wName = new char[name.size() + 1];
strcpy (wName, name.c_str());

```
Thanks again.

---

### Post by dwhitney67 on 2009-03-11
Declaring the size of an array during runtime is against ISO C++ programming standards.  If you compile with the -pedantic compiler flag you will see something similar to the following:
```

g++ -Wall -ansi -pedantic test.cpp 
...
test.cpp:6: error: ISO C++ forbids variable length array &#8216;array&#8217;

```

Aside from that "little" issue, why is it that you require a C-style char array??

If you attempt something similar to the following, then you should have no problems:
```

#include <string>
#include <cstring>

int main()
{
  std::string foo("foo");
  char* array = new char[foo.length() + 1];
  strcpy(array, foo.c_str());
  // ...
  delete [] array;
}

```
But the question still lingers; why do you need a C-style string?  Why not just declare another std::string?

---

### Post by Npl on 2009-03-11
> **the_real_fourthdimension said:**
> Thanks.  I thought it might be something like that, so I changed the code to this, but I'm still having issues:
```

char * wName;
name = "alphaLower" + length;
wName = new char[name.size() + 1];
strcpy (wName, name.c_str());

```
Thanks again.
There is an own Method for copying strings to char-arrays. Should be your prefered way of doing it.
```
char * wName;
name = "alphaLower" + length;
wName = new char[name.size() + 1];
name.copy(wName, string::npos);
wName[name.size()] = '0';
```

---

