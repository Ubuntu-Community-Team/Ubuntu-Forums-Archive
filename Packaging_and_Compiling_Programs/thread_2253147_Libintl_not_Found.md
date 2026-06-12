---
title: "Libintl not Found"
date: 2014-11-17
forum: Packaging and Compiling Programs
---

### Post by Alex_Collins on 2014-11-17
I've been setting up a website developed by someone else(Web-Cat) and this involves the program auto-compiling some code. The code fails to compiling seemingly because of an unincluded library called libintl. I've done what searching I can but despite finding that it seems to be connected to the getText package installing that does not seem to solve the problem. What is this package? And if special how do I link to the package?

The exact error code in case that is helpful. 
g++ -O0 -g3 -Wall -fnon-call-exceptions -finstrument-functions -DCXXTEST_INCLUDE_SYMREADER_DIRECTLY -c -I/cxxtest -I/cxxtest/bfd -I/tmp/tomcat7-tomcat7-tmp/MUN/acollins "-IBasic Tests" BankAccount.cpp
gcc -o runStudentTests.exe ../../../../../../../../UserScripts/MUN/acollins/CppTddPlugin/obj/assert.o BankAccount.o -lstdc++ -lbfd -liberty -lintl
/usr/bin/ld: cannot find -lintl
collect2: error: ld returned 1 exit status

---

### Post by secretservgy on 2014-11-17
From what I found, you could try to remove "intl" from build.xml and use fprintf instead of fiprintf.

---

### Post by steeldriver on 2014-11-17
Hello and welcome to the forums

Have you tried building it without the -lintl ? AFAIK, the libintl.h header file is provided by libc6-dev, so I wonder whether intl object code has been subsumed into the standard library?

If it doesn't work, at least the list of undefined objects would give us something to go on

BTW not quite sure why you're compiling with g++ and then linking using gcc with libstdc++ added explicitly - can you provide a link to the instructions you're following?

---

### Post by Alex_Collins on 2014-11-18
Thanks very much for the help. I changed the calls of [COLOR=#000000]fiprintf to fprintf  and the code works fine now.[/COLOR]

---

