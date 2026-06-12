---
title: "hp pavilion dv9700 wifi works but!!!!!"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Priest.Lucard on 2008-08-30
I installed the drivers for the WiFi card in the laptop and it does work but each time i boot the system i have to go into a terminal and type this.

cd /
cd home
cd lucard
cd hybrid_wl
sudo make -C /lib/modules/2.6.24-21-generic/build M=`pwd` clean
sudo make -C /lib/modules/2.6.24-21-generic/build M=`pwd`
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko

Then the WiFI works. 
Does anyone know how i can make it load this each time i boot up so i do not have to keep going in to the terminal.

Ubuntu 8.04 on a 32 bit install
Broadcom Corporation - BCM4322
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by InfinityCircuit on 2008-08-31
Copy the module you have compiled to your /lib/modules/$(uname -r)/misc directory and add it to "/etc/modules" so it will be loaded at boot.

---

### Post by Priest.Lucard on 2008-08-31
> **InfinityCircuit said:**
> Copy the module you have compiled to your /lib/modules/$(uname -r)/misc directory and add it to "/etc/modules" so it will be loaded at boot.

can you give me the list of command to do that. 
Sorry but i am still not good at the commands

I do not have a file or folder called /etc/modules. Do i need to make one?
I do not think i have a Misc folder i did cd /lib/modules/$(uname -r)/misc and i do not have a folder with that name.

---

