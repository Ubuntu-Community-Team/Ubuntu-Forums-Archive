---
title: "Problems compiling MINUIT (cernlib) in ubuntu 11.10"
date: 2011-12-09
forum: Packaging and Compiling Programs
---

### Post by jose. on 2011-12-09
Hi to all,
Time ago, I upgraded ubuntu to version 11.10, but since then, I have not been able to compile any program that uses MINUIT (cernlib). The error message reads: 

fort77-4987-1.c: (.text+0xf): undefined reference to `minuit_'
collect2: ld returned 1 exit status

The command line that used to work was "f77 program.for  -L/usr/local/cernlib -lmathlib -lkernlib" (or with gfortran), but now  there is no way. I tried to reinstall cernlib and the compilers but it  doesn't solves the problem. I would be very thankful if you could help  me with this. Thanks in advance.


                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11514996")                                                                                    [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11514996")

---

