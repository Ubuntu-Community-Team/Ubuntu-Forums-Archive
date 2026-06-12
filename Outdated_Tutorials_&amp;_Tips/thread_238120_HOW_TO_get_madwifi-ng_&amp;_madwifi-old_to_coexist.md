---
title: "HOW TO: get madwifi-ng &amp; madwifi-old to coexist in dapper linux-restricted-modules"
date: 2006-08-17
forum: Outdated Tutorials &amp; Tips
---

### Post by stanwebber on 2006-08-17
*** please note this method has proved to be VERY UNSTABLE.  at the current time following this guide is a VERY BAD IDEA.  will update if this changes ***

madwifi-ng has already been included in dapper linux-restricted-modules-2.6.15-26; however, in it's current state it's unusable so the system defaults to madwifi-old.  if you want madwifi-ng working NOW (with the ability to switch between old & ng code with a simple reboot) & integrated into the ubuntu package system, ready for future updates, follow this guide

1. install dependancies
```
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install sharutils
```

2. download & extract the fixed source code i uploaded [here]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/54619") to /usr/local/src.  also overwrite ath/if_ath_pci.c to update device id list
```
cd /usr/local/src
sudo wget http://librarian.launchpad.net/3929697/madwifi-ng.tar.gz
sudo wget http://librarian.launchpad.net/3930016/if_ath_pci.c
sudo tar -zxvf madwifi-ng.tar.gz
sudo mv -f if_ath_pci.c /usr/local/src/madwifi-ng/ath
```

3. compile & install the fixed source code.  answer [i]gnore to all questions; otherwise, madwifi-old modules will be removed
```
cd /usr/local/src/madwifi-ng
make clean
make
sudo make install
```

4. source installs modules into lib/modules/'uname -r'/net by default.  linux-restricted-modules-2.6.15-26 uses madwifi-ng.  we need to fix this so the package system can install future updates
```
cd /lib/modules/'uname -r'
sudo rm -r madwifi-ng
sudo mv net madwifi-ng
```

5. because of their closed-source binary-only code linux-restricted-modules-2.6.15-26 handles the ath_hal & new_ath_hal modules in a special way.  both modules are compiled from scratch each & every startup in lib/modules/'uname -r'/volatile which is located on a virtual tmpfs so the final compiled modules never touch your hdd.  we need to replicate this for the package system.  also, we need to remove the compiled new_ath_hal from /lib/modules/'uname -r'/madwifi-ng
```
sudo rm /lib/modules/'uname -r'/madwifi-ng/new_ath_hal.ko
cd /usr/local/src/madwifi-ng/ath
sudo mv -f ah_osdep.o /lib/linux-restricted-modules/`uname -r`/new_ath_hal
sudo mv -f new_ath_hal.mod.o /lib/linux-restricted-modules/`uname -r`/new_ath_hal
sudo mv -f hal.o /lib/linux-restricted-modules/`uname -r`/new_ath_hal
```

6. configure linux-restricted-modules-2.6.15-26 to use either the madwifi-old or madwifi-ng code.  edit /etc/default/linux-restricted-modules-common & add the following line

to use madwifi-ng
```
DISABLED_MODULES="ath_hal"
```
or to use madwifi-old
```
DISABLED_MODULES="new_ath_hal"
```

7. reboot the system & update module dependancies.  this is necessary because the ath_hal or new_ath_hal modules haven't been built yet (only on reboot)
```
depmod -a
```

8. finished.  if you want you can modprobe the ath_pci or new_ath_pci modules now; otherwise, they'll be loaded automatically on each subsequent reboot from now on

to undo all of the above
```
sudo apt-get --reinstall linux-restricted-modules-`uname -r`
```

---

