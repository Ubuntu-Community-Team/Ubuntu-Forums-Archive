---
title: "Compiling javascript alongside C++ project"
date: 2009-11-13
forum: Packaging and Compiling Programs
---

### Post by jaytron on 2009-11-13
Hi all,

I'm attempting to compile a program but I'm running into some issues. The program is mostly coded in C++ but part of the program makes use of javascript via spidermonkey. The make file attempts to compile the javascript files into .o objects and link them

 g++ -ljs -lboost_thread-mt -lboost_regex -lboost_system-mt -lnspr4 -lxerces-c -lmysqlpp  -Wl,-V  -g -I/usr/local/include/boost-1_38/ -I/usr/local/include/mysql++ -I/usr/include/mysql -I/usr/local/include/nspr -I/usr/local/include/boost -I/usr/local/include/js -MMD -MP -MF build/Debug/GNU-Linux-x86/resources/constants.o.d -o build/Debug/GNU-Linux-x86/resources/constants.o resources/constants.js
GNU ld (GNU Binutils for Ubuntu) 2.18.93.20081009
  Supported emulations:
   elf_i386
   i386linux
   elf_x86_64
/usr/bin/ld:resources/constants.js: file format not recognized; treating as linker script
/usr/bin/ld:resources/constants.js:25: syntax error
collect2: ld returned 1 exit status

 Is there something special i need to do here? (note: the above is an exert from the make file with a flag removed, heres the actual make file line:
 
g++ -ljs -lboost_thread-mt -lboost_regex -lboost_system-mt -lnspr4 -lxerces-c -lmysqlpp   -c -g -Wall -I/usr/local/include/boost-1_38/ -I/usr/local/include/mysql++ -I/usr/include/mysql -I/usr/local/include/nspr -I/usr/local/include/boost -I/usr/local/include/js -MMD -MP -MF build/Debug/GNU-Linux-x86/resources/constants.o.d -o build/Debug/GNU-Linux-x86/resources/constants.o resources/constants.js
g++: resources/constants.js: linker input file unused because linking not done

i took out the -c flag as that seemed to be causing the linking problem

Any ideas on this one? Thanks in advance.

---

