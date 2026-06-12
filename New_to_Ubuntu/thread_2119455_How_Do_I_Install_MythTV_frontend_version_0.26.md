---
title: "How Do I Install MythTV frontend version 0.26?"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by Old Jimma on 2013-02-23
Hi Community:

How do I install MythTV frontend, version 0.26?

Thanks,
Old Jimma

:popcorn:

---

### Post by x64Architecture on 2013-02-23
Run the following commands in the terminal:
```

wget http://www.mythtv.org/download/mythtv/0.26.0
tar jxvf mythtv-0.26.0.tar.bz2
cd mythtv-0.26.0
./configure
make
make install

```

---

### Post by Old Jimma on 2013-02-24
Thanks for your reply X64Archtecture:

When I did the 

> ./configure

I got the following (error?) message:

> 
g++ is unable to create an executable file.
Check your ECXXFLAGS: [ ]
If g++ is a cross-compiler, use the --enable-cross-compile option.
Only do this if you know what [COLOR="Red"]cross compiling[/COLOR] means.
C++ compiler test failed.

If you think configure made a mistake, make sure that you are using the latest
version of MythTV from git.  If the latest version fails, report the problem to the
[email]mythtv-dev@mythtv.org[/email] mailing list or IRC #mythtv on irc.freenode.net
Include the log file "config.ep" produced by configure as this will help
solving the problem.


I don't know what [COLOR="Red"]cross compiling[/COLOR] means, so... what do I do now?

Thanks,
Old Jimma

---

### Post by Old Jimma on 2013-02-26
Please see solution at: [http://ubuntuforums.org/showthread.php?t=2119332]("http://ubuntuforums.org/showthread.php?t=2119332")

---

