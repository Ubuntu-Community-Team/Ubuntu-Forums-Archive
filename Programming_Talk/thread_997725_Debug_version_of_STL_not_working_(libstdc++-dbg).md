---
title: "Debug version of STL not working? (libstdc++-dbg)"
date: 2008-11-30
forum: Programming Talk
---

### Post by yang on 2008-11-30
I'm using Ubuntu 8.10 64-bit, and I just installed libstdc++6-4.3-dbg, but after running g++ -g3 on the following simple C++ program:

```

#include <vector>
using namespace std;
inline int f() { return 0; }
int main() {
  vector<int> xs;
  xs.push_back(0);
  return f();
}

```

gdb still complains that

```

(gdb) p xs.at(0)
Cannot evaluate function -- may be inlined

```

(Notice that "p f()" works; I'm just expecting the same to be true of STL functions.)  Thanks in advance for any help with this!

---

