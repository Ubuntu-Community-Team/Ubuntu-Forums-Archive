---
title: "OpenBUGS"
date: 2008-04-02
forum: Packaging and Compiling Programs
---

### Post by spamalot on 2008-04-02
hi all,

i'm trying to install OpenBUGS but run into a pb:

a) [http://web.maths.unsw.edu.au/~tduong/research/rlinbugs.html](http://web.maths.unsw.edu.au/~tduong/research/rlinbugs.html)

i'm following a), which basically says:
in .bashrc, add your version 
export LINBUGS_HOME="/c/tduong/home/bin/openbugs" 
export LINBUGS_TEMP="/c/tduong/home/temp"
create a file called linbugs containing the following commands
#!/bin/bash
export LD_ASSUME_KERNEL=2.4.1
cd $LINBUGS_HOME
if [ \! -e $LINBUGS_TEMP ] ; then
        mkdir $LINBUGS_TEMP
fi
if [ -e bugs.so ] ; then
        ./cbugs "$LINBUGS_HOME" "$LINBUGS_TEMP" "/bugs.so"
else
        ./cbugs "$LINBUGS_HOME" "$LINBUGS_TEMP" "/brugs.so"

cbugs does not come with the package, but the source is here
[http://www.math.helsinki.fi/openbugs/Manuals/Developer/CBugs.html](http://www.math.helsinki.fi/openbugs/Manuals/Developer/CBugs.html)

and i do
gcc -o cbugs CBugs.c -ldl 

Check that LinBugs is executing properly by typing in the command line whilst in the directory $LINBUGS_HOME

./linbugs

here's what i get:
./cbugs: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

---

### Post by spamalot on 2008-04-02
ps: alternatively there appears to be a precompiled version of cbugs here:

[http://www.gatsby.ucl.ac.uk/~iam23/compnotes/openbugs/cbugs](http://www.gatsby.ucl.ac.uk/~iam23/compnotes/openbugs/cbugs)

if i replace it with the one i generated from source and ./linbugs i get really uggly messages:
./cbugs: line 1: syntax error near unexpected token `('
./cbugs: line 1: `ELF&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@&#65533;4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4&#65533; &#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4&#65533;&#65533;&#65533;4&#65533;4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533; &#65533; &#65533;X&#65533;&#65533;t&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4&#65533;&#65533;4&#65533;4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;/lib/ld-linux.so.2&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;GNU&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;  &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                               &#65533;&#65533;&#65533;ï¿½ï¿½ï¿½
                                                                           ï¿½ï¿½ï¿½'
&#9226;&#9148;@&#9508;&#9225;&#9508;&#9532;&#9500;&#9508;:/&#9508;&#9149;&#9148;/&#9484;&#9146;&#9228;&#9618;&#9484;/O&#9147;&#9226;&#9532;BUGS$

---

### Post by spamalot on 2008-04-02
3rd attempt, based on 

[http://rcsg.rice.edu/rcsg/notes/linbugs.html](http://rcsg.rice.edu/rcsg/notes/linbugs.html)

 gcc -o cbugs CBugs.c -ldl -m32
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status

---

### Post by mc4man on 2008-04-02
Do you have something like lib32gcc1 ,  lib32stdc++6 , gcc-multilib available (don't have 64 bit somewhat of guess)

---

### Post by spamalot on 2008-04-02
Thanks!

Good guess i.e. gcc ... -m32 now works, but i'm still left with this:

$./linbugs
./cbugs: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

---

### Post by mc4man on 2008-04-02
libdl.so.2 is a link to libdl-2.6.1.so which is included in libc6, Is there a 32 bit ver. of libc6 your supposed to have?. ( for what your doing ) Note - messing around with libc6 can bork your install - I'd only do so if very sure

edit [http://packages.ubuntu.com/gutsy/libc6-dev-i386](http://packages.ubuntu.com/gutsy/libc6-dev-i386)

---

### Post by spamalot on 2008-04-03
Thanks for the advice and the warning. At this point I might turn to the other option which is to install Wine and run the windows version.

---

### Post by mc4man on 2008-04-03
I don't think there's any issue installing that lib (along with libc6 ), i just hate saying do something I can't try 1st.
As long as all your libc6 versions are the same you should be good
As in 2.6.1 - for gutsy

---

### Post by spamalot on 2008-04-04
already have this installed:
GNU C Library: 32bit shared libraries for AMD64

---

### Post by spamalot on 2008-04-05
i mean lib6-i386, with description:
GNU C Library: 32bit shared libraries for AMD64 
This package includes shared versions of the standard C
library and the standard math library, as well as many others.
This is the 32bit version of the library, meant for AMD64 systems.

---

### Post by DrakeGis on 2008-06-05
Did you were able to figure out how to make linbugs to run ?
I'm getting this errors after compiling linbugs

error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
mkdir: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
./cbugs: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

Any ideas ? I'm running Ubuntu Hardy on an AMD 86x64 laptop.

---

### Post by AceOfMasta on 2008-09-09
I was getting that same problem as the above post. I tried the following:

```
cp linbugs linbugs.bak

cat linbugs.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > linbugs
```

However, now I get the following errors:

```
failed to install signal
32
failed to install signal
33
 
****
* BlackBox
* trap #107
- HostFiles.Directory.Old  (pc=00002AF3, fp=BF8A1B84)
- StdLoader.ThisObjFile  (pc=0000031D, fp=BF8A21A0)
- StdLoader.ReadHeader  (pc=0000075F, fp=BF8A23C0)
- StdLoader.LoadMod  (pc=0000107B, fp=BF8A24D8)
- StdLoader.LoadMod  (pc=000011E0, fp=BF8A25F0)
- StdLoader.LoadMod  (pc=000011E0, fp=BF8A2708)
- StdLoader.Hook.ThisMod  (pc=00001355, fp=BF8A271C)
- Kernel.ThisMod  (pc=00001224, fp=BF8A2838)
- Init.Init  (pc=0000004B, fp=BF8A2850)
- Init.$$  (pc=0000000A, fp=BF8A2860)
- Kernel.InitModule  (pc=00001133, fp=BF8A286C)
- Kernel.ThisLoadedMod  (pc=000011AF, fp=BF8A2884)
****

```

---

