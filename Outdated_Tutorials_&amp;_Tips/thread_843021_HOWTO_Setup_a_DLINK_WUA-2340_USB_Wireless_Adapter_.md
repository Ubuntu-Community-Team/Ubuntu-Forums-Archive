---
title: "HOWTO: Setup a DLINK WUA-2340 USB Wireless Adapter in Hardy"
date: 2008-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by orphean on 2008-06-27
So you want to have a working wireless setup in Hardy and you happen to have a D-Link WUA-2340 Wireless USB adapter.  Fear not! For this will give you a nice working setup.

We will be using ndiswrapper to install the driver for the adapter, so we should ensure all components of it are installed:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

Now would be a good time to start to download the driver, grab it from:

[ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip](ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip)

Now unzip the file:
```

cd <directory where you downloaded the zip>
unzip WUA2340_driver_140.zip
```

Now we need to setup ndiswrapper to use the driver we just downloaded.

Firstly, we need to get ndiswrapper itself setup properly.

```
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

The preceding incantation will load the ndiswrapper module and ensure that it loads automatically at startup.  To ensure the module loaded correctly now is a good time to check it:

```
sudo lsmod | grep ndiswrapper
```

You should see a couple of lines with 'ndiswrapper' in them, if you don't then the module did not load correctly. It's beyond the scope of this howto to troubleshoot that issue unfortunately.

Now that ndiswrapper is installed and loaded up we need to install the driver.

```
cd 20071112-WUA-2340-S0026
cd Drivers
cd WinXP_2K
sudo ndiswrapper -i netA5AGU.inf
```

You may get some output stating that it is changing the registers from 256 to 64, this is not an issue and you can safely ignore it.

Now make sure it installed properly:

```
sudo ndiswrapper -l
```

You should see that the driver is installed and the device is present.

Now in a perfect world, you would be done now.  However network-manager in hardy will not display any wireless networks for you to connect to.  Rest assured your wireless adapter is installed and working, the problem is with network-manager.

There are two ways you can go from here.  The first involves setting the wireless network you want to connect to manually (this might be good if you only use your wireless connection at home).  The other choice is to replace network-manager with WICD which does work properly with this setup.
[B]
The Network Administration Method[/B]
[LIST]
[*]Open System->Administration->Network
[*]You should see your wireless connection in the list, click the Unlock button to make changes.
[*]Select your wireless connection and hit the properties button.
[*]Deselect 'Roaming'
[*]Select your wireless network from the list and enter in your WPA/WEP information for the card.
[*]Click ok, and now you have a working wireless connection. Congrats!
[/LIST]

**The WICD Method**
For this method we will install WICD which is an alternative to network-manager that has the benefit of, you know, working with this adapter.

Before you start you should know:
**Installing WICD will remove network-manager and ubuntu-desktop from your system.  This is not an issue for day to day use but ubuntu-desktop MUST be installed for distribution upgrades to work properly (Ie, Hardy->Ibex).  Before you dist-upgrade to Ibex, reinstall the ubuntu-desktop package (this will uninstall WICD).**

Now that the disclaimer is out of the way, lets get going.

We need to add the WICD repository to our sources.list.

```
gksu gedit /etc/apt/sources.list
```

Append the following to the file then Save and close it: 
```
deb http://apt.wicd.net hardy extras 
```

Now update your packages and install WICD:
```
sudo apt-get update
sudo apt-get install wicd
```

You will be prompted if you want to install this package from an unverified repository.  If you wish the installation to proceed, type Yes.

Now that WICD is installed type Alt-F2 and then /opt/wicd/tray.py to launch the tray applet.  Double-clicking the applet will display a list of all wireless networks in range.  Use the dropdown arrow next to your network and enter your encryption key for your network, click connect automatically at start, then click connect. Now you should be connected to your wireless network!

To make the applet load automatically at startup do the following:
[LIST]
[*]System->Preferences->Sessions
[*]Click Add
[*]Enter WICD for the name
[*]Enter /opt/wicd/tray.py for the command
[*]Enter WICD Tray Applet for the description.
[*]Click OK
[*]Click Close
[/LIST]

And that's it!  Hope this HOWTO helped those who are in the same boat as me.

---

### Post by kenfeyl on 2008-07-06
Thanks for the tutorial, but I think it's limited to 32-bit systems. On my amd64 Hardy, it doesn't work. After modprobe'ing, I get a message in my /var/log/syslog telling me that the driver is 32-bit but my system is 64-bit. Any pointers to a 64-bit solution?

---

