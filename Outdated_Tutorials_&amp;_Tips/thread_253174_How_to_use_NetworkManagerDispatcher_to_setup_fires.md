---
title: "How to use NetworkManagerDispatcher to setup firestarter per interface and more..."
date: 2006-09-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Darrena on 2006-09-07
NetworkManager provides a dispatcher that runs everytime an interface state changes, this dispatcher runs every script in alphabetical order in the directory /etc/NetworkManager/dispatcher.d and sends two variables to it, the interface name and the state of the interface (up and down). All scripts are run as root.  The following is a script for NetworkManager that sets the right interface but this can be used as an example to do a lot more such as using whereami to determine location and then mount remote filesystems or have services that are dependent on network connectivity restart.

So using this you can do some great things based on which interface is up or down.

Advanced users will probably want to write their own iptables script and launch it based on interface script but many users would just like Firestarter to run on the correct interface.

This assumes you have two nic's a wired on eth0 and a wireless on eth1, if your interfaces are named differently please change them.

Since the configuration file for firestarter is set to read-only we need copy it out for each interface, make the files writable, edit them to to reference the proper interface, save them and make them read-only again.  We then do the same for the firestarter startup scripts.

First lets create the new configuration files:
```
sudo cp /etc/firestarter/configuration /etc/firestarter/configuration-eth0
sudo cp /etc/firestarter/configuration /etc/firestarter/configuration-eth1

```
Set the files to be writable:
```
sudo chmod +w /etc/firestarter/configuration-eth0
sudo chmod +w /etc/firestarter/configuration-eth1
```

Edit each file so that it references the proper interface:
```
sudo gedit /etc/firestarter/configuration-eth0
```

Edit the file so that the following lines are set to eth0
```
# Name of external network interface
IF="eth0"

# Name of internal network interface
INIF="eth0"
```

Do the same for the other configuration file:
```
sudo gedit /etc/firestarter/configuration-eth1
```

Edit the file so that the following lines are set to eth1
```
# Name of external network interface
IF="eth1"

# Name of internal network interface
INIF="eth1"
```

Finally set the configuration files to read only
```
sudo chmod -w /etc/firestarter/configuration-eth0
sudo chmod -w /etc/firestarter/configuration-eth1
```

Now we need to copy and modify the firestarter.sh startup script:
```
sudo cp /etc/firestarter/firestarter.sh /etc/firestarter/firestarter-eth0.sh
sudo cp /etc/firestarter/firestarter.sh /etc/firestarter/firestarter-eth1.sh
```

Now we modify each script to point to the proper configuration files we created above.
```
sudo gedit /etc/firestarter/firestarter-eth1.sh
```

Modify this line so it points to the proper configuration file that we created earlier:
```
# Load Configuration
source /etc/firestarter/configuration-eth1 2>&1
```

Now we do the same for the other interface script:
```
sudo gedit /etc/firestarter/firestarter-eth0.sh
```

Modify this line so it points to the proper configuration file that we created earlier:
```
# Load Configuration
source /etc/firestarter/configuration-eth0 2>&1

```

ALMOST DONE!  Now we just create the dispatcher script:
```
sudo gedit /etc/NetworkManager/dispatcher.d/firestarter
```

copy and paste the following:
```
#!/bin/bash
if [ $1 == "eth0" ] && [ $2 == "up" ]; then
    /etc/firestarter/firestarter-eth0.sh start
fi

if [ $1 == "eth0" ] && [ $2 == "down" ]; then
    /etc/firestarter/firestarter-eth0.sh stop
fi

if [ $1 == "eth1" ] && [ $2 == "up" ]; then
    /etc/firestarter/firestarter-eth1.sh start
fi

if [ $1 == "eth1" ] && [ $2 == "down" ]; then
    /etc/firestarter/firestarter-eth1.sh stop
fi
```

Set the file to be executable:
sudo chmod +x /etc/NetworkManager/dispatcher.d/firestarter

And you are done!  

Note: If you have Firestarter or the GUI set to start with your system then it will give an error that it cannot find the interface, this is because the interface is not up until you login to Network Manager.

---

### Post by Rob_H on 2006-10-21
This is exactly what I needed. Thanks!

Also gave me a few ideas for customization based on what network I'm connecting to.

---

### Post by headshok on 2007-09-04
Thanks for this, still works great with Feisty...

I added a few things to control what inbound services were allowed for my 3 interfaces.  
Wired eth0
Wireless eth1
Sprint PCS ppp0

I wanted SMB and SSH when eth0 is up, but not for eth1 and ppp0

You'll have to set the permissions on most of the files in /etc/firestarter to u+w to make these modifications... Dont forget to set them back with u-w when your finished!!!

I copied the directory /etc/firestarter/inbound to inbound-eth0 inbound-eth1 inbound-ppp0

Then I removed SSH  and SMB from /etc/firestarter/inbound-eth1/allow-service
(and in the ppp0 dir)

I copied the /etc/firestarter/firewall file into firewall-eth0 firewall-eth1 firewall-ppp0

in each file I modified the 2 lines that referenced /etc/firestarter/inbound to be /etc/firestarter/inbound-eth0 (or eth1, ppp0) 

I modified the line in /etc/firestarter/firestarter-eth0.sh (and eth1.sh ppp0.sh) "reload-inbound-policy" change /etc/firestarter/inbound/setup to be /etc/firestarter/inbound-eth0/setup

Then in each inbound directory I modified the setup file to correspond to the correct interface (there are 2 lines in each file)

