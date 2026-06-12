---
title: "compiler error"
date: 2007-05-14
forum: Programming Talk
---

### Post by jamescai on 2007-05-14
Hello All,

I got compiler error for my c++ structure,

struct LTestString
{
int len;
char str[];
};

LTestString s = {3, "ab"};

the error message is: error: initializer-string for array of chars is too long.
I need to use char str[] of dynamic size. I used gcc 4.1.2
BTW, it works in windows environment. 

Thanks!
James

---

### Post by talowe on 2007-05-14
> **jamescai said:**
> Hello All,

I got compiler error for my c++ structure,

struct LTestString
{
int len;
char str[];
};

LTestString s = {3, "ab"};

the error message is: error: initializer-string for array of chars is too long.
I need to use char str[] of dynamic size. I used gcc 4.1.2
BTW, it works in windows environment. 

Thanks!
James

```
char* str;
```

instead of

```
char str[]
```

works.  But why not

```
#include <string>
using std::string;

string s="ab";
```

---

### Post by hod139 on 2007-05-14
Replacing char[] with char* will cause a memory leak, and probably a difficult to debug segfault later on since you haven't allocated the memory for the string.  If you used char* you would need to write something like:

```
struct LTestString
{ 
  explicit LTestString(int _len, const char * const _str) 
  {
    len = _len;
    str = new char[_len];
    strncpy(str, _str, len-1);
    str[len-1] = '\0';  // Just in case str is longer than len
  }
  ~LTestString()
  {
    if(str)
      delete[] str;
  }

  int len;
  char *str;
};


int main(void){
  LTestString s(3, "ab");

  return 0;
}

```If this is C++, why not use std::string as talowe suggested?

---

### Post by jamescai on 2007-05-14
Thank you for your reply. Since I port windows app to linux, I can't change too much source codes. I need to keep this structure. Any other solutions?

Thanks!
James

---

### Post by Lux Perpetua on 2007-05-15
Well, FYI, ```
char str[];
``` is not a valid C++ declaration, so something's gotta give.

---

### Post by hod139 on 2007-05-15
> **Lux Perpetua said:**
> Well, FYI, ```
char str[];
``` is not a valid C++ declaration, so something's gotta give.
You can use the ```
char str[]
``` declaration only if you know the size of the array at comile time, for example
```

char str[] = "ab";

```is perfectly legal, since the size of str can be determined.  If the size is unknown, then dynamic memory allocation is required, which is the solution I posted earlier.

[quote=jamescai] I need to keep this structure. Any other solutions?
[/quote]
As was stated earlier, since this is C++ why not replace the character array with a std::string?
```

#include <string>

struct LTestString
{
  int len;
  //char str[];
  std::string str;
};

LTestString s = {3, "ab"};

```

---

