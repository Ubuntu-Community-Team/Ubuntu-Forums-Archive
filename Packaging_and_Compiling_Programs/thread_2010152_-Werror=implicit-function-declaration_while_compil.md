---
title: "-Werror=implicit-function-declaration while compiling"
date: 2012-06-25
forum: Packaging and Compiling Programs
---

### Post by joblafors on 2012-06-25
Hello, im trying to compile wifi drivers but get some warnings while doing it.

I searched all files for "-Werror=implicit-function-declaration", but cant find it anywhere, how to remove this warning as error thing.

```

home@home-desktop:~/Desktop/compat/compat-wireless-3.2.5-1$ sudo make
make -C /lib/modules/3.2.0-25-generic/build M=/home/home/Desktop/compat/compat-wireless-3.2.5-1 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic'
  CC [M]  /home/home/Desktop/compat/compat-wireless-3.2.5-1/net/wireless/util.o
/home/home/Desktop/compat/compat-wireless-3.2.5-1/net/wireless/util.c: In function ‘cfg80211_change_iface’:
/home/home/Desktop/compat/compat-wireless-3.2.5-1/net/wireless/util.c:810:2: error: implicit declaration of function ‘br_port_exists’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/home/home/Desktop/compat/compat-wireless-3.2.5-1/net/wireless/util.o] Error 1
make[2]: *** [/home/home/Desktop/compat/compat-wireless-3.2.5-1/net/wireless] Error 2
make[1]: *** [_module_/home/home/Desktop/compat/compat-wireless-3.2.5-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic'
make: *** [modules] Error 2

```

Thank you for your help.

---

### Post by steeldriver on 2012-06-25
did you install any build packages before trying the 'make'? the usual recommendation is to install the build-essential meta package which will make sure you get gcc/g++ with all the trimmings

```
apt-get install build-essential
```It kind of looks like 'make' is finding the default 'cc' compiler not gcc

---

### Post by joblafors on 2012-06-25
> **steeldriver said:**
> did you install any build packages before trying the 'make'? the usual recommendation is to install the build-essential meta package which will make sure you get gcc/g++ with all the trimmings

```
apt-get install build-essential
```It kind of looks like 'make' is finding the default 'cc' compiler not gcc

Yes "build-essential" is at newest version.

---

### Post by steeldriver on 2012-06-25
well then I don't know - likely Werror-implicit-function-declaration is enabled by a catch-all warning like -Wall which is why you can't find an explicit reference to it in the makefile

beyond that I can't help - sorry

---

### Post by oldos2er on 2012-06-25
Moved to Packaging and Compiling Programs.

---

### Post by Bachstelze on 2012-06-26
Where does this code come from? Generally, errors when building a driver indicate that the code is not compatible with the kernel version on the system.

---

### Post by joblafors on 2012-06-27
Thank you all for your help and interest in this.
I managed to get this working, and yes Kernel version was one of the problems, but just the first one :)

---

### Post by latebeat on 2013-02-04
> **joblafors said:**
> Hello, im trying to compile wifi drivers but get some warnings while doing it.

I searched all files for "-Werror=implicit-function-declaration", but cant find it anywhere, how to remove this warning as error thing.

```

home@home-desktop:~/Desktop/compat/compat-wireless-3.2.5-1$ sudo make
make -C /lib/modules/3.2.0-25-generic/build M=/home/home/Desktop/compat/compat-wireless-3.2.5-1 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic'
  CC [M]  /home/home/Desktop/compat/compat-wireless-3.2.5-1/net/wireless/util.o
/home/home/Desktop/compat/compat-wireless-3.2.5-1/net/wireless/util.c: In function ‘cfg80211_change_iface’:
/home/home/Desktop/compat/compat-wireless-3.2.5-1/net/wireless/util.c:810:2: error: implicit declaration of function ‘br_port_exists’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/home/home/Desktop/compat/compat-wireless-3.2.5-1/net/wireless/util.o] Error 1
make[2]: *** [/home/home/Desktop/compat/compat-wireless-3.2.5-1/net/wireless] Error 2
make[1]: *** [_module_/home/home/Desktop/compat/compat-wireless-3.2.5-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic'
make: *** [modules] Error 2

```

Thank you for your help.

Hello,

I'm having the exact same complilation error, did you solve it somehow?

---

### Post by MadCow108 on 2013-02-04
the proper solution is to search for the function signature of *br_port_exists* in all the files and dump it into the file that needs it (or include the header that holds the signature)

more can't be said without source

---

### Post by latebeat on 2013-02-05
> **MadCow108 said:**
> the proper solution is to search for the function signature of *br_port_exists* in all the files and dump it into the file that needs it (or include the header that holds the signature)

more can't be said without source

Would you mind explaining that to me a little more?
I'm trying to compile compat-wireless for 12.04 lts like you did from source, and I'm having the exact same error.

[http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.2/](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.2/)

---

