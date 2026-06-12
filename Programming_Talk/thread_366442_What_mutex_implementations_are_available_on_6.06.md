---
title: "What mutex implementations are available on 6.06?"
date: 2007-02-20
forum: Programming Talk
---

### Post by dthury on 2007-02-20
I'm trying to install/run Oracle's DB XML database on 6.06. The build they provided "seemed" to go OK; however, when I tried some commands from their command line, got some errors.   Working through an Oracle Tech support form for the product, I found the following excerpt:

> To avoid this error, explicitly specify the mutex implementation DB should use, with the—with-mutex=MUTEX configuration flag:

    --with-mutex=MUTEX
        To force Berkeley DB to use a specific mutex implementation,
        configure with --with-mutex=MUTEX, where MUTEX is the mutex
        implementation you want. For example,
        --with-mutex=x86/gcc-assembly will configure Berkeley DB to use
        the x86 GNU gcc compiler based test-and-set assembly mutexes.
        This is rarely necessary and should be done only when the
        default configuration selects the wrong mutex implementation. A
        list of available mutex implementations can be found in the
        distribution file dist/aclocal/mutex.ac

My question is "What mutex implementations are available:confused: ?   Once I know, I can specify the correct input for the "--with-mutex=xxxx"!   Do I have this x86/gcc-assembly mutex implementation?  (I could not find any files with names like this!)   Can I download/install it?

Any ideas??

---

### Post by thumper on 2007-02-21
Perhaps you could try 'posix'.

Not sure if this is what it is after, but worth a try.

---

### Post by dthury on 2007-02-22
I have nothing against POSIX, and am willing to install it! Where/how do I get it?  I'm kinda new to Ubuntu and the whole Linux environment.  As I read/research this problem through the DBXML support forums, it looks like I'll need some source code for the POSIX pthreads.

What do I need to get/install, and where should I get it:confused:?

Thanks,

---

### Post by thumper on 2007-02-22
posix is the native threading model of linux.

You shouldn't need to install anything.

---

### Post by dthury on 2007-02-22
The pieces the build script needs are not there!  The DBXML build script seems to be looking for a file(s) in a location named something like POSIX/pthreads, or lib/POSIX/pthreads (I'm not at my ubuntu workstation now, so am working strictlty from memory (and poorly ;) ) .  I have NO directories on my system named POSIX!!

If I could find what I presume are the POSIX pthreads source modules, I think that would resolve my problem!!

---

### Post by dthury on 2007-02-23
I have just successfully rebuilt DBXML 2.3.10, and the problem I was having is now gone!!??!!

The only difference between my previous builds is that I logged on as root to expand the tar file kit, and issue its build command!!

My previous attempts used sudo to move the expanded kit into its desired location (/usr/local), then run its build script!!

Does this make sense?  what's the difference between sudo and logging as root??

regards,
  Denny

---

