---
title: "copy_n from GNU C++ Library"
date: 2009-03-19
forum: Programming Talk
---

### Post by flylehe on 2009-03-19
Hi,
I am using copy_n from GNU C++ Library under Ubuntu 8.10. My code is like this:
```

#include <ext/algorithm>
using namespace std;

void myfun(char * flags ) {
    char * flags_new = new char[3];
    copy_n(flags, 3, flags_new);// both copy_n and copy would give not in this scope error.
    delete [] flags_new;
  }

int main()
{
    char flags[3]={'a','b','c'};
    myfun(flags );
    return 0;
}

```
I got error : "‘copy_n’ was not declared in this scope".
I look up for copy_n in GNU C++ standard library document and find "ext/algorithm" to include. I was wondring what is the problem and how to fix it? Thanks!

---

### Post by dwhitney67 on 2009-03-20
I don't quite understand what you are seeking, nor why you are attempting to use a function that is not covered by the C++ standard, but instead a GNU extension.  Your code may not be portable to another system.  But if that is what you want, I think the only issue you need to be aware of is that copy_n() is not part of the std namespace; it is part of the __gnu_cxx namespace.

```

#include <ext/algorithm>    // this header also includes <algorithm>
#include <iostream>

void dispChar(const char ch)
{
  std::cout << ch << " ";
}

void myfun(const char* flags)
{
  char* flags_new = new char[3];

  __gnu_cxx::copy_n(flags, 3, flags_new);

  std::for_each(flags_new, flags_new+3, dispChar);
  std::cout << std::endl;

  delete [] flags_new;
}

int main()
{
  char flags[3] = {'a','b','c'};

  std::for_each(flags, flags+3, dispChar);
  std::cout << std::endl;

  myfun(flags);
}

```

---

