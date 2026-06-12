---
title: "need help with gcc"
date: 2007-07-01
forum: Programming Talk
---

### Post by cansport on 2007-07-01
I'm sure this one is a simple fix, probably related to the environment settings but it is driving me nuts - I noticed I am not the only user who has posted about the complexity of getting a C compiler to work under Linux...

I've recently installed Ubuntu and thought I would get back to programming with C, something I haven't done in a long time. The problem I have is that I cannot use any of the higher math functions in <math.h>. 

For example, when compiling the following bit of code:

[COLOR="Blue"][I]#include <math.h>
#include <stdio.h>

int main() {
   
	double d, d2;

	d = 1.4579;
	d2 = sqrt(1.4579);
	printf("%3.1f\n", d2);
}[/I][/COLOR]

It will compile and execute with no errors or warnings, but when I try something like :

[COLOR="Blue"][I]#include <math.h>
#include <stdio.h>

int main() {
   
	double d, d2;

	d = 1.4579;
	d2 = sqrt(d);
	printf("%3.1f\n", d2);
}[/I][/COLOR]
  
I get the following error associated with the linker (I think):
[COLOR="Red"][I]/tmp/ccuh2QFO.o: In function `main':
test.c: (.text+0x3c): undefined reference to `sqrt'
collect2: ld returned 1 exit status
[/I][/COLOR]

It does not matter which of the functions within <math.h> I try, I get the same error. 

I am using Ubuntu 7.04 on a Dell Inspiron 1501 with AMD Turion 64 x2 processor. A dump of gcc results in the following:

[COLOR="Blue"][I]gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
[/I][/COLOR]

I have searched for similar topics on this board and others, but have not found anything which is why I am thinking it might be a simple fix. With information gleaned from some of the posts, I have found and downloaded the *-dev libraries for the AMD64 release, but still no luck. Any insight would be most helpful...

---

### Post by moma on 2007-07-01
It compiles your program without errors, BUT the linker ([COLOR="Red"]ld[/COLOR]) fails because you do not link it to the math library "lib**m**.so" (where the actual math functions reside).  

Use the -l argument and the library name "m" to link your program.

You can do it in 2 steps:

First, compile the code (but do not link to external libraries). This produces pure object code (.o) but's not executable.  (study: ELF format).
$[COLOR="SeaGreen"] gcc -c yourcode.c  -o yourcode.o[/COLOR]

Link the program by putting together all object files (*.o) and external libraries (*.so).  The result is an executable program.  (study: ELF format).  
Gcc calls the "ld" linker module to do the job.

$ [COLOR="SeaGreen"]gcc yourcode.o  -lm  -o yourcode[/COLOR]

Run it 
$ [COLOR="SeaGreen"]./yourcode[/COLOR]
---

Or do it all (compile + link) on one line 
$ [COLOR="SeaGreen"] gcc yourcode.c -lm -o yourcode[/COLOR]
---

Notice:  
1) The /usr/include/math.h file includes signatures (prototypes) of all math functions,  but the actual code resides in the lib**m**.so lib. That's why your code must link to it.
--
2) Dynamic vs. Static lib:
Library names with ending [COLOR="Magenta"].so[/COLOR] (such as lib**m**.so) are called dynamic libraries. These are equivalent to Microsoft Windows' DLL.  Dynamic means that you link to library at runtime (when you start a program). The size of executable is therefore small but the required external libraries _must exist_ in the system when you install and run the program.  

!  Linux creates a cache over dynamic libraries (*.so) by running the "ldconfig" command. This cache makes runtime loading and linking very quick. 
See /etc/ld.so.conf file. Run also "sudo ldconfig -vv"  and "man ldconfig".

Library names with ending [COLOR="Magenta"].a[/COLOR] (such as lib**m**.a) are called static libraries. Static means that the code from library is baked into the executable at compile time. This makes the size of executable notably bigger but the executable is self-contained, it does not require external libraries at installation or when you start the program. It has everything within.

An example:  I often download the statically linked [Opera browser]("http://www.opera.com/download/?platform=linux")  (select: "Other/Static DEB" from the list) because it always works. It's bigger than the ordinary Linux-package but there's no need to struggle with external dependencies. 

So both lib types have both pros + cons.
---

[COLOR="Red"]??[/COLOR] But how do you create a statically linked executable (eg. of your sample code) [COLOR="Red"]??[/COLOR]

PS. Interested in a good development IDE (integrated development environment)? 
Take a [look at Code::Blocks IDE...]("http://ubuntuforums.org/showthread.php?p=2816470#post2816470")

---

### Post by Ragazzo on 2007-07-01
Compile it with the **-lm** flag when you need the math library. 

** d2 = sqrt(1.4579);** worked probably because the compiler calculated the result so no function call was needed.

---

### Post by cansport on 2007-07-02
Thanks, just what i needed. I thought it was simply a matter of pointing the linker in the right direction, but with the myriad of libraries that are installed, which one? 

Another question then - is there a document somewhere that lists the library to link to for a given function call? I mean, there are lots out there that give the include file. Guess I need to do some more research.

---

