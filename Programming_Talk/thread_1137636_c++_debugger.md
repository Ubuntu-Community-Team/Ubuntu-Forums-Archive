---
title: "c++ debugger"
date: 2009-04-25
forum: Programming Talk
---

### Post by cybo on 2009-04-25
does anyone know of any c++ debuggers? i mean specifically for c++. i use ddd (gui for gdb) but sometimes i need to see what is stored in my lists, vectors and queues and it would be nice if i could do that. ddd just allows you to see just the addresses stored, but i would like to see actual contents.

---

### Post by dwhitney67 on 2009-04-25
I agree; gdb is less than useful when attempting to analyze the contents of and STL container.

However, I just tested a simple program with the debugger to see if I could display the contents of an int vector, and sure enough, it is possible.

Here's the code:
```

#include <vector>
#include <iostream>
#include <algorithm>

template <typename T>
void display(const T& value)
{
  std::cout << value << " ";
}

int main()
{
  std::vector<int> vec;
  vec.push_back(10);
  vec.push_back(20);
  vec.push_back(30);

  std::for_each(vec.begin(), vec.end(), display<int>);
  std::cout << std::endl;
}

```

To display the int values in the vector, I issued the following ddd (actually, gdb) command to display the first element in the vector:
```

(gdb) p *(vec._M_impl._M_start + 0)

```
To display the other two values, I merely changed the index to 1 and 2, respectively.

Now, a vector is a trivial container than, say, an STL map.  Thus I do not know if such a scheme can be used for other containers.

---

### Post by Xender1 on 2009-04-25
I have run into the same problem as you..... and for some bigger projects not being able to see the value of the data stored is a big problem and makes debugging hell!

I have tried multiple IDE's etc... to see what was up... but all in all I felt what was best for me was setting up a virtual box of XP and running Visual Studio.

---

### Post by cybo on 2009-04-26
thank you for the help everyone.

---

### Post by Namtabmai on 2009-04-26
I found these a while back,

[http://www.stanford.edu/~afn/gdb_stl_utils/](http://www.stanford.edu/~afn/gdb_stl_utils/)

Very helpful when using gdb and STL.

---

