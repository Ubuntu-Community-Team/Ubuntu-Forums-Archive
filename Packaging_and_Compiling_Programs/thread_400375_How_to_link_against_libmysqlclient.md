---
title: "How to link against libmysqlclient"
date: 2007-04-03
forum: Packaging and Compiling Programs
---

### Post by bluedalmatian on 2007-04-03
Hi

Im trying to compile a program under GCC which uses the mysqlclient library like this:

g++ -I /usr/include/mysql/ DBTransaction.cpp test.cpp -L /usr/lib -l mysqlclient -lz


According to Synaptic libmysqlclient12 is installed and its .so files appear in /usr/lib but I get this error:

/usr/bin/ld: cannot find -llibmysqlclient12
collect2: ld returned 1 exit status

I'm on 5.04 Hoary Hedgehog.

Thanks in advance. Sorry if this has been asked before but Ive searched round and cant find anything.

Andrew

---

### Post by hod139 on 2007-04-03
You need to install the libmysqlclient12-dev package.  

Also, you should know 5.04 has reached end-of-life, and is no longer being supported.  Ubuntu 5.10 (Breezy Badger) reaches end-of-life April 13th 2007.  You really should consider upgrading at least to 6.06 LTS (Dapper Drake), which will be supported until 2009.

---

### Post by bluedalmatian on 2007-04-03
thanks.  im not sure what the difference is between libmysqlclient12 and libmysqlclient12-dev, except Synaptic says they conflict.

Ive managed to get it working for now by using the following gcc command:

g++ -I /usr/include/mysql/ DBTransaction.cpp test.cpp /usr/lib/libmysqlclient.so.12


Is there a way to install the static library (.a) instead?

I do intend to upgrade as soon as my new dvd drive arrives :lolflag: 

Andrew

---

### Post by WW on 2007-04-05
Static libraries are usually provided by the -dev packages. In this case, libmysqlclient.a is provided by libmysqlclient12-dev.

---

