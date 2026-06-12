---
title: "kdevelop and shared libraries"
date: 2006-08-16
forum: Programming Talk
---

### Post by yola77 on 2006-08-16
Dear Ubuntu Users,

I have a problem with kdevelop and shared libraries. I am using Ubuntu-6.01 with kdevelop 3.3.2.

I am trying to integrate Geant4.8.1 in an IDE so I can debug. I have a working version of kdevelop3. Using a C++ simple hello world template I am attempting to add required '.so' libraries.

I have followed the official kdevelop3 FAQ and have spent many hours on-line for the answer, but no joy. 

This appears when executing a simple program with added libraries in kdevelop:

 ./test: error while loading shared libraries: libG4bosons.so: cannot open shared object file: No such file or directory

Even though I have added LD_LIBRARY_PATH to my 
"Project->Project Options-> Configure Options" with the appropriate path to the library. If I export the LD_LIBRARY_PATH to a bash shell and run my kdevelopProject-test/src/debug/test executable i get something else:

Hello, world!
*** glibc detected *** double free or corruption (!prev): 0x0804e0d8 ***
Aborted

As you can see it almost works but it appears that there is a problem with kdevelop. Have I missed something? 

Please help!

Thank you.

---

