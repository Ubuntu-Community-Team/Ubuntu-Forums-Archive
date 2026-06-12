---
title: "Building GMP"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by dplusplus on 2008-07-05
I was trying to install gcc, but i got this error:
get configure: error: Building GCC requires GMP 4.1+ and MPFR 2.3.0+.



So, then i tried to install gnu mp (gmp), and i got this error:
checking for suitable m4... configure: error: No usable m4 in $PATH or /usr/5bin (see config.log for reasons).

Any idea where am i going wrong? Thanks in advance.

- Dev

---

### Post by the_doc on 2008-07-05
> **dplusplus said:**
> I was trying to install gcc...

Easier to go via synaptic.

> **dplusplus said:**
> No usable m4 in $PATH or /usr/5bin (see config.log for reasons).

sudo apt-get install m4

---

### Post by nowshining on 2008-07-05
more than likely u'll need the -dev version of any libs it asks for. Sometimes u'll need to download a newer ver. than in synaptic. :) which means more compiling, etc..

by the way GCC is in the repos.

---

### Post by dplusplus on 2008-07-06
Thanks a lot guys, ok i have figured this out that i dont exactly need m4 for gcc installation.
I was actually trying to get simplescalar working to work with gcc.

Now I have gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2) installed.

So I Was trying to install simplescalar, so i did the following without any error:
tar xvfz simplesim-3v0d.tgz
make config-alpha
make clean

After that i did :
make sim-safe
this gave me error:
machine.h:224: error: array type has incomplete element type
Then i saw in one site, it was instructed:
&#9679; machine.h in simplesim folder - change line 224 from "extern enum md_opcode md_mask2op[];" to "extern enum md_opcode *md_mask2op;" 
&#9679; machine.c in simplesim folder - change line 78 from "enum md_opcode md_mask2op[MD_MAX_MASK+1];" to "enum md_opcode *md_mask2op;
I did the same and then compiled again, and then typed "make sim-safe" again and worked fine with lots of warnings though.

Ok somehow fine till now, and then typed:
./sim-safe ./tests-alpha/bin/test-math
Gave me error:
Segmentation fault (core dumped)

Going by the various forum talks, I can understand till now that it is trying to access some other memory segments, and I need to correct some
pointer addresses maybe. But still can't figure out what exactly am i supossed to do or make any other changes.

Help is kindly needed.

Regards and thanks 

- Dev

---

### Post by bumanie on 2008-07-06
For gcc installation > sudo apt-get install build-essentialBuild-essential is the gcc "C" compiler.

---

### Post by dplusplus on 2008-07-06
I m done with gcc installation, just cant move on with this simplescalar installation :(

---

### Post by nowshining on 2008-07-06
try

./configure

and if that doesn't error out,

make

sudo checkinstall -D make install

install Checkinstall first if u don't have it. :)

---

