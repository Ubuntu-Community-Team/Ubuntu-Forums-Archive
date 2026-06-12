---
title: "GDB and C++ Line Numbers"
date: 2011-09-06
forum: Programming Talk
---

### Post by jmjatlanta on 2011-09-06
I am having difficulty with GDB and C++ in Ubuntu, and am unsure where to go for answers. Here's the basics:

I have a simple program:
<code>
#include <iostream>
#include <map>
#include <string>

int main(int argc, char* argv[]) {
        std::map<std::string, std::string> dict;
        dict["Hello"] = "World!";
        std::cout << "Map size is " << dict.size() << std::endl;
        return 0;
}
</code>

and I compile via:

g++ -O0 -ggdb -o DebugTest DebugTest.cpp

I step through the code, and hit the line

dict["Hello"] = "World"; 

I enter "n" to get to the next line, and the program runs all the last lines (I get the expected output on STDOUT) and stops in __libc_start_main(). 

I have attempted to do the same thing in Cygwin on my Windows XP box, and it works as expected, stepping through the remaining lines. But with Ubuntu (Natty), it seems to run all the lines and jump to the end.

If I type "break 7" it works, as it finds the "dict["Hello"] = ..." line. If I type "break 8" gdb says "No line 8 in file "DebugTest.cpp""

Here's the output of my GDB session:

gdb DebugTest
GNU gdb 6.8
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-pc-linux-gnu"...
(gdb) break main
Breakpoint 1 at 0x8048bde: file DebugTest.cpp, line 6.
(gdb) run
Starting program: /home/jmjatlanta/development/cpp/cpplanguage/DebugTest/DebugTest

Breakpoint 1, main (argc=1, argv=0xbf82b8d4) at DebugTest.cpp:6
6               std::map<std::string, std::string> dict;
(gdb) n
7               dict["Hello"] = "Test";
(gdb) n
Number of elements: 1
0x002e1e37 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
(gdb) n
Single stepping until exit from function __libc_start_main,
which has no line number information.

Program exited normally.
(gdb)

---

### Post by Arndt on 2011-09-06
> **jmjatlanta said:**
> I am having difficulty with GDB and C++ in Ubuntu, and am unsure where to go for answers. Here's the basics:

I have a simple program:
<code>
#include <iostream>
#include <map>
#include <string>

int main(int argc, char* argv[]) {
        std::map<std::string, std::string> dict;
        dict["Hello"] = "World!";
        std::cout << "Map size is " << dict.size() << std::endl;
        return 0;
}
</code>

and I compile via:

g++ -O0 -ggdb -o DebugTest DebugTest.cpp

I step through the code, and hit the line

dict["Hello"] = "World"; 

I enter "n" to get to the next line, and the program runs all the last lines (I get the expected output on STDOUT) and stops in __libc_start_main(). 

I have attempted to do the same thing in Cygwin on my Windows XP box, and it works as expected, stepping through the remaining lines. But with Ubuntu (Natty), it seems to run all the lines and jump to the end.

If I type "break 7" it works, as it finds the "dict["Hello"] = ..." line. If I type "break 8" gdb says "No line 8 in file "DebugTest.cpp""

Here's the output of my GDB session:

gdb DebugTest
GNU gdb 6.8
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-pc-linux-gnu"...
(gdb) break main
Breakpoint 1 at 0x8048bde: file DebugTest.cpp, line 6.
(gdb) run
Starting program: /home/jmjatlanta/development/cpp/cpplanguage/DebugTest/DebugTest

Breakpoint 1, main (argc=1, argv=0xbf82b8d4) at DebugTest.cpp:6
6               std::map<std::string, std::string> dict;
(gdb) n
7               dict["Hello"] = "Test";
(gdb) n
Number of elements: 1
0x002e1e37 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
(gdb) n
Single stepping until exit from function __libc_start_main,
which has no line number information.

Program exited normally.
(gdb)

For what it's worth, it works for me. I get to line 7, and 8, and 9. Doing 'next' on line 10 brings me to __libc_start_main.


```
GNU gdb (GDB) 7.1-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/arndt/tmp/DebugTest...done.
```

I run 10.04 (lucid).

---

### Post by jmjatlanta on 2011-09-06
> **Arndt said:**
> 
I run 10.04 (lucid).


Ahhh. There is the issue. Your GDB was newer than mine, even though I'm on a newer version of Ubuntu. I attempted to remove and reinstall gdb but got the same 6.8 version back. So I downloaded the source and recompiled. I'm now at 7.3.1, and everything works.

I'm suspecting that when I downloaded an older version of insight, it came with the old version of gdb. Why I couldn't upgrade via apt-get I don't know, and at this point it doesn't bother me.

Thanks for your help!

-jmjatlanta

---

