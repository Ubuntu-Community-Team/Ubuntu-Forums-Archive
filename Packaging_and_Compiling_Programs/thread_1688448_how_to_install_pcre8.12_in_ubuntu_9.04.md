---
title: "how to install pcre8.12 in ubuntu 9.04"
date: 2011-02-15
forum: Packaging and Compiling Programs
---

### Post by kingkong22 on 2011-02-15
Hello,
I just downloaded pcre8.12 package & unpacked it in a directory under my home directory, then I typed ./configure to configure the system, it popped up some error messages without Makefile generated ! I wonder why it didn't generated the file, Makefile ? below are some error messages:

cannot remove `conf6399': No such file or directory
cannot remove `conf6399.exe': No such file or directory
cannot remove `conf6399.file': No such file or directory
cannot remove `conf6399.dir': No such file or directory
removed file `conf6399'
cannot remove `conf6399.exe': No such file or directory
rm: cannot remove `conf6399.dir/conf6399.file': No such file or directory
removed file `conf6399.file'
rm: cannot remove `conftest*': No such file or directory
rm: cannot remove `confdefs.h': No such file or directory
checking for a BSD-compatible install... rm: cannot remove `conftest.one': No such file or directory
rm: cannot remove `conftest.two': No such file or directory
rm: cannot remove `conftest.dir': No such file or directory
removed file `conftest.one'
removed file `conftest.two'
removed directory `conftest.dir'
/usr/bin/install -c
checking whether build environment is sane... removed file `conftest.file'
yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... removed file `conftest.make'
yes

---

