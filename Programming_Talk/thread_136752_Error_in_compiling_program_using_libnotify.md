---
title: "Error in compiling program using libnotify"
date: 2006-02-26
forum: Programming Talk
---

### Post by idn on 2006-02-26
I am going to write a program to play around with libnotify. I have never written an app under linux before, and I am having trouble getting started. I have the following code

```
#include <libnotify/notify.h>
#include <glib.h>

#include <string.h>

#include <stdio.h>

main()
{

          printf ("Hello World!\n");

}
```



Just a hello world program which also includes the libnotify headers, but I get the ollowing error (see screenie)

I have the glib2.0-dev and gtk2.0 dev packages installed as well as build-essential and libnotify-dev

Any ideas?

---

