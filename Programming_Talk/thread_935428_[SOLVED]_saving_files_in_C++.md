---
title: "[SOLVED] saving files in C++"
date: 2008-10-01
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-01
so im writting a program that needs file i/o...only thing is ive found no good tutorials...they are either confusing or the header they are telling me to use (fstream.h) is said not to be found by the compiler...any insight?

thanks

---

### Post by Sinkingships7 on 2008-10-01
That's very odd. It's quite standard...

Post the output of

```
sudo ls -A /usr/include/
```

---

### Post by jimi_hendrix on 2008-10-01
found the error...the tutorial told me to do <fstream.h> so i tried that and it didnt compile and i tried "fstream.h" and that didnt compile...it should have been just <fstream> now using the "learn C++" link in LaRoza's wiki to learn file I/O

whats the difference between <library_name> and "library_name.h"

---

### Post by Sinkingships7 on 2008-10-01
> **jimi_hendrix said:**
> 
whats the difference between <library_name> and "library_name.h"

<header_name> is meant to include a 'standard' (usually) header file that comes with the compiler, or just one in your PATH (confirmation needed).

"header_name" is used to include a header that you created yourself, and need to point to specifically. You can even do things like

#include "/home/jimi_hendrix/code/my_header.h" 

to point to headers that aren't in the same location as your compiling file.

---

### Post by jimi_hendrix on 2008-10-01
ok and last question...then we've gotten off topic and i will mark it solved...and whats a namespace (i hate when tutorials dont explain the stuff you need to know) like [PHP]using namespace std; [/PHP]

---

### Post by LaRoza on 2008-10-01
> **jimi_hendrix said:**
> ok and last question...then we've gotten off topic and i will mark it solved...and whats a namespace (i hate when tutorials dont explain the stuff you need to know) like [PHP]using namespace std; [/PHP]

[http://en.wikipedia.org/wiki/Namespace_(computer_science)](http://en.wikipedia.org/wiki/Namespace_(computer_science))

All the standard library functions will be in std.

You shouldn't use using namespace...

```

#include <iostream>

int main()
{
    std::cout << "Hello world" << std::endl;
    return 0;
}

```

---

### Post by jimi_hendrix on 2008-10-01
> **LaRoza said:**
> [http://en.wikipedia.org/wiki/Namespace_(computer_science)](http://en.wikipedia.org/wiki/Namespace_(computer_science))

All the standard library functions will be in std.

You shouldn't use using namespace...

```

#include <iostream>

int main()
{
    std::cout << "Hello world" << std::endl;
    return 0;
}

```

once again bad tutorials...any reason why not?

---

### Post by Sinkingships7 on 2008-10-01
> **jimi_hendrix said:**
> once again bad tutorials...any reason why not?

Because LaRoza's a borg and likes to do it the hard way. :)

As a general rule, you shouldn't use namespaces in your own header files with classes and stuff, but I see no reason not to use it in your main program.

---

### Post by LaRoza on 2008-10-01
> **jimi_hendrix said:**
> once again bad tutorials...any reason why not?

Well, until you knwo what they are and when you should do that, one should use it.

---

### Post by LaRoza on 2008-10-01
> **Sinkingships7 said:**
> Because LaRoza's a borg and likes to do it the hard way. :)

but I see no reason not to use it in your main program.

No, I don't like doing things I don't know.

How many times do I see students "learning" C++, yet do the "using namespace std;" without knowing why, and worse, getting confused and lost when they see "std::cout", etc.

But you are right, I am Borg and I don't do things the hard way and I consider C++ "the hard way". ;)

---

### Post by Sinkingships7 on 2008-10-01
> **LaRoza said:**
> No, I don't like doing things I don't know.
Point taken, and well-made.

> **LaRoza said:**
> 
How many times do I see students "learning" C++, yet do the "using namespace std;" without knowing why, and worse, getting confused and lost when they see "std::cout", etc.


Very true. 'Magic' code is a big reason why a few of us here support beginners learning languages like Python, so they don't have to fret over 'magic' code. :)

---

### Post by jimi_hendrix on 2008-10-01
the wikipedia page seems to say that a namespace is a collection of objects/data types/functions/identifiers...now i get it

---

### Post by rnodal on 2008-10-01
I used to think that:

[PHP]using namespace std;[/PHP]

was the way to go always. Why would anyone bother to type std:: every time? Until you start using a lot of 3rd party libraries and realize how useful is to have std::something, namex::something in terms of keeping your code readable.

-r

---

### Post by dwhitney67 on 2008-10-01
> **jimi_hendrix said:**
> so im writting a program that needs file i/o...only thing is ive found no good tutorials...they are either confusing or the header they are telling me to use (fstream.h) is said not to be found by the compiler...any insight?

thanks

You may want to bookmark the [C++ reference guide]("http://www.cplusplus.com/reference/"), and use it as your technical tutorial when dealing with C++ iostreams or the STL.

In most cases, if you click on an object type (e.g. ofstream) and then on the constructor link for that object, there is a clear-cut example on what header files need to be included, and complete code as well, that can be compiled and tested.

---

### Post by nvteighen on 2008-10-02
> **LaRoza said:**
> 
You shouldn't use using namespace...


And what were we doing at the old Sysres with those "from ... import *" statements? ;) Interestingly, that was a great example on why such things should be avoided: the main namespace is to be used for the main level, whichever it is in a certain place of code. And cluttering the main namespace leads to really confusing code: the computer will always know where stuff has been placed (if it has been placed, of course), but you?

You better keep namespaces do their job. They have a reason to exist, and possibly is one of the best features C++ has. In C, people use to simulate namespaces using x_function notation to put function in the "namespace" x... actually, just a notation convention, but leads to long names and verbose code (Have you seen GTK+ code written in C vs. those written in Python or C++?).

Then, about #include <aaaa> vs. #include <aaaa.h> vs. #include "aaaa.h"

1. **#include <aaaa>** is proper, standard and modern C++.
2. **#include <aaaa.h>** is proper and standard C, and it has been always that way. But it's old and obsolete C++.
3. **#include "aaaa.h"** is both proper, standard and modern C and C++, but it will look at your local directory for the header file before looking at the system directories'.

---

### Post by dwhitney67 on 2008-10-02
> **nvteighen said:**
> And what were we doing at the old Sysres with those "from ... import *" statements? ;)
 ...
