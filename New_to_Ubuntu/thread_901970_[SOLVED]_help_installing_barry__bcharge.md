---
title: "[SOLVED] help installing barry / bcharge"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by adobrakic on 2008-08-26
I've already made a thread about this before, which helped me, but now i'm trying to install this on Linux Mint. I'm using the same instructions as the ones i did on Ubuntu, and everything works until i try to do 'sudo make install,' which gives me:

```
ado@ado-desktop ~/Desktop/barry-0.13 $ sudo make install
Making install in .
make[1]: Entering directory `/home/ado/Desktop/barry-0.13'
rm -f ./barry
ln -s ./src ./barry
make[2]: Entering directory `/home/ado/Desktop/barry-0.13'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pkgconfig" || mkdir -p -- "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'libbarry-0.pc' '/usr/local/lib/pkgconfig/libbarry-0.pc'
make[2]: Leaving directory `/home/ado/Desktop/barry-0.13'
make[1]: Leaving directory `/home/ado/Desktop/barry-0.13'
Making install in src
make[1]: Entering directory `/home/ado/Desktop/barry-0.13/src'
source='time.cc' object='time.lo' libtool=yes \
	DEPDIR=.deps depmode=none /bin/bash ../depcomp \
	/bin/bash ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I..    -ansi -Wall -fno-strict-aliasing -g   -c -o time.lo time.cc
libtool: ignoring unknown tag CXX
mkdir .libs
 g++ -DHAVE_CONFIG_H -I.. -ansi -Wall -fno-strict-aliasing -g -c time.cc  -fPIC -DPIC -o .libs/time.o
../libtool: line 1281: g++: command not found
make[1]: *** [time.lo] Error 1
make[1]: Leaving directory `/home/ado/Desktop/barry-0.13/src'
make: *** [install-recursive] Error 1
ado@ado-desktop ~/Desktop/barry-0.13 $ 

```

I don't get what the problem is.

---

### Post by fdesign on 2008-08-26
I think you don't have g++ installed

I would suggest you do this:

```

sudo apt-get build-essential
```

and then try again.

---

### Post by adobrakic on 2008-08-27
```

ado@ado-desktop ~ $ sudo apt-get build-essential
[sudo] password for ado: 
E: Invalid operation build-essential
ado@ado-desktop ~ $ 

```

:[

---

### Post by patrickballeux on 2008-08-27
You forgot the "install" command in your line...

the complete line would be :

**sudo apt-get install build-essential**

Good luck!

---

### Post by adobrakic on 2008-08-27
Wow, sorry, I didn't even realize.
I feel dumb :X! Thanks :D

---

