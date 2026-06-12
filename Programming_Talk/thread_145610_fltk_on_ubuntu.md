---
title: "fltk on ubuntu"
date: 2006-03-16
forum: Programming Talk
---

### Post by bela on 2006-03-16
Hi,
I ve just install the ubuntu last release,
on my sarge debian, i can  install without problem  ( from the source) the fltk  (  graphical interface for C++) it needs dev  and lib X11, open gl. On sarge it was enough to install libx11-dev and opengl, ;;; to compile the fltk from the source.
but not on ubuntu , the configure doesn't find anywhere libx11 ( I installed a lot of other libraries libxft, ...,  ) while it exist.

always it gives:

checking for X... no
configure: error: Configure could not find required X11 libraries
./configure: line 8268: exit: aborting.: numeric argument required
./configure: line 8268: exit: aborting.: numeric argument required
root@belaOffice:/usr/local/fltk-1.1.6#


the fltk ( .deb ) is installed normally but not from the source.
has anyone an idea.
thanks for answer
bela

---

### Post by EsD on 2006-10-16
I am having a same problem as well and dont know how to solve it.

I am using ubuntu 6.06 GNOME currently.
I think, I've got everything required to installed the fltk 1.1.6. or fltk 1.1.7
like:
gcc 3.4.6 (stable)
libxft1 6.8.2-1
libx11-6
libx11-dev
fluid 1.1.7-1
libfltk1.1
libfltk1.1-dev

but I still can't install this fltk :( 
maybe problem with my CC
I don't really know how to Set the CC vble

I typed this "$export CC=gcc" on my terminal (without " ) it show error 
command not found even when I put sudo before $ sign.

no clue at all :-? 

can any senior or expert help this newby?  :mrgreen: 
thx

---

### Post by po0f on 2006-10-16
EsD,

Try installing the [xorg-dev](http://packages.ubuntu.com/dapper/x11/xorg-dev) meta-package.  The list of packages it installs is on that page.

---

### Post by EsD on 2006-10-16
cool...:D  it works:mrgreen: 
thanks alot po0f ;) 
I just need to go to synaptic package manager and type xorg-dev on search then apply them.:-D 

I used fltk 1.1.6 that I got from this following site
[http://www.fltk.org/software.php?VERSION=1.1.x-r5520&FILE=fltk/1.1.6/fltk-1.1.6-source.tar.bz2](http://www.fltk.org/software.php?VERSION=1.1.x-r5520&FILE=fltk/1.1.6/fltk-1.1.6-source.tar.bz2)

type : tar -xjvf fltk-1.1.6-source.tar.bz2     to extract them

then cd fltk-1.1.6/
after that type sudo ./configure
then make
then sudo make install

after the installation successful
type fluid & to run the program ;) 

hope this information help other newby like me
:-D 

thanks again po0f

---

### Post by Ravenna on 2006-12-01
I'm trying to install fltk-1.1.7 on drake.  The config command goes through okay, (I'd seen the above messages and fixed that problem).  But when I type "sudo make install" I get an error that says:

rm: cannot remove '/usr/local/bin/fltk-config': is a directory
make: *** [install] Error 1

Any help would be appreciated, if anyone is still paying attention to this thread, that is.  ;)

---

### Post by po0f on 2006-12-01
Ravenna,

Dapper's [FLTK](http://packages.ubuntu.com/dapper/libs/libfltk1.1) is already 1.1.7.  Any special reason you are compiling it?

As for your original problem, try deleting the directory it's complaining about, and re-running `sudo make install`:
```
[FONT="Courier New"]$ sudo rm -rf /usr/local/bin/fltk-config
$ sudo make install[/FONT]
```
If you run into the same error, post the "install" rule from the Makefile, if you would.

---

### Post by sacredfaith on 2010-02-05
po0f, 

Thank you so much! After installing xorg-dev...everything installed pretty smoothly.

Kind Regards,

-sf

---

### Post by madtom1999 on 2010-09-20
I'm using fltk from the Ubuntu repository but FLUID wont work:
Could not launch 'FLUID' 
Failed to execute child process "cd" (No such file or directory)


(64 bit 10.04)

---

### Post by juancarlospaco on 2010-09-20
Too bad that program dont generate Python code  :D

---

### Post by madtom1999 on 2010-09-21
SOLVED: Could not launch 'FLUID'
Failed to execute child process "cd" (No such file or directory)
I got this on 32 bit kubuntu 32 and 64 bit ubuntu!

It seems the menu item the package install is bad
I checked in synaptic and it should point to /usr/bin/fluid

---

### Post by 2009Prius on 2010-10-05
> **madtom1999 said:**
> SOLVED: Could not launch 'FLUID'
Failed to execute child process "cd" (No such file or directory)
I got this on 32 bit kubuntu 32 and 64 bit ubuntu!

It seems the menu item the package install is bad
I checked in synaptic and it should point to /usr/bin/fluid

Thanks that helped! :)

---

### Post by darius007 on 2011-09-02
I am trying to install fltk-2.0.x-alpha-r8800 on Ubuntu and it seems I am missing GLUT. 


the make is failing at glpuzzle.cxx:

Linking glpuzzle...
glpuzzle.o: In function `Reshape(int, int)':
glpuzzle.cxx:(.text+0x881): undefined reference to `glViewport'
glpuzzle.o: In function `computeCoords(int, int, int, float*, float*)':
glpuzzle.cxx:(.text+0x1081): undefined reference to `glGetFloatv'
glpuzzle.cxx:(.text+0x108e): undefined reference to `glGetFloatv'
glpuzzle.o: In function `reset()':
glpuzzle.cxx:(.text+0x130f): undefined reference to `glutChangeToMenuEntry(int, char const*, int)'
...........


I have freeglut3, glutg3, nvidia-glx-173, libgl1-mesa-glx, libglu1-mesa, libglut3 installed.

Any help would be greatly appreciated.

Cheers,
Darius

---

