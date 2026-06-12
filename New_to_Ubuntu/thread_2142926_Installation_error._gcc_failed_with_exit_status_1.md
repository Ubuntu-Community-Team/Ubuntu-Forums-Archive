---
title: "Installation error. gcc failed with exit status 1"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by kramer65 on 2013-05-07
I want to install a Python module (gevent) using the command below, which leads to the error belows. I don't understand why it leads to a gcc error. As far as I know gcc is installed.

Does anybody know what's wrong here?

```
kramer@kramer-P5K:~$ sudo pip install gevent
[sudo] password for kramer: 
Downloading/unpacking gevent
  Running setup.py egg_info for package gevent
    
Downloading/unpacking greenlet (from gevent)
  Running setup.py egg_info for package greenlet
    
Installing collected packages: gevent, greenlet
  Running setup.py install for gevent
    building 'gevent.core' extension
    gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.7 -c gevent/core.c -o build/temp.linux-i686-2.7/gevent/core.o
    In file included from gevent/core.c:253:0:
    gevent/libevent.h:9:19: fatal error: event.h: File or folder does not exist
    compilation terminated.
    error: command 'gcc' failed with exit status 1
    Complete output from command /usr/bin/python -c "import setuptools;__file__='/home/kramer/build/gevent/setup.py';exec(compile(open(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --single-version-externally-managed --record /tmp/pip-vjwW2k-record/install-record.txt:
    running install

running build

running build_py

running build_ext

building 'gevent.core' extension

gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.7 -c gevent/core.c -o build/temp.linux-i686-2.7/gevent/core.o

In file included from gevent/core.c:253:0:

gevent/libevent.h:9:19: fatal error: event.h: File or folder does not exist.

compilation terminated.

error: command 'gcc' failed with exit status 1

----------------------------------------
Command /usr/bin/python -c "import setuptools;__file__='/home/kramer/build/gevent/setup.py';exec(compile(open(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --single-version-externally-managed --record /tmp/pip-vjwW2k-record/install-record.txt failed with error code 1
Storing complete log in /home/kramer/.pip/pip.log
```

---

### Post by kramer65 on 2013-05-07
Nevermind. Just found the answer. I had to install libevent-dev like so:

apt-get install libevent-dev

---

