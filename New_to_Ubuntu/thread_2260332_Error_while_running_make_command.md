---
title: "Error while running make command"
date: 2015-01-11
forum: New to Ubuntu
---

### Post by gyan4 on 2015-01-11
I am trying to install Omnet++. After executing ./configure when I am giving make command I am getting following error message:
```
/omnetpp-4.5$ make
make MODE=release
make[1]: Entering directory `/home/gyan/omnetpp-4.5'
***** Configuration: MODE=release, TOOLCHAIN_NAME=gcc, LIB_SUFFIX=.so ****
===== Checking environment =====
===== Compiling utils ====
make[2]: Entering directory `/home/gyan/omnetpp-4.5/src/utils'
Copying scripts to bin directory...
/bin/sh: 1: /home/gyan/omnetpp-4.5/src/utils/install-prog: Permission denied
make[2]: *** [all] Error 126
make[2]: Leaving directory `/home/gyan/omnetpp-4.5/src/utils'
make[1]: *** [utils] Error 2
make[1]: Leaving directory `/home/gyan/omnetpp-4.5'
make: *** [allmodes] Error 2
```

---

### Post by Impavidus on 2015-01-11
I can't say what make is trying to do exactly, but it says it's trying to copy scripts to some bin directory. If this is some sort of system-wide bin directory (like /usr/local/bin, and not /home/user/bin), it needs root permission, which would mean running it as **sudo make**. It's best to first figure out what make is trying to do. Usually make just compiles something, but it seems in this case it also installs it. Running processes as root without knowing what they are supposed to do is a bit dangerous.

---

### Post by nerdtron on 2015-01-11
Probably your make command needs write permissions on the folder /home/gyan/omnetpp-4.5 but since you extracted it (I think) is that the ownership is different.
So in that case:
```
 sudo chown -R gyan:gyan /home/gyan/omnetpp-4.5
```

Be careful with compiling sources and be sure that you know what you are doing.

---

### Post by gyan4 on 2015-01-12
Yes it is extractd and I tryied to execute chown as specified. But even after running chown I am getting same error message!
Need more suggestions

---

### Post by nerdtron on 2015-01-12
Is the file /home/gyan/omnetpp-4.5/src/utils/install-prog executable?

```
chmod +x /home/gyan/omnetpp-4.5/src/utils/install-prog
```

---

### Post by mc4man on 2015-01-12
You might want to take a read thru here - 
[http://www.omnetpp.org/pmwiki/index.php?n=Main.InstallingOnUnix](http://www.omnetpp.org/pmwiki/index.php?n=Main.InstallingOnUnix)

---

### Post by gyan4 on 2015-01-13
Thanx alot nerdtron!!! it worked

---

### Post by sandyd on 2015-01-13
Hi, if you have found a solution to your thread, please mark your thread as [SOLVED] by going to Thread Tools -> Mark Thread as Solved.

Thanks!

---

