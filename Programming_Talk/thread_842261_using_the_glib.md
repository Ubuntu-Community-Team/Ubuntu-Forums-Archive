---
title: "using the glib"
date: 2008-06-27
forum: Programming Talk
---

### Post by Okar on 2008-06-27
Hi,
I would like to write a program that uses the glib. however I get a bunch of errors while compiling. I get these even when using a "Hello World" Program that includes the glib.h and is linked against glib-2.0.
There is probably something general I'm doing wrong.
The Program
```
#include <stdio.h>
#include <glib.h>
int main(void) {
	printf("test");
}
```
The compile command:
```
gcc -I/usr/include/glib-2.0 -lglib-2.0 test2.c 
```
the errors
[errors]("http://ubuntuusers.de/paste/373501/")
are they all caused by: ```
/usr/include/glib-2.0/glib/gtypes.h:30:24: error: glibconfig.h: No such file or directory
```? and why don't I have this header file (a locate doesn't find it)

---

### Post by Zugzwang on 2008-06-27
Using the search function of google helps: [http://www.linux.ie/old-list/3563.html]("http://www.linux.ie/old-list/3563.html")

Edit: Whenever you are searching for missing package files, use packages.ubuntu.com: [http://packages.ubuntu.com/search?searchon=contents&keywords=glibconfig.h&mode=exactfilename&suite=hardy&arch=any]("http://packages.ubuntu.com/search?searchon=contents&keywords=glibconfig.h&mode=exactfilename&suite=hardy&arch=any")

---

### Post by xlinuks on 2008-06-27
Hi, this works:
```

gcc  -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include test2.c

```

---

### Post by kknd on 2008-06-27
The recommended way to do this is by using the output of 

[PHP] pkg-config --cflags --libs glib-2.0[/PHP]

Like:

[PHP]
gcc -c *.c `pkg-config --cflags glib-2.0`
gcc *.o -o exec `pkg-config --libs glib-2.0`
[/PHP]

---

