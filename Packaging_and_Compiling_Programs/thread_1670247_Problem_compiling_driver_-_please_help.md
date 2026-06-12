---
title: "Problem compiling driver - please help"
date: 2011-01-18
forum: Packaging and Compiling Programs
---

### Post by aerek on 2011-01-18
I am trying to compile a touchscreen driver.  This is the output after running 'make'

```
root@localhost:/lib/ts/plugins# make
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I../src    -DTSLIB_INTERNAL -fvisibility=hidden -DGCC_HASCLASSVISIBILITY -O2 -Wall -W -MT linear.lo -MD -MP -MF .deps/linear.Tpo -c -o linear.lo linear.c
../libtool: line 838: X--tag=CC: command not found
../libtool: line 871: libtool: ignoring unknown tag : command not found
../libtool: line 838: X--mode=compile: command not found
../libtool: line 1005: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 1006: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../libtool: line 1149: Xgcc: command not found
../libtool: line 1149: X-DHAVE_CONFIG_H: command not found
../libtool: line 1149: X-I.: command not found
../libtool: line 1149: X-I..: command not found
../libtool: line 1149: X-I../src: No such file or directory
../libtool: line 1149: X-DTSLIB_INTERNAL: command not found
../libtool: line 1149: X-fvisibility=hidden: command not found
../libtool: line 1149: X-DGCC_HASCLASSVISIBILITY: command not found
../libtool: line 1149: X-O2: command not found
../libtool: line 1149: X-Wall: command not found
../libtool: line 1149: X-W: command not found
../libtool: line 1149: X-MT: command not found
../libtool: line 1149: Xlinear.lo: command not found
../libtool: line 1149: X-MD: command not found
../libtool: line 1149: X-MP: command not found
../libtool: line 1149: X-MF: command not found
../libtool: line 1149: X.deps/linear.Tpo: No such file or directory
../libtool: line 1149: X-c: command not found
../libtool: line 1202: Xlinear.lo: command not found
../libtool: line 1207: libtool: compile: cannot determine name of library object from `': command not found
make: *** [linear.lo] Error 1

```

I have tried re-installing libtool but I still get the error.  Cany anyone help me figure out what is going on here?

---

### Post by Zoot7 on 2011-01-19
A google search of some of those errors is throwing up references to bugs, might I ask, what's the driver you're attempting to compile?

Nonetheless the following may be of interest to you:
```
mark-xps:/home/mark# apt-file search X-I
gclcvs-doc: /usr/share/doc/gclcvs-doc/gcl-si/Low-Level-X-Interface.html
python-plastex-doc: /usr/share/doc/python-plastex-doc/html/module-plasTeX-Imagers.html
texlive-fonts-extra: /usr/share/texmf-texlive/fonts/afm/public/brushscr/BrushScriptX-Italic.afm
texlive-fonts-extra: /usr/share/texmf-texlive/fonts/type1/public/brushscr/BrushScriptX-Italic.pfb
```

It's one of the few that apt-file actually finds something for, mind you I'm on Debian, no doubt the Ubuntu repos are quite different.

---

### Post by aerek on 2011-01-22
The driver is for a cypress-i2c capacitive touchscreen running on an ARM based Ubuntu Maverick uSD card.  I also google searched and came up with the error being either bugs or referencing older versions of libtool (1.5 I believe).

---

