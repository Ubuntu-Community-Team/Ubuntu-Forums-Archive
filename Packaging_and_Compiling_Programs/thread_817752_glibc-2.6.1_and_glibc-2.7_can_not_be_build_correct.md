---
title: "glibc-2.6.1 and glibc-2.7 can not be build correctly with apt-get source -b lib6"
date: 2008-06-03
forum: Packaging and Compiling Programs
---

### Post by flymj on 2008-06-03
I want to debug the ld-linux.so on ubuntu7.10, and I find there is some issues on the lib6's build.
The procedure I use is listed below:
[COLOR="Blue"]apt-get build-dep libc6
apt-get source -b libc6[/COLOR]
then I got the error message:
[COLOR="Magenta"]Applying patches...failed! (check /home/code/glibc-2.6.1/stamp-dir/patch-log for details)
make: *** [/home/code/glibc-2.6.1/stamp-dir/patch-stamp] Error 1[/COLOR]
patch-log:
[COLOR="magenta"]Applying patch amd64/local-linuxthreads-gscope.diff
patch: **** File linuxthreads/sysdeps/x86_64/tls.h seems to be locked by somebody else under Perforce
Patch amd64/local-linuxthreads-gscope.diff does not apply (enforce with -f)[/COLOR]
I also tried to disable this patch, but got another error message on other files with same reason.
The test is also done on Ubuntu8.04 with glibc2.7, the issue is still there.

Therefore, does anybody know how to solve this issue or does that expected result?

---

