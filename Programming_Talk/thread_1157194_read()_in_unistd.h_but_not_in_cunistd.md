---
title: "read() in unistd.h but not in cunistd"
date: 2009-05-12
forum: Programming Talk
---

### Post by monkeyking on 2009-05-12
This wont compile
[PHP]
#include <cstdio>
#include <cunistd>
#include <cstdio>

int main(){
  char buf[100];
  int fds[2];
  
  read(fds[0],buf,5);

  return 0;
}

[/PHP]
This on the other hand
[PHP]
#include <cstdio>
#include <unistd.h>
#include <cstdio>

int main(){
  char buf[100];
  int fds[2];
  
  read(fds[0],buf,5);

  return 0;
}
[/PHP]

Can someone tell me whats wrong,
and what thesolution is.

thanks in advance

---

### Post by johnl on 2009-05-12
1. Might help to post the compiler output.  

2. I don't think there is such a thing as <cunistd>.  unistd.h is not part of the C standard library, so there is no reason to have a C++ wrapper for it.

3. If in the unlikley event that you *do* have a <cunistd>, then, like the other C++ wrappers, it places all it's members into the 'std' namespace.  So you will need to reference any functions contained in that header appropriately (std::read).

---

