---
title: "[Dahdi] Installation error"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by bsubramanian on 2014-07-01
**Ubuntu 12.04 (Precise)**


**root@li100-34:/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1#** make
make -C linux all
make[1]: Entering directory `/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1/linux'
make -C drivers/dahdi/firmware firmware-loaders
make[2]: Entering directory `/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1/linux/drivers/dahd
i/firmware'
make[2]: Leaving directory `/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1/linux/drivers/dahdi
/firmware'
You do not appear to have the sources for the 3.2.0-65-virtual kernel installed.
make[1]: *** [modules] Error 1
make[1]: Leaving directory `/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1/linux'
make: *** [all] Error 2


**root@li100-34:/usr/src#** uname -r
3.2.0-65-virtual


**root@li100-34:/usr/src#** dpkg -l | grep linux-headers
ii linux-headers-3.2.0-65 3.2.0-65.98 Header files related
to Linux kernel version 3.2.0
ii linux-headers-3.2.0-65-generic 3.2.0-65.98 Linux kernel headers
for version 3.2.0 on 64 bit x86 SMP
ii linux-headers-3.2.0-65-virtual 3.2.0-65.98 Linux kernel headers
for version 3.2.0 on 64 bit x86 Virtual Guests
ii linux-headers-generic 3.2.0.65.77 Generic Linux kernel
headers
ii linux-headers-virtual 3.2.0.65.77 Linux kernel headers
for virtual machines
**root@li100-34:/usr/src# **


**root@li100-34:/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1#** make clean
make -C linux clean
make[1]: Entering directory `/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1/linux'
make -C drivers/dahdi/firmware clean
make[2]: Entering directory `/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1/linux/drivers/dahd
i/firmware'
rm -f dahdi-fw-*.o
make[2]: Leaving directory `/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1/linux/drivers/dahdi
/firmware'
make -C /lib/modules/3.2.0-65-virtual/build M='/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1/
linux/drivers/dahdi/oct612x' clean
make: Entering an unknown directory
make: *** /lib/modules/3.2.0-65-virtual/build: No such file or directory. Stop.
make: Leaving an unknown directory
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/usr/src/dahdi-linux-complete-2.9.1.1+2.9.1/linux'
make: *** [clean] Error 2


Can anyone please help me on this issue? I need to fix this within today 


Thanks
Bala

---

### Post by bsubramanian on 2014-07-01
Is there anyone for me to reply?

Thanks in advance :)
Bala

---

### Post by sandyd on 2014-07-01
Dahdi already exists in the repos - you dont need to compile it

You can install it with
```

sudo apt-get install dahdi-linux dahdi-dkms
```

Most of the time, it is better to install applications from the repositories because the repositories provide regular bug and security updates to the packages.

---

