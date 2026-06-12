---
title: "can't see wirless networks"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by coldascrystal on 2012-11-02
hi my unbuntu cant seem to display  wireless connections it can connect to my old one but i changed routers so i need to change it 

user@user-900:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux user-900 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 i686 i386 GNU/Linux
user@user-900:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. L2 Fast Ethernet [1969:2048] (rev a0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8233]
	Kernel driver in use: atl2
user@user-900:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0951:1606 Kingston Technology Eee PC 701 SD Card Reader [ENE UB6225]
Bus 001 Device 004: ID 05e3:0505 Genesys Logic, Inc. 
Bus 003 Device 003: ID 10c4:81b9 Cygnal Integrated Products, Inc. 
user@user-900:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user@user-900:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

---

### Post by Rezliw on 2012-11-02
Configure new router to use mac address of old router

---

### Post by grahammechanical on 2012-11-02
Do you see this?

> Soft blocked: yes

That means the wireless adapter is turned off by software. Do you have wireless enabled in the Network Manager icon menu? Do you have networking enabled? 

Regards

---

### Post by NikTh on 2012-11-02
> **coldascrystal said:**
> 
user@user-900:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
    **Soft blocked: yes**
    Hard blocked: no

Hi ,

you can try to unblock with this command 

```
sudo rfkill unblock all
``` 
or
```
sudo rfkill unblock wifi
```

Thanks

---

### Post by squakie on 2012-11-02
Did you have MAC filtering on the old router?  If so, be sure you've got the MAC's set correctly.  

Be sure you have matched the security type and pass phrase/passkey correctly.

Can you ping the router?

---

### Post by coldascrystal on 2012-11-03
tanks unblocking works but when i restart its blocked again any idea how to stop it?

---

### Post by NikTh on 2012-11-04
> **coldascrystal said:**
> tanks unblocking works but when i restart its blocked again any idea how to stop it?

This is a workaround and not exactly a solution but you can do you "job". 

Give this command in terminal and it should be smooth. 

```
sudo sed '/^[^#]*exit 0/i (sleep 5;rfkill unblock all)&' -i /etc/rc.local
``` 

Copy-paste the line from here to your terminal and then reboot.

Thanks

---

