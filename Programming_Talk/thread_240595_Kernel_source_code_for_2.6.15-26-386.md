---
title: "Kernel source code for 2.6.15-26-386"
date: 2006-08-21
forum: Programming Talk
---

### Post by psylvester on 2006-08-21
Hello, 
Im trying to download the source code for kernel 2.6.15-26-386, however I failed to download.please let me know how can I get the soruce code for my current kernel which is "2.6.15-26-386"

Please see the ERROR Im getting when I complie asterisk programm,

"You do not appear to have the sources for the 2.6.15-26-386 kernel installed."



root@asterisk:/usr/src# sudo apt-get install linux-source-2.6.15
Reading package lists... Done
Building dependency tree... Done
linux-source-2.6.15 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


root@asterisk:/usr/src# sudo apt-get install linux-source-2.6.15-26-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-source-2.6.15-26-386
root@asterisk:/usr/src#


root@asterisk:/usr/src/zaptel-1.2.7# make ZAPTELVERSION="1.2.7" build_tools/make_version_h > version.h.tmp if cmp -s version.h.tmp version.h ; then echo; else \
                mv version.h.tmp version.h ; \
        fi

rm -f version.h.tmp

You do not appear to have the sources for the 2.6.15-26-386 kernel installed.
make: *** [linux26] Error 1
root@asterisk:/usr/src/zaptel-1.2.7#root@asterisk:/usr/src/zaptel-1.2.7#
uname -a
Linux asterisk 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

Thanks,
Prashanth
Blore.

---

### Post by mlind on 2006-08-21
If you're trying to compile a kernel module, install linux-headers-2.6.15-26-386 package instead. Then you should create /usr/src/linux symlink that points to installed kernel headers on /usr/src folder.

---

### Post by psylvester on 2006-08-21
Hi ,

Thanks ! it worked.
sudo apt-get install linux-headers-2.6.15-26-386

Regarding the link, Could you please explain me? I have these many things under /src/

root@asterisk:/usr/src# cd linux-
linux-headers-2.6.15-26/     linux-headers-2.6.15-26-386/ linux-source-2.6.15.tar.bz2
root@asterisk:/usr/src# pwd
/usr/src
root@asterisk:/usr/src#



Thanks in advance,
Sylvester

---

### Post by mlind on 2006-08-21
> **psylvester said:**
> Hi ,

Thanks ! it worked.
sudo apt-get install linux-headers-2.6.15-26-386

Regarding the link, Could you please explain me? I have these many things under /src/

root@asterisk:/usr/src# cd linux-
linux-headers-2.6.15-26/     linux-headers-2.6.15-26-386/ linux-source-2.6.15.tar.bz2
root@asterisk:/usr/src# pwd
/usr/src
root@asterisk:/usr/src#



Thanks in advance,
Sylvester


If you already got the kernel module compiled, then you don't have to do the symlink. If you get erros when trying to compile the module, try
```

sudo ln -s /usr/src/linux-headers-2.6.15-26-386 /usr/src

```

---

