---
title: "Compiler Error"
date: 2009-09-13
forum: Programming Talk
---

### Post by abotaha on 2009-09-13
Hi all, 
i have the following error when i want to compiler the program

[B]**** Build of configuration Debug for project BN ****

**** Internal Builder is used for build               ****
g++ -oBN.exe src\BN.o
C:\MinGW\bin\..\lib\gcc\mingw32\3.4.5\..\..\..\..\mingw32\bin\ld.exe: cannot open output file BN.exe: Permission denied
collect2: ld returned 1 exit status
Build error occurred, build is stopped
Time consumed: 171  ms.  
[/B]
i am using eclipse c++. I appreciate any help. 

Thanks in advance.

---

### Post by Zugzwang on 2009-09-13
Check where the linker is trying to put the executable file (there must be a path given somehow). As the error message states, you might not have write access to it due to various reasons (e.g., due to using a restricted user you cannot write anywhere, the directory might be on a CD or flagged read-only, etc.)

Also read section 2 of [this post]("http://ubuntuforums.org/showthread.php?t=1258665"). It will tell you why you probably will not get more detailed help here.

---

### Post by geirha on 2009-09-13
It's saying it doesn't have permission to create the resulting BN.exe file. Do you have write access to the directory?

---

### Post by abotaha on 2009-09-13
Thank you guys for your consideration.
:D:popcorn::popcorn:

---

