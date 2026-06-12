---
title: "IP alias and NetManager"
date: 2009-09-06
forum: Outdated Tutorials &amp; Tips
---

### Post by tkoco on 2009-09-06
A tip for the Ubuntu community!

I had a need to add a static IP address to an existing NetworkManager controlled network interface. A search on Google turned up conflicting information which did not work correctly. After much testing, I found a stable answer. This tip has been verified on the current Jaunty 9.04 Ubuntu release.

You will need to modify the ```
/etc/network/interfaces
``` file and add a new script to the ```
/etc/NetworkManager/dispatcher.d
``` directory.

The default contents of the "interfaces" file cover only the "lo" interface. To modify the file in a terminal, ```
sudo gedit /etc/network/interfaces
``` and add the following information. Change the IP address information to meet your needs and save the edits. ```
auto lo
iface lo inet loopback

iface eth0:0 inet static
address 192.168.222.215
netmask 255.255.255.0
gateway 192.168.222.1
```

 Now you will need to add a new startup script so that NetworkManager knows about the new IP configuration. ```
sudo gedit /etc/NetworkManager/dispatcher.d/eth-alias
``` Add the following code and save it. ```
#!/bin/bash

iface="$1"
shift

action="$1"
shift

if [ "$iface" = "eth0" -a "$action" = "up" ]; then
/sbin/ifup --force eth0:0
fi
```
Once you finish creating the new script, you will need to make it executable. ```
 sudo chmod 755 /etc/NetworkManager/dispatcher.d/eth-alias
```

With that action finished, you simply stop the NetworkManager via the icon in the top panel of the desktop. And then restart it. To verify that the configuration took hold, in a terminal window, just type in "ifconfig" and Enter. You should see the eth0 and eth0:0 interfaces listed in the output text.

Lastly, this fix is permanent. Reboot your machine and login. Open a terminal window and do "ifconfig" and Enter.

Update:

After reading the Ubuntu Forum policy about outside information, I am giving credit where credit is due. I am listing the two main websites whose information was instrumental in creating this solution.

First was this site: [**This article on NnixCraft website**]("http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html") <- This solution, as written, does not work with NetManager.

And this website: [**This piece written by Mihai Ibanescu**]("http://mihai.ibanescu.net/networkmanager-and-virtual-interfaces") <- This article, as written, is flawed. While the extra interface eth0:0 is created, the assigned IP is a random address.

Combining these two pieces of information becomes the correct solution which I wrote above.

---

