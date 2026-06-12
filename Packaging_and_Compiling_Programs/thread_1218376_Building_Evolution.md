---
title: "Building Evolution"
date: 2009-07-20
forum: Packaging and Compiling Programs
---

### Post by Jaqoup on 2009-07-20
Hi There,
i'm kind of new to the development in ubuntu
i'm trying to build evolution
i've downloaded the source code of 2.26.1 and downloaded all it's dependencies, configured it and on "make" it is built successfully.
but wherever i change anything in the code and rebuild it, nothing is affected
i launch the "evolution" file from the shell folder
or "make install" and launch "evolution" from the terminal
but always nothing is changed, like i've changed nothing in the code

am i missing something ?

Thanx.

---

### Post by Grishka on 2009-07-21
> **Jaqoup said:**
> Hi There,
i'm kind of new to the development in ubuntu
i'm trying to build evolution
i've downloaded the source code of 2.26.1 and downloaded all it's dependencies, configured it and on "make" it is built successfully.
but wherever i change anything in the code and rebuild it, nothing is affected
i launch the "evolution" file from the shell folder
or "make install" and launch "evolution" from the terminal
but always nothing is changed, like i've changed nothing in the code

am i missing something ?

Thanx.

'make clean' before 'make'.

---

### Post by Jaqoup on 2009-07-21
yeah, i did that, but nothing is affected
but i'm opening another instance of evolution while "make install"ing does that affect ?

---

### Post by TrueTom on 2009-07-21
Check if 'make install' put evolution in '/usr/l**ocal**/bin'...

---

### Post by Jaqoup on 2009-07-23
yeah i've checked that folder and found that make install puts the executable there
but also when i open that executable nothing is changed although i changed much in the code :S:S

BTW. i'm changing in the code of the composer module

---

### Post by Jaqoup on 2009-07-31
ah i found the reason :D
i was opening another instance of the program, so it opens the opened instance instead of the built one :s

Thanx all

---

