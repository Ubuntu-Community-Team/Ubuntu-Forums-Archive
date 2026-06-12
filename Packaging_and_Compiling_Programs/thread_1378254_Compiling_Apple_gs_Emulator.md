---
title: "Compiling Apple //gs Emulator"
date: 2010-01-11
forum: Packaging and Compiling Programs
---

### Post by ..::| Dave89 |::.. on 2010-01-11
I want to run an Apple //gs emulator called Kegs ([http://kegs.sourceforge.net/](http://kegs.sourceforge.net/)), but it needs to be compiled, does compiling need programming skills, or anything like that?  I have none of that.  There is a compiling readme text file with KEGS but it's not Ubuntu specific.

TIA

---

### Post by SevenMachines on 2010-01-11
compiling doesnt need programming skills but you need to be happy using a command line. if you are, quickly looking at kegs it seems to be relatively easy to build. you'll need build-essential and at least xorg-dev installed from the repositories though, perhaps some more.
then, in the src/ directory of the kegs source run

$rm vars; ln -s vars_x86linux vars
$make

it should build successfully and leave you with a binary called xkegs

---

### Post by ..::| Dave89 |::.. on 2010-01-12
I'm not sure I'm doing this right, I posted the terminal contents here:

dave2389@dave2389-laptop:~$ cd /home/dave2389/kegs.0.91/src/
dave2389@dave2389-laptop:~/kegs.0.91/src$ $rm vars; ln -s vars_x86linux vars
vars: command not found
ln: creating symbolic link `vars': File exists
dave2389@dave2389-laptop:~/kegs.0.91/src$ $make

EDIT: I got it to compile.  I was right, I wasn't doing it properly the first time.

---

