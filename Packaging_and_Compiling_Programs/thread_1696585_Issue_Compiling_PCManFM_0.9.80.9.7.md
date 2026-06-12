---
title: "Issue Compiling PCManFM 0.9.8/0.9.7"
date: 2011-02-27
forum: Packaging and Compiling Programs
---

### Post by beastrace91 on 2011-02-27
I am trying to build PCManFM on Ubuntu but the compile keeps failing out with this message in terminal:

```
pcmanfm.c: In function ‘unix_signal_handler’:
pcmanfm.c:108: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
pcmanfm.c: In function ‘on_unix_signal’:
pcmanfm.c:114: warning: passing argument 2 of ‘g_io_channel_read_chars’ from incompatible pointer type
/usr/include/glib-2.0/glib/giochannel.h:247: note: expected ‘gchar *’ but argument is of type ‘int *’
pcmanfm.c: In function ‘on_single_inst_command’:
pcmanfm.c:162: warning: assignment from incompatible pointer type
pcmanfm.c: In function ‘pass_args_to_existing_instance’:
pcmanfm.c:209: warning: passing argument 2 of ‘single_inst_send_strv’ from incompatible pointer type
single-inst.h:64: note: expected ‘const char **’ but argument is of type ‘char **’
pcmanfm.c: In function ‘main’:
pcmanfm.c:234: warning: enumeration value ‘SINGLE_INST_SERVER’ not handled in switch
pcmanfm.c: In function ‘pcmanfm_open_folder_in_terminal’:
pcmanfm.c:509: warning: initialization from incompatible pointer type
pcmanfm.c:614:35: error: macro "fm_copy_file" requires 3 arguments, but only 2 given
pcmanfm.c: In function ‘pcmanfm_create_new’:
pcmanfm.c:614: error: ‘fm_copy_file’ undeclared (first use in this function)
pcmanfm.c:614: error: (Each undeclared identifier is reported only once
pcmanfm.c:614: error: for each function it appears in.)
make[3]: *** [pcmanfm-pcmanfm.o] Error 1
make[3]: Leaving directory `/media/sda6/Bodhi/Packages/pcmanfm/pcmanfm-0.9.8/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/media/sda6/Bodhi/Packages/pcmanfm/pcmanfm-0.9.8'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/media/sda6/Bodhi/Packages/pcmanfm/pcmanfm-0.9.8'
dh_auto_build: make -j1 returned exit code 2
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

I've tried the 0.9.7 and 0.9.8 source code packages from source forge - any ideas what I am missing/doing wrong?

~Jeff

---

### Post by MadCow108 on 2011-02-27
what os are you using?
I assume your trying to compile the packet?

the 0.9.7 packet in ubuntu 10.10 and the original source alone work in 10.10.
but 0.9.8 does also not work on my system, it possibly it has some additional dependencies unknown to me.

edit: are you building on natty?
It fails to build the maverick version with the same message in a clean natty chroot.

you then should us the natty version:
[https://launchpad.net/ubuntu/+source/pcmanfm/0.9.8+git-6240436419-0ubuntu1](https://launchpad.net/ubuntu/+source/pcmanfm/0.9.8+git-6240436419-0ubuntu1)
or backport the patch: 01-libfm-0.1.14-API-changes.patch from that package to 0.9.7

---

### Post by beastrace91 on 2011-02-27
I have a newer version of libfm I compiled and installed as well - 0.1.5 from git, I am using a 10.04 base but I have a number of newer packages compiled up and installed on the system.

~Jeff

---

### Post by MadCow108 on 2011-02-28
then you need to backport 01-libfm-0.1.14-API-changes.patch
as the name of the patch indicates libfm has changed their api and it is not yet in pcmanfm

---

