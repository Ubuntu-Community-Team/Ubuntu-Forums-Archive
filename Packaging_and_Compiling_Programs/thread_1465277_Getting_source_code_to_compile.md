---
title: "Getting source code to compile"
date: 2010-04-29
forum: Packaging and Compiling Programs
---

### Post by mikesmith00 on 2010-04-29
I'm working on some research for my math professor, and he asked me to attempt to compile this program, because we need to get it compiled and running before we start to edit it to work on our dynamical system.

[http://www.pawelpilarczyk.com/cmgraphs/](http://www.pawelpilarczyk.com/cmgraphs/)

The one that isn't working is in cmgraphs.zip.   To start though, I downloaded CHOMP, compiled, and got the library files libchompbitmaps.a, libchompcapd-auxil.a, libchompcapd-bitSet.a, libchompcapd-bzip2.a, libchompcapd-chom.a, and libchompcapd-homengin.a.  I copied these into /usr/lib.  Next I downloaded the CAPD library and did the same.  I also copied the include folders from both compilations into /usr/include.  I originally got quite a few errors, and went into the cmgraphs code and edited it to add #include<algorithm> and #include<memory>, and that reduced the errors I had to just (This is the command line output)

make target=unx
g++ -ansi -pedantic -Wall -O2 -s -L../capd/lib -L../chomp/lib cmgraphs.o -o cmgraphs  -lcapdpoincare -lcapddynsys -lcapddynset -lcapdmap -lcapdvectalg -lcapdrounding -lcapdinterval -lcapdauxil -lcapdcapd -lchomp -lpng -lz -llapack
/usr/bin/ld: cannot find -lcapdpoincare
collect2: ld returned 1 exit status
make: *** [cmgraphs] Error 1

If you could help me debug this problem it would be greatly appreciated, or at least point me in the right direction to where I can go to find this.  I've only programmed in Matlab and Python, so C++ is a new kind of monster for me.  Thank you.

[EDIT: I don't know if I'm in the right forum or not, if this needs moved to Programming Talk, then can one of the admins move it?  Also, I've made it a little bit further by changing the make file slightly, but it still can't find -lcapdpoincare and I don't see it anywhere in the CAPD folder]

---

### Post by SevenMachines on 2010-04-29
hi, can i check if capd compiled fine without errors? if so then libcapdpoincare should be in the capd (lowercase, i only mention as you've typed CAPD in your post) directory. eg
~/Desktop/cmgraphs$ ls ../capd/lib/libcapdpoincare.a 
../capd/lib/libcapdpoincare.a

if you 'make' in the the cmgraph directory then it looks for capd libraries in ../capd/lib, if you've got a different name for the capd directory (ie CAPD) then you'd need to change the cmgraph makefile

---

### Post by mikesmith00 on 2010-04-30
It actually wasn't installed, I thought it was.  I went back and reinstalled the capd library, and that fixed it.  Thank you very much

---

