---
title: "From helloworld.c to helloworld.deb"
date: 2010-06-28
forum: Packaging and Compiling Programs
---

### Post by arvigeus on 2010-06-28
```
#include <stdlib.h>
int main(void) {
system("notify-send", "Hello, World!"); //ignore errors in this line
return 0;
}
```
I have the following code. What do I have to do to make it full blown linux app? I mean first to make a ordinary './configure', 'make', 'make instal' procedure and later to manually make it to deb (along with dependencies). In two words I need some manual how to build a real program (I have coding experience), along with explanations what does each thing (and no auto generating tools). Also, some guide on writing gnome applets would be appreciated.

---

### Post by Diabolis on 2010-06-28
[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

### Post by SevenMachines on 2010-06-28
just a couple more links
[simple makefile tutorial]("http://mrbook.org/tutorials/make/")
[simple autotools tutorial]("http://markuskimius.wikidot.com/programming:tut:autotools/")

---

### Post by arvigeus on 2010-06-29
Thanks, really helped me out!

---

