---
title: "Create a .deb from source"
date: 2005-11-18
forum: Packaging and Compiling Programs
---

### Post by Téragone on 2005-11-18
Hello,

How to create a .deb from source package which require outside build directory like binutils or glibc ?

Thanks

---

### Post by frodon on 2005-11-18
If your goal is to make a .deb for your use or few friends, checkinstall is the best solution.
Install it and when you compile a software type "sudo checkinstall -D" instead of "sudo make install", it will install the software giving synaptic all the needed informations to see it and create a .deb.

---

### Post by mgor on 2005-11-18
check this thread: [http://www.ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall](http://www.ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall)

---

### Post by cstudent on 2005-11-18
[QUOTE=mgor]check this thread: [http://www.ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall](http://www.ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall)[/QUOTE]


Sweet. Thanks for the link. I love it when I learn something useful.

Bill

---

### Post by Téragone on 2005-11-18
Merci Frodon,

I will try it but what are the other solution ? I'm curious about them.


Thanks also mgor

---

