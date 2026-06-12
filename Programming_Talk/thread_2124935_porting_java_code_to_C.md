---
title: "porting java code to C"
date: 2013-03-12
forum: Programming Talk
---

### Post by hasanalikhattak on 2013-03-12
i have to port a java library to c, the library californium is written in java and i need it for the contiki-os which is written in C.
 i have not much expertise in C which is why i am asking if you guys can provide with some tutorials or tools which can help in porting the code to C

---

### Post by ofnuts on 2013-03-13
Porting is keeping the language, but aiming for a different platform (OS/CPU).

What you want is a rewrite... and I seriously doubt that you can do it in a reasonable time given that you admit you have little experience in C.

But Californium is just a Java implementation of the CoAP framework and there is already a C implementation of same: [http://sourceforge.net/projects/libcoap/](http://sourceforge.net/projects/libcoap/) . You may have to "port" it to contiki, though.

---

