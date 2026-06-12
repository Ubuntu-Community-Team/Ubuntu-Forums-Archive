---
title: "How to monitor file read/writes"
date: 2006-04-13
forum: Programming Talk
---

### Post by prophet on 2006-04-13
I need a program that monitors file read/writes with filtering capabilities. I was thinking that this would make it easier to find out which files are used by a specific application to save configuration settings so that I can modify it or restrict other users from modifying it.

Filemon for linux no longer works ever since the kernel has been modified according to a forum on the sysinternals site. lsof doesn't seem to have an option to filter based on burst writes. i.e. I cannot, say, let it run, edit the configuration through the GUI, save it (am assuming burst write happens here), then go through the output and just look for write accesses. dnotify looks like it just calls another program which means that I'd have to program an application which I don't know how to do.

Right now, I feel that the file organization in linux is a bit too crowded and confusing. I often see folders with files from other applications all lumped into one. I have been doing some reading and know that there are standards for where programs put files, but these documentations are long. Then since the location of installed files is hardcoded into the application package (unlike in windows where you can choose where to install)- I'm just not confident that all programmers would coimpletely read through and follow the guidelines. A filemon-like utility would be extremely helpful in this regard as using it for a while would help in the understanding for where files usually go and what filenames are usually used. I hope there is such a program, or if not, I hope I have encouraged someone to write one..:) thanks in advance.

---

