---
title: "The Gnome terminal and Segmentation fault"
date: 2006-11-07
forum: Programming Talk
---

### Post by mesh2005 on 2006-11-07
I'm facing a strange problem. I have three machines, one is ubuntu, one is a windows machine and the third one is a redhat 7.2 machine. I connected remotely to the redhat machine using my ubuntu machine to compile a C program and I got many segmentation faults even with some trivial code like fprintf statments added to the source code. I connected to the same redhat machine using my windows machine (through putty) and the I tried to compile the same program. It worked immediately without any segmentation fault !

Could anyone explain it? I'm using the Gnome terminal to connect the redhat machine from my ubuntu machine.

Thank you

---

### Post by hod139 on 2006-11-21
Can you show the code?  Using different ssh clients to connect to the redhat machine shouldn't make a difference in the binaries being produced.

---

