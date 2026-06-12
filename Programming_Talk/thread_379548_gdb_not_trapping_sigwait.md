---
title: "gdb not trapping sigwait"
date: 2007-03-08
forum: Programming Talk
---

### Post by samm on 2007-03-08
I have a threaded program uses a thread to call sigwait and handle signals.  When running this program in GDB, it fails to trap SIGINT and terminates my program instead of returning control to gdb.  Running on an IBM Thinkpad T42 with Edgy Eft. I tried using the default gdb (6.4.90-debian) and gdb pulled from CVS today, it fails to trap the signal in both cases.  Here is a shorted version the code and sample invocation (compile with g++ -o sigwait -pthread sigwait.cc) :

```

#include <pthread.h>
#include <csignal>
#include <iostream>

using namespace std;

void* threadFunc(void* arg);

int main() {
    sigset_t set;
    sigemptyset( &set );
    sigaddset( &set, SIGINT );
    sigaddset( &set, SIGTERM );

    // Block new threads from getting signals
    pthread_sigmask(SIG_BLOCK, &set, NULL );

    // Create a thread
    pthread_t id;
    pthread_attr_t attr;
    pthread_attr_init(&attr);
    pthread_create(&id, &attr, threadFunc, (void*)NULL);

    // wait for signal
    int sig = 0;
    do {
        int rc = sigwait( &set, &sig );
        if (rc != 0) {
            cerr << "error in sigwait" << endl;
            exit(-1);
        }
        cout << "received signal " << sig << endl;

    } while (sig != SIGINT);
}

void* threadFunc(void *) {
    while(true) { sleep(1); }
}

```

sample gdb session where I hit control-C to interrupt the program:
```

samm@joule:~/gdb-build$ ./gdb/gdb ~/sigwait 
GNU gdb 6.6.50.20070308-cvs
Copyright (C) 2007 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i686-pc-linux-gnu"...
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) info handle SIGINT
Signal        Stop      Print   Pass to program Description
SIGINT        Yes       Yes     No              Interrupt
(gdb) run
Starting program: /home/samm/sigwait 
[Thread debugging using libthread_db enabled]
[New Thread -1210939728 (LWP 26670)]
[New Thread -1210942560 (LWP 26673)]
received signal 2

Program exited normally.
(gdb) 

```

uname output:
```

samm@joule:~/gdb-build$ uname -a
Linux joule 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
samm@joule:~/gdb-build$ 

```

I would expect gdb to trap the signal and not pass it on to the program (as evident by the info handle SIGINT output) but that clearly isn't the case.  Any ideas here?  I did a google search and found some mentions of a bug in the 2.6 kernel but I haven't got much further than that:

[http://sources.redhat.com/ml/gdb/2006-04/msg00015.html](http://sources.redhat.com/ml/gdb/2006-04/msg00015.html)

---

### Post by Mr. C. on 2007-03-08
Its been a while, but have you looked at:

help handle

in gbd?  Some signals need to be handled specially.

MrC

---

### Post by samm on 2007-03-09
Hi Mr. C, in my gdb output in the original post it shows SIGINT is supposed to be handled by gdb and not sent to the program.

---

### Post by Mr. C. on 2007-03-09
Apologies - I missed that.  Too fatigued I suppose.

This might best be resolved via any GDB mailing list, or GDB expert's list.

MrC

---

