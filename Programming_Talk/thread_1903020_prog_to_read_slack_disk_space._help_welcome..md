---
title: "prog to read slack disk space. help welcome."
date: 2012-01-01
forum: Programming Talk
---

### Post by F.G. on 2012-01-01
hi folks,

I want to write a program to read the slack space in a disk drive. the operating system i would be running it on would be some version of ubuntu, redhat, and possibly arch.

i wrote a program a while back, which just incremented an array pointer out of bounds, and read all the main memory in windows7 quite happily. however as a result of sensible security measures this did not work in linux, i mean i could reallocate the memory (etc, etc) but this would create an expanding memory space which would eat up the working memory of the machine.

besides... i want to read the hard disk, not the main memory. also it would be nice to iteratively go through the slack space, not reserving the memory space. also i want it to output as chars.  now, the output can go to stdout, or to a file, obviously memory space will be an issue as i will be running it on the same machine, on the same disk (so i can't output and save all the data, although some kind of filtering mechanism could be used, only to save interesting data). i guess maybe reading to stdout and the pipe/grepping to an output redirect could be a solution, eg:
```
./myprogram | grep some_error_code > output_file.txt
``` 

so, the motivation behind this is to check out old data logs, which reside, un-deleted in slack space on the root partition (a-la-kaspersy style, if anyone saw the recent kaspersky duqu report).

programming-wise i'm planning to use C, although i am open to suggestion, and do have some proficiency in C++, Python, Tcl, Ruby (and some JVM stuff which wont really be applicable).

any suggestions / help will be very welcome.  thanks for all and any replies.  my main problem is that i don't know how to access the HD without using a file pointer or how to do it iteratively without locking all the space.

---

