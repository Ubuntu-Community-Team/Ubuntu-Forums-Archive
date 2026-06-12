---
title: "Have loaded missing headers, but they are still reported missing !"
date: 2011-04-23
forum: Packaging and Compiling Programs
---

### Post by kliq on 2011-04-23
Hello.

I'm trying to compile a program that I downloaded and it reports [amongst many other things]:```
 
....
gcc -O2  -L/usr/X11R6/lib -lX11 -lXext -o viewer viewer.c
viewer.c:28:22: error: X11/Xlib.h: No such file or directory
viewer.c:29:33: error: X11/extensions/XShm.h: No such file or directory
......

```So I fetched the headers and [after many more failed attempts at compiling] decided to store them in:
```

/usr/X11R6/lib/X11/extensions
/usr/X11R6/lib/X11
/usr/X11R6/lib
/usr/X11R6/include/X11
/usr/X11R6/X11

```All at the same time ! 

But the compile error message remains the same

Can anyone help, please.

---

### Post by SevenMachines on 2011-04-24
You would need to add the -I (capital i) option to the compiler with the path to the includes,
```
 -I/usr/X11R6/include/
```More importantly though, it sounds like you've downloaded, compiled, and installed these libraries yourself, and you've installed them in the system directory hierarchy. This is a very bad idea, and also not at all needed.

If you really want to install your own compiled libraries, install them to the /usr/local hierarchy, eg /usr/local/lib/, /usr/local/include, etc, its what its there for. This means you arent going to overwrite any files essential to your running system

But the best way, by far, and the way that should be used unless you *really* need to install you own library version for some specific reason is to use the repository versions. 

For example, if you're trying to compile a program and you see
```
viewer.c:29:33: error: X11/extensions/XShm.h: No such file or directory
```The first thing is to find out what package supplies those headers
```
$ apt-file update
$ apt-file search XShm.h
libxext-dev: /usr/include/X11/extensions/XShm.h
```So we need to install the libxext-dev package, which will also bring in all the libraries and headers it needs automatically, saving all that effort
```
$ sudo apt-get install libxext-dev
```Since /usr/include is on the search path for the compiler, and the file installs inside this directory to X11/extensions, the XShm.h header will be found without any additional compiler options

If we actually needed to add compiler options to get the right paths and so on, because we're using the repository version we have more help built in since many packages use something called pkg-config to sort this out for us. in this case,
```
$ dpkg -L libxext-dev |grep pkgconfig/
/usr/lib/x86_64-linux-gnu/pkgconfig/xext.pc

```So, this packages uses pkg-config, now we can get all the right compiler options automatically
```
$ pkg-config --cflags --libs xext
 -L/usr/lib/x86_64-linux-gnu -lXext 
```So in practice, we would include this command in our compiler line in between backquotes `,
```
$ gcc -o myprog myprog.c `pkg-config --cflags --libs xext`
```

---

### Post by kliq on 2011-04-24
Thank you very much for your help SevenMachines.
The program now compiles.

However as I'm neither a hobbyist, student nor professional programmer, I am left [albeit pleasantly] bemused; because:

a) where/what is:  'lXext'  as distinct from:  'lxext' ?

b) if the compiler wasn't looking in or beneath   /usr/X11R6/lib
then where was it looking for  Xlib.h  &  XShm.h?
I've never had a   /usr/X11R6/include/   in my system:
   2.6.32-24-generic #39-Ubuntu SMP i686 GNU/Linux

c) I had both the wrong   Xlib.h  & the wrong  XShm.h  too (from TenDRA).
They appear to have altogether different content!
But surely it is especially bad practice to give a header file the same name as a pre-existing header file?
After all, one of each  Xlib.h  & each  XShm.h  must have have been written before the other  Xlib.h  &  XShm.h.

{ & do you think that 'they' will ever see fit to make lower case l  actually look like an 'elle' ?  ](*,) }

---

### Post by SevenMachines on 2011-04-25
(a) -lXext tells the compiler to link the executable using that library, in this case libXext. Note the format, whereas the actual library is
/usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
the name that is passed to the linker is the actual library name minus the 'lib' prefix and the suffix (.so.6.4.0). Since linux filenames, unlike dos, are case specific, 'Xext' and 'xext' are also completely different names.

