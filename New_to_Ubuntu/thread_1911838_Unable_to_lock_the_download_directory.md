---
title: "Unable to lock the download directory"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-01-19
Attempting to install auto-apt
Terminal: sudo apt-get install auto-apt

Reported errors:
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
Have done this previously without any errors. Have reinstalled Lucid since then
Any ideas?:confused:

---

### Post by cortman on 2012-01-19
Very easy fix. Apparently you either have Synaptic, Software Centre, or aptitude running in the background. If you do have a GUI package program running, go ahead and close out. Otherwise-
In the terminal type


```
ps -ef |grep apt
```

This will bring up a list of apt processes. Use

```
kill -9 process_id
```

to terminate them. The PID is the four digit number in the second column from left.
Kill all the processes except 

```
grep --color=auto apt
```

---

### Post by Bumpalot on 2012-01-19
Did I do this wrong??
bump@bumpyputer:~$ ps -ef |grep apt
root      1756     1  0 12:12 ?        00:00:00 apt-get install auto-apt
root      1758  1756  0 12:13 ?        00:00:00 /bin/sh -c /usr/sbin/dpkg-preconfigure --apt || true
root      1759  1758  0 12:13 ?        00:00:00 /usr/bin/perl -w /usr/sbin/dpkg-preconfigure --apt
bump      1916  1900  0 12:19 pts/2    00:00:00 grep --color=auto apt
bump@bumpyputer:~$ kill -9 process_id 1756
bash: kill: process_id: arguments must be process or job IDs
bash: kill: (1756) - Operation not permitted
bump@bumpyputer:~$ kill -9 1756
bash: kill: (1756) - Operation not permitted
bump@bumpyputer:~$

---

### Post by drmrgd on 2012-01-19
Since those processes are owned by root (i.e. you used sudo to execute them), you need to be root to kill them.  Try adding sudo in front of the kill commands.

---

### Post by Buntumatic on 2012-01-19
You need sudo to kill processes that do not belong to you, for instance a process you started using sudo belongs to root.
FWIW, pkill and killall take process names instead of PID.
Finally, sometimes if the process is crashed a stale pid file is left behind, in this case you need to rm that pid file by hand to let system know the process is not running.

---

### Post by cortman on 2012-01-19
> **Bumpalot said:**
> Did I do this wrong??
bump@bumpyputer:~$ ps -ef |grep apt
root      1756     1  0 12:12 ?        00:00:00 apt-get install auto-apt
root      1758  1756  0 12:13 ?        00:00:00 /bin/sh -c /usr/sbin/dpkg-preconfigure --apt || true
root      1759  1758  0 12:13 ?        00:00:00 /usr/bin/perl -w /usr/sbin/dpkg-preconfigure --apt
bump      1916  1900  0 12:19 pts/2    00:00:00 grep --color=auto apt
bump@bumpyputer:~$ kill -9 process_id 1756
bash: kill: process_id: arguments must be process or job IDs
bash: kill: (1756) - Operation not permitted
bump@bumpyputer:~$ kill -9 1756
bash: kill: (1756) - Operation not permitted
bump@bumpyputer:~$

Sorry- I forgot to mention you need sudo. In your case you could run

```
sudo kill -9 1756 1758 1759
```

---

### Post by Bumpalot on 2012-01-19
Sorry guys, I am going around in circles!!
Here are my attempts....
bump@bumpyputer:~$ ps -ef |grep apt
root      1756     1  0 12:12 ?        00:00:00 apt-get install auto-apt
root      1758  1756  0 12:13 ?        00:00:00 /bin/sh -c /usr/sbin/dpkg-preconfigure --apt || true
root      1759  1758  0 12:13 ?        00:00:00 /usr/bin/perl -w /usr/sbin/dpkg-preconfigure --apt
bump      2015  1999  0 12:38 pts/1    00:00:00 grep --color=auto apt
bump@bumpyputer:~$
bump@bumpyputer:~$ sudo kill -9 1756
kill: No such process
bump@bumpyputer:~$ sudo kill pid 1756
kill: No such process
ERROR: garbage process ID "pid".
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.
bump@bumpyputer:~$ sudo kill -L
 1 HUP      2 INT      3 QUIT     4 ILL      5 TRAP     6 ABRT     7 BUS
 8 FPE      9 KILL    10 USR1    11 SEGV    12 USR2    13 PIPE    14 ALRM
15 TERM    16 STKFLT  17 CHLD    18 CONT    19 STOP    20 TSTP    21 TTIN
22 TTOU    23 URG     24 XCPU    25 XFSZ    26 VTALRM  27 PROF    28 WINCH
29 POLL    30 PWR     31 SYS     
bump@bumpyputer:~$ udo kill -l
Error:  0: couldn't open source file <kill.ui>
kill.ui: No such file or directory
bump@bumpyputer:~$
bump@bumpyputer:~$ sudo pkill -9 apt-get install auto-apt
Usage: pkill [-SIGNAL] [-fvx] [-n|-o] [-P PPIDLIST] [-g PGRPLIST] [-s SIDLIST]
    [-u EUIDLIST] [-U UIDLIST] [-G GIDLIST] [-t TERMLIST] [PATTERN]
bump@bumpyputer:~$

---

### Post by cortman on 2012-01-19
My bad- I should have been more clear. The previous post has the exact command for you to run, provided the PIDs are still the same.

---

### Post by Bumpalot on 2012-01-19
bump@bumpyputer:~$ ps -ef |grep apt
root      1758     1  0 12:13 ?        00:00:00 /bin/sh -c /usr/sbin/dpkg-preconfigure --apt || true
root      1759  1758  0 12:13 ?        00:00:00 /usr/bin/perl -w /usr/sbin/dpkg-preconfigure --apt
bump      2336  2319  0 16:11 pts/1    00:00:00 grep --color=auto apt
bump@bumpyputer:~$ sudo kill -9 1758 1759
[sudo] password for bump: 
kill: No such process
bump@bumpyputer:~$ sudo kill -9 1756 1759
kill: No such process
kill: No such process
bump@bumpyputer:~$
What now??

---

### Post by cortman on 2012-01-20
> **Bumpalot said:**
> bump@bumpyputer:~$ ps -ef |grep apt
root      1758     1  0 12:13 ?        00:00:00 /bin/sh -c /usr/sbin/dpkg-preconfigure --apt || true
root      1759  1758  0 12:13 ?        00:00:00 /usr/bin/perl -w /usr/sbin/dpkg-preconfigure --apt
bump      2336  2319  0 16:11 pts/1    00:00:00 grep --color=auto apt
bump@bumpyputer:~$ sudo kill -9 1758 1759
[sudo] password for bump: 
kill: No such process
bump@bumpyputer:~$ sudo kill -9 1756 1759
kill: No such process
kill: No such process
bump@bumpyputer:~$
What now??

It means you killed them. I've gotten random "no such process" errors myself, when I KNOW the processes exist, by running ps. I imagine it's a bug.

You should be able to lock the download directory and use apt-get now.

---

### Post by Bumpalot on 2012-01-20
Thanks cortman - problem is solved. I really appreciate your help.:)

---

### Post by cortman on 2012-01-20
Glad to be of help! Any other questions, always feel free to ask.

---

