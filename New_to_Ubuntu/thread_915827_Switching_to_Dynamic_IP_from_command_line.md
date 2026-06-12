---
title: "Switching to Dynamic IP from command line"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by wibbleberry on 2008-09-10
I have an ubuntu server set up without a GUI and need to switch it from static to dynamic IP from the command line. I cannot download any packages as it was configured on a different router to the one I am using now. If it is more complicated than a few settings changes in config files I will have to make other arrangements. Anyone have a set of commands that can do this?

---

### Post by Titan8990 on 2008-09-10
```
jordan@bourne:~$ cat /etc/network/interfaces
\# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth0 inet manual
```


Change the word "manual" to "dhcp" under the interface you would like to change in the file /etc/network/interfaces

---

### Post by wibbleberry on 2008-09-10
Brilliant. Had to go brush up on vi. Ta vm.

---

### Post by dcommini on 2010-09-14
> **Titan8990 said:**
> ```
jordan@bourne:~$ cat /etc/network/interfaces
\# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth0 inet manual
```
Change the word "manual" to "dhcp" under the interface you would like to change in the file /etc/network/interfaces


Thank you for this! I changed mine over to static ip and lost my internet connection, switching back to dynamic helped.

---

### Post by pricetech on 2010-09-14
> **wibbleberry said:**
> Brilliant. Had to go brush up on vi. Ta vm.

nano is simpler.

---