### Post by moma on 2007-07-02
Re-hello,

To find a library name, 
I usually engage some search functions on the command line.

A sample:  What library provides function "gp_camera_folder_list_files" ?

$ [COLOR="SeaGreen"]find /usr/lib -type f -name "lib*" -exec strings -f  {} \; | grep gp_camera_folder_list_files[/COLOR]

You may need to repeat this search for /lib and /usr/local/lib directories too.

The "strings" command reads any binary file (object file or object file's data sections) and returns any readable ascii text it find there. 

The "find" command is very powerful tool.  You ought learn to use it.
---

This manual 
[http://www.faqs.org/docs/Linux-HOWTO/Program-Library-HOWTO.html#AEN70](http://www.faqs.org/docs/Linux-HOWTO/Program-Library-HOWTO.html#AEN70)
mensions an example of "nm" command.  The example in the manual will not work in Linux because the argument list (number of files) is too large for it.  Xargs is the command to handle very large argument lists.

I think this script is better.
[http://www.futuredesktop.org/tmp/findlib.sh](http://www.futuredesktop.org/tmp/findlib.sh)

Eg.
$ [COLOR="SeaGreen"]sh findlib.sh gp_camera_folder_list_files[/COLOR]
------------

Unfortunately I do not know any documentation of match between include files and library names.
------------

Notice:  readelf, nm and objdump commands reveal various info about symbols in executables and object files.  Eg. try 
$ readelf -sW  yourcode.o 
$ readelf -sW  yourcode 

$  readelf -sW /lib/libpthread.so.0
---
$ objdump -x  yourcode.o
------

For more information, study 
$ man readelf
$ man objdump 
etc.
------

[COLOR="Red"]Let us not forget the manual pages. [/COLOR]
[http://en.wikipedia.org/wiki/Manual_page_(Unix)]("http://en.wikipedia.org/wiki/Manual_page_(Unix)")

What manual page packages does Ubuntu offer?
$ [COLOR="SeaGreen"]apt-cache search manpages [/COLOR]
...
**manpages-dev** - Manual pages about using GNU/Linux for development
manpages-de-dev - German development manpages
manpages-fr-extra - French version of the manual
**manpages-posix** - Manual pages about using POSIX system
**manpages-posix-dev **- Manual pages about using a POSIX system for development

Let's install manpage*dev packages (consider also manpages-posix package)
$ [COLOR="SeaGreen"]sudo apt-get install manpages-dev manpages-posix-dev [/COLOR]

Note: What manpage sections ( 1 - 8 ) does the package cover?
$ [COLOR="YellowGreen"]apt-cache show manpages-posix-dev[/COLOR]

Test it:
Now try to find manual page for "printf" and "sqrt" commands
$ [COLOR="SeaGreen"]man printf[/COLOR]

Search especially among C library functions (man page section 3)
$ [COLOR="SeaGreen"]man 3  printf   [/COLOR]

$ [COLOR="SeaGreen"]man sqrt [/COLOR]
$ [COLOR="SeaGreen"]man pthread_create [/COLOR]
$ [COLOR="SeaGreen"]man 7 pthreads[/COLOR]

$ [COLOR="SeaGreen"]**whatis pthread_create**[/COLOR]


etc...

---

### Post by chrisN_uk on 2007-07-02
I have a similar problem. I'm trying to use a module called g2 with this code:

```
#include <g2.h>
#include <g2_PS.h>



main()
{
    int id;
    id = g2_open_PS("rect.ps", g2_A4, g2_PS_land); 
    g2_rectangle(id, 20, 20, 150, 150); 
    g2_close(id);
}

```

and i get 

```
chris@chris:/home/coding/cpp$ gcc -lm -o g2code g2code.cpp
g2code.cpp:12:2: warning: no newline at end of file
/tmp/ccYreINK.o: In function `main':
g2code.cpp:(.text+0x29): undefined reference to `g2_open_PS'
g2code.cpp:(.text+0x5f): undefined reference to `g2_rectangle'
g2code.cpp:(.text+0x6a): undefined reference to `g2_close'
/tmp/ccYreINK.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

I'm sure I've installed everything correctly....

---

### Post by moma on 2007-07-02
Hello hello,

"Cansport" may want to continue his own debate.
But hei, here we go.

First, you may need to rename your code to **g2code.c**.  
**gcc** is by default a C compiler that processes .h and .c files. 
And **g++** is a C++ compiler that processes .h, cpp and .cxx files.

The error "`__gxx_personality_v0'" in your listing is caused by wrong file ending (.c  vs  .cpp and the compiler).

So do
$ [COLOR="SeaGreen"] gcc -static  -g -O2   g2code.c -lg2   -lm -lX11 -lXext  -o g2code[/COLOR]

or compile your .cpp file using gcc and link to **libstdc++.so** library. Like this
$ [COLOR="SeaGreen"]gcc g2code.cpp  -lg2   -lm -lX11 -lXext **-lstdc++ ** -o g2code[/COLOR]

Of course you can drop all the extra stuff:  -g -O2   -lXext etc.. (you may need them later when your code evolves)
And I think gcc adds "-static" automatically because the only g2 library it finds is the static libg2.**a**.

$ [COLOR="SeaGreen"]**gcc** g2code.cpp  -lg2   -lm  **-lstdc++**  -o g2code[/COLOR]
is equivalent to:
$ [COLOR="SeaGreen"]**g++** g2code.cpp  -lg2   -lm  -o g2code[/COLOR]

or just when compiling a .c file
$ [COLOR="SeaGreen"]gcc g2code.c  -lg2   -lm  -o g2code[/COLOR]

Good habit thou is to include -Wall that gives warnings of many important anomalies in the code.
$ [COLOR="SeaGreen"]gcc -Wall g2code.c  -lg2   -lm  -o g2code[/COLOR]

If the above did not help, then 
--------------------------------------------------------------
**1)** You have installed  g2 with these commands (in the g2's source code folder)
$ [COLOR="SeaGreen"]./configure [/COLOR]
$ [COLOR="SeaGreen"]make depend[/COLOR]
$ [COLOR="SeaGreen"]make[/COLOR]
$ [COLOR="SeaGreen"]sudo make install [/COLOR]

**2) **Now, compile the examples. The samples are pretty complete so if they compile, anything will compile.
Go to the "demo" directory.
$ [COLOR="SeaGreen"]cd  g2-0.72[/COLOR]
$ [COLOR="SeaGreen"]cd  demo [/COLOR]

Compile the demos.
$ [COLOR="SeaGreen"]make [/COLOR]

Test a few of them.
$ ls -l 
$ [COLOR="SeaGreen"]./g2_test[/COLOR]

$ [COLOR="SeaGreen"]./g2_splines_demo[/COLOR]
--------------------------------------

**3)** Next, let's learn how those examples were compiled and linked.

Copy your source code to the **demo** directory. 
I assume here that the name of your code is "**test1.c**"  (and executable name is: **test1**)

In the demo directory, 
edit the demo's **Makefile** and add your project (test1.c) to it. It's very easy to do so.
$  [COLOR="SeaGreen"]gedit Makefile [/COLOR]

I have attached an example of the Makefile.  
Open it, search for "test1" and learn of it.  Edit your demo folder's Makefile accordingly. 
There are changes or additions in 3 - 4  places.

**4)** Save your Makefile. 
Compile + link your project. In the demo directory, issue:
$ [COLOR="SeaGreen"]make [/COLOR]
(As you see, it compiles the changed files only)

Run your code
$ [COLOR="SeaGreen"]./test1[/COLOR]
--------------------------------------------------------------

Notice following details:
The g2's installation puts include files into  /usr/local/include
$  ls -l /usr/local/include/g2*

It puts a static library to /usr/local/lib 
$ ls -l /usr/local/lib/*g2*
------------------------------------------------

g2 produces drawings or documents in postscript and other formats. The "display" command is quite handy way to show them. Eg
$ [COLOR="SeaGreen"]display g2_splines_demo.ps[/COLOR]
Display is part of the  "**imagemagick**" package in Ubuntu. Install it.
------------------------------------------------

[COLOR="Magenta"]Related package: [http://www.ferzkopp.net/joomla/content/view/19/14/]("http://www.ferzkopp.net/joomla/content/view/19/14/")[/COLOR]
Search for 
$  [COLOR="SeaGreen"]apt-cache search sdl | grep gfx[/COLOR]
libsdl-gfx1.2-4 - drawing and graphical effects extension for SDL
libsdl-gfx1.2-dev - development files for SDL_gfx

Unfortunately neither Edgy or Feisty have the latest version of SDL_gfx.
Bug-report sent: [https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/124030]("https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/124030")

---

### Post by chrisN_uk on 2007-07-02
Thanks, thats a huge help!

---

### Post by eccarvalho on 2009-10-24
Hello!
 
I'm trying to use library g2 and it is being impossible to use the function g2_open_gd in file g2_gd.h
 
I've red carefully the previous post and I noticed that in the demo make file all the example files related with GD and X11 are commented, so they are never compiled nor linked. I tried uncomment one of them (the simple_gd.c) and it came with the same error has with my own test - 22: undefined reference to `g2_open_gd' -.

I have also noticed that after installing the g2 library the files .h related with this "features" (GD and X11: g2_gd.h and g2_X11.h) are not copied to the default include directory as the others. They remain in the original directory of the g2 library code.
 
What can I do to use this open function? I have already installed gd and even zlib.
 
 
If anyone can help I would be very pleased!
 
Thank you
 
Elsa

---

### Post by MadCow108 on 2009-10-24
how have you installed the library?
if installed per package manager
```

sudo apt-get install libg20 libg2-dev

```
the files are in /usr/include /usr/lib the default ubuntu patchs, so you can compile it like this:
```

gcc -lg2 file.c

```

if not then check where it was installed and adapt the -I and -L flags of gcc to mirror the location of the files
e.g.
```

gcc -I/usr/local/include -L/usr/local/lib -lg2 file.c

```
this searches for headers in /usr/local/include and in /usr/local/lib for the library libg2.[somelibrary extension]


installation over packet manager is recommended in ubuntu

---

