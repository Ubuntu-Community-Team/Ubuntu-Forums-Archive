---
title: "Kylix 3 on new Linux Distribution"
date: 2010-02-10
forum: Programming Talk
---

### Post by petetheking on 2010-02-10
Hello guys,

I want and need Kylix 3 to run on Ubuntu 9.10 (newest Ubuntu). Installation was no problem, but I can't run it.

I have read nearly all forums in the web and it seems no problem with Suse 10.0, but I need it for Ubuntu 9.10!

Please help me guys!! Give me a step by step tutorial!

PLEASE!!!

Greets Peter

---

### Post by Zugzwang on 2010-02-10
First step: Describe why you cannot run Kylix. 

Give details like error messages you get, etc. Try starting Kylix from the command line and copy&paste the error messages here.

---

### Post by petetheking on 2010-02-10
king@ubuntu:~/kylix3/bin$ ./startbcb
/home/king/kylix3/bin/bcblin: relocation error: /home/king/kylix3/bin/libwine.borland.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
king@ubuntu:~/kylix3/bin$ export LD_ASSUME_KERNEL=2.4.1
king@ubuntu:~/kylix3/bin$ ./startbcb
/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
king@ubuntu:~/kylix3/bin$ ./startbcb
/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
king@ubuntu:~/kylix3/bin$ ls
ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
king@ubuntu:~/kylix3/bin$

Thx! 

Do you speak german? --> Zugzwang

---

### Post by Zugzwang on 2010-02-10
According to search results...