(b) I dont think   /usr/X11R6/include/ is used by anything, it might have been in the past as i remember, but in this case it looks like you created it on compilation of those X libraries. 
The default search path for compiler includes is 
```
/usr/local/include
*libdir*/gcc/*target*/version/include  
/usr/*target*/include
/usr/include
```Searched top to bottom
see, [http://gcc.gnu.org/onlinedocs/cpp/Search-Path.html](http://gcc.gnu.org/onlinedocs/cpp/Search-Path.html) for more 

For example on my computer i get (along with a lot of other details about the compiler), 
```
$ touch test.c
$ gcc -v -c test.c 
.....
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/include
 /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
.....

```(c) Linux works on fundamentally different principles to something like windows, there are pluses and minuses. For example, if I have 10 programs that all use a library, libX for example then, as a generalisation,

* On windows these programs will all link to their own specific versions of libX, and they will all be distributed including it, and will run using that version. 

* Linux uses shared libraries, there is only one version of libX on the system, each of our 10 programs will load that library at runtime, they dont have their own versions.

On the one hand, if a program comes with its own version of libX then this helps to guarantee the platform it will be running on. On the downside, we now have 10 different of copies of libX on the system, eating up our hard drive.

Using shared libraries means that we save disk space since we have only one libX, but means that programs that use it must be built against a compatible enough version to use the system library, which may well be a different version on the hundreds of different linux distributions. 
This is one of the reasons closed source programs can often be a nightmare on linux, they are built against a version of a library on a few distributions at best, used on different versions and distributions they may not work against the included library versions on that system. With open source software the code can be built against whatever platform required, at any time, by anyone, making sure compatibility can be maintained.

The biggest reason the shared library way is the right way, at least in my opinion, is simply security. Think of this scenario...

* Libraries not shared
- Our 10 programs use 10 different versions of libX, included in their executables.   
- The developers of libX discover a horrible bug in their code that allows a hacker to break into your computer and steal everything, this happens *a lot*!
- The developers fix the bug.
- Some of our 10 programs update their versions of libX to fix the dangerous bug, some take a long time to do so leaving the user vulnerable, some of the programs are now unsupported by their companies or have gone out of business, they will *never* be fixed, the user is left completely vulnerable even if only one program doesnt fix the bug.

* Shared Libraries
- Our 10 programs use a systems one and only version of libX
- The developers of libX discover a horrible bug in their code that  allows a hacker to break into your computer and steal everything, this  happens *a lot*!
- The developers fix the bug.
- libX is updated on the system
- All 10 programs are instantly fixed, the user is protected. worst case scenario is that some of the 10 programs break and need to be updated by their developers to work again, but at least the dangerous security bug is no longer there.

This is why there is, at least in most cases, one version of the library and one version of the headers. You can install different versions to different places or with different names manually, in some cases especially in development this is exactly what you want to do, but its not something you want the system to do by design.

Well, thats all just my (possibly ill-informed) explanation/opinion!

p.s. Using the ubuntu font my 'little l' actually looks like a little l! theres a lot of fonts out there though :)

---

### Post by kliq on 2011-04-25
Well like you, I am using Ubuntu, too, but  the attached shows what it gives me.

Anyway, you mentioned:
...there is only one version of libX on the system, each of our 10 programs will load that library at runtime, they dont have their own versions.

but the (unsuccesful) TenDRA copys of the Xlib.h (& XShm.h) headers that I first had, were 'apt-got' from the same place as the (successful) libx11-dev copys.
So it seems that Windows' philosophy is being practiced right here in Ubuntu :icon_frown: !

---

### Post by SevenMachines on 2011-04-25
Sadly i'm on amd64 which doesnt seem to have a tendra compiler version to check out, but i dont really understand what you mean. as far as i can see there is no Xlib.h or XShm.h included with tendra, only the compilers standard libs.
[http://packages.ubuntu.com/natty/i386/tendra/filelist](http://packages.ubuntu.com/natty/i386/tendra/filelist)
You seem to be using gcc to compile in the first message, i'm not sure i see exactly where tendra is involved?

---

### Post by kliq on 2011-05-01
Visiting your link I found that  Xlib.h & XShm.h were listed there:

```
.
.
/usr/lib/TenDRA/lib/include/x5/lib.api/X11/Xlib.h
.
.
/usr/lib/TenDRA/lib/include/x5/ext.api/X11/extensions/XShm.h
.
.

```TenDRA became involved at the begining of my problem, before my first post & while I was proceeding on vague ideas.
I put them where I thought they perhaps ought to be and then used gcc to compile.

But my point is that there are 2 different Xlib.h & XShm.h and not just one of each.

---

