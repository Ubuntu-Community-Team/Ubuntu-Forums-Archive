---
title: "Config seperate LAN cards independently?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by InTheShires on 2008-08-09
Ok, so I use my wifi for internet, which works just fine, and it uses a DHCP via the Router.

I use my wired LAN port to directly access a separate device, with a fixed ip.

Currently I have to turn off/disable the wifi so I can use the Ethernet port. This is a bit of a pain really.

Can I set it so I can have both devices on at the same time, but still use (for example) gFTP to access the static LAN ip. (Currently gFTP automatically looks to use the wifi for a connection, so I've got to disable wifi, so it will use the LAN port with the static ip)

Hope this makes sense!

---

### Post by hyper_ch on 2008-08-09
well, wifi and lan settings are stored in /etc/network/interfaces....

so make sure the wifi runs and then manually add the lan entries to it and restart the networking
```

sudo /etc/init.d/networking restart

```
although you should be able to configure both from the network manager.

---

### Post by InTheShires on 2008-08-09
I think I've got things wrong.

After a bit more messing about, it looks like it's a firewall issue. I've got FireStarter running, however if I turn off FireStarter, both devices work properly, so it seems the firewall is blocking the wired LAN.

Problem is, I can't see how to allow it to let wired connection through?

I've tried a couple of things, but it's still not allowing the connection.

At least I'm a bit further on!

Any further help appreciated.

ITS.

---

### Post by hyper_ch on 2008-08-09
firestarter is not a firewall

---

### Post by help1 on 2008-08-09
[URL="http://managementart.blogspot.com"]EARNING HERE :lolflag:$10000000/DAY:lolflag:
SIMPLE VISIT US :lolflag:http://managementart.blogspot.com[/URL]

---

### Post by InTheShires on 2008-08-09
> **hyper_ch said:**
> firestarter is not a firewall

What is it then? :confused:

It calls itself a "Desktop firewall", and it looks like a firewall in it's settings.  :confused:

---

### Post by hyper_ch on 2008-08-09
firestarter is an outdated tools to configure iptables - the actual firewall.

---

### Post by InTheShires on 2008-08-09
> **hyper_ch said:**
> firestarter is an outdated tools to configure iptables - the actual firewall.

Right, ok. But it's, or the iptables, is still blocking me using the wired LAN port.

How do I over come this?

---

### Post by hyper_ch on 2008-08-10
I have no clue what you added for filters for iptables by running firestarter...

---

### Post by InTheShires on 2008-08-11
> **hyper_ch said:**
> I have no clue what you added for filters for iptables by running firestarter...

That's the point though. I haven't added anything. If I had, I'd know where to look. I just followed the advice here, in a security thread for using Firestarter. 

As Firestarter is "outdated" what should I be looking to use, or setup?

---

### Post by DGortze380 on 2008-08-11
> **hyper_ch said:**
> I have no clue what you added for filters for iptables by running firestarter...

dude, at least try to be helpful.


> That's the point though. I haven't added anything. If I had, I'd know where to look. I just followed the advice here, in a security thread for using Firestarter.

As Firestarter is "outdated" what should I be looking to use, or setup?

Firestarter is perfectly fine for a GUI to iptables on a desktop machine. Sounds to me like firestarter only supports configuring one network device? (Someone correct me if I'm wrong). You may have to remove firestarter and manually configure iptables. No experience with this, but I'm sure someone here does.

---

### Post by InTheShires on 2008-08-11
> **DGortze380 said:**
> dude, at least try to be helpful.




Firestarter is perfectly fine for a GUI to iptables on a desktop machine. Sounds to me like firestarter only supports configuring one network device? (Someone correct me if I'm wrong). You may have to remove firestarter and manually configure iptables. No experience with this, but I'm sure someone here does.

Thanks for the response mate, appreciated.

---

### Post by hyper_ch on 2008-08-11
> **InTheShires said:**
> That's the point though. I haven't added anything.
By installing firestarter it just blocks everything. So you did add something.

> **InTheShires said:**
> I just followed the advice here, in a security thread for using Firestarter.
What advice did you follow? Have a read through this sticky in teh security sub-forum: [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)
Most likely a firewall is not needed.

> **DGortze380 said:**
> dude, at least try to be helpful.
Dude, at least try to be helpful.

> **DGortze380 said:**
> Firestarter is perfectly fine for a GUI to iptables on a desktop machine.
Yet firestarter is outdated and the new tool is UFW - if you really need to alter the default rules in iptables.

---

### Post by dfreer on 2008-08-11
You can always output the current rules of iptables with the following command:
```
sudo iptables -L
```

I've always preferred to manually add entries to iptables, it isn't that hard if you are willing to learn the syntax and know a bit about IP addresses and ports, and it's a great firewall.

---

### Post by john test on 2008-08-11
Below is the link for Firestarter.  They might be able to help you configure Firestarter to handle both Interfaces properly or perhaps provide an upgrade to do so

[http://www.fs-security.com/](http://www.fs-security.com/)

If you google gui iptables you will find several GUI Interfaces for your firewall (iptables)that you could try if firestarter just won't work.

Are you able to open Firestarter to see what the settings are?  (

---

### Post by InTheShires on 2008-08-14
Many thanks for the useful input dfreer, and john test, much appreciated.

I have since removed Firestarter, and have installed a GUI for UFW, so I will see how that works out. I'll try and find time today to hook up the other device and use both LAN cards and see what occurs. (Now that I'm not using the "outdated" Firestarter.)

---

### Post by dfreer on 2008-08-14
This is what I like to do for a default desktop firewall:
Create a file called /etc/iptables.up.rules (can be any name you like as long as you remember it). This file will be used to flush any existing rules and add your rules everytime the network goes up. Open up a text editor and enter the following:
```

*filter
:INPUT ACCEPT [9473:7088853]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [69711:38731179]

## Established ports used by outgoing connections
## This is essential. Otherwise you would be able to send 
## packets, but you won't be able to recieve any (e.g. no 
## webpages will load)
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

## Accept All lo connections
## Your system will talk to itself over the loopback connection. 
## You'll want this.
-A INPUT -i lo -j ACCEPT

## Drop Everything Else
## This will simply ignore any other packets coming in on the 
## specified network interface. This also means you will not 
## respond to pings. Go ahead and comment out any interface you 
## don't have, and add ones you do that aren't mentioned.
-A INPUT -i eth0 -j DROP
-A INPUT -i eth1 -j DROP
-A INPUT -i wlan0 -j DROP

COMMIT

```

You could simply use the following commmand to add the rules:
```
sudo iptables-restore < /etc/iptables.up.rules
```

But to add it so that it flushes the rules and creates the firewall when the network goes up, you need to add a line to your /etc/network/interfaces file:

```

# The loopback network interface
auto lo
iface lo inet loopback

# A static IP configured network interface
auto eth0
iface eth0 inet static
    address 192.168.1.5
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1


# A static IP configured network interface with the firewall script
auto eth0
iface eth0 inet static
**  pre-up iptables-restore < /etc/iptables.up.rules**
    address 192.168.1.5
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

# A DHCP enabled network interface
auto eth0
iface eth0 inet dhcp

# A DHCP enabled network interface with the firewall script
auto eth0
iface eth0 inet dhcp
**  pre-up iptables-restore < /etc/iptables.up.rules**

```

Anyways, hope this helps! When you want to enable a service to run on your machine, like samba file sharing, you just need to edit /etc/iptables.up.rules to allow the service to run (after the RELATED,ESTABLISHED rule and before the DROP rules), then restart your network (sudo /etc/init.d/networking restart).

EDIT: The only problem I can think of with your situation is if you want a device on one network card to access a device on the other network card through your Ubuntu machine (e.g. you are connected to the internet on one interface and you want to share the internet to the machine on the other interface). You'll need to create a rule to allow the traffic to pass through your firewall.

---

### Post by InTheShires on 2008-08-27
> **dfreer said:**
> 
EDIT: The only problem I can think of with your situation is if you want a device on one network card to access a device on the other network card through your Ubuntu machine (e.g. you are connected to the internet on one interface and you want to share the internet to the machine on the other interface). You'll need to create a rule to allow the traffic to pass through your firewall.

Thanks for that, useful stuff. I'll give all that a bash soon, and see how I get on. Thank you.

I'm currently disabling UFW (using the GUI) to get my parameters working. And also to access files on the network. (Bit of a pain, but there you go. I need time to sort it, and it's not something I have much of atm.)

---

### Post by ayenack on 2008-08-27
Take a look at this.

[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

If it doesn't work try this.

I haven't read all the post on this thread so if this has been said already forgive me.

Remove Firestarter.

**sudo apt-get remove --purge firestarter**

Then visit the site bellow and click on downlod in the panel to the left.

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Once done open a terminal and type.

**sudo ufw enable**

This will enable the UbuntuFirewall (UFW Uncomplicated Firewall.) If you now click in Applications>Internet>Gufw_Firewall_Configuration you will be able to config the firewall.

For more info look here.

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

It should solve your problem and enable use of both interfaces.

Hope this helps.

---

