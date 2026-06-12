---
title: "ndiswrapper-1.58rc1 will not build on 3.8.0-26"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by jaysnbullfrog on 2013-07-18
Hello,

This is my first post EVER, so bear with me.

I've been poking around bug pages and forums all week and I still can't  seem to get my wifi to work using ndiswrapper.  Ndiswrapper version 1.58  installs fine with no problems except that my wifi will stop after   5-10 minutes. I've had this problem with earlier version of Ndiswrapper.
I have to restart ndiswrapper:
```

sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

```

Only for it to work for another 5-10 minutes

Then  I tried to install the version that has worked for me in the past  (1.58rc1) on Bodhi with 3.4 kernel (If I can remember correctly) and
 I get the following when I try to make.

```
jaysnbullfrog@NEO-Bahamut:~/Downloads/ndiswrapper-1.58rc1$ sudo make
[sudo] password for jaysnbullfrog: 
make -C utils
make[1]: Entering directory `/home/jaysnbullfrog/Downloads/ndiswrapper-1.58rc1/utils'
gcc -g -Wall -I../driver  -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/jaysnbullfrog/Downloads/ndiswrapper-1.58rc1/utils'
make -C driver
make[1]: Entering directory `/home/jaysnbullfrog/Downloads/ndiswrapper-1.58rc1/driver'


Cannot find kernel build files in /usr/src/linux-headers-3.8.0-26-generic
Please give the path to kernel build directory with
the KBUILD=<path> argument to make


make[1]: *** [config_check] Error 1
make[1]: Leaving directory `/home/jaysnbullfrog/Downloads/ndiswrapper-1.58rc1/driver'
make: *** [driver] Error 2
```


Apparently this is a common bug that I cannot seem to find any solution to:
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1106051](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1106051)
i tried the workaround without success.


I'm using Netgear wnda3100v2  wireless usb adapter
with the windows drivers from the disc bcmwlhigh5.inf

If someone could offer me any help it would be HIGHLY apperciated.

---

