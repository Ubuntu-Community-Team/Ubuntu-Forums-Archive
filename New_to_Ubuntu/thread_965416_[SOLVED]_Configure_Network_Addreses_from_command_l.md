---
title: "[SOLVED] Configure Network Addreses from command line!"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-10-31
Hello, anyone can help me in how to configure the network addresses like
ip, dns, gateway, mask, from command line without using the gui interface?

Thanks

---

### Post by Titan8990 on 2008-10-31
DNS I am not sure about but assigning a static IP is easy.I have already wrote a guide for it that I will copy and paste here.

Before I begin I would like to make any readers aware that this guide is Debian (and its derivatives) specific. This means that you will not be able to go in Slackware or RHEL and expect files mentioned in this guide to exist because they will not.

This guide will show you how a static IP address is set up. It is a fairly simple processes so lets get started.


[edit] Setting the Static IP

The file that contains the configurations for your network interfaces is located at /etc/network/interfaces. Here is an example of the default configuration of that file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```



As you can see each interface is represented by two lines. The first one indicates whether or not the interface will activate automatically or manually. The above configuration automatically brings up the eht0 interface whenever a) the computer is rebooted b) networking is restarted. Here is an example of manual and automatic setups:

Automatic:

auto eth0

Manual:

manual eth0

Whenever a interface is set to manual this means that it must be started with the command "sudo ifconfig INTERFACE up".
Now, moving along to the second line of the interface. This will determine if your network address is acquired via DHCP or statically set. In the above example (default) it is set to dhcp indicated by the dhcp at the end of the line. In order to get a static address we will change "dhcp" to "static". Then we will have three new lines. These lines will be, in order: IP address, subnet mask, default gateway.

I am a big fan of examples, so lets have a look:

DHCP:

iface eth0 inet dhcp

Static:

iface eth0 inet static

address 192.168.192.24

netmask 255.255.255.0

gateway 192.168.192.1

Once you have made the change then you must restart networking. This is done with the following command:

sudo /etc/init.d/networking restart 


So complete it would look like this:

auto eth0
iface eth0 inet static
address 192.168.192.24
netmask 255.255.255.0
gateway 192.168.192.1

---

### Post by dolman25 on 2008-10-31
cd into /etc/network/ in there is the config file called interfaces
to access and change the config settings type
sudo nano interfaces

---

### Post by Sarmacid on 2008-10-31
To quickly make the changes
```
sudo ifconfig <interface> <ip> netmask <netmask>
```

That won't be preserved if you reboot.

To set a new gateway
```
route add
```
Not sure about the exact syntax after that, but you can search for it or use man route.

To set DNS, you have to modify a text file
```
sudo nano /etc/resolv.conf
```

Add the server's ip like this
```
nameserver <ip>
```

---

### Post by drakeman007 on 2008-10-31
Awesome help guys! everyting works, sorry i dont want to use the gui that much, the gui is easy, i want something more advance then i use the gui hehehe..
thanks.

---

### Post by Balachmar on 2008-11-10
Just to inform:
A fix is found in:
[http://ubuntuforums.org/showthread.php?p=6049183](http://ubuntuforums.org/showthread.php?p=6049183)

and that is far easier then the fixes mentioned in this thread. also enables you to still use network manager.

---

