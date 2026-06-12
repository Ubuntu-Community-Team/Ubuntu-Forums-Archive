---
title: "bash: ./fileName: cannot execute binary file"
date: 2007-04-01
forum: Programming Talk
---

### Post by jsym on 2007-04-01
Hello to anyone who thiks they might be able to help,

Whenever I try to build a c++ project via the terminal I am met with the following error:

```

g++ [various .h and .cpp files] -o fileName

./fileName

bash: ./fileName: cannot execute binary file

```

I doesn't matter what files I use--even "HelloWorld" causes the error--nor what directory I run from.  All my read-write-execute permissions are good too.  Further,this does not seem to be the "Object File vs. Executable File" issue that has been posted elsewhere, unless the "-c" is being thrown in by some background script or the like I don't know about.

Further confusing this is is the fact that I can drop the exact same code/files into eclipse and it compiles and runs without issue inside the workbench.   I'd be happy running my code from eclipse if it wasn't so slow (Yes, I have made the Sun-java "upgrade".  The computer having the execution issue is a 64bit AMD 3200+ with a gig of RAM which, I suspect, should be running faster than my pentium-M laptop with 768M RAM, even though the desktop is running Ubuntu and the laptop Gentoo.  Perhaps I am wrong about this?) and I suspect (hope?) that running directly from the terminal would give me the speed I require to generate and analyze a mass of data (any suggestions on this front would be welcome as well).

Thank you.

---

### Post by Wybiral on 2007-04-01
Can you print the "hello world" source and the exact command you used to compile?

Also, there shouldn't be various ".h" files in your compile command... Headers are meant for source, not in the compile command.

---

### Post by jsym on 2007-04-01
SOLVED (although I'm not really sure how!  What follows is the post I was typing up as I was recreating the issue for about the tenth time in two days.)

Well, now that I go back and check the "HelloWorld" program again, everything is fine with it, but not with my own code.

Just for completeness, my HelloWorld program is the following:
```

#include <iostream>

using namespace std;

int main()
{
  cout<<"Hello World!"<<endl;

  return 0;
}

```

I build and run it as follows:

```

$ g++ main.cpp -o helloWorld
$ ./helloWorld
Hello World!
$
```

There are 11 files that I need to wrap up and stick together to make my own program run (main.cpp + 5 .h + 5 .cpp).  When I use the same command I get burned, as follows:
```

$ g++ main.cpp agent.cpp agent.h game.cpp game.h .match.cpp match.h singleRand.cpp singleRand.h VERandGenerator.cpp VERandGenerator.h -o SuperTEST

In file included from main.cpp:32:
singleRand.h:6:1: warning: "NULL" redefined
In file included from /usr/include/wctype.h:35,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/cwctype:52,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/locale_facets.h:46,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/basic_ios.h:44,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ios:50,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ostream:44,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/iostream:44,
                 from main.cpp:21:
/usr/lib/gcc/x86_64-linux-gnu/4.0.3/include/stddef.h:400:1: warning: this is the location of the previous definition
main.cpp:574:2: warning: no newline at end of file
In file included from agent.cpp:2:
singleRand.h:6:1: warning: "NULL" redefined
In file included from /usr/include/wctype.h:35,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/cwctype:52,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/locale_facets.h:46,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/basic_ios.h:44,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ios:50,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ostream:44,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/iostream:44,
                 from agent.cpp:1:
/usr/lib/gcc/x86_64-linux-gnu/4.0.3/include/stddef.h:400:1: warning: this is the location of the previous definition
agent.cpp:559:3: warning: no newline at end of file
In file included from game.cpp:2:
singleRand.h:6:1: warning: "NULL" redefined
In file included from /usr/include/wctype.h:35,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/cwctype:52,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/locale_facets.h:46,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/basic_ios.h:44,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ios:50,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ostream:44,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../include/c++/4.0.3/iostream:44,
                 from game.cpp:1:
/usr/lib/gcc/x86_64-linux-gnu/4.0.3/include/stddef.h:400:1: warning: this is the location of the previous definition
game.cpp:514:2: warning: no newline at end of file
match.cpp:39:2: warning: no newline at end of file

$ ./SuperTEST
$ bash: ./SuperTEST: cannot execute binary file
$

```

Or at least that's what USED to happen.  When I did all this again simply scrolling through the terminal buffer for the commands it worked just fine.

Why it wouldn't do any of this two days ago is beyond me.  It's not like anything changed.  At least it works.

Thank you Wybiral for offering to help, apparently that was enough to convince my machine to smarten up.:)

---

