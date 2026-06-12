---
title: "Program"
date: 2014-06-10
forum: Programming Talk
---

### Post by spacerocket on 2014-06-10
Hello,

I wrote an example that was in a book

```
#include "std_lib_facilities.h"



int main()
{

      cout<<"Hello, World!\n";

      return 0;

}
```


And when trying to compile -> fatal error: std_lib_facilities.h: No such file or directory
 #include<std_lib_facilities.h>

In the book says: How do you find std_lib_facilities.h? Download it from our support site [www.stroustrup.com/]("http://www.stroustrup.com/") ??

---

### Post by lisati on 2014-06-10
I might be mistaken, but I believe that something like the following might be what is needed in a C programm instead of the line that is triggering the error:
```
#include <stdio.h>
```

The appropriate equivalent for C++ code eludes my recollection for the moment.

edit: have a look here: [http://www.cplusplus.com/doc/tutorial/program_structure/](http://www.cplusplus.com/doc/tutorial/program_structure/)

---

### Post by dwhitney67 on 2014-06-10
> **spacerocket said:**
> 
In the book says: How do you find std_lib_facilities.h? Download it from our support site [www.stroustrup.com/]("http://www.stroustrup.com/") ??
Well, did you download the file??

If not, forget about it for now, and merely include <iostream>.  Your program should appear as:
```

#include <iostream>

int main()
{
      std::cout<<"Hello, World!" << std::endl;
}

```
Note that cout and endl are in the std namespace; thus the need to specify such as I have shown.  Alternatively, you could specify to include that namespace within your program with a statement such as "using namespace std;" -- but that would be lame for such a trivial program.

As for the return statement at the end of the main() function, that is superfluous in C++; in other words, it is not required since the default return value for C++ programs is always 0, unless otherwise specified to be another number.


P.S.  You should avoid the temptation to specify a "using namespace std;" directive within a header file.  I'm surprised that Stroustrup did that.  But then again, maybe not.  Programmers who work in academia and those that work in the real world operate on different frequencies.

---

### Post by spacerocket on 2014-06-11
Yes, though at this stage I`m trying to follow the book, and write the code like the author did and get it working. If I try to compile some other programs I get error message as well. At this stage I should download std_lib_facilities.h? The authors code is designed for that?

I notice that the author of this book does not include any header files in some of his codes, so maybe he expects I`m using std_lib_facilities.h.

Anyway now I`m getting error message when I want to compile something but what`s the point of asking help if my questions get banned when I don`t know something?

---

### Post by spacerocket on 2014-06-11
Actually the author says in his book that alternatively I could use these at the beginning of each code:

#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
#include<cmath>
using namespace std;

"This uses the standard library directly and will keep you going until chapter 5 and will be explained in detail later (&8.7)."   Now I can compile programs but still don`t like that my threads get banned.

---

### Post by dwhitney67 on 2014-06-11
> **spacerocket said:**
> ... but still don`t like that my threads get banned.

Your threads are showing up on the forum, so I'm not sure what you are complaining about.

---

### Post by spacerocket on 2014-06-11
[http://ubuntuforums.org/showthread.php?t=2229070](http://ubuntuforums.org/showthread.php?t=2229070)


I have now solved this issue but anyway.

---

