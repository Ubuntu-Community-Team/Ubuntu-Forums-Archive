---
title: "[C++] Basic Development on Gnome"
date: 2011-06-10
forum: Programming Talk
---

### Post by notgary on 2011-06-10
I'm trying to write a C++ application on Gnome/Ubuntu as my first non-academic exercise in programming and I'm having trouble getting started with it. I can't find any information on the different header files I need to include in order to access the functions in the Gnome API. I've looked around the Gnome developer site and found a few example programs that contain the lines

```
#include <glib-object.h>
#include <gtkmm.h>
#include "config.h"
```

However, these are just examples of the use of these particular headers and don't tell me what functionality they provide in general. I've found the Gnome API documentation, but that just contains a list of all the available functions without any context.

The specific problem I'm trying to solve is getting at the passwords stored in the Gnome Keyring. There's some [example code]("http://live.gnome.org/GnomeKeyring/StoringPasswords") that details how to store and retrieve passwords but those are just snippets from larger programs and don't tell me how to get started writing one.

There are two things I'm looking for here:

[LIST=1]
[*]The most important one is finding out about the available headers on Gnome. Where can I learn about what ones there are, what functionality they provide and what packages I need to install to be able to use them.
[*]This one doesn't matter if the above one gets sorted out, but if it doesn't, then a complete example program that retrieves a password from the Gnome Keyring and stores it as a variable would help me get started.
[/LIST]

---

### Post by Petrolea on 2011-06-10
It's hard to find programs already written, but a piece of code can help a lot. Then it is up to you to implement it in your program. If you have no idea how, I'd recommend that you first learn some other things before that and it will help you understand harder problems.

Documentation is great if you know how to use it. I don't know everything about GTK, so when there's a problem I look up the function, it tells me what it does, what arguments it needs and then I implement it in my code. Learn some more C++ and GTK and you will start to understand it.

---

### Post by notgary on 2011-06-10
Thanks a lot for your response, but my problem is that I don't even know where to begin with Gnome programming. The list of available functions is extensive, but I can't find anything that tells me what header files I need to include in order to use them. There's a list of functions [here]("http://developer.gnome.org/gnome-keyring/stable/gnome-keyring-Simple-Password-Storage.html") for accessing the passwords in Gnome Keyring, but there's nothing on what my #include directive is supposed to be.

---

### Post by Petrolea on 2011-06-10
> **notgary said:**
> Thanks a lot for your response, but my problem is that I don't even know where to begin with Gnome programming. The list of available functions is extensive, but I can't find anything that tells me what header files I need to include in order to use them. There's a list of functions [here]("http://developer.gnome.org/gnome-keyring/stable/gnome-keyring-Simple-Password-Storage.html") for accessing the passwords in Gnome Keyring, but there's nothing on what my #include directive is supposed to be.

