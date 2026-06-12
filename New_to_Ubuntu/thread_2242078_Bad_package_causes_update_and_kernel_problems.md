---
title: "Bad package causes update and kernel problems"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by farrinux on 2014-08-30
This morning I saw that there were updates to install. However it wanted to do only a partial upgrade. So I continued until it was done.  I then went to the terminal to see what was going on.  After doing a 

```
sudo apt-get update
``` 

and 

```
sudo apt-get upgrade
``` 

I saw that some packages were being held back.  One was a kernel update and some others.

I checked into the problem and read that I could use 

```
sudo apt-get dist-upgrade
```

I did so and it worked.  However I noticed thare was an error in the kernel upgrade about a package.

```
Error! Bad return status for module build on kernel: 3.13.0-35-generic (x86_64)
Consult /var/lib/dkms/dvbhdhomerun/0.0.16~saucy/build/make.log for more information.
```

The log file says,

```
DKMS make.log for dvbhdhomerun-0.0.16~saucy for kernel 3.13.0-35-generic (x86_64)
Sat Aug 30 08:54:57 CDT 2014
Building driver... ccflags-y=-Idrivers/media/dvb-core -Idrivers/media/frontends -Idrivers/media/dvb/dvb-core -Idrivers/media/dvb/frontends
make -C /lib/modules/`uname -r`/build  M=/var/lib/dkms/dvbhdhomerun/0.0.16~saucy/build modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-34-generic'
  CC [M]  /var/lib/dkms/dvbhdhomerun/0.0.16~saucy/build/dvb_hdhomerun_init.o
/var/lib/dkms/dvbhdhomerun/0.0.16~saucy/build/dvb_hdhomerun_init.c:29:23: fatal error: dvb_demux.h: No such file or directory
 #include "dvb_demux.h"
                       ^
compilation terminated.
make[2]: *** [/var/lib/dkms/dvbhdhomerun/0.0.16~saucy/build/dvb_hdhomerun_init.o] Error 1
make[1]: *** [_module_/var/lib/dkms/dvbhdhomerun/0.0.16~saucy/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-34-generic'
make: *** [dvb_hdhomerun] Error 2
```

I have tried to purge this package with

```
sudo apt-get purge dvbhdhomerun-0.0.16~saucy
```. 

However it errors out with,

```
user@my_comp:~$ sudo apt-get purge dvbhdhomerun-0.0.16~saucy
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dvbhdhomerun-0.0.16~saucy
E: Couldn't find any package by regex 'dvbhdhomerun-0.0.16~saucy'
```

I would like to know how to stop this error on the next kernel update and remove this package.  I know this package was installed in saucy 13.10. I also know that when I upgraded from 13.10 to 14.04 that I had a similar issue with this. dvdhdhomerun is a DVB driver and I suppose that is why I have the trouble on the kernel updates.

---

### Post by Frogs Hair on 2014-08-30
I would install the ppa-purge and try again . The purge will revert the sources list and remove the package/s if not already. There are no 14.04 builds. 

```
sudo apt-get install ppa-purge 
``````

sudo add-apt-repository --remove ppa:someppa/ppa
``` I think the command should look as follows , but I'm not positive .

```
sudo add-apt-repository --remove ppa:tfylliv/dvbhdhomerun/ppa
```

[https://launchpad.net/~tfylliv/+archive/ubuntu/dvbhdhomerun](https://launchpad.net/~tfylliv/+archive/ubuntu/dvbhdhomerun)

---

### Post by sbnwl on 2014-08-30
You might be having broken update:
First complete the update
```
sudo dpkg --configure -a
```

This will try to complete/fix the previous broken update.
If you see nothing thrown on output then you can safely try to update again.

---

### Post by farrinux on 2014-08-30
Thanks Frogs Hair and snbwl

Tried both but the return was.......

```
usr@my_comp:~$ sudo add-apt-repository --remove ppa:tfylliv/dvbhdhomerun/ppa
Cannot add PPA: 'ppa:tfylliv/dvbhdhomerun/ppa'.
Please check that the PPA name or format is correct.
```

That is the correct PPA.

and

```
user@my_comp:~$ sudo dpkg --configure -a
user@my_comp:~$
```

No return. As I said previously the update did go through.


After doing more research I think the problem lies in DKMS.

dvdhdhomerun is a DVB driver and ends up being a module in the kernel I believe.

But since the DKMS compile failed.  It is not listed in the modules nor is it listed as being loaded.
 
How do I keep it from happening again on the next kernel update? 

I do not know what the trigger is for DKMS to try and compile this.  I have tried to delete packages and PPA's  and there is nothing there.

---

### Post by farrinux on 2014-08-30
I hope I found the answer,  After a little more digging.  It seems the answer may be just to delete old linux images.  I had a few and dumped them all to the last three.  I could see during the process where it was deleting this module from the DKMS tree.

---

