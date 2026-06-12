---
title: "sig fault"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by iason on 2008-10-19
I run a program in a screen, it crashes alot and I am unable to open the screen. is this common, cause i would like to be able to screen -r and relaunch the program.  setting this up in a cronjob.  but right now there is that screen process that is now owned by root, well the /dev/pts/1 is. 

a@jasonj:~$ ps x
  PID TTY      STAT   TIME COMMAND
 5134 pts/0    S      0:00 su user
 5188 pts/0    S      0:00 bash
15441 ?        Ss     0:00 SCREEN
15447 pts/3    Ss     0:00 /bin/bash
16149 pts/3    S+     0:00 /bin/sh ./run.sh
16150 pts/3    S+     2:34 bin_unix/bc_server
25858 pts/0    R+     0:00 ps x
27755 ?        Ss     0:00 SCREEN
27756 pts/2    Ss+    0:00 /bin/bash
a@jasonj:~$ screen -r 15441
Cannot open your terminal '/dev/pts/0' - please check.
a@jasonj:~$ ls /dev/pts
0  2  3
a@jasonj:~$ ls -la /dev/pts
total 0
drwxr-xr-x 2 root        root      0 Oct 17 06:14 .
drwxr-xr-x 6 root        root   2120 Oct 17 06:15 ..
crw------- 1 root        tty  136, 0 Oct 19 17:02 0
crw--w---- 1 a tty  136, 2 Oct 18 18:38 2
crw--w---- 1 a tty  136, 3 Oct 19 16:37 3
a@jasonj:~$ exit
exit

---

