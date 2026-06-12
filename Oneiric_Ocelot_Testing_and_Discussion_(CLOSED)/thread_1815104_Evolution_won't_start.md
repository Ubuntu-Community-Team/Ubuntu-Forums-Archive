---
title: "Evolution won't start"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rubenverweij on 2011-07-30
Hi all!

I'm having problems with Evolution 3.1.4-0ubuntu1.
It won't start thanks to this error:
```
(evolution:2567): evolution-shell-CRITICAL **: shell_settings_pspec_for_key: assertion `schema_name != NULL' failed
Segmentation fault (core dumped)

```
Is anyone else seeing this/does anyone know how to fix it?
I'm not sure whether or not to file a bug report, maybe it has something to do with my settings.

Thanks!

---

### Post by mc4man on 2011-07-30
On one of my installs, an older one, evolution is the same, likely dead and buried
(tried many things, will not open

On a very fresh install it does open fine though it will not 'Remember,,' the password, has to be re-entered every time.
Did file bug on this, the former didn't bother because it is working on the newer install and from the current iso live  session.

---

### Post by lsrg on 2011-08-01
> **rubenverweij said:**
> Hi all!

I'm having problems with Evolution 3.1.4-0ubuntu1.
It won't start thanks to this error:
```
(evolution:2567): evolution-shell-CRITICAL **: shell_settings_pspec_for_key: assertion `schema_name != NULL' failed
Segmentation fault (core dumped)

```
Is anyone else seeing this/does anyone know how to fix it?
I'm not sure whether or not to file a bug report, maybe it has something to do with my settings.

Thanks!

I have the same problem!

---

### Post by mc4man on 2011-08-01
While in a week ago install evolution would install and run as described in post 2, on one just done (07/31 iso) same crash
Your apport crash would likely report - 
"evolution crashed with SIGSEGV in g_str_equal()"

2 open bug reports - 
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/817468](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/817468)

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/818135](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/818135)

What changed in a week, not sure. (well a lot of related packages upgreded though no impact on previous install

---

### Post by olivier.blanc on 2011-08-01
Running evolution in gdb environment will allow evolution to start :

gdb evolution
start

---

### Post by rubenverweij on 2011-08-04
> **olivier.blanc said:**
> Running evolution in gdb environment will allow evolution to start :

gdb evolution
start
I tried this, I got the following output (Evolution still didn't start):
```
gdb evolution
GNU gdb (Ubuntu/Linaro 7.2-1ubuntu11) 7.2
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/evolution...(no debugging symbols found)...done.
(gdb) start
Temporary breakpoint 1 at 0x1c86
Starting program: /usr/bin/evolution 
[Thread debugging using libthread_db enabled]

Temporary breakpoint 1, 0x00111c86 in main ()
(gdb)
```
Am I doing something wrong? Thanks for your help!

---

### Post by rubenverweij on 2011-08-04
Okay, very strange. It seems that Evolution *is* in fact running, the only problem is that the window is not visible on any workspace, nor is the indicator initialized nor any icons displayed in the unity launcher. But I can see the process via top. :S

Edit: under waiting channel it says "ptrace_stop". Is this in any way significant?

---

### Post by rubenverweij on 2011-08-04
Please also see this open bug report: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/687365](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/687365).

---

### Post by t-c on 2011-09-08
I also have an Evolution issue, worked fine 3 days ago(6/9/2011) but now it won't. From terminal;
"evolution: symbol lookup error: evolution: undefined symbol: g_unix_signal_add_watch_full"
There doesn't appear to be any process relating to evolution running.

---

### Post by Bowmore on 2011-09-08
@t-c: See to that you have the latest updates of evolution (3.1.91-0ubuntu1) and evolution-data-server (3.1.91-0ubuntu1). Those are now all mirrored on the main server and should fix your problem.

Bug: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/843769](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/843769)

---

