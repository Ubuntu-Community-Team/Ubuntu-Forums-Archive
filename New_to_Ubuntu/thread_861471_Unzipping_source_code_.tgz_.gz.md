---
title: "Unzipping source code .tgz .gz"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by venture on 2008-07-16
I'm trying to get a program called namot off of sourceforge.
The filename on sourceforge says-  namot-2.2.0-pre4.tgz  
The file type says-  Source .gz
I download it and filename appears as-  namot-2.2.0-pre4.gz 
I extract into the same file and it comes up as a tar archive
I tried to extract again becuase it doesn't look like a folder/directory and ark recognizes it as a tar archive and fails to extract because the file is not a directory. 

I want to install this program, what is the next step?

---

### Post by crashcoredump on 2008-07-16
Have you tried ```
tar xvf <archivename> <filename>
``` in the cli?

Or is just possible to select it in the arch manager and choose *install?*

---

### Post by venture on 2008-07-16
No there is no binary it needs to be compiled from source.

The code returned from that command is 

[root@andLinux ~]# tar xvf namot-2.2.0-pre4 namot
tar: namot-2.2.0-pre4: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
[root@andLinux ~]# 

The extracted file looks like a little yellow box with a blue rectangle above and the bottom corner of the tile folded over

---

### Post by RomeReactor on 2008-07-16
Hi. Is [this]("http://sourceforge.net/project/showfiles.php?group_id=31437&package_id=23475&release_id=133548") the file? Make sure the file downloaded correctly; it's possible it didn't finish downloading (the file should be 1.1 MB).

---

### Post by venture on 2008-07-17
Yeah thats it and it downloaded all the way. Could you unzip it properly?

---

### Post by oldos2er on 2008-07-17
Instead if opening it with Ark, right-click on the file and click 'Extract Here.' Then open konsole in the directory it creates, and run ./configure

---

### Post by RomeReactor on 2008-07-17
> **venture said:**
> Yeah thats it and it downloaded all the way. Could you unzip it properly?

Yes, it unpacked a folder with the appropriate files. Try oldos2er's suggestion; have you re-downloaded the file, just to make sure the first download wasn't corrupted?

---

### Post by venture on 2008-07-17
I right click and extract here and I do get all of the files but they are inside an icon that looks like a box not a folder.
Here is the location

tar:/mnt/c/FileShare/namot-2.2.0-pre4/namot-2.2.0-pre4

What is that "tar:" in front? I thought it should have been extracted

Also I have it a folder inside of my C drive in windows (running andLinux) and I mounted the C drive so I can access all of my windows files while using linux. Is that a problem? To be on the safe side when compiling which directory would be better?

---

### Post by RomeReactor on 2008-07-17
TAR is an archive of files, without compression; TAR.GZ is a TAR archive compressed with GZIP. I'm unsure as to why Ark is having trouble unpacking it in one go. Now try extracting the contents of the TAR file, and see if you finally get the folder.

If this is still giving you trouble, open a Konsole and change directory to where the .TGZ archive is and run:
```
tar -xvzf namot-2.2.0-pre4.tgz
```

---

### Post by venture on 2008-07-18
Ok I figured out the issue. I moved the file into /floppy and after moving it namot came up as a directory. Extracting it with the code you posted worked perfectly. 

Now I just configured it (./configure) and there were no errors
But when I tried to compile it ( make ) and a ton of errors came up. 

The first errors came up with python
namot_wrap.c:13:20: error: Python.h: No such file or directory
namot_wrap.c:274: error: expected specifier-qualifier-list before 'PyObject'
namot_wrap.c:280: error: expected specifier-qualifier-list before 'PyObject_HEAD

The install file talks about python but how do you use LD_LIBRARY_PATH and PYTHONPATH

---

### Post by bumanie on 2008-07-18
Try > sudo apt-get install build-essential and then try again. It is a compiler - not sure whether it works with python, but I think it does.

---

### Post by venture on 2008-07-30
I have build-essential and it gets through configure but dies in make. 
Here is the code 
Does anyone see the problem?

[root@andLinux namot-2.2.0-pre4]# make
make  all-recursive
make[1]: Entering directory `/etc/namot-2.2.0-pre4'
Making all in src
make[2]: Entering directory `/etc/namot-2.2.0-pre4/src'
source='namot_wrap.c' object='_pynamot_la-namot_wrap.lo' libtool=yes \
        depfile='.deps/_pynamot_la-namot_wrap.Plo' tmpdepfile='.deps/_pynamot_l
a-namot_wrap.TPlo' \
        depmode=gcc3 /bin/sh ../depcomp \
        /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -
