---
title: "Do I have a problem with gcc?"
date: 2013-01-03
forum: Programming Talk
---

### Post by sim085 on 2013-01-03
Hello,

I have this problem when I am trying to compile an Arduino example (for WiFi-shield) but thought of asking the question here since on the Internet I found that the problem could be related to the gcc. 

Basically when I try to compile the example I get the following error:

```

/usr/share/arduino/libraries/WiFi/WiFi.cpp: In member function ‘uint8_t* WiFiClass::macAddress(uint8_t*)’:
/usr/share/arduino/libraries/WiFi/WiFi.cpp:112:1: error: unable to find a register to spill in class ‘POINTER_REGS’
/usr/share/arduino/libraries/WiFi/WiFi.cpp:112:1: error: this is the insn:
(insn 35 25 26 2 (set (reg:QI 23 r23)
        (mem/c:QI (plus:HI (reg/f:HI 28 r28)
                (const_int 2 [0x2])) [3 S1 A8])) /usr/share/arduino/libraries/WiFi/WiFi.cpp:110 18 {movqi_insn}
     (nil))
/usr/share/arduino/libraries/WiFi/WiFi.cpp:112: confused by earlier errors, bailing out

```

I checked the code and the error seem to be related with a function named memcpy(...). If I delete the call to that function the example compiles without any problem.

Note that on Windows (version 7) the same example works without any issue.

As I said on the net I found that the problem could be related with the gcc. However I could not find much more information. I did a call to apt-get update and apt-get upgrade to see if this would solve my problems. However I still have the same problem.

Does anyone here know from where maybe this issue might be coming from?

---

### Post by Bachstelze on 2013-01-03
The error is not sufficient, we also need to know the command youare running (at least). Also, this is C++ so you should compile it with g++, not gcc.

---

