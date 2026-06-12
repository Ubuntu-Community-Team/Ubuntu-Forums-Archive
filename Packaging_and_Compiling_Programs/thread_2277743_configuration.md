---
title: "configuration"
date: 2015-05-11
forum: Packaging and Compiling Programs
---

### Post by SEBASTIAN_JOY on 2015-05-11
Iam trying to configure CESM software.I downloaded the cesm working copy and create a a new case in my home dir using command ./create_newcase -case ~/mycase.01 -res f19_g16 -compset B_1850 -mach bluefire.when I configure the case on the newly created dir mycase.01,it shows 'Generating run script 
env: /home/madhuv/ccsm4_working_copy/scripts/ccsm_utils/Machines/mkbatch.bluefire: No such file or directory.configure error: configure generate_batch error.'
so Iam unable to follow the further commands.pls help me.

---

### Post by dino99 on 2015-05-11
you probably have forgotten to set the downloaded file executable  (sudo chown +x theCESMfile) (then redo the installation)

---

### Post by SEBASTIAN_JOY on 2015-05-15
Iam trying to install the libxml2 library.during installing this error occures.
make[4]: Entering directory `/home/madhuv/y/libxml2-2.9.2/python'
  CC     libxml.lo
libxml.c:14:20: fatal error: Python.h: No such file or directory
 #include <Python.h>
                    ^
compilation terminated.
make[4]: *** [libxml.lo] Error 1
make[4]: Leaving directory `/home/madhuv/y/libxml2-2.9.2/python'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/madhuv/y/libxml2-2.9.2/python'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/madhuv/y/libxml2-2.9.2/python'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/madhuv/y/libxml2-2.9.2'
make: *** [all] Error 2.
please help me.

---

### Post by SEBASTIAN_JOY on 2015-05-15
[COLOR=#000000]Iam trying to install the libxml2 library.during installing this error occures.[/COLOR]
[COLOR=#000000]make[4]: Entering directory `/home/madhuv/y/libxml2-2.9.2/python'[/COLOR]
[COLOR=#000000]CC libxml.lo[/COLOR]
[COLOR=#000000]libxml.c:14:20: fatal error: Python.h: No such file or directory[/COLOR]
[COLOR=#000000]#include <Python.h>[/COLOR]
[COLOR=#000000]^[/COLOR]
[COLOR=#000000]compilation terminated.[/COLOR]
[COLOR=#000000]make[4]: *** [libxml.lo] Error 1[/COLOR]
[COLOR=#000000]make[4]: Leaving directory `/home/madhuv/y/libxml2-2.9.2/python'[/COLOR]
[COLOR=#000000]make[3]: *** [all-recursive] Error 1[/COLOR]
[COLOR=#000000]make[3]: Leaving directory `/home/madhuv/y/libxml2-2.9.2/python'[/COLOR]
[COLOR=#000000]make[2]: *** [all] Error 2[/COLOR]
[COLOR=#000000]make[2]: Leaving directory `/home/madhuv/y/libxml2-2.9.2/python'[/COLOR]
[COLOR=#000000]make[1]: *** [all-recursive] Error 1[/COLOR]
[COLOR=#000000]make[1]: Leaving directory `/home/madhuv/y/libxml2-2.9.2'[/COLOR]
[COLOR=#000000]make: *** [all] Error 2.[/COLOR]
[COLOR=#000000]please help me.[/COLOR]

---

### Post by buzzingrobot on 2015-05-15
libxml2 is a common package installable from the Ubuntu repositories (sudo apt-get install libxml2) and, I believe, part of a default install.  Is there a particular reason you are building it from source.?

---

### Post by dino99 on 2015-05-15
Please explain what you are doing, and how. Tell us the source of that library you try to install.
Note that libxml2 is already installed on ubuntu, as it is a dependency of many other packages.

---

### Post by oldos2er on 2015-05-15
Moved to Packaging & Compiling Programs.

Have you installed python-dev? What version of Ubuntu are you running?

Edit: Threads merged. Please don't create more than one thread for the same or similar questions.

---

