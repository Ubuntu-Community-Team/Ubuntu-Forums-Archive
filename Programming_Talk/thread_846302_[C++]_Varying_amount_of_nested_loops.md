---
title: "[C++] Varying amount of nested loops"
date: 2008-07-01
forum: Programming Talk
---

### Post by Sockerdrickan on 2008-07-01
Hi what's the best way to use a varying amount of nested for loops in c++? :KS

---

### Post by Zugzwang on 2008-07-01
> **Tux0r said:**
> Hi what's the best way to use a varying amount of nested for loops in c++? :KS

If I understand you correctly, you might want to use recursion. Here's an example:
[PHP]
#include <iostream>

#define REC_LEVEL 4
// This would be in you "globals.h"

int recurse(int *levels, int current) {
  if (current==REC_LEVEL) {
    std::cout << "Current value: ";
    for (uint i=0;i<REC_LEVEL;i++) std::cout << levels[i] << " ";
    std::cout << std::endl;
  } else {
    for (levels[current]=0;levels[current]<4;levels[current]++) {
      recurse(levels,current+1);
    }
  }
}


int main() {
        int m[REC_LEVEL];
        for (uint i=0;i<REC_LEVEL;i++) m[i] = 0;
        recurse(m,0);
        return 0;
}
[/PHP]

Alternatively, you can use some "combination iterator" class or such. But I have never seen one so far. ;-)

---

### Post by Sockerdrickan on 2008-07-01
I totally forgot about recursion... Thanks!

---

