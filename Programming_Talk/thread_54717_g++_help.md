---
title: "g++ help"
date: 2005-08-05
forum: Programming Talk
---

### Post by jarg on 2005-08-05
I have no clue how to get g++ to run, I am pretty sure I have all the files installed (I found an old thread), but I really have no clue how to run anything under linux. Any help on running it?

---

### Post by DJ_Max on 2005-08-05
What are you trying to do? Normally, you open a terminal
```
g++ FILENAME.cpp -o BINNAME
```

---

### Post by jarg on 2005-08-06
[QUOTE=DJ_Max]What are you trying to do? Normally, you open a terminal[/QUOTE]
thanks but I got an error

```
jared@ubuntu:~$ g++ /home/jared/Desktop/firtprogram.cpp -o BINNAME
In file included from /usr/include/c++/3.3/backward/iostream.h:31,
                 from /home/jared/Desktop/firtprogram.cpp:3:
/usr/include/c++/3.3/backward/backward_warning.h:32:2: warning: #warning This fi le includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples in clude substituting the <X> header for the <X.h> header for C++ includes, or <sst ream> instead of the deprecated header <strstream.h>. To disable this warning us e -Wno-deprecated.
jared@ubuntu:~$

```

when running
```
// my first program in C++

#include <iostream.h>

int main ()
{
  cout << "Hello World!";
  return 0;
}
```

do you know what that means?

---

### Post by cwaldbieser on 2005-08-06
[QUOTE=jarg]
```
// my first program in C++

#include <iostream.h>

int main ()
{
  cout << "Hello World!";
  return 0;
}
```
[/QUOTE]

Try:
```
// my first program in C++

#include <iostream>

int main ()
{
  std::cout << "Hello World!";
  return 0;
}
```

It looks like you just got a warning for using the old-style C++ headers.  At the present, the C++ standard library uses "<foo>" includes where you see "<foo.h>" in older references.  The namespace (std) is also important once you start using the new headers.

---

### Post by DJ_Max on 2005-08-06
To add to what cwaldbieser said. He means adding 
```
 using namespace std;
```

---

### Post by cwaldbieser on 2005-08-06
[QUOTE=DJ_Max]To add to what cwaldbieser said. He means adding 
```
 using namespace std;
```[/QUOTE]

For toy programs, the [using] directive is OK.  But once you start writing more complicated programs, it becomes better practice to forgo the [using] directive and just qualify your symbols.  Especially in header files that you expect someone else to include.  Otherwise, you just end up polluting the namespace.

---

### Post by LordHunter317 on 2005-08-06
Or, qualify your symbols on a per-symbol basis, at the smallest reasonable scope (usually function-scope):```

#include <iostream>

int main() {
    using std::cout;
    using std::endl;

    cout << "Hello World" << endl;
}
```

---

