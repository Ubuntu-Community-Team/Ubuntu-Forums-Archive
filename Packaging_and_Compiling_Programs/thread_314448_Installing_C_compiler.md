---
title: "Installing C compiler"
date: 2006-12-07
forum: Packaging and Compiling Programs
---

### Post by cweagle on 2006-12-07
I’m completely new to Linux, and I’m trying to install a C Compiler.  For now I’m going off a boot disk.  I’ve downloaded several c compiler packages such as TCC, GCC, & Tendra, but when I open them none of the executables want to work.  I also am having a hard time recognizing the items in the package.  Is there suppose to be executables for Linux programs that installs the programs when you click on the icon?  It almost looks like you have to assemble the compiler from several smaller pieces of software.](*,)

---

### Post by endersshadow on 2006-12-07
Well, first of all, welcome to Linux!

In order to start building programs, you're going to need a metapackage called "build-essential."  A metapackage is a package in the repositories that is an empty package, but depends on a bunch of packages, so it makes downloading a group of software much easier (such as programming tools).

You see, how we install programs (especially common ones) in Ubuntu is via Synaptic Package Manager (System > Administration > Synaptic Package Manager).  Get out [this guide](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Repositories) on adding repositories.  Generally, if it's not in the repos, you download a .tar.bz2 or .tar.gz, which is the source code.  You can then compile that by untarring it (right click on it and hit "Extract"), and then doing the ./configure && make && make install (see [here](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_compile_.deb_files_from_source)).

Anyway, let's get you started writing C:

First, open up a terminal (Applications > Accessories > Terminal).

Next, type in:

```
gedit hello_world.c &
```

A blank text editor will pop up.  Just put in this code (for learning purposes...I know you know C):

```
#include <stdio.h>

int main (int argc, char *argv[])
{
     printf("Hello World!\n");
     return 0;
}
```

Just hit the save icon, and then switch back to the terminal.

In the terminal, type:

```
gcc -o hello_world hello_world.c
./hello_world
```

What this does is it tells gcc to compile hello_world.c and output it to a file named hello_world.  If you'd like to see all of the options of gcc, simply type "man gcc" (w/o quotes) in the terminal, and use the arrows to scroll.

The second command tells the computer to execute hello_world that exists in the present working directory.

Have fun!

---

### Post by seahay on 2006-12-12
Following this thread with interest.

New to Linux/Ubuntu and programing.

Downloaded and installed gcc and associated files with the Synaptic Package Manager.

Followed your examples above exactly( copy and paste ;)  ) and received this message:

hello_world.c:1:19: error: stdio.h: No such file or directory
hello_world.c: In function ‘main’:
hello_world.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

I assumed the "error: stdio.h: No such file or directory" meant I didn't have C Standard Library on my computer. I searched for glibc at Synaptic, but could only find documentation for glibc - but I did find dietlibc and downloaded and installed, but alas the same error message.

Am I on the right track? Or completely lost?

---

### Post by po0f on 2006-12-12
seahay,

Go ahead and install [build-essential](http://packages.ubuntu.com/edgy/devel/build-essential), but the specific package you need is [libc6-dev](http://packages.ubuntu.com/edgy/libdevel/libc6-dev).  Oh yeah, [manpages-dev](http://packages.ubuntu.com/edgy/doc/manpages-dev) is a must as well.  :)

---

### Post by seahay on 2006-12-12
Sort of an oops here, but looking through the 'Installed' packages with Synaptic I came across libglib2.0-0 - "The GLib library of C routines" so I guess I didn't need dietlibc. DoH!

poOf - Downloaded 'libc6-dev_2.4-1ubuntu12_i386.deb on Intel x86 machines' successfuly, but received this error while opening(installing?):

Error: Dependency is not satisfiable: libc6


Is that a fatal install error? 

Hate to be a pain. :???:

---

### Post by seahay on 2006-12-12
Okies - downloaded ''libc6-dev_2.3.6-1ubuntu20' instead - as I am running Dapper and found this in the Dapper section of 'packages'.

Got an error regarding a conflict with libc6 - probably from the previous attempt, but it did say it was installed this time and, Lo and Behold, the endersshadow test compile worked perfectly. Huzzah!

Thanks for the help po0f - a major hurdle seems to be behind me and now I can dig into C programming with compiler in hand.

Why? I don't know.

Thanks again,
   seahay

---

### Post by Wybiral on 2006-12-15
C and C++ are two wonderful languages, and linux is a good place to develop with each of them. Best of luck!

---

### Post by Badge_x on 2009-01-05
This post helped me a lot, thanks guys :)

---

