---
title: "HOWTO: compile &amp; install madwifi-old/ng without breaking linux-restricted-modules"
date: 2006-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by stanwebber on 2006-01-06
for breezy this howto assumes you have the following packages installed:
build-essential
linux-headers-`uname -r`
gcc-3.4
sharutils (thanks to enodr for reminder)

1. **cd /usr/local/src**

2. **sudo wget [http://snapshots.madwifi.org/madwifi-old-current.tar.gz](http://snapshots.madwifi.org/madwifi-old-current.tar.gz)**
or for madwifi-ng
**sudo wget [http://snapshots.madwifi.org/madwifi-ng-current.tar.gz](http://snapshots.madwifi.org/madwifi-ng-current.tar.gz)**

3. **sudo tar -zxvf madwifi-XX-current.tar.gz**
**cd madwifi-XX-current**
replace XX with old or ng

4. **EXPORT CC=gcc-3.4**
or for madwifi-ng edit madwifi-ng-current/hal/public/i386-elf.inc & change this line:
> CC=    ${TOOLPREFIX}gcc
to this:
> CC=    ${TOOLPREFIX}gcc-3.4

5. **sudo make clean**
**sudo make**

6. **sudo make install**
answer [r]emove to all questions

7. **cd ath_hal**
[B]sudo cp ah_osdep.o /lib/linux-restricted-modules/`uname -r`/ath_hal
sudo cp ath_hal.mod.o /lib/linux-restricted-modules/`uname -r`/ath_hal
sudo cp hal.o /lib/linux-restricted-modules/`uname -r`/ath_hal[/B]

8. [B]cd /lib/modules/`uname -r`
sudo rm -r madwifi
sudo mv net madwifi
sudo rm madwifi/ath_hal.ko[/B]

finish

to undo all of the above:
**sudo apt-get --reinstall linux-restricted-modules-`uname -r`**

---

### Post by kk_davey on 2006-02-19
The Makefile's in madwifi-old releases have accompanying Makefile.kernel's in some directories (e.g. ath/, ath_hal/ etc).  These files have commented out lines for both kernel versions 2.4.x & 2.6.x. I assume it's necessary to uncomment the line specific to your kernel version?

Thanks,
Katie

---

### Post by enodr on 2006-03-18
In order to build the driver you also need the uudecode tool which in the sharutils package. So if you get this error:
```
# make
Checking requirements... FAILED
The 'uudecode' tool was not found on your system. Please make sure
it is installed in your PATH, then try again.
make: *** [sanitycheck] Erreur 1
```
Do:
```
# sudo apt-get install sharutils[PHP][/PHP]
```

---

### Post by stanwebber on 2006-03-29
[QUOTE=kk_davey]I assume it's necessary to uncomment the line specific to your kernel version?[/QUOTE]

i know from practical experience it's not necessary to edit anything for 2.6 kernel...no idea for 2.4 kernel

---

### Post by bl3s5in on 2007-09-26
I tried this with the ng version and 
ah_osdep.o
hal.o 

Do not exist.

---

