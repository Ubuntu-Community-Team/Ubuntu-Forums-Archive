---
title: "can the C++ system() function take a variable input?"
date: 2007-10-23
forum: Programming Talk
---

### Post by rajan on 2007-10-23
Hi, as the thread title says, I'm wondering if there's a way in my C++ program to pass a variable input. 

These are roughly what I'm trying to do, but they don't work

```

system("echo" inputvariablestringhere);

```

or alternatively,

```

stringa = "hello";
stringb = "echo";
inputvariablestringhere = stringb+stringa;
system(inputvariablestringhere);

```

the last one also does not work when i replace the last line with

```

system(inputvariablestringhere.c_str);

```

If it's not clear, what I'm trying to do is to call the system from my C++ program and specifically a ```
cp -ur 
``` where i pass the contents of an array containing strings (one by one) to copy them. Thus I need to be able to pass the contents of the array to the system(). I have heard that popen might be the way to go, but I can't find any good (in depth) reading online about it. 

I appreciate any help.

---

### Post by aks44 on 2007-10-23
```
#include <string>

int main()
{
  std::string s1 = "echo";
  std::string s2 = "It works !!";
  std::string s3 = s1+" "+s2;
  system(s3.c_str());
}
```

---

### Post by rajan on 2007-10-23
STUPID PARENTHESES!!! (or just stupid me)

i searched for the answer to this for at least 1.5 hours and none of the other sites helped. thanks a lot aks44!

---

### Post by aks44 on 2007-10-23
> **rajan said:**
> STUPID PARENTHESES!!! (or just stupid me)

Hmm I don't mean to be rude, but the parentheses themselves can't really blamed. :p

Don't get me wrong though, errors happen, and in fact they often are the best way to learn... Next time you won't do that mistake ;)

---

