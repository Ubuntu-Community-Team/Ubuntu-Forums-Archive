---
title: "basename/dirname in c/c++"
date: 2009-06-15
forum: Programming Talk
---

### Post by monkeyking on 2009-06-15
Sorry for bothering you people, it works.


edit.
The basename that returns the filename without the path is defined in libgen.h and works out the box.

But its friend  'dirname' that return the directoryname,
I can't seem to track this one down.

Does anyone know if it exists for c/c++?

btw it should exist but I cant get it to work

man 3 basename

[PHP]
#include<iostream>
#include<cstring>

#include<libgen.h>

int main(){
  const char *ch = "asdfasdf/asdf.cpp";
  std::cout<<basename(ch) << std::endl;
  std::cout<<dirname(strdup(ch)) << std::endl;
  return 0;
}

[/PHP]

---

### Post by Zugzwang on 2009-06-16
I wonder how you compile your snipplet. For me, the compiler complains about casting a "const char*" to a "char *" - And this is evidence for the fact that you are using the functions incorrectly.

Indeed, when looking at the man page for "basename", it is stated that calling this function may modify the original string. So you need to copy the strings **before** calling these functions:

[PHP]
#include<iostream>
#include<cstring>

#include<libgen.h>
#include<stdlib.h>

int main(){
  const char *ch = "asdfasdf/asdf.cpp";

  char *ch1 = strdup(ch);
  char *ch2 = strdup(ch);
  
  std::cout<<basename(ch1) << std::endl;
  std::cout<<dirname(ch2) << std::endl;

  free(ch1);
  free(ch2);

  return 0;
}  
[/PHP]

Having a look at the compiler warnings ("-Wall") and looking at the man page of "basename" would have helped you solving this issue.

---

### Post by monkeyking on 2009-06-16
> **Zugzwang said:**
> 
....
Having a look at the compiler warnings ("-Wall") and looking at the man page of "basename" would have helped you solving this issue.

Thats excatly what I did :)

---

