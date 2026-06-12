---
title: "problem compiling c++ file"
date: 2009-05-29
forum: Programming Talk
---

### Post by bagljash on 2009-05-29
hello

I'm noobie when it comes to linux and to programing. I've started learning C++ but I've stumbled upon the problem. When I try to compile my "HelloWorld" program I get following lines in my Terminal:

```
bagljash@bagljash:~/Desktop$ g++ HELLO.cpp 
HELLO.cpp:1:22: error: iostream.h: No such file or directory
HELLO.cpp: In function ‘int main()’:
HELLO.cpp:5: error: ‘cout’ was not declared in this scope
```

Similarly when I try compiling this program in Eclipse it comes with same problem i.e.    iostream.h: No such file or directory

I've tried searching for solution here on Ubuntu Forums but I couldn't find it. But on the other hand I don't know what should I search for and how to name this problem.

Thank you in advance for your help.

---

### Post by _Purple_ on 2009-05-29
Use only iostream instead of iostream.h. If you still get error, can you post your code?

---

### Post by dwhitney67 on 2009-05-29
Also preface the cout/endl with a std:: or specify a "using namespace std" directive in your main() function.

If you still have problems, then it is probably because you do not have a compiler installed on your system.  To get it:
```

sudo apt-get install build-essential

```

P.S.  When including iostream.h (with the .h extension), one would typically expect a compiler warning indicating that the deprecated name-style for the header is being used; not a file-not-found error.

---

### Post by MadCow108 on 2009-05-29
maybe your header looks like this:
#include "iostream.h"

while it should be:
#include <iostream>

c++ standardlibraries, in comparision to c, are encapsuled in <> and have no ending.

@dwhitney67
#include <iostream.h> and #include "iostream.h" give a file not found error and no warning with g++ 4.3 on my system

---

### Post by dwhitney67 on 2009-05-29
> **MadCow108 said:**
> ...

@dwhitney67
#include <iostream.h> and #include "iostream.h" give a file not found error and no warning with g++ 4.3 on my system
I don't doubt you.  I was testing with g++ 4.1.2 under CentOS 5; the warnings is as follows:
```

g++ test.cpp 
In file included from /usr/lib/gcc/i386-redhat-linux/4.1.2/../../../../include/c++/4.1.2/backward/iostream.h:31,
                 from test.cpp:1:
/usr/lib/gcc/i386-redhat-linux/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.


```

---

### Post by bagljash on 2009-05-30
@ _Purple_
I've tried changing <iostream.h> to <iostream> but it didn't work out and I got following lines in Terminal

```
bagljash@bagljash:~/Desktop$ g++ HELLO.cpp 
HELLO.cpp: In function ‘int main()’:
HELLO.cpp:5: error: ‘cout’ was not declared in this scope

```

Here's how my code looks like, maybe there's really syntax error that I'm not seeing.

```
#include <iostream>

int main()
{
        cout << "Hello World! \n";
                return 0;
}

```

@dwhitney67

I've already tried 

```
sudo apt-get install build-essential
```

it gave me following notification 
```
bagljash@bagljash:~/Desktop$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libfreebob0 libqca2 libdevil-dev libxerces-c2-dev liballegro4.2-plugin-jack
  libjack0 libaldmb1 liblualib50-dev libxerces-c28 liblualib50 smc-data
  liblua50-dev lua50 libcelt0 libffado0 libtiff4-dev libcegui-mk2-1 libdumb1
  libtiffxx0c2 libxml++2.6-2 libfreeimage3 libcegui-mk2-dev open-invaders-data
  libboost-filesystem1.37.0 liblua50 libboost-system1.37.0 liballegro4.2
  libdevil1c2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by _Purple_ on 2009-05-30
> **bagljash said:**
> @ _Purple_
I've tried changing <iostream.h> to <iostream> but it didn't work out and I got following lines in Terminal

```
bagljash@bagljash:~/Desktop$ g++ HELLO.cpp 
HELLO.cpp: In function &#8216;int main()&#8217;:
HELLO.cpp:5: error: &#8216;cout&#8217; was not declared in this scope

```

Here's how my code looks like, maybe there's really syntax error that I'm not seeing.

```
#include <iostream>

int main()
{
        cout << "Hello World! \n";
                return 0;
}

```



As dwhitney67 has already mentioned you have to add "using namespace std" like this
```
#include <iostream>

using namespace std;

int main()
{
        cout << "Hello World! \n";
                return 0;
}
```

Else you will have to use std::.

---

### Post by jowilkin on 2009-05-30
change it to ```
#include <iostream>

using namespace std;

int main()
{
        cout << "Hello World! \n";
                return 0;
}
```

or

```
#include <iostream>

int main()
{
        std::cout << "Hello World! \n";
                return 0;
}
```

---

### Post by jowilkin on 2009-05-30
> **MadCow108 said:**
> 
@dwhitney67
#include <iostream.h> and #include "iostream.h" give a file not found error and no warning with g++ 4.3 on my system

It was pretty annoying when they made that change.  Broke a lot of the C++ code in my lab.  Yeah yeah, they should have been using iostream instead, but the code was written in the early days of C++ and "just worked" for a long time.  For a while I just copied iostream.h over to the system until I could go through and update all the source.

---

### Post by bagljash on 2009-05-30
Thank you very much guys, now it works, I've managed to successfully compile my first program. After compiling it in Terminal, file "a.out" was created on my Desktop, but don't know how to start it. How do you start it from terminal?

Thanks again. Btw the code I posted earlier was from book Teach Your Self C++ in 21 days, is this book good for beginner? Do you have any references on some C++ books for beginners?

---

### Post by dwhitney67 on 2009-05-30
> **bagljash said:**
> Thank you very much guys, now it works, I've managed to successfully compile my first program. After compiling it in Terminal, file "a.out" was created on my Desktop, but don't know how to start it. How do you start it from terminal?

Thanks again. Btw the code I posted earlier was from book Teach Your Self C++ in 21 days, is this book good for beginner? Do you have any references on some C++ books for beginners?
If your book was indicating that you use "iostream.h", then I would say that it is out of date.  But you can still use it; just be aware of the differences.  The main thing to get out of learning C++ is the use of class inheritance.

How did you compile the code... from the terminal?  If so, that is also how you would run the program.
```

g++ prog.cpp
./a.out

```

---

### Post by bagljash on 2009-06-01
> **dwhitney67 said:**
> If your book was indicating that you use "iostream.h", then I would say that it is out of date.  But you can still use it; just be aware of the differences.  The main thing to get out of learning C++ is the use of class inheritance.

How did you compile the code... from the terminal?  If so, that is also how you would run the program.
```

g++ prog.cpp
./a.out

```


Yes that's the way I compiled my code and I've got it running with
```
 ./a.out 
``` 

Thank you.

---

### Post by Volt9000 on 2009-06-01
Just thought I'd throw my two cents in:

If you don't like the default a.out filename you can specify your own with the -o option:

```

g++ file.cpp -o outputfile

```

As for your book-- I have the same book, and it's quite outdated. You should stay away from it, as it uses the old-style C++ standards. Find yourself a nice book which teaches you ISO C++.

---

