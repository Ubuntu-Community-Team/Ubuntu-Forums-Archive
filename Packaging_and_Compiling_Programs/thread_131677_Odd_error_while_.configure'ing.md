---
title: "Odd error while ./configure'ing"
date: 2006-02-16
forum: Packaging and Compiling Programs
---

### Post by shibasu on 2006-02-16
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Now, this error has occured over several attemps at compiling various and not at all similiar applications. The same error has come up each time. I'll remind you i've added very little to my Ubuntu install (Fresh install) - So i'm not sure what it could be. 

\\:D/  - Added because it looked cute. 

Appreciate any help that you can lend me, if needed I can paste the relevent parts of the config.log as well.

---

### Post by orlox on 2006-02-16
Do you have the "build-essential" package installed?
if not, run:

sudo apt-get install build-essential

---

