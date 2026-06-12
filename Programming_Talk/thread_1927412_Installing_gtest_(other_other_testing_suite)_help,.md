---
title: "Installing gtest (other other testing suite) help, new to Ubuntu"
date: 2012-02-17
forum: Programming Talk
---

### Post by frickm42 on 2012-02-17
Hi, I recently made the switch to Ubuntu 11.10 about a month or so ago from windows.

I am computer science undergraduate and I've been trying to install a testing suite for my c++ programs. My school uses gtest, and this is the one I've been trying to install, but to put it simply, Ive had a hell of a time getting it to work.

I found some help at [http://manpages.ubuntu.com/manpages/natty/en/man1/gtest-config.1.html](http://manpages.ubuntu.com/manpages/natty/en/man1/gtest-config.1.html)

The line: If the info and gtest-config programs are  properly  installed
       at your site, the command

              info gtest-config

       should give you access to the complete manual.

info gtest-config runs fine, but nothing I try to compile works correctly. It always gives me an error. The compile line I try to use is: 


g++ *.cpp –lpthread –lgtest

but the errors I get are:
g++: error: –lpthread: No such file or directory
g++: error: –lgtest: No such file or directory

I'm not sure where to go from here, and all the instructions I have found don't really help. Does anyone know how to fix this, or if anyone knows any other testing suites to use I'll give them a shot, I just need something that works.

Thanks alot

---

### Post by nothingspecial on 2012-02-18
*Thread moved to **Programming Talk**.*

---

### Post by BeniaminK on 2012-11-15
Gtest doesn't install .so library in your system. Instead it just creates source files for you to compile, include or do whatever you would like to do with them.
See the full install file list:
[http://packages.ubuntu.com/quantal/amd64/libgtest-dev/filelist](http://packages.ubuntu.com/quantal/amd64/libgtest-dev/filelist)

You can find information out there that you need.

---

