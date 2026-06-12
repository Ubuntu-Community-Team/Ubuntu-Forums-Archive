---
title: "Missing predefs.h"
date: 2011-11-09
forum: Programming Talk
---

### Post by Rodayo on 2011-11-09
I'm trying to build the ANSI C port for Unix v6. I'm cloned this git repo, git://pdos.csail.mit.edu/xv6/xv6.git

When I run make I get the following error:
```
/usr/include/features.h:323:26: fatal error: bits/predefs.h: No such file or directory
```Does anyone know what could be causing it and how to fix it?

Found a fix. I needed the proper libc includes for 32-bit builds. I'm running a 64-bit machine. So I just ran:

sudo apt-get install libc6-dev-i386

---

### Post by fabiovh on 2012-07-10
thanks, saved me time!

---

### Post by Patagonicus on 2012-07-27
Thanks too, also saved me a lot of time !!! :)

---

### Post by descendents1 on 2012-08-31
Thank you! This also worked for me while I was installing OpenACC accelerator tools for PGI on my Ubuntu 12 64 bit machine. I already had my CUDA drivers squared away.

---

### Post by MikeCyber on 2012-09-23
Thanks for: [http://www.garagegames.com/community/forums/viewthread/131742](http://www.garagegames.com/community/forums/viewthread/131742)

---

### Post by Darent on 2012-10-28
I had the exact same error message while trying to install a flash workaround for dual  monitor fullscreen issue, just saying for if somebody reach  this page with the same problem, it solved and now it installs well. Thanks a lot!

---

### Post by qwerty9967 on 2012-11-29
Worked for me.  Perfect!  Thanks!

---

### Post by cnunezcast on 2012-12-19
Thanks for the post!. I had the same problem. I was trying to use OPNET modeler and compile my project. With this solution it worked perfectly!.

---

### Post by sherrylar on 2013-06-16
It works for me. Thanks for the post!

---

### Post by sramanujam on 2013-12-12
> **Rodayo said:**
> I'm trying to build the ANSI C port for Unix v6. I'm cloned this git repo, git://pdos.csail.mit.edu/xv6/xv6.git

When I run make I get the following error:
```
/usr/include/features.h:323:26: fatal error: bits/predefs.h: No such file or directory
```Does anyone know what could be causing it and how to fix it?

Found a fix. I needed the proper libc includes for 32-bit builds. I'm running a 64-bit machine. So I just ran:

sudo apt-get install libc6-dev-i386

Worked like magic!

---

### Post by teledyn on 2013-12-25
> **sramanujam said:**
> Worked like magic!

not in 13.10 -- I get 

E: Unable to locate package libc-dev-i386

Am I missing something? :(

---

### Post by ScienziatoBestia on 2013-12-31
me too, same problem under ubuntu 13.10 amd64
where I can find this header?

---

### Post by ScienziatoBestia on 2013-12-31
ok I solved installing this package
g++-4.8-multilib

---