Touché!

---

### Post by dribeas on 2008-10-02
> **nvteighen said:**
> Then, about #include <aaaa> vs. #include <aaaa.h> vs. #include "aaaa.h"

1. **#include <aaaa>** is proper, standard and modern C++.
2. **#include <aaaa.h>** is proper and standard C, and it has been always that way. But it's old and obsolete C++.
3. **#include "aaaa.h"** is both proper, standard and modern C and C++, but it will look at your local directory for the header file before looking at the system directories'.

All of them are proper C++. The standard states that <> should be used for standard or C++ implementation headers (headers provided by the compiler implementor) while "" is to be used for user headers. The one difference that the standard states is that headers included with "" _must_ be files. That is interesting as the compiler provider can decide not to provide files for standard headers. That is to say that g++ could opt not to include iostream header file, but have the compiler fill in the code whenever requested with <>.

Now, back to real life, most compilers don't make such a strong difference between the two. VS won't search for the file in the current directory if the include uses brackets. Most compilers first look in the current directory when finding "" and then fall back to searching in system/project wide include directories, while <> first looks in all other directories and then in the current directory.

Then, when deciding between fstream / fstream.h, the C++ standard used to have headers ending in .h, while the current standard has removed the suffix (at the same time that it redefined some of the internals). For standard C includes (xxx.h), the current C++ standard defines equivalent headers by the name cxxx. The difference being two fold: functions and constants have been moved to std namespace and macros have been removed for constants.

---

### Post by mssever on 2008-10-02
When it comes to namespaces, Python handles them better than any other language I know. You can spend time trying to figure out namespaces in C++, but if you write Python for very long, they'll become the most natural thing in the world (unless you use [FONT=Courier New]from some_module import *[/FONT] which is evil in most cases).

---

### Post by dwhitney67 on 2008-10-02
> **mssever said:**
> When it comes to namespaces, Python handles them better than any other language I know. You can spend time trying to figure out namespaces in C++, but if you write Python for very long, they'll become the most natural thing in the world (unless you use [FONT=Courier New]from some_module import *[/FONT] which is evil in most cases).

In C++, it is actually quite simple to set up a namespace.  That you feel it is difficult is astonishing.

Foo.h:
[PHP]namespace Foo
{
  static const unsigned int value = 10;
}[/PHP]
Main.cpp:
[PHP]#include "Foo.h"
#include <iostream>

int main()
{
  std::cout << "value = " << Foo::value << std::endl;
  return 0;
}[/PHP]
Above I could have used the "using namespace Foo", or merely prefix 'value' with the namespace name.  I chose the latter because it is clearer as to where the variable 'value' is defined.

Is this really that difficult?

---

### Post by rnodal on 2008-10-02
> **dwhitney67 said:**
> In C++, it is actually quite simple to set up a namespace.  That you feel it is difficult is astonishing.

Foo.h:
[PHP]namespace Foo
{
  static const unsigned int value = 10;
}[/PHP]
Main.cpp:
[PHP]#include "Foo.h"
#include <iostream>

int main()
{
  std::cout << "value = " << Foo::value << std::endl;
  return 0;
}[/PHP]
Above I could have used the "using namespace Foo", or merely prefix 'value' with the namespace name.  I chose the latter because it is clearer as to where the variable 'value' is defined.

Is this really that difficult?

Thank you!

---

### Post by mssever on 2008-10-02
> **dwhitney67 said:**
> In C++, it is actually quite simple to set up a namespace.  That you feel it is difficult is astonishing.
I never said it's difficult. But when I was starting out, writing 'using namespace std;' seemed to me to be magic programming. The syntax rules are simple, but syntax is only a small part of the topic. I found that Python taught me the why's of namespaces better than C++ did, and it taught me how to use them to my advantage.

(Disclaimer: It's been a long time since I've written any C++ and when I did work with C++ I was a green newbie programmer.)

---

### Post by lisati on 2008-10-02
I think some of the discussion here is beginning to seep into my dense conditioned-by-BASIC head: a lot of the hoo-hah about namespace is readability and deciding what belongs where.

---

