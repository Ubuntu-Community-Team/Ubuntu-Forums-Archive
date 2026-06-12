---
title: "openNI callback register error !! plz help"
date: 2012-09-09
forum: Programming Talk
---

### Post by Alec3327 on 2012-09-09
hi,
i'm trying to run the hand tracking code ( which is copied from ProrammingGuide document provided by OpenNI) on an ARM dev board (beagleboard_xm)
by searching the internet i managed to install OpenNI and Sensorkinect on the board ( using linux ubuntu 12.04 for arm) and the sample code "simpleviewer" works ( it shows the depth of the central point )
However, when i tried the hand tracking code in Openni's PDF programming guide (which needed a fix too i needed to declare a varible in order to compile it) the program exits instead of printing the hand point coordination.
i've also tried to run the code by "GDB" debugger and this is the output:

"Program received signal SIGSEGV, Segmentation fault.
0x40052c8a in xnRegisterGestureCallbacks () from /usr/lib/libOpenNI.so"

as it says the problem is in the callback register function... but i've no idea what is causing this...
BTW i have tried the code on a laptop (32 bits) and the code works perfectly ( different Openni and sensor source code i did it 3 months ego, i mean i cloned them 3 months ago but the openni running on arm was cloned 2 days ago ). it means the code is working on a 32 bit laptop but not arm.

i'm assuming it has something to do with the compatibility of Openni and SensorKinect that i cloned from github ( i've read somewhere that the new version are not compatible) but the thing is the "simpleviewer" sample code works...


any suggestions ? and i havent installed NITE on the ARM , but i dont think it's needed, is it ? does it have something to do with arm ubuntu ?

(email is line6s3 @ gmail. com)

---

### Post by Alec3327 on 2012-09-12
Any info on this issues? Has anyone ever tried to contact openNI directly?

---

### Post by oldos2er on 2012-09-12
Moved to Programming Talk.

---

