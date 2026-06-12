---
title: "HOW TO: Configure vpn client 4.8 in Ubuntu 6.10"
date: 2006-11-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Laalitha on 2006-11-12
I am a total newbie to linux and ubuntu. After installing ubuntu edgy eft I strugled a few weeks to get the cisco vpnclient 4.8 to work. I couldn't do without it since my campus network required to use it.

I read a few howtos and got it working finally

So here goes

Before doing anything logon as super user. It makes things easy.

FIRST install network-manager-gnome and the pptp plugin
========================================================

You can do this in various ways through synaptic, automatix, or apt-get.

here's the apt-get commands

```

apt-get install network-manager-gnome 
apt-get install network-manager-pptp 

```

When you do this the network manager applet will start to run in your system tray. It has a similar icon to your network monitor icon. And it will appear beside it

SECOND Go and edit the "interfaces" file @ /etc/network
=========================================================

replace

```

iface eth1 inet dhcp
wireless-essid MY_NETWORK 

```

with

```

auto eth1
iface eth1 inet dhcp

```

I assume your wireless network interface is eth1. If not replace as appropriate.

THIRDLY you have to shutdown the network manager and restart. 
=============================================================

here are the commands

```

ps -ef | grep NetworkManager

When you run this command you'll get a result like

root      4295     1  0 00:56 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      4329     1  0 00:56 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      7535  7511  0 02:07 pts/2    00:00:00 grep NetworkManager

you have to kill both the 'NetworkManager' and the 'NetworkManagerDispatcher' by running the following commands. (use the relevent pids)

kill -9 4295
kill -9 4329

Then restart application by running the following commands

/etc/init.d/networking restart
/usr/sbin/NetworkManager

```

Now go and left click on the NetworkManager applet icon on the system tray .You should see the available wireless networks with their signal strengths. If you have already connected to a wired lan that will also be indicated by the wired option being toggled on.

(Now if you go thru Network Monitor and check the properties of your eth1 connection you will see that it is not enabled. LEAVE IT THAT WAY.)

FOURTHLY you install the cisco vpnclient 4.8
=============================================

Before doing this you should have linux headers installed. Get this from synaptic. Before doing this get your kernel version by typing uname -r and install the relevent headers

cd to the directory which you unpacked it and run ./vpn_install or whatever the install file you have.

Just follow the installation mostly you can answer yes or enter since the answers to the questions asked are taken by default. This worked for me but it may not work for everybody.

After you've install copy the .pcf file (eg: abc.pcf) relevent to your network into the /etc/CiscoSystemsVPNClient/Profiles directory.

then run the following command to start the vpnclient (you need super user access)

```

/etc/init.d/vpnclient_init start

```

and to connect run

```

vpnclient connect abc

```

That's it if it got connected you should have the following resulting screen

```

root@LSIL-PrecisionM60:/home/laalitha# vpnclient connect abc
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at xxx.xx.x.xxx
User Authentication for msu...

Enter Username and Password.

Username []:
Password []:

```
After you enter your username and password it should continue to give you
```
 
Authenticating user.
Negotiating security policies.
Securing communication channel.

Your VPN connection is secure.

VPN tunnel information.
Client address: xxx.xx.xxx.xxx
Server address: xxx.xx.x.xxx
Encryption: 168-bit 3-DES
Authentication: HMAC-MD5
IP Compression: None
NAT passthrough is inactive
Local LAN Access is disabled


```

Now you are connected thru vpn to the network

To disconnect open another terminal and type

```

vpnclient disconnect

```

Most people I asked said to use vpnc or pptp or some other daemon but none were successful for my campus network. But the above procedure enabled me to connect to my campus network

The installation of the NetworkManager was taken from the guide at this link 
[http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php](http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php)
I thank B.Daily for that info. 

Hope this helps some people who have a difficult time with vpn.
Bye

Laalitha

---

### Post by in_flu_ence on 2007-01-26
VPN tunnel information.
Client address: xxx.xx.xxx.xxx
Server address: xxx.xx.x.xxx
Encryption: 168-bit 3-DES
Authentication: HMAC-MD5
IP Compression: None
NAT passthrough is inactive
Local LAN Access is disabled

It works for me in my school. MAKE SURE YOU DON"T CLOSE YOUR TERMINAL OR IT WILL AUTO-DISCONNECT

I am finding a way to avoid that.

---

### Post by kevinsun on 2007-03-25
But where can I download Cisco vpn client for Linux?  Can someone post a link here?  :(

---

