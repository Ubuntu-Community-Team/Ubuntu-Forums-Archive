---
title: "ps -efx | grep java6"
date: 2016-09-09
forum: New to Ubuntu
---

### Post by houmingc on 2016-09-09
what does linux command ps -efx | grep java6 means

---

### Post by ajgreeny on 2016-09-09
Have a look at **man ps** in terminal when you have this type of query and you should find all the details you need.
> ps - report a snapshot of the current processes.

-e     Select all processes.  Identical to -A.

x      Lift the BSD-style "must have a tty" restriction, which is imposed upon the set of all processes when
              some BSD-style (without "-") options are used or when the ps personality setting is BSD-like.  The set
              of processes selected in this manner is in addition to the set of processes selected by other means.
              An alternate description is that this option causes ps to list all processes owned by you (same EUID as
              ps), or to list all processes when used together with the a option.

-f     Do full-format listing. This option can be combined with many other UNIX-style options to add
              additional columns.  It also causes the command arguments to be printed.  When used with -L, the NLWP
              (number of threads) and LWP (thread ID) columns will be added.  See the c option, the format keyword
              args, and the format keyword comm.
**| grep java6** pipes, ie passes the output to **grep** which searches for the java6 string and shows only lines that contain that string.

---

