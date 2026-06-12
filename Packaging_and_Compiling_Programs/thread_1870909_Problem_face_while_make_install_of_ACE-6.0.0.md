---
title: "Problem face while make install of ACE-6.0.0"
date: 2011-10-28
forum: Packaging and Compiling Programs
---

### Post by agni07 on 2011-10-28
After I do sudo make, it abruptly ends with the error message as below.


Making all in tests
make[1]: Entering directory `/home/xx/Desktop/ACE_wrappers/build/tests'
make  all-recursive
make[2]: Entering directory `/home/xx/Desktop/ACE_wrappers/build/tests'
Making all in .
make[3]: Entering directory `/home/xx/Desktop/ACE_wrappers/build/tests'
/bin/bash ../libtool --tag=CXX   --mode=link g++  -W -Wall -Wpointer-arith  -g -O2 -pthread -pipe -O3 -I. -I..   -o Svc_Handler_Test Svc_Handler_Test-Main.o Svc_Handler_Test-Svc_Handler_Test.o libTest_Output.la ../ace/libACE.la -lrt -ldl 
libtool: link: g++ -W -Wall -Wpointer-arith -g -O2 -pthread -pipe -O3 -I. -I.. -o .libs/Svc_Handler_Test Svc_Handler_Test-Main.o Svc_Handler_Test-Svc_Handler_Test.o  ./.libs/libTest_Output.a ../ace/.libs/libACE.so -lrt -ldl -pthread
Svc_Handler_Test-Main.o: file not recognized: File truncated
collect2: ld returned 1 exit status
make[3]: *** [Svc_Handler_Test] Error 1
make[3]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/tests'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/tests'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/tests'
make: *** [all-recursive] Error 1

 I am a new comer in Linux and working first time on ACE.. I need to make n install it to run DDS.
Kindly help earliest.:confused:

P.S.: I also checked the Svc_Handler_Test.cpp for any errors in sourcearchive.com and found them to be exactly same. 

Thanx in advance

---

### Post by MG&amp;TL on 2011-10-28
General things:

1. Don't run as root when make-ing-you only need to when make-installing

2. Is there a README  file you could post please?

---

### Post by agni07 on 2011-10-28
Thanx for the immediate reply.
Now there is another error as given below when i do only * make*

g++: /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crti.o: No such file or directory
g++: /usr/lib/gcc/i486-linux-gnu/4.4.3/crtbeginS.o: No such file or directory
g++: /usr/lib/gcc/i486-linux-gnu/4.4.3/crtendS.o: No such file or directory
g++: /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crtn.o: No such file or directory
make[3]: *** [libACE.la] Error 1
make[3]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/ace'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/ace'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/ace'
make: *** [all-recursive] Error 1
 I have also attached the readme file.

---

### Post by MG&amp;TL on 2011-10-28
Errr..sorry, I see no readme...did you press the attach button?

Are you building in you home directory, or in another (restricted) place? If it's in a restricted place, then do use sudo make. Usually, however, it turns up in your download folder.

What makes me say that is the bit about gcc....perhpas you could tell us what ACE is and where to get it?

---

### Post by agni07 on 2011-10-31
I also checked up the /usr/lib/gcc but couldnt find i486- linux-gnu folder. there is only i686-linux-gnu folder.

---

### Post by agni07 on 2011-10-31
Solved!!
upgraded to 11.10 from 10.10
and then did ../configure and make install
now no error.

---

### Post by MG&amp;TL on 2011-10-31
Okay. Whatever works for you. :) If it ain't broke, don't fix it.

---

