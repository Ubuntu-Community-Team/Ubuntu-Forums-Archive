---
title: "gbt+2 install problem"
date: 2005-06-18
forum: Packaging and Compiling Programs
---

### Post by BabyUbuntu on 2005-06-18
hello ubuntu

its my 2nd day, i tried to installed gtk+2 but i got problem ...

root@babyubuntu:/home/babyubuntu/Mydocument/gtk+-2.0.3 #./configure --prefix=/usr

---- compile process ---

checking for freetype-config... /usr/local/bin/freetype-config
checking for FT_New_Face in -lfreetype... yes
checking For sufficiently new FreeType (at least 2.0.1)... no
configure: error: pangoxft Pango backend found but did not find freetype libraries

root@babyubuntu:/home/babyubuntu/Mydocument/gtk+-2.0.3#

configure: error: pangoxft Pango backend found but did not find freetype libraries

<-- i thougt i have to install pangocft ... then i asked it to mr google and mr sourceforge... i got this file freetype-2.1.8.. than i tried to install it


root@babyubuntu:/home/babyubuntu/Mydocument/freetype-2.1.8 # ./configure --prefix=/usr/

FreeType build system -- automatic system detection

The following settings are used:

platform unix
compiler cc
configuration directory ./builds/unix
configuration rules ./builds/unix/unix.mk

If this does not correspond to your system or settings please remove the file
`config.mk' from this directory then read the INSTALL file for help.

Otherwise, simply type `make' again to build the library,
or `make refdoc' to build the API reference (the latter needs python).

make: Nothing to be done for `unix'.
root@babyubuntu:/home/babyubuntu/Mydocument/freetype-2.1.8 #

someone told me that i have to upgrade my freetype then i upgrade my freetype-2.1.8 --> freetype-2.1.10

Otherwise, simply type `make' again to build the library,
or `make refdoc' to build the API reference (the latter needs python). <-- basic this.. then i installed phyton..

root@babyubuntu:/home/babyubuntu/Mydocument/freetype-2.1.10 # make refdoc
---- process ---
root@babyubuntu:/home/babyubuntu/Mydocument/freetype-2.1.10 #make install 
-process---

i instaled debian package too for freetype 
root@cupid:/home/cupid/Mydocument # dpkg -i libttf2_1.4pre.20030402-1.1_i386.deb
Selecting previously deselected package libttf2.
(Reading database ... 74134 files and directories currently installed.)
Unpacking libttf2 (from libttf2_1.4pre.20030402-1.1_i386.deb) ...
Setting up libttf2 (1.4pre.20030402-1.1) ...

root@cupid:/home/cupid/Mydocument # 

its done... then i back at gtk+2..

root@babyubuntu:/home/babyubuntu/Mydocument/gtk+-2.0.3 #./configure --prefix=/usr

---- compile process ---

checking for freetype-config... /usr/local/bin/freetype-config
checking for FT_New_Face in -lfreetype... yes
checking For sufficiently new FreeType (at least 2.0.1)... no
configure: error: pangoxft Pango backend found but did not find freetype libraries


i asked mr google and sourceforge again how to install freetype-2.1.8 .. and they said same answer ..
./configure
make
make install

without problem like mine.. any solution for my problem , help pls.

thank u very much

---

### Post by minh on 2005-10-29
hello,
i'am having same pb, does anyone know about it?

---

### Post by ntlam on 2007-07-23
I also got this problem. any idea please.

---

### Post by kexin on 2010-09-01
I found it!
Should edit file configure:
add "#include <ft2build.h>" before "#include <freetype/freetype.h>"!

---

### Post by qywwm on 2011-01-05
make clean first

---

