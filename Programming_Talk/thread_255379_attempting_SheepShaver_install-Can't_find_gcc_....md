---
title: "attempting SheepShaver install-Can't find gcc ..."
date: 2006-09-11
forum: Programming Talk
---

### Post by jroryb on 2006-09-11
I'm new to Ubuntu and I'm trying to compile the SheepShaver Mac Emulator. I installed gcc via the Synaptic Package Manager. I also added /usr/lib/gcc to $PATH via

PATH=$PATH:/usr/lib/gcc
export PATH

I verified it is there via

echo $PATH

and /usr/lib/gcc is the last item

Yet when I execute ./autogen.sh I get a response that says:

no acceptable C compiler found in $PATH

AND I get 3 aclocal:configure.ac warnings:

macro 'AM_PATH_GTK_2_0' not found in library
macro 'AM_PATH_GTK' not found in library
macro 'AM_PATH_ESD' not found in library

Any and all help, pointers, advice, and wisdom will be appreciated.

---

### Post by ape on 2006-09-11
Looks like you're missing some development packages. 

Try installing libesd0-dev and libgtk2.0-dev to start with and then see what else is still missing when you try your compiling again.

---

### Post by kaamos on 2006-09-11
and make sure you have build-essential installed

---

### Post by jroryb on 2006-09-12
Thanks for the information, I got farther this time. I now get these errors:

Running aclocal: aclocal:configure.ac:267: warning: macro `AM_PATH_GTK' not found in library

checking for GTK+ - version >= 1.3.15... yes (version 2.8.20)
./configure: line 7413: syntax error near unexpected token `1.2.0,'
./configure: line 7413: `  AM_PATH_GTK(1.2.0,'

Any suggestions? Thanks for the help.

---

### Post by jroryb on 2006-09-12
I took a different approach; I downloaded the .rpm version and used alien to convert it -- and it installed; BUT

I am still getting an error concerning gtk:

SheepShaver: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Therefore, I need to install this, but the only place I can find it says it is contained in a GTK+ package (and a GTK+ package is already installed so I am confused?)

How can I install this (and which version) without killing my present install?

Thank You

---

### Post by jroryb on 2006-09-14
I found the solution and now have a running SheepShaver 2.3 Mac Emulator on Ubuntu 6.06. In summary (after trying to compile from src (although this would probably work now that I have the libgtk1.2 and libglib1.2 installed)

downloaded the sheepshaver .rpm distro
converted the .rpm to .deb using alien

--> at this point SheepShaver would not launch as it needed the libgtk1.2

then found this note on the forums:

[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

about expanding your sources.list

(this MAY not have been necessary for the next step, but it is what I did)

and found a note SOMEWHERE (didn't document) about using sudo apt-get and then ran:

sudo apt-get install libgtk1.2

which installed both of the libraries.

per the GTK+ site: "Some applications still require GTK+ 1.2, an older stable version of GTK+. You can have the runtime and development environments for both GTK+ 2.x and GTK+ 1.2 installed simultaneously on your computer."

There are still issues to resolve (CD access)... But some are I am sure due to my running ubuntu in parallels under OS X on this particular machine.

Thanks to all!

---

