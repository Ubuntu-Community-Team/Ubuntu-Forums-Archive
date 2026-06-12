---
title: "Record which files are and are not used or accessed?"
date: 2010-05-21
forum: Programming Talk
---

### Post by altonbr on 2010-05-21
I'm doing some contracting and my work is requiring me to clean up lots of old code. Is there any way I can run a PHP/MySQL application locally and have Apache or bash or something record which files have been accessed and which haven't while I run the application?

e.g.```
files used:
index.php
inc/functions.php

files not used:
inc/functions-bak.php
```

---

### Post by diesch on 2010-05-21
You can use *strace* to see which files are accessed by a program, e.g.

```
strace -e trace=file -o logfile some_program
```or 

```
strace -e trace=file -o logfile -p PID
``` where PID is the process ID of a running program.  The output is written to logfile.

Use *trace=open* instead of *trace=file* if you only want the files that are opened.

---

### Post by altonbr on 2010-05-27
> **diesch said:**
> You can use *strace* to see which files are accessed by a program, e.g.

```
strace -e trace=file -o logfile some_program
```or 

```
strace -e trace=file -o logfile -p PID
``` where PID is the process ID of a running program.  The output is written to logfile.

Use *trace=open* instead of *trace=file* if you only want the files that are opened.
Well I would need to trace apache and php then no? How would I trace apache when it has so many threads too?

---

### Post by diesch on 2010-05-27
The option *-f* tells strace to trace child processes, too. 

Either start Apache using *-f * or trace every process on its own.

---

### Post by rnerwein on 2010-05-28
> **altonbr said:**
> Well I would need to trace apache and php then no? How would I trace apache when it has so many threads too?

hi
strace -e trace=file -o logfile some_program
be careful ! --> 
trace=file will give you only system calls where a filename is given. if the file descriptor is inherited and
read,write,lseek,lstat ...... etc. is used by a child process those calls are not shown in the trace !
you have to use: trace=read,write,lstat ....etc. too.  :-)

ciao

---

### Post by diesch on 2010-05-28
> **rnerwein said:**
> 
strace -e trace=file -o logfile some_program
be careful ! --> 
trace=file will give you only system calls where a filename is given. if the file descriptor is inherited and
read,write,lseek,lstat ...... etc. is used by a child process those calls are not shown in the trace !
you have to use: trace=read,write,lstat ....etc. too.  :-)


To just see which files are accessed it's usually enough to see the syscalls that use a file name. To see the file descriptor related calls you can use* trace=desc* - but I don't think that's of much value in this case.

---

### Post by rnerwein on 2010-05-28
> **diesch said:**
> To just see which files are accessed it's usually enough to see the syscalls that use a file name. To see the file descriptor related calls you can use* trace=desc* - but I don't think that's of much value in this case.

hi 
ok you are rright but only if you use: 
strace -f -e trace=file -o logfile [COLOR=Blue]some_program
:-) and not -p PID
[/COLOR]

---

### Post by altonbr on 2010-06-02
I think this strace program is a little over my head:
```
$ strace -e trace=file -o logfile apache2
apache2: bad user name ${APACHE_RUN_USER}
$ export APACHE_RUN_USER=www-data
$ strace -e trace=file -o logfile apache2
apache2: bad group name ${APACHE_RUN_GROUP}
$ export APACHE_RUN_GROUP=www-data
$ strace -e trace=file -o logfile apache2
Syntax error on line 52 of /etc/apache2/sites-enabled/default-ssl:
SSLCertificateKeyFile: file '/etc/ssl/private/ssl-cert-snakeoil.key' does not exist or is empty
```

---

### Post by soltanis on 2010-06-02
From man strace:

```

       -p pid      Attach to the process with the process  ID  pid  and
                   begin  tracing.   The trace may be terminated at any
                   time  by  a  keyboard  interrupt  signal   (CTRL-C).
                   strace  will  respond  by  detaching itself from the
                   traced process(es) leaving  it  (them)  to  continue
                   running.   Multiple -p options can be used to attach
                   to up to 32 processes in addition to command  (which
                   is optional if at least one -p option is given).

```

You should maybe just run Apache in the background and then have strace attach to it. If you are having difficulties with too many child processes or worker threads, then you can consider modifying the Apache configuration to make it spawn a single process (or use a different server).

---

### Post by geirha on 2010-06-02
Not exactly what you are asking for, but you could use inotifywait(1) to monitor filesystem events. It won't give you information on what process is causing them, but I believe it is likely that only apache will be accessing files under that dir anyway (and possibly a few cronjobs). Note that inotify is linux-specific and depends on it being enabled in the kernel.

```
inotifywait -m -r /var/www
```

Another thing is looking at the accesstime of files. If the filesystem is mounted with relatime or noatime options, remount it to use atime instead, then you can use find with -atime/-amin options to see which files hasn't been accesed for x days/minutes.

---

### Post by diesch on 2010-06-03
> **altonbr said:**
> I think this strace program is a little over my head:
```
$ strace -e trace=file -o logfile apache2
apache2: bad user name ${APACHE_RUN_USER}
$ export APACHE_RUN_USER=www-data
$ strace -e trace=file -o logfile apache2
apache2: bad group name ${APACHE_RUN_GROUP}
$ export APACHE_RUN_GROUP=www-data
$ strace -e trace=file -o logfile apache2
Syntax error on line 52 of /etc/apache2/sites-enabled/default-ssl:
SSLCertificateKeyFile: file '/etc/ssl/private/ssl-cert-snakeoil.key' does not exist or is empty
```

You can't start Apache that way, you'll get the same errors if you just try to run *apache2* without *strace*.

```
 strace -e trace=file -o logfile -f /etc/init.d/apache2 start
```should work. Or use the *-p *to attache strace to a running instance of Apache of you aren't interested in what Apache does at startup.

---

### Post by altonbr on 2010-06-03
> **diesch said:**
> You can't start Apache that way, you'll get the same errors if you just try to run *apache2* without *strace*.

```
 strace -e trace=file -o logfile -f /etc/init.d/apache2 start
```should work. Or use the *-p *to attache strace to a running instance of Apache of you aren't interested in what Apache does at startup.
Ahh, my problems was I didn't know I was actually _running_ Apache2, I thought I was just telling strace to attach to the program already running. That's what I get when I don't RTFM.

Thanks.

---

