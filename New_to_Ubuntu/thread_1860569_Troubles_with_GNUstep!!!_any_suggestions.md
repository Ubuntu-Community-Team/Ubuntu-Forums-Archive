---
title: "Troubles with GNUstep!!! any suggestions?"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by AEllerbrock on 2011-10-14
i'm trying to program objective c on ubuntu and i installed gnustep and its packages with this code lines:
sudo apt-get install gnustep
sudo apt-get install gnustep-devel gobjc

then i made a hello world program on gedit and saved it on my desktop. i found in a tutorial to compile it this way
(in the terminal)

. /usr/share/GNUstep/Makefiles/GNUstep.sh

gcc `gnustep-config --objc-flags` -lgnustep-base /home/andreas/Desktop/hello.m -o hello

when i press enter this message appears>:
"/home/andreas/Desktop/hello.m:10:1: fatal error: error writing to /tmp/ccxZ4Qaj.s: No space left on device
compilation terminated."

im pretty sure i have enough space...does anybody know why did i found that message and how to fix it?

---

### Post by dFlyer on 2011-10-14
From a terminal enter df -H and post the results.

---