You can test it easily by being connected with eth1
sudo /etc/firestarter/firestarter-eth1.sh stop
sudo /etc/firestarter/firestarter-eth1.sh start
then run 
sudo iptables --list and look to see if the SSH is there for eth1

I havent yet figured out how to set the gui to save configuration changes to the correct inbound directories, if anybody has a clue how that could be done I'd appreciate some info. It doesnt even seem to read from the correct directories when it displays under the policy tab.  
Also I shut off "Apply policy changes immediately" in the firestarter preferences to prevent the gui from loading the policy in /etc/firestarter/inbound/setup when you open the gui.

To make changes simply do so in the gui, then just copy the /etc/firestarter/inbound/allow-service allow-from and forward files into the correct inbound(interface) directory. 

This can also be modified for outgoing setups but for my needs that can remain static across the different connections.


Sorry this isnt the best howto but I figured anybody that requires this amount of control over their firewall should be able to get it going from these directions.
Firestarter seems to be quite stubborn with multiple interfaces but its fairly scalable and with a little work its turned out to be a great app for me!

---

### Post by lumitoro on 2008-09-30
> **headshok said:**
> Thanks for this, still works great with Feisty...

I added a few things to control what inbound services were allowed for my 3 interfaces.  
Wired eth0
Wireless eth1
Sprint PCS ppp0

I wanted SMB and SSH when eth0 is up, but not for eth1 and ppp0

You'll have to set the permissions on most of the files in /etc/firestarter to u+w to make these modifications... Dont forget to set them back with u-w when your finished!!!

I copied the directory /etc/firestarter/inbound to inbound-eth0 inbound-eth1 inbound-ppp0

Then I removed SSH  and SMB from /etc/firestarter/inbound-eth1/allow-service
(and in the ppp0 dir)

I copied the /etc/firestarter/firewall file into firewall-eth0 firewall-eth1 firewall-ppp0

in each file I modified the 2 lines that referenced /etc/firestarter/inbound to be /etc/firestarter/inbound-eth0 (or eth1, ppp0) 

I modified the line in /etc/firestarter/firestarter-eth0.sh (and eth1.sh ppp0.sh) "reload-inbound-policy" change /etc/firestarter/inbound/setup to be /etc/firestarter/inbound-eth0/setup

Then in each inbound directory I modified the setup file to correspond to the correct interface (there are 2 lines in each file)

You can test it easily by being connected with eth1
sudo /etc/firestarter/firestarter-eth1.sh stop
sudo /etc/firestarter/firestarter-eth1.sh start
then run 
sudo iptables --list and look to see if the SSH is there for eth1

I havent yet figured out how to set the gui to save configuration changes to the correct inbound directories, if anybody has a clue how that could be done I'd appreciate some info. It doesnt even seem to read from the correct directories when it displays under the policy tab.  
Also I shut off "Apply policy changes immediately" in the firestarter preferences to prevent the gui from loading the policy in /etc/firestarter/inbound/setup when you open the gui.

To make changes simply do so in the gui, then just copy the /etc/firestarter/inbound/allow-service allow-from and forward files into the correct inbound(interface) directory. 

This can also be modified for outgoing setups but for my needs that can remain static across the different connections.


Sorry this isnt the best howto but I figured anybody that requires this amount of control over their firewall should be able to get it going from these directions.
Firestarter seems to be quite stubborn with multiple interfaces but its fairly scalable and with a little work its turned out to be a great app for me!

Fantastic...you can also use this to set up a proxy(using gconftool) for all apps(that use system defined proxy) according to your network SSID by using the "dbus-send" in the script. ex.: "dbus-send --system --dest=org.freedesktop.NetworkManager --print-reply /org/freedesktop/NetworkManager/Devices/eth0 org.freedesktop.NetworkManager.getActiveNetwork |grep NetworkManager | tr -d '" ' | cut -f8 -d/" returns the SSID of the wireless network for the eth0 NIC

---

### Post by misha680 on 2009-09-22
> **lumitoro said:**
> Fantastic...you can also use this to set up a proxy(using gconftool) for all apps(that use system defined proxy) according to your network SSID by using the "dbus-send" in the script. ex.: "dbus-send --system --dest=org.freedesktop.NetworkManager --print-reply /org/freedesktop/NetworkManager/Devices/eth0 org.freedesktop.NetworkManager.getActiveNetwork |grep NetworkManager | tr -d '" ' | cut -f8 -d/" returns the SSID of the wireless network for the eth0 NIC

I am trying this on Jaunty:
```

misha@misha-5101:~/Desktop$ dbus-send --system --dest=org.freedesktop.NetworkManager --print-reply /org/freedesktop/NetworkManager/Devices/eth1 org.freedesktop.NetworkManager.getActiveNetwork |grep NetworkManager 
Error org.freedesktop.DBus.Error.UnknownMethod: Method "getActiveNetwork" with signature "" on interface "org.freedesktop.NetworkManager" doesn't exist

```

but get a weird error. Any ideas?

Thank you
Misha

---

### Post by suilix on 2009-10-14
Here's a single script to ...
```

#!/bin/sh
# Automatically configure firestarter to use the active interface.
# As root...
# 1) Create this script at /etc/NetworkManager/dispatcher.d/02firestarter
# 2) chmod +x /etc/NetworkManager/dispatcher.d/02firestarter
# Note: The numeric prefix can be changed to alter the dispatch order.
if [ $2 = "up" ]; then
	/etc/firestarter/firestarter.sh stop
	sed -i "s/IF=\".*\"/IF=\"$1\"/" /etc/firestarter/configuration
	/etc/firestarter/firestarter.sh start
fi
# vi:set tabstop=4 hardtabs=4 shiftwidth=4:

```

---

