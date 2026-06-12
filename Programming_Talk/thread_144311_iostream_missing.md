---
title: "iostream missing?"
date: 2006-03-14
forum: Programming Talk
---

### Post by beej101 on 2006-03-14
i used to be able to use the iostream.h header but now i can't use it (i.e. cout unavailable etc) could i have unwittingly uninstalled certain package iostream belongs to?  thanks...

i'm getting iostream.h no such file or directory error

---

### Post by jerome bettis on 2006-03-14
```
#include <iostream> // (no .h for c++ libs)
using namespace std;
int main()  {
    cout "asdfaf";
}

// or

#include <iostream>
int main()  {
    std::cout "adsfasdf";
}
```

---

### Post by thumper on 2006-03-14
**jerome bettis** you're missing your '<<'s
```

#include <iostream>
int main() {
   std::cout << "Hello World\n";
}
```

---

### Post by beej101 on 2006-03-14
im not using namespace... i want it to be a simple include as in:

#include <iostream.h>

int main(){

   cout << "hello\n";

   return 0;
}

at the term i type:
  gcc -o mycprog mycprog.c
i get:
iostream.h missing file or directory (or something along this line)
could i have mucked up my libraries when i try to remove some package using synaptic? thanks!

---

### Post by gord on 2006-03-14
remove the .h from the include :)
#include <iostream>

---

### Post by thumper on 2006-03-14
Your problem is your desire not to use namespaces.  The problem is that namespaces are part of standard C++.

If you really don't want to prefix things with std:: then put the following in your source file:
```
using namespace std;
```
It is considered bad form, but it will give you the desired result.

iostream.h is the old pre-standard header file (pre 1998 - so really quite old really).

---

### Post by beej101 on 2006-03-14
hmm i do embrace new standards i'm just thinking even if i can use the new one (namespaces) if my system doesn't allow me to use the old one(header include etc) then there must be something wrong with my install.

---

### Post by supirman on 2006-03-14
g++ -o myprog myprog.c

You're apparently trying to mix c and c++.  With the above, you'll get warning about the deprecated header, but it will still work.

---

### Post by thumper on 2006-03-14
My advice is to just use the new one.  Don't start bad habits.

---

### Post by zkissane on 2006-03-14
[QUOTE=beej101]hmm i do embrace new standards i'm just thinking even if i can use the new one (namespaces) if my system doesn't allow me to use the old one(header include etc) then there must be something wrong with my install.[/QUOTE]

That's what "deprecated" means:  it could be removed at any time; you have been warned.

---

### Post by hod139 on 2006-03-14
If you want to test if iostream is still installed, you can run 
```

find /usr/include/ -name iostream

```
and if you get results, the file exists.  For example, on my machine I get 
```

~$ find /usr/include/ -name iostream
/usr/include/c++/4.0.2/iostream
/usr/include/c++/3.4/iostream
/usr/include/c++/3.3/iostream

```

As supirman said, I think the problem is that you are mixing c++ and c code.  cout is part of c++, and as such you should name your files mycprog.cpp and using 
```
g++ -o myprog myprog.cpp
```
and as others have stated, include it using the "correct" header  
#include <iostream>

Finally, you must use the std namespace, so anywhere you want to use cout, you must say std::cout (I also avoid the using keyword).

Hope this helps.

---

### Post by saul on 2006-03-25
Yes, it helped hold139, thanks.

I had the same problem, so I installed "g++" package and the file "iostream" got installed. Once this done the commands for compiling a file that includes iostream are g++.../c++... but not gcc... (I think) :p. Bye.

---