[http://www.lmgtfy.com/?q=%22version+GLIBC_2.0+not+defined+in+file+libc.so.6+with+link+time+reference%22+Kylix](http://www.lmgtfy.com/?q=%22version+GLIBC_2.0+not+defined+in+file+libc.so.6+with+link+time+reference%22+Kylix)

.. you might want to try "export LD_ASSUME_KERNEL=2.4.0".

---

### Post by petetheking on 2010-02-10
> **Zugzwang said:**
> According to search results...

[http://www.lmgtfy.com/?q=%22version+GLIBC_2.0+not+defined+in+file+libc.so.6+with+link+time+reference%22+Kylix](http://www.lmgtfy.com/?q=%22version+GLIBC_2.0+not+defined+in+file+libc.so.6+with+link+time+reference%22+Kylix)

.. you might want to try "export LD_ASSUME_KERNEL=2.4.0".

king@ubuntu:~/kylix3/bin$ ./startbcb
/home/king/kylix3/bin/bcblin: relocation error: /home/king/kylix3/bin/libwine.borland.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
king@ubuntu:~/kylix3/bin$ export LD_ASSUME_KERNEL=2.4.0
king@ubuntu:~/kylix3/bin$ ./startbcb
/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
king@ubuntu:~/kylix3/bin$ ls
ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
king@ubuntu:~/kylix3/bin$ 

Same ....

---

### Post by Zugzwang on 2010-02-10
Please verify that "libdl.so.2" is in "/lib". If that is the case, try "export LD_LIBRARY_PATH=/lib" and run it again.

Is it possible that you run Linux in 64-bit mode and the version of Kylix you have is for 32-bit?

---

### Post by petetheking on 2010-02-10
> **Zugzwang said:**
> Please verify that "libdl.so.2" is in "/lib". If that is the case, try "export LD_LIBRARY_PATH=/lib" and run it again.

Is it possible that you run Linux in 64-bit mode and the version of Kylix you have is for 32-bit?

king@ubuntu:~/kylix3/bin$ export LD_LIBRARY_PATH=/lib
king@ubuntu:~/kylix3/bin$ ./startbcb
/home/king/kylix3/bin/bcblin: relocation error: /home/king/kylix3/bin/libwine.borland.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
king@ubuntu:~/kylix3/bin$ export LD_ASSUME_KERNEL=2.4.0
king@ubuntu:~/kylix3/bin$ ./startbcb
/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
king@ubuntu:~/kylix3/bin$ export LD_LIBRARY_PATH=/lib/
king@ubuntu:~/kylix3/bin$ ./startbcb
/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
king@ubuntu:~/kylix3/bin$ ls /lib/lib
Display all 148 possibilities? (y or n)
king@ubuntu:~/kylix3/bin$ ls /lib/libdl
libdl-2.10.1.so  libdl.so.2

---

### Post by Zugzwang on 2010-02-10
Ah, can you try editing the "startbcb" script in order to add this "ASSUME_KERNEL" line in front of all calls to actual programs? It seems as that line prevents "bash" from starting.

---

### Post by petetheking on 2010-02-10
> **Zugzwang said:**
> Ah, can you try editing the "startbcb" script in order to add this "ASSUME_KERNEL" line in front of all calls to actual programs? It seems as that line prevents "bash" from starting.

#!/bin/bash

# BEGIN STRING TABLE

KYDEF_LOCALE="en_US"
LC_ALL_IS_C1="The LC_ALL environment variable is set to C.  Kylix cannot start with this setting."
LC_ALL_IS_C2="Defaulting LC_ALL to"

# END STRING TABLE

if [ -z "$LANG" ]; then
   LANG=$KYDEF_LOCALE
   export LANG
fi

if [ "$LC_ALL" = "C" ]; then
   echo "$LC_ALL_IS_C1"
   echo "$LC_ALL_IS_C2 $KYDEF_LOCALE."
   LC_ALL=$KYDEF_LOCALE
   export LC_ALL
fi

export LD_LIBRARY_PATH=/home/king/kylix3/bin/mozilla:$LD_LIBRARY_PATH
export MOZILLA_FIVE_HOME=$HOME/.borland/borpreview
source /home/king/kylix3/bin/kylixpath /home/king/kylix3 >/dev/null
/home/king/kylix3/bin/bcblin $*
export LD_LIBRARY_PATH=/lib
export LD_ASSUME_KERNEL=2.4.0
#########################################################

king@ubuntu:~/kylix3/bin$ ./startbcb
/home/king/kylix3/bin/bcblin: relocation error: /home/king/kylix3/bin/libwine.borland.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
king@ubuntu:~/kylix3/bin$ export LD_ASSUME_KERNEL=2.4.0
king@ubuntu:~/kylix3/bin$ ./startbcb
/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
king@ubuntu:~/kylix3/bin$ 


On the TOP there is the file startbcb!

---

### Post by petetheking on 2010-02-10
> **petetheking said:**
> #!/bin/bash

# BEGIN STRING TABLE

KYDEF_LOCALE="en_US"
LC_ALL_IS_C1="The LC_ALL environment variable is set to C.  Kylix cannot start with this setting."
LC_ALL_IS_C2="Defaulting LC_ALL to"

# END STRING TABLE

if [ -z "$LANG" ]; then
   LANG=$KYDEF_LOCALE
   export LANG
fi

if [ "$LC_ALL" = "C" ]; then
   echo "$LC_ALL_IS_C1"
   echo "$LC_ALL_IS_C2 $KYDEF_LOCALE."
   LC_ALL=$KYDEF_LOCALE
   export LC_ALL
fi

export LD_LIBRARY_PATH=/home/king/kylix3/bin/mozilla:$LD_LIBRARY_PATH
export MOZILLA_FIVE_HOME=$HOME/.borland/borpreview
source /home/king/kylix3/bin/kylixpath /home/king/kylix3 >/dev/null
/home/king/kylix3/bin/bcblin $*
export LD_LIBRARY_PATH=/lib
export LD_ASSUME_KERNEL=2.4.0
#########################################################

king@ubuntu:~/kylix3/bin$ ./startbcb
/home/king/kylix3/bin/bcblin: relocation error: /home/king/kylix3/bin/libwine.borland.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
king@ubuntu:~/kylix3/bin$ export LD_ASSUME_KERNEL=2.4.0
king@ubuntu:~/kylix3/bin$ ./startbcb
/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
king@ubuntu:~/kylix3/bin$ 


On the TOP there is the file startbcb!

I reorder code an got new error:

/home/king/kylix3/bin/bcblin: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory


Code of startbcb:

#!/bin/bash -v

# BEGIN STRING TABLE

KYDEF_LOCALE="en_US"
LC_ALL_IS_C1="The LC_ALL environment variable is set to C.  Kylix cannot start with this setting."
LC_ALL_IS_C2="Defaulting LC_ALL to"

# END STRING TABLE

if [ -z "$LANG" ]; then
   LANG=$KYDEF_LOCALE
   export LANG
fi

if [ "$LC_ALL" = "C" ]; then
   echo "$LC_ALL_IS_C1"
   echo "$LC_ALL_IS_C2 $KYDEF_LOCALE."
   LC_ALL=$KYDEF_LOCALE
   export LC_ALL
fi

export LD_LIBRARY_PATH=/home/king/kylix3/bin/mozilla:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=/lib
export LD_ASSUME_KERNEL=2.4.0
export MOZILLA_FIVE_HOME=$HOME/.borland/borpreview
source /home/king/kylix3/bin/kylixpath /home/king/kylix3 >/dev/null
/home/king/kylix3/bin/bcblin $*

---