DLIB_HOME="\"/usr/local/share/namot\"" -DHELP_FILE_DIR="\"/usr/local/share/namo
t\""  -g -O2 -c -o _pynamot_la-namot_wrap.lo `test -f 'namot_wrap.c' || echo '.
/'`namot_wrap.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLIB_HOME=\"/usr/local/share/namot\" -DHELP_F
ILE_DIR=\"/usr/local/share/namot\" -g -O2 -c namot_wrap.c -MT _pynamot_la-namot
_wrap.lo -MD -MP -MF .deps/_pynamot_la-namot_wrap.TPlo  -fPIC -DPIC -o _pynamot
_la-namot_wrap.lo
namot_wrap.c:13:20: error: Python.h: No such file or directory
namot_wrap.c:274: error: expected specifier-qualifier-list before 'PyObject'
namot_wrap.c:280: error: expected specifier-qualifier-list before 'PyObject_HEA
D'
namot_wrap.c:284: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:291: error: expected declaration specifiers or '...' before 'FILE'
namot_wrap.c: In function 'swig_varlink_print':
namot_wrap.c:294: warning: incompatible implicit declaration of built-in functi
on 'fprintf'
namot_wrap.c:294: error: 'fp' undeclared (first use in this function)
namot_wrap.c:294: error: (Each undeclared identifier is reported only once
namot_wrap.c:294: error: for each function it appears in.)
namot_wrap.c:295: error: 'swig_varlinkobject' has no member named 'vars'
namot_wrap.c:295: error: 'swig_globalvar' has no member named 'next'
namot_wrap.c:297: error: 'swig_globalvar' has no member named 'next'
namot_wrap.c: At top level:
namot_wrap.c:303: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:317: error: expected declaration specifiers or '...' before 'PyObj
ect'
namot_wrap.c: In function 'swig_varlink_setattr':
namot_wrap.c:318: error: 'swig_varlinkobject' has no member named 'vars'
namot_wrap.c:321: error: 'swig_globalvar' has no member named 'set_attr'
namot_wrap.c:321: error: 'p' undeclared (first use in this function)
namot_wrap.c:323: error: 'swig_globalvar' has no member named 'next'
namot_wrap.c:325: error: 'PyExc_NameError' undeclared (first use in this functi
on)
namot_wrap.c: At top level:
namot_wrap.c:329: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e 'PyTypeObject'
namot_wrap.c:347: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:360: error: expected ')' before '*' token
namot_wrap.c:414: error: expected ')' before '*' token
namot_wrap.c:506: error: expected ')' before '*' token
namot_wrap.c:538: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:576: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:589: error: expected ')' before '*' token
namot_wrap.c:672: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:728: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:743: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:759: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:777: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:791: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:837: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:897: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:943: error: expected '=', ',', ';', 'asm' or '__attribute__' befor
e '*' token
namot_wrap.c:1003: error: expected '=', ',', ';', 'asm' or '__attribute__' befo
re '*' token
namot_wrap.c:1024: error: expected '=', ',', ';', 'asm' or '__attribute__' befo
re '*' token
namot_wrap.c:1070: error: expected '=', ',', ';', 'asm' or '__attribute__' befo
re '*' token
namot_wrap.c:1085: error: expected '=', ',', ';', 'asm' or '__attribute__' befo
re '*' token
namot_wrap.c:1131: error: expected '=', ',', ';', 'asm' or '__attribute__' befo
re '*' token
namot_wrap.c:1177: error: expected '=', ',', ';', 'asm' or '__attribute__' befo
re '*' token
namot_wrap.c:1223: error: expected '=', ',', ';', 'asm' or '__attribute__' befo
re '*' token
namot_wrap.c:1269: error: expected '=', ',', ';', 'asm' or '__attribute__' befo
re '*' token
namot_wrap.c:1315: error: expected '=', ',', ';', 'asm' or '__attribute__' befo
re '*' token
namot_wrap.c:1329: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1343: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1368: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1404: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1425: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1510: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1525: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1546: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1561: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1576: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1591: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1614: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1635: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1657: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1706: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1730: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re 'SwigMethods'
namot_wrap.c: In function 'init_pynamot':
namot_wrap.c:1796: error: expected '=', ',', ';', 'asm' or '__attribute__' befo                         re '*' token
namot_wrap.c:1796: error: 'SWIG_globals' undeclared (first use in this function                         )
namot_wrap.c:1798: error: 'PyObject' undeclared (first use in this function)
namot_wrap.c:1798: error: 'm' undeclared (first use in this function)
namot_wrap.c:1798: error: 'd' undeclared (first use in this function)
namot_wrap.c:1801: error: 'SwigMethods' undeclared (first use in this function)
make[2]: *** [_pynamot_la-namot_wrap.lo] Error 1
make[2]: Leaving directory `/etc/namot-2.2.0-pre4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/etc/namot-2.2.0-pre4'
make: *** [all] Error 2
[root@andLinux namot-2.2.0-pre4]#

---

### Post by RomeReactor on 2008-07-30
Have you installed **python-dev**?
```
sudo aptitude install python-dev
```

---

### Post by venture on 2008-07-31
No I hadn't
I downloaded it and make came up with new errors
Any ideas

In file included from /usr/include/zlib.h:34,
                 from /usr/include/png.h:383,
                 from graphics.c:35:
/usr/include/zconf.h:328: error: duplicate 'unsigned'
/usr/include/zconf.h:328: error: two or more data types in declaration specifiers
make[2]: *** [_pynamot_la-graphics.lo] Error 1
make[2]: Leaving directory `/etc/namot-2.2.0-pre4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/etc/namot-2.2.0-pre4'
make: *** [all] Error 2
[root@andLinux namot-2.2.0-pre4]#

---

### Post by jucas_lo on 2010-10-14
did you solve your problem?

because I'm having the same issue

---

### Post by CharlesA on 2010-10-14
This thread is old, so it would probably be better to create a new thread detailing all the errors and whatnot.

---

