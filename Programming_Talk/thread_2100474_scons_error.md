---
title: "scons error"
date: 2013-01-01
forum: Programming Talk
---

### Post by krksidhu on 2013-01-01
Hi, 

This is K. Rama Krishna Sidhartha,

I have installed opennebula, mysql database in kubuntu 12.04 OS.
While I am executing 

oneadmin@ubuntu:~$ scons mysql=yes

scons: *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/Main.py", line 904, in _main
oneadmin@ubuntu:~$

I also tried without mysql=yes also as follows...
oneadmin@ubuntu:~$ scons

scons: *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/Main.py", line 904, in _main
oneadmin@ubuntu:~$

But I am getting the same error....

May I know the where is the problem and let me know how to resolve it......

Thanking you....

---

### Post by dwhitney67 on 2013-01-02
Just to clarify, scons is a tool for building software.  You are invoking this tool from what appears to be your home directory; I would have expected to see it invoked within a directory containing the contents of a source-code package.

I know that MySQL can be installed from the Synaptics Repository (thus no need to build it from source).  As for OpenNebula, this too can be obtained from Synaptics.

Thus I'm not quite certain there is a need to build anything, unless of course you are attempting to use bleeding-edge releases of these products.

---

