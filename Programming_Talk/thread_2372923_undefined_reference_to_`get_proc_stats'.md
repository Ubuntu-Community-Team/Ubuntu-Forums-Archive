---
title: "undefined reference to `get_proc_stats'"
date: 2017-09-30
forum: Programming Talk
---

### Post by slymaximus on 2017-09-30
Trying to obtain the parent process PID of a process I tried using get_proc_stats() of proc/readproc.h from libprocps-dev / libprocps3-dev / libprocps4-dev (depending on installing distribution) but each time while I am compiling with g++ or gcc I got 
```
testprocs.cpp:(.text+0x114): undefined reference to `get_proc_stats'
```
even if I installed  this libprocps library.

I have no idea what should I do to fix this issue (tested on Raspbian OS and Bash Ubuntu on Windows10).
One of the examples I tried is here.
[https://github.com/zedtux/test_libprocps/blob/master/main.cpp](https://github.com/zedtux/test_libprocps/blob/master/main.cpp)

---

### Post by slymaximus on 2017-09-30
I tried to compile that file expliciting calling the shared library but unfortunately is not working.
```
g++ -std=c++11 -L/usr/lib/arm-linux-gnueabihf -llibprocps testprocs.cpp -o myprog -fpermissive
```


Trying to figure out where was searching for the lib:
```

ld -lzlib --verbose
==================================================
attempt to open //usr/arm-linux-gnueabihf/lib/libibprocps.so failed
attempt to open //usr/arm-linux-gnueabihf/lib/libibprocps.a failed
attempt to open //usr/local/lib/arm-linux-gnueabihf/libibprocps.so failed
attempt to open //usr/local/lib/arm-linux-gnueabihf/libibprocps.a failed
attempt to open //usr/local/lib/libibprocps.so failed
attempt to open //usr/local/lib/libibprocps.a failed
attempt to open //lib/arm-linux-gnueabihf/libibprocps.so failed
attempt to open //lib/arm-linux-gnueabihf/libibprocps.a failed
attempt to open //lib/libibprocps.so failed
attempt to open //lib/libibprocps.a failed
attempt to open //usr/lib/arm-linux-gnueabihf/libibprocps.so failed
attempt to open //usr/lib/arm-linux-gnueabihf/libibprocps.a failed
attempt to open //usr/lib/libibprocps.so failed
attempt to open //usr/lib/libibprocps.a failed
ld: cannot find -libprocps

```


But it didn't find it even if it is there:
```

$ ldconfig -p | grep libprocps
        libprocps.so.3 (libc6,hard-float) => /lib/arm-linux-gnueabihf/libprocps.so.3
        libprocps.so (libc6,hard-float) => /usr/lib/arm-linux-gnueabihf/libprocps.so

```
It's late, I am tired and I might miss something. In case you see what's I'm doing wrong please let me know.&#65532; Ubuntu, Linux and OS Chat&#65532; The Cafe&#65532; Market&#65532; Mobile Technology Discussions&#65532; Announcements & News&#65532; Weekly Newsletter&#65532; Membership Applications&#65532; The Fridge Discussions&#65532; Forum Council Agenda&#65532; Forum Fe

---

### Post by spjackson on 2017-09-30
I can't solve your intial problem. However, [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=731959](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=731959) suggests that get_proc_stats changed from public to private some time back, but you'll need to follow up on that yourself.

> **slymaximus said:**
> I tried to compile that file expliciting calling the shared library but unfortunately is not working.
```

g++ -std=c++11 -L/usr/lib/arm-linux-gnueabihf -llibprocps testprocs.cpp -o myprog -fpermissive

```

but this is plain wrong in 2 respects.
[LIST=1]
[*]The library must come after testprocs.cpp. 
[*]It is correctly written as -lprocps without the 'lib'. The way you have written it will look for liblibprocps.a or liblibprocps.so. 
[/LIST]

---

### Post by slymaximus on 2017-10-02
> **spjackson said:**
> 
but this is plain wrong in 2 respects.
[LIST=1]
[*]The library must come after testprocs.cpp.
[*]It is correctly written as -lprocps without the 'lib'. The way you have written it will look for liblibprocps.a or liblibprocps.so.
[/LIST]

Thank you for clarifications! This time seems fine
```

