---
title: "Compiling Pyflag on Ubuntu 10.04"
date: 2010-05-31
forum: Programming Talk
---

### Post by felixdzerzhinsky on 2010-05-31
Pyflag will not ```
make install
``` 

I get the following error:

 ```
test -z "/usr/local/share/pyflag" || /bin/mkdir -p "/usr/local/share/pyflag"
 /usr/bin/install -c -m 644 data/magic data/regexps.txt data/magic.mime data/regkeys.txt data/magic.mime.mgc data/magic.mgc data/magic.mgc data/magic.mime.mgc images/changelog.html '/usr/local/share/pyflag'
/usr/bin/install: will not overwrite just-created `/usr/local/share/pyflag/magic.mgc' with `data/magic.mgc'
/usr/bin/install: will not overwrite just-created `/usr/local/share/pyflag/magic.mime.mgc' with `data/magic.mime.mgc'
make[2]: *** [install-pkgdataDATA] Error 1
make[2]: Leaving directory `/home/felixdz/forensics/pyflag_0'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/felixdz/forensics/pyflag_0'
make: *** [install-recursive] Error 1
felixdz@gUN:~/forensics/pyflag_0$ 

```

What is going wrong?

This is how to install pyflag

[http://www.pyflag.net/cgi-bin/moin.cgi/HowToInstall](http://www.pyflag.net/cgi-bin/moin.cgi/HowToInstall)

---

### Post by Can+~ on 2010-05-31
```
sudo make install
```

---

### Post by felixdzerzhinsky on 2010-06-01
> **Can+~ said:**
> ```
sudo make install
```

I already sudo'ed.

Same error.

---

### Post by dwhitney67 on 2010-06-01
> **felixdzerzhinsky said:**
> 
Same error.
Did you type this statement yourself, or did it come from a script?
```

/usr/bin/install -c -m 644 data/magic data/regexps.txt data/magic.mime data/regkeys.txt data/magic.mime.mgc data/magic.mgc data/magic.mgc data/magic.mime.mgc images/changelog.html '/usr/local/share/pyflag'

```
Two of the files (ie the ones which install complains about) are specified twice.  Don't do that!

The files that are specified twice are:
[LIST]
[*]data/magic.mime.mgc
[*]data/magic.mgc
[/LIST]

---

### Post by Skinner_au on 2010-07-30
I'm having a similar problem here. My ubuntu-fu is exhausted :\

```

sudo make install
[sudo] password for aresadmin: 
Making install in src
make[1]: Entering directory `/home/aresadmin/Downloads/pyflag-0.87-pre1/src'
Making install in lib
make[2]: Entering directory `/home/aresadmin/Downloads/pyflag-0.87-pre1/src/lib'
Making install in .
make[3]: Entering directory `/home/aresadmin/Downloads/pyflag-0.87-pre1/src/lib'
make[4]: Entering directory `/home/aresadmin/Downloads/pyflag-0.87-pre1/src/lib'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'sgzip' '/usr/local/bin/sgzip'
/usr/bin/install -c sgzip /usr/local/bin/sgzip
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'evtool' '/usr/local/bin/evtool'
/usr/bin/install -c evtool /usr/local/bin/evtool
gcc -shared  -I/usr/include/python2.6 -I../../src/include -L -lpython2.6 -o pypacket.so pypacket.c .libs/pypacket.a -lssl -lcrypto  -lssl -lcrypto      -L/usr/lib -lz -lpthread -ldl  -lutil 
In file included from /usr/include/python2.6/Python.h:8,
                 from ../../src/include/pypacket.h:4,
                 from pypacket.c:8:
/usr/include/python2.6/pyconfig.h:1031:1: warning: "_POSIX_C_SOURCE" redefined
In file included from /usr/include/string.h:26,
                 from ../../src/include/misc.h:37,
                 from ../../src/include/packet.h:76,
                 from pypacket.c:7:
/usr/include/features.h:210:1: warning: this is the location of the previous definition
pypacket.c:323: warning: initialization from incompatible pointer type
/usr/bin/ld: cannot find -lssl
collect2: ld returned 1 exit status
make[4]: *** [pypacket.so] Error 1
make[4]: Leaving directory `/home/aresadmin/Downloads/pyflag-0.87-pre1/src/lib'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/aresadmin/Downloads/pyflag-0.87-pre1/src/lib'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/aresadmin/Downloads/pyflag-0.87-pre1/src/lib'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/aresadmin/Downloads/pyflag-0.87-pre1/src'
make: *** [install-recursive] Error 1

```

---

### Post by Zugzwang on 2010-07-30
> **Skinner_au said:**
> I'm having a similar problem here. My ubuntu-fu is exhausted :\


Actually, the error is here:
```

/usr/bin/ld: cannot find -lssl

```

the lines before were just warnings.

This warning tells you this some library file for the library named "ssl" could not be found during the linking phase. In Ubuntu, for compiling programs using some library, you also need to install the "-dev" package for that library. So go and install the "libssl-dev" package and try again.

---

### Post by dankdave on 2011-05-18
> **Zugzwang said:**
> Actually, the error is here:
```

/usr/bin/ld: cannot find -lssl

```

the lines before were just warnings.

This warning tells you this some library file for the library named "ssl" could not be found during the linking phase. In Ubuntu, for compiling programs using some library, you also need to install the "-dev" package for that library. So go and install the "libssl-dev" package and try again.

Thanks for the tip.  I came across this post while trying to install mpi4py:

[http://mpi4py.scipy.org/docs/usrman/install.html](http://mpi4py.scipy.org/docs/usrman/install.html)

The error I was getting said:

```

/usr/bin/ld: cannot find -lssl
collect2: ld returned 1 exit status

```

and installing libssl-dev fixed the problem.

---

### Post by Skinner_au on 2011-05-18
Wow I dont even remember posting this, but I do seem to remember getting PyFlag working, so I assume your tip worked for me too.

Thanks

---