Why not try tutorials?
[http://developer.gnome.org/gtkmm-tutorial/3.0/](http://developer.gnome.org/gtkmm-tutorial/3.0/)

---

### Post by notgary on 2011-06-10
Gtkmm is just for creating interfaces. I'm trying to write code that does a lot of stuff behind the scenes, such as working with the password store.

---

### Post by simeon87 on 2011-06-10
Have you downloaded the development package? I think they're in libgnome-keyring-dev. You should also be able to find the headers in there.

---

### Post by cracker89 on 2011-06-10
> **Petrolea said:**
> Why not try tutorials?
[http://developer.gnome.org/gtkmm-tutorial/3.0/](http://developer.gnome.org/gtkmm-tutorial/3.0/)

Good idea.. Just what I was looking for too. 
Cheera!):P

---

### Post by notgary on 2011-06-10
Is there nowhere on the internet that details what the headers are and what they do?

---

### Post by SevenMachines on 2011-06-10
General gnome dev stuff with some app tutorials
[http://developer.gnome.org/](http://developer.gnome.org/)

I'd recommend installing devhelp, gnome stuff tends to integrate with that so run it and (if the dev packages are installed) you'll find things like the gnome-keyring documentation in it plus much more

---

### Post by notgary on 2011-06-10
I have Devhelp installed, but it's just a mirror of the API documentation I found on developer.gnome.org. It lists of all the functions, but no way to include them in your program using the #include directive.

---

### Post by SevenMachines on 2011-06-10
A general way to know the includes for me might be something like, for example for gnome keyring

* Install the dev package
```
 $ sudo apt-get install libgnome-keyring-dev
```* Find which header files it includes
```
$ dpkg -L libgnome-keyring-dev |grep include
/usr/include
/usr/include/gnome-keyring-1
/usr/include/gnome-keyring-1/gnome-keyring.h
/usr/include/gnome-keyring-1/gnome-keyring-memory.h
/usr/include/gnome-keyring-1/gnome-keyring-result.h
```* Check if it uses pkg-config to make compiling easier
```
$ dpkg -L libgnome-keyring-dev |grep pkgconfig
/usr/lib/pkgconfig
/usr/lib/pkgconfig/gnome-keyring-1.pc
```* See what directives pkg-config generates 
```
$ pkg-config --cflags --libs gnome-keyring-1
-I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/gnome-keyring-1  -L/usr/lib/x86_64-linux-gnu -lgnome-keyring -lglib-2.0 
```So we now know all we need to to use these headers. There are 3 header files inside the /usr/include/gnome-keyring-1 include directory. Since /usr/include is the the compiler search directory for headers we could just inlude the headers relative to that, eg

myprogram.c:
```
#include <gnome-keyring-1/gnome-keyring.h>
```But we can see from the pkg-config  output that it adds /usr/include/gnome-keyring-1 to the include search path, so its probably best to use that instead

myprogram.c:
```
#include <gnome-keyring.h>
```And then compile using pkg-config, for example somthing like... 
```
$ gcc -o myprog myprogram.c `pkg-config --cflags --libs gnome-keyring-1'
```

Hopefully thats some help anyway

---

### Post by Petrolea on 2011-06-10
Why do you worry so much about these headers? Compiler will warn you if you don't use the required ones and if you use headers that you don't need won't hurt you a lot.

---

### Post by notgary on 2011-06-10
Thanks a lot for your response. This has been most helpful, but I'm still having problems.

I've gotten the library installed

```
$ sudo apt-get install libgnome-keyring-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnome-keyring-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```

I've located the header files in the filesystem

```
$ dpkg -L libgnome-keyring-dev | grep include
/usr/include
/usr/include/gnome-keyring-1
/usr/include/gnome-keyring-1/gnome-keyring.h
/usr/include/gnome-keyring-1/gnome-keyring-memory.h
/usr/include/gnome-keyring-1/gnome-keyring-result.h
```

I've checked to see if it uses dpkg to make compilation easier

```
$ dpkg -L libgnome-keyring-dev | grep pkgconfig
/usr/lib/pkgconfig
/usr/lib/pkgconfig/gnome-keyring-1.pc
```

I've checked to see what directed pkg-config generates

```
$ pkg-config --cflags --libs gnome-keyring-1
-I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/gnome-keyring-1  -L/usr/lib/i386-linux-gnu -lgnome-keyring -lglib-2.0  
```

My program looks like this

```
#include <gnome-keyring.h>

int main () {
}
```

and the output from the compiler looks like this

```
$ g++ -o main main.cpp 'pkg-config --cflags --libs gnome-keyring-1'
g++: pkg-config --cflags --libs gnome-keyring-1: No such file or directory
main.cpp:1:27: fatal error: gnome-keyring.h: No such file or directory
compilation terminated.
```

I changed the include directive back to

```
# include <gnome-keyring-1/gnome-keyring.h>
```

and that fixed that problem, but now I'm getting

```
$ g++ -o main main.cpp 'pkg-config --cflags --libs gnome-keyring-1'
g++: pkg-config --cflags --libs gnome-keyring-1: No such file or directory
In file included from main.cpp:1:0:
/usr/include/gnome-keyring-1/gnome-keyring.h:27:18: fatal error: glib.h: No such file or directory
compilation terminated.
```

Two questions here:

[LIST=1]
[*]Do you know why I've had to include the longer path to the gnome-keyring.h file
[*]Why am I getting the error about glib.h not being found?
[/LIST]

---

### Post by Petrolea on 2011-06-11
> **notgary said:**
> Thanks a lot for your response. This has been most helpful, but I'm still having problems.

I've gotten the library installed

```
$ sudo apt-get install libgnome-keyring-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnome-keyring-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```

I've located the header files in the filesystem

```
$ dpkg -L libgnome-keyring-dev | grep include
/usr/include
/usr/include/gnome-keyring-1
/usr/include/gnome-keyring-1/gnome-keyring.h
/usr/include/gnome-keyring-1/gnome-keyring-memory.h
/usr/include/gnome-keyring-1/gnome-keyring-result.h
```

I've checked to see if it uses dpkg to make compilation easier

```
$ dpkg -L libgnome-keyring-dev | grep pkgconfig
/usr/lib/pkgconfig
/usr/lib/pkgconfig/gnome-keyring-1.pc
```

I've checked to see what directed pkg-config generates

```
$ pkg-config --cflags --libs gnome-keyring-1
-I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/gnome-keyring-1  -L/usr/lib/i386-linux-gnu -lgnome-keyring -lglib-2.0  
```

My program looks like this

```
#include <gnome-keyring.h>

int main () {
}
```

and the output from the compiler looks like this

```
$ g++ -o main main.cpp 'pkg-config --cflags --libs gnome-keyring-1'
g++: pkg-config --cflags --libs gnome-keyring-1: No such file or directory
main.cpp:1:27: fatal error: gnome-keyring.h: No such file or directory
compilation terminated.
```

I changed the include directive back to

```
# include <gnome-keyring-1/gnome-keyring.h>
```

and that fixed that problem, but now I'm getting

```
$ g++ -o main main.cpp 'pkg-config --cflags --libs gnome-keyring-1'
g++: pkg-config --cflags --libs gnome-keyring-1: No such file or directory
In file included from main.cpp:1:0:
/usr/include/gnome-keyring-1/gnome-keyring.h:27:18: fatal error: glib.h: No such file or directory
compilation terminated.
```

Two questions here:

[LIST=1]
[*]Do you know why I've had to include the longer path to the gnome-keyring.h file
[*]Why am I getting the error about glib.h not being found?
[/LIST]

1.) Because the file is in that directory. Include looks in default /usr/include directory, but keyring stored .h in another directory within the default one (/usr/include/gnome-keyring-1).

2.) You try to include glib.h from gnome-keyring-1 directory. It isn't there.

---

