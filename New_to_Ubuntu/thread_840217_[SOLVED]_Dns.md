---
title: "[SOLVED] Dns"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by agent-orange on 2008-06-25
I am still new to all this.
I am using Xubuntu 7.04 and on the System - Network screen and then the DNS tab it shows an address of 192.168.1.1 (Which is correct for my router). When it is set to this I can not get online but if I add 62.24.199.13 which is my ISP's DNS server the internet works.  Unfortunatly after a while this resets its self to only having 192.168.1.1.

Is there a way a can change this, maybe CLI, so that it is set with the correct DNS address and not change.

Thanks in advance.
D

---

### Post by wormser on 2008-06-25
You can use this [guide]("https://www.opendns.com/start/ubuntu.php") to add your ISPs DNS or use the OpenDNS servers.  Another option is to put the DNS address in your router.

> To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:[INDENT]    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
$ sudo ifdown eth0 && sudo ifup eth0 [/INDENT]You may be required to change eth0 to your own network device's name if it uses a non-standard name.


---

