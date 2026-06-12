---
title: "no fstream.h ???!!!"
date: 2007-03-23
forum: Programming Talk
---

### Post by the_nomad on 2007-03-23
does this header file exist?? im trying to write to a file but the compiler says ```
  error: &#8216;g&#8217; was not declared in this scope

```
when using ```
g<<inits <<"\n";
```, g being declared as it follows ```
cout<<"location (e.g. c:\xxx.txt"; cin>>loc;
	ofstream g(loc);
```]
im asking if it does exist coz when using sudo whereis fstream.h i dont get anything

thanx in advance

---

### Post by Wybiral on 2007-03-23
How about...
```

#include <fstream>

```

But something tells me you either didn't include ALL of the errors/warning in your post, or you are actually using g out of it's scope. All of the warnings and possible some code would help. Assuming that you've already installed build-essential.


Half of the problems people have with C++ is that they try to use deprecated headers. Like "iostream.h" and "fstream.h"
If you get a "deprecated" header warning, try dropping an ".h" somewhere because that's usually the problem.

C++ has went through too many changes...

---

### Post by the_nomad on 2007-03-23
#include <fstream>

```

icmd.cpp:26: error: &#8216;ofstream&#8217; was not declared in this scope
icmd.cpp:26: error: expected `;' before &#8216;g&#8217;
icmd.cpp:100: error: &#8216;g&#8217; was not declared in this scope

```

line 26: ofstream g(loc);
line 100: g<<inits <<"\n";

---

### Post by Wybiral on 2007-03-23
Did you happen to...
```

using namespace std;

```
?

Most of the standard io stuff is in that namespace.

---

### Post by the_nomad on 2007-03-23
no, i just include the files i need and then the main function... i saw this using name space std; before but i dont know exactly what is it..

---

### Post by yabbadabbadont on 2007-03-23
Sounds like you need to read a good book on learning C++.  Unfortunately, I don't know of any off the top of my head.  You might use google to search for some free online tutorials though.

---

### Post by Wybiral on 2007-03-23
The functions are in a namespace which means you have two options:

1.
```

#include <iostream>
#include <fstream>

using namespace std;

int main()
{
   string buffer;
   ifstream g("file");
   g >> buffer;
   cout << buffer;
   g.close();
}

```

2.
```

#include <iostream>
#include <fstream>

int main()
{
   std::string buffer;
   std::ifstream g("file");
   g >> buffer;
   std::cout << buffer;
   g.close();
}

```


How have you been able to use iostream without namespaces?

---

### Post by ashmew2 on 2009-09-19
You can use iostream without namespaces on Windows. There's a compiler called  Borland Turbo C++ 3.0 where you can do this.
also , shouldnt string.h be included as well for declaring strings ?

---