g++ -std=c++11 testprocs.cpp -L/usr/lib/arm-linux-gnueabihf -lprocps -o myprog -fpermissive

```
so it seems fine
```

attempt to open //usr/lib/arm-linux-gnueabihf/libprocps.so succeeded
-lprocps (//usr/lib/arm-linux-gnueabihf/libprocps.so)
libdl.so.2 needed by //usr/lib/arm-linux-gnueabihf/libprocps.so
found libdl.so.2 at //lib/arm-linux-gnueabihf/libdl.so.2
libc.so.6 needed by //usr/lib/arm-linux-gnueabihf/libprocps.so
found libc.so.6 at //lib/arm-linux-gnueabihf/libc.so.6
ld-linux-armhf.so.3 needed by //usr/lib/arm-linux-gnueabihf/libprocps.so
found ld-linux-armhf.so.3 at //lib/arm-linux-gnueabihf/ld-linux-armhf.so.3
ld: warning: cannot find entry symbol _start; defaulting to 00010104

```

And indeed, this method seems not to be public anymore.
```

$ nm -D /usr/lib/arm-linux-gnueabihf/libprocps.so | grep get_
         U __ctype_get_mb_cur_max
00007a5c T get_ns_id
00007a34 T get_ns_name
0000ae5c T get_pid_digits
00009710 T get_slabinfo

```
Where the hack should I find it or do really exist other methods to get parent PID of an existing external process? This is trivial on Windows...

---

### Post by slymaximus on 2017-10-02
Tested on an ubuntu server with libprocps4-dev and the same results... 
```

silviu@ubuntu-server:~$ g++ -std=c++11 testprocs.cpp -L/usr/lib/x86_64-linux-gnu -lprocps -o myprog -fpermissive
/tmp/ccwAwP1a.o: In function `main':
testprocs.cpp:(.text+0x114): undefined reference to `get_proc_stats'
collect2: error: ld returned 1 exit status
silviu@ubuntu-server:~$ nm -D /usr/lib/x86_64-linux-gnu/libprocps.so | grep get_
                 U __ctype_get_mb_cur_max
00000000000096d0 T get_ns_id
00000000000096b0 T get_ns_name
000000000000ccc0 T get_pid_digits
000000000000b5c0 T get_slabinfo
                 U sd_pid_get_machine_name
                 U sd_pid_get_owner_uid
                 U sd_pid_get_session
                 U sd_pid_get_slice
                 U sd_pid_get_unit
                 U sd_pid_get_user_unit
                 U sd_session_get_seat

```

---

### Post by norobro on 2017-10-02
> **slymaximus said:**
> or do really exist other methods to get parent PID of an existing external process? [COLOR=#000000]This is trivial on Windows..[/COLOR]It's trivial on Linux, too. Message #35  in the link spjackson supplied has the answer:```
#include <iostream>
#include <cstring>
#include <cstdlib>
#include <proc/readproc.h>


using std::cout;


int main (int argc, char* argv[])
{
    if(argc > 1)
    {
        int pid = (pid_t) atoi(argv[1]);
        proc_t proc_info;
        memset(&proc_info, 0, sizeof(proc_info));
        PROCTAB *pt_ptr = openproc(PROC_FILLSTATUS | PROC_PID, &pid);
        if(readproc(pt_ptr, &proc_info) != 0) {
            cout << "Program: " << proc_info.cmd;
            cout << "\tPID: " << proc_info.tid;
            cout << "\tPPID: " << proc_info.ppid << "\n";
        } else {
            cout << "PID not found\n";
        }
        closeproc(pt_ptr);
    } else {
        cout << "Usage: " << argv[0] << " <PID>\n";
    }
    return 0;
}
```

---

### Post by slymaximus on 2017-10-02
Thanks, I'll try!

---

### Post by slymaximus on 2017-10-02
It works. Thanks!

---

### Post by norobro on 2017-10-02
You're welcome!

---

