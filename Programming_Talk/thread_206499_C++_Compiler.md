---
title: "C++ Compiler"
date: 2006-06-30
forum: Programming Talk
---

### Post by PoisoN2003 on 2006-06-30
Hey im looking for a compiler so i can learn c++ 

The only thing is the book is ment to be for windows when i tried a compiler in ubuntu i didnt underrstand how to set it up and it kept giving me an error when compiling

Any idea what i could do 
i have wine cedega and crossover
I havent tried the windows compiler yet

---

### Post by thumper on 2006-06-30
```
sudo apt-get install build-essential
```

Create yourself a new directory for your playing around.

Create the file hello.cpp
```
#include <iostream>

int main()
{
   std::cout << "Hello World\n";
}
```

compile it with
```
g++ -o hello hello.cpp
```
(-o says what to call the output of the compilation step [a.out by default])

execute it with
```
./hello
```

and you are away laughing.

---

### Post by PoisoN2003 on 2006-06-30
Here is another quick question whats the diffrence between gtk+ c++ or somethign and windows c++
since i want to train but my book is directed for c++ and cant launch the compiled stuff from the linux

---

### Post by thumper on 2006-06-30
GTK is a gui toolkit.  A library that is called from C++.  The Win32 API is also a gui toolkit, but with a different API.

GTK is also available on windows I believe.  wxWindows is another cross platform GUI library, and so is QT.

Examples in your windows book should work fine as long as they aren't using windows specific stuff (like <windows.h>).

---

### Post by PoisoN2003 on 2006-06-30
What compiling method should i use?
WXWINDOWS
Gnomemm
gtkmm
Im using anjuta the stuff compiles fine like this
```
#include <iostream>

using namespace std;



int main() {

    cout << "Never Fear Poison is here";

    return 0;

}

```
But when i press build
it gives me a bunch of error messeges
```
Building file: Ch1app1.cpp ...
g++ `wx-config --cxxflags`       "Ch1app1.cpp"  `wx-config --libs`    -o "Ch1app1"
g++: `wx-config: No such file or directory
g++: `wx-config: No such file or directory
cc1plus: error: unrecognized command line option "-fcxxflags`"
cc1plus: error: unrecognized command line option "-flibs`"
Completed ... unsuccessful
Total time taken: 1 secs

```

---

