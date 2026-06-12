---
title: "String.h header file doea not have any functions!!!"
date: 2011-03-02
forum: Packaging and Compiling Programs
---

### Post by ajaybhat999 on 2011-03-02
Hi. I am a new user to ubuntu. I will be using ubuntu for programming purposes. I compiled a basic program in gcc compiler(version 4.4). The program calls strrev() function in string.h header file. The compiler returns an error that strrrev() function is not found.
I opened the /usr/include/c++ folder and opened the string.h header file. But it did't have function definition of strrev() or any other string operation functions.
I even downloaded the string.h header file and tried to paste in /usr/include/c++ directory but unable to do so. 
please help!!!

---

### Post by ibuclaw on 2011-03-02
I assume strrev reverses a string?

Can't see any reference to it in the [POSIX specification]("http://pubs.opengroup.org/onlinepubs/9699919799/nframe.html") so I assume it's a non-standard C function, and there would be no such equivalent to whatever you had on Windows.

So you'll need to implement your own.

Regards

---

### Post by ajaybhat999 on 2011-03-19
ok. 
Thanks for the reply...:D

---

