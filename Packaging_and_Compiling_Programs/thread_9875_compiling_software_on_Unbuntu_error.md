---
title: "compiling software on Unbuntu error"
date: 2005-01-02
forum: Packaging and Compiling Programs
---

### Post by tiiim on 2005-01-02
hi!

What tools do i need to compile on Ubuntu? I downloaded GCC and other random lib files but trying to compile. One of them fails and at end of ./configure i get:

configure: error: C++ preproccesor... "/lib/cpp" fails sanity check 


any ideas?

Also im looking into geting into more coding so what files would i need and things (and hopefully this should sort out any other problems in future).

Tim  :D  :confused:

---

### Post by offby1 on 2005-01-02
[QUOTE=tiiim]hi!

What tools do i need to compile on Ubuntu? I downloaded GCC and other random lib files but trying to compile. One of them fails and at end of ./configure i get:

configure: error: C++ preproccesor... "/lib/cpp" fails sanity check 


any ideas?

Also im looking into geting into more coding so what files would i need and things (and hopefully this should sort out any other problems in future).

Tim  :D  :confused:[/QUOTE]
 You need to do ```
sudo apt-get install build-essential
``` which will install the basics for building applications from source.

---

### Post by tiiim on 2005-01-02
cheers im glad i got the basics installed now!  :D

---

