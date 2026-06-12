---
title: "I suspect GDB isn't working because of no debug info for it"
date: 2018-02-24
forum: Programming Talk
---

### Post by s3a on 2018-02-24
Hello to everyone who's reading this. :)

I'm having trouble debugging a C++ program I'm working on.:

My system is a hybrid of stable, testing, and to a lesser extent, unstable.

_Here is what I believe to be relevant information (in no particular order).:_
```

ldd BinaryOfMyProject
	linux-vdso.so.1 (0x00007ffe253b2000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fdcf4d5b000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fdcf4a10000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fdcf47f8000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fdcf4442000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fdcf52fc000)

```

```

ls -la /usr/lib/debug/usr/lib/libstdc++.so.6.0.22 
lrwxrwxrwx 1 root root 51 Feb 23 23:47 /usr/lib/debug/usr/lib/libstdc++.so.6.0.22 -> /usr/lib/x86_64-linux-gnu/debug/libstdc++.so.6.0.22

```

_The relevant output from GDB:_
```

info locals
theFile = <incomplete type>

```

```

dpkg -l | grep -i libstd
ii  libstdc++-5-dev:amd64                    5.5.0-8                           amd64        GNU Standard C++ Library v3 (development files)
ii  libstdc++-6-dev:amd64                    6.3.0-18+deb9u1                   amd64        GNU Standard C++ Library v3 (development files)
ii  libstdc++-8-dev:amd64                    8-20180218-1                      amd64        GNU Standard C++ Library v3 (development files)
ii  libstdc++6:amd64                         8-20180218-1                      amd64        GNU Standard C++ Library v3
ii  libstdc++6:i386                          8-20180218-1                      i386         GNU Standard C++ Library v3
ii  libstdc++6-6-dbg:amd64                   6.3.0-18+deb9u1                   amd64        GNU Standard C++ Library v3 (debugging files)

```

```

apt-cache search libstdc++ | grep -i dbg
lib32stdc++6-6-dbg - GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-6-dbg - GNU Standard C++ Library v3 (debugging files)
libstdc++6-6-dbg - GNU Standard C++ Library v3 (debugging files)
libx32stdc++6-6-dbg - GNU Standard C++ Library v3 (debugging files)
lib32stdc++6-7-dbg - GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-7-dbg - GNU Standard C++ Library v3 (debugging files)
libstdc++6-7-dbg - GNU Standard C++ Library v3 (debugging files)
libx32stdc++6-7-dbg - GNU Standard C++ Library v3 (debugging files)
lib32stdc++6-8-dbg - GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-8-dbg - GNU Standard C++ Library v3 (debugging files)
libstdc++6-8-dbg - GNU Standard C++ Library v3 (debugging files)
libx32stdc++6-8-dbg - GNU Standard C++ Library v3 (debugging files)
lib32stdc++6-5-dbg - GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-5-dbg - GNU Standard C++ Library v3 (debugging files)
libstdc++6-5-dbg - GNU Standard C++ Library v3 (debugging files)
libx32stdc++6-5-dbg - GNU Standard C++ Library v3 (debugging files)

```

```

apt-cache policy g++
g++:
  Installed: 4:6.3.0-4
  Candidate: 4:6.3.0-4
  Version table:
     4:7.2.0-1d1 475
        475 http://debian.mirror.iweb.ca/debian buster/main amd64 Packages
        450 http://debian.mirror.iweb.ca/debian sid/main amd64 Packages
 *** 4:6.3.0-4 525
        525 http://debian.mirror.iweb.ca/debian stretch/main amd64 Packages
        100 /var/lib/dpkg/status

```

For what it's worth, I'm using the latest Eclipse IDE for C/C++ from upstream.

Also, Eclipse is using g++ with the -g3 flag (which means it has the most verbose debugging compilation mode enabled).

I still keep getting that <incomplete type> output from GDB.

Does anyone know what I'm doing wrong? If so, could you please let me know how to fix my problem?

Any input would be greatly appreciated!

---

### Post by r-senior on 2018-03-03
What level of optimization are you using? What happens if you add -Og to the options?

---

