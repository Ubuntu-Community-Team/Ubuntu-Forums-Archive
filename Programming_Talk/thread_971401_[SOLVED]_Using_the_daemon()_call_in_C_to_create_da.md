---
title: "[SOLVED] Using the daemon() call in C to create daemons?"
date: 2008-11-04
forum: Programming Talk
---

### Post by gpsmikey on 2008-11-04
Greetings -- In looking into createing simple daemons in C, I can find the basic info on it in a number of tutorials etc, however, I was wondering if anyone had any examples using the daemon() call that exists in some Linux versions (including Ubuntu) for creating simple daemons ??  I want to create a simple serial logging daemon that monitors the serial port (status from the hot tub) and logs it to a file for later analysis.  Any simple examples or pointers would be appreciated !!  

Thanks
mikey

---

### Post by supirman on 2008-11-05
There's nothing to using the daemon() call.  Here's a simple example.  Calling daemon() will detach your process from a controlling tty, close stdin/stdout, and will also fork & exit the parent so that your process becomes a child of init.  

For debugging, I added a -f option.  If you specify -f, the program won't call daemon() so that you'll get your printfs.  If you don't specify -f, the application will call daemon() and you won't see any more printfs.


```
#include <ctype.h>
#include <stdbool.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>


int main(int argc, char** argv)
{
  bool run_in_foreground;
  int loop_count;
  int c;

  opterr = 0;

  while((c = getopt(argc, argv, "f")) != -1)
  {
    switch(c)
    {
    case 'f':
      run_in_foreground = true;
      break;

    case '?':
      printf("Unrecognized option '%c'.\n", optopt);
      return 1;

    default:
      abort();
    }
  }


  printf("This is my application...\n");

  if(!run_in_foreground)
  {
    printf("This is the last message you'll see, since I'm going to call daemon()\n");
    daemon(0,0);
  }
  else
  {
    printf("I'm in the foreground, so you'll still see my printfs\n");
  }


  for(loop_count = 0; loop_count < 10; loop_count++)
  {
    printf("Loop count is %d\n", loop_count);
    sleep(1);
  }

  return 0;
}

```

Hope that helps a bit.

---

### Post by dwhitney67 on 2008-11-05
> **supirman said:**
> ...
```
...
#include <stdbool.h>
...

  bool run_in_foreground;

...

```
...
Be careful of mixing C++ data types (e.g. bool) into a C program.  The program may not be portable.

For further reference on the differences between C and C++: [http://people.cs.uchicago.edu/~iancooke/osstuff/ccc.html](http://people.cs.uchicago.edu/~iancooke/osstuff/ccc.html)

---

### Post by gpsmikey on 2008-11-05
thanks for the info people -- I will see if I can crash my system when I get home tonight.  Looks like a really simple way to create the daemon (and the idea of the '-f' is good for debugging too !! ).  thanks much !!

mikey

---

### Post by supirman on 2008-11-05
That's not a c++ data type -- stdbool.h is part of the c99 standard...  :confused:

---

### Post by dwhitney67 on 2008-11-05
On my Ubuntu 8.04 system, stdbool.h is located in /usr/include/c++/4.2/tr1.

On my Fedora 9 system, stdbool.h is located in /usr/include/c++/4.3.0/tr1.

The thing I see in common between both systems is the "c++" in the path.

---

### Post by supirman on 2008-11-05
Sorry, you're wrong.

```
$ locate stdbool.h
/usr/include/c++/4.2/tr1/stdbool.h
[COLOR="Red"]/usr/lib/gcc/i486-linux-gnu/4.2/include/stdbool.h[/COLOR]

```


```
 $gcc -v -c daemon.c
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 /usr/lib/gcc/i486-linux-gnu/4.2.4/cc1 -quiet -v daemon.c -quiet -dumpbase daemon.c -mtune=generic -auxbase daemon -version -fstack-protector -fstack-protector -o /tmp/ccsfMarj.s
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/local/include"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.2.4/../../../../i486-linux-gnu/include"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
[COLOR="Red"]#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/gcc/i486-linux-gnu/4.2.4/include
 /usr/include
End of search list.
[/COLOR]GNU C version 4.2.4 (Ubuntu 4.2.4-1ubuntu3) (i486-linux-gnu)
	compiled by GNU C version 4.2.4 (Ubuntu 4.2.4-1ubuntu3).
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: e2971cf2189271aeeb10133511ecea3a
 as --traditional-format -V -Qy -o daemon.o /tmp/ccsfMarj.s
GNU assembler version 2.18.0 (i486-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.18.0.20080103

```

Notice the search path and the file location, highlighted in red.  

Plus, see the c99 standard since you're confused: [http://www.comeaucomputing.com/techtalk/c99/#bool](http://www.comeaucomputing.com/techtalk/c99/#bool)

---

### Post by dwhitney67 on 2008-11-05
I stand corrected.

---

