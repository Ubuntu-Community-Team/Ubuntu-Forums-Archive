---
title: "ethernet connection not working"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by pkm2112 on 2012-06-26
My ethernet Atheros AR8162 Fast Ethernet(rev 10)

Ubuntu version is 12.04 64bit

I followed these steps

apt-get upgrade

Downloaded  compat-wireless-2012-05-10.tar.bz2

executed bunzip2 to unzip  tar file

tar -xvf compat-wireless-2012-05-10.tar

scripts/driver-select atl1c
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
Backup exists: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
root@ps-Inspiron-5420:~/compat-wireless-2012-05-10# 

make
make -C /lib/modules/3.2.0-25-generic/build M=/root/compat-wireless-2012-05-10 modules
make[1]: Entering directory `/lib/modules/3.2.0-25-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.2.0-25-generic/build'
make: *** [modules] Error 2


Please help

---

### Post by wildmanne39 on 2012-06-26
Hi try:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
then try to compile again.
Thanks

---

### Post by andriansah on 2012-10-31
> **pkm2112 said:**
> My ethernet Atheros AR8162 Fast Ethernet(rev 10)

Ubuntu version is 12.04 64bit

I followed these steps

apt-get upgrade

Downloaded  compat-wireless-2012-05-10.tar.bz2


Try compat-wireless-2012-02-28-p

./scripts/driver-select alx

make

sudo make install

reboot and plug in your wire network

---

