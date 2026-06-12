---
title: "strace - A very powerful troubleshooting tool for all Linux users"
date: 2006-05-07
forum: Programming Talk
---

### Post by newbie2 on 2006-05-07
>  Many times I have come across seemingly hopeless situations where a program when compiled and installed in GNU/Linux just fails to run. In such situations after I have tried every trick in the book like searching on the net and posting questions to Linux forums, and still failed to resolve the problem, I turn to the last resort which is trace the output of the misbehaving program. Tracing the output of a program throws up a lot of data which is not usually available when the program is run normally. And in many instances, sifting through this volume of data has proved fruitful in pin pointing the cause of error.

For tracing the system calls of a program, we have a very good tool in strace. What is unique about strace is that, when it is run in conjunction with a program, it outputs all the calls made to the kernel by the program. In many cases, a program may fail because it is unable to open a file or because of insufficient memory. And tracing the output of the program will clearly show the cause of either problem.

The use of strace is quite simple and takes the following form:
[http://linuxhelp.blogspot.com/2006/05/strace-very-powerful-troubleshooting.html](http://linuxhelp.blogspot.com/2006/05/strace-very-powerful-troubleshooting.html)

---

