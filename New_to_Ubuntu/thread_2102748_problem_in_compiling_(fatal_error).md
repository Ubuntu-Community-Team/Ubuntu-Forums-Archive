---
title: "problem in compiling (fatal error)"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by haresh chavda on 2013-01-08
dear all , i'm have installed vm ware on my windows xp (32bit) machine.
then i have installed ubuntu 12.04LTS in that. it is working fine.
now i want to run beaglebone with this.

it requires to install FTDI ,USB to serial driver.
i have downloaded it from site : [http://www.jayconsystems.com/em-18-rfid-reader.html](http://www.jayconsystems.com/em-18-rfid-reader.html)
it is in ".tar.gz" format.
i have extracted this with "tar -xzvf " in "/usr/local/src/"
and run "make".

but it gives fatal error

> h@ubuntu:/usr/local/src/ftdi_sio$ make
gcc -Wall -D__KERNEL__ -DMODULE -I/lib/modules/3.2.0-29-generic-pae/build/include -D__SMP__ -DSMP -DMODVERSIONS -include /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h -I/usr/src/linux-3.2.0-29-generic-pae/drivers/usb/serial/ -O   -c -o ftdi_sio.o ftdi_sio.c
cc1: fatal error: /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h: No such file or directory
compilation terminated.
make: *** [ftdi_sio.o] Error 1please let me know how to install this driver.
driver folder only contains following files,

> h@ubuntu:/usr/local/src/ftdi_sio$ ls
ftdi_sio.c  ftdi_sio.h  Makefile  Rules.makeit does not have config file or *.sh file.

---

### Post by steeldriver on 2013-01-08
Is there a README file in the archive? if so did you follow the instructions there?

It looks like you don't have the linux-headers package that is needed for the compilation

```
sudo apt-get install linux-headers-$(uname -r)
```There may be other issues though

---

### Post by haresh chavda on 2013-01-08
> **steeldriver said:**
> Is there a README file in the archive? if so did you follow the instructions there?

It looks like you don't have the linux-headers package that is needed for the compilation

```
sudo apt-get install linux-headers-$(uname -r)
```There may be other issues though

hi , i dont have readme file in that folder.
it only contais this files,
> h@ubuntu:/usr/local/src/ftdi_sio$ ls
ftdi_sio.c  ftdi_sio.h  Makefile  Rules.make


i have run this command ,following is my out put.
> h@ubuntu:/usr/local/src/ftdi_sio$ sudo apt-get install linux-headers-$(uname -r)[sudo] password for h: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-29-generic-pae is already the newest version.
linux-headers-3.2.0-29-generic-pae set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 272 not upgraded.
please suggest any thing else..

---

### Post by cdaringe2 on 2014-01-06
I have this same issue.  I have inspected my /lib/modules folders and have done a find command on it without success!  Subscribing.  Will update if I find a solution!

---

### Post by Yellow Pasque on 2014-01-06
I see some suggestions of simply commenting out the lilne that tries to include that file.

---

### Post by cdaringe2 on 2014-01-06
So, after some additional googling, it became clear that I shouldn't have to install this driver after-the-fact as the FTDI support is already bundled in (I'm running kUbu 12.X, 3.2.0-57/58).  When plugging my board in, I do a lsusb, and clearly see it listed.  Sure enough, I restarted my machine later that night, and suddenly my board was visible.
Don't get it.  I changed nothing, and didn't install the driver.  It works now.  Good luck man.

---

### Post by Yellow Pasque on 2014-01-06
> **cdaringe2 said:**
> Good luck man.

Thanks

---

