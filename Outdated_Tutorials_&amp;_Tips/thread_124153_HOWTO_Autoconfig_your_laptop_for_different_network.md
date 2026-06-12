---
title: "HOWTO: Autoconfig your laptop for different networks"
date: 2006-01-31
forum: Outdated Tutorials &amp; Tips
---

### Post by el3ktro on 2006-01-31
**What this guide will do**
This How-To is for those of you who use a laptop in several different networks, and are tired of always re-configuring the network by hand. When you do all the steps in this How-To, your laptop will configure itself automagically whenever you move it to a new network.

This is my very first how-to, so please post any comments/suggestions & questions if you have any!

I have a laptop computer which I move around in several wired networks: at home, at work, in my university and probably also elsewhere. Sometimes I also have no cable plugged in at all. I was searching for a solution to automatically configure the network depending on in which network I am, and depending on if the cable is plugged in at all.

I found a very slick solution to this which only needs two small programs: ifplugd and guessnet. The advantage of this solution is that your network is still controlled by the standard Debian ifupdown system, guessnet is just a little addon which will run some tests on your network before ifupdown is called, and ifplugd will basically detect if your network cable is plugged in or not. It will also shut down your network device when your laptop goes to sleep and re-acivate it on resume.

Guessnet can do several tests on the network to find out where you are with your laptop and configure the networking accordingly. These tests are based on ARP requests, so you need not only IP addresses, but also the MAC addresses in your networks. Using ARP has the advantage that even if two networks have a host with the same IP (it's common that home networks have a router at 192.168.1.1 for example) you can still distinguish between the two networks because there will always be different MAC addresses.



**What this guide will NOT do**
This guide will not cover wireless devices, simply because I don't have one and couldn't tell you much about it. But guessnet also works with wireless devices and can run appropiate tests (search for an access point etc.), you can find information about this when you follow the link at the end of this guide.



**Step 1: Install guessnet & ifplugd**
This is straightforward:

```

apt-get install guessnet ifplugd

```

This will install both together with one or two small libs that are needed.



**Step 2: Tell your system to use guessnet**
All network configuration is done by the ifupdown init script which as it's configuration in /etc/network/interfaces. Usually, the ifupdown init script of Ubuntu looks into this file and configures all network interfaces as described there. We first have to tell ifupdown that instead of just configuring the interface, it should first ask guessnet to find out in which network we are. To do this, add this code snippet at the beginning of /etc/network/interfaces:

```

mapping eth0
        script guessnet-ifupdown
        map default: none
        map timeout: 3
        map verbose: true

```

**Step 3: Configure all the different networks you use**
Somewhere down the config file you'll either have a DHCP or a static configuration for your network card(s), probably looking like this:

```

iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        gateway 192.168.1.1
auto eth0

```

Instead of such a single configuration for eth0, we will have several different configurations, one for each of the networks that you're in. So please comment (#) the current entry for the interface you want to configure, or delete it completely, we won't need it anymore. 

We will add several possible network configurations now. Each network configuration will have a unique name that you can choose freely, I'll use the names "home" and "work" in my examples. Here they are:

```

iface home inet static
        address 192.168.1.20
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-search my-home-isp.net
        dns-nameservers 62.206.1.4 62.206.2.4
        test peer address 192.168.1.1 mac 00:11:09:D2:22:32

iface work inet static
        address 10.0.0.55
        netmask 255.0.0.0
        gateway 10.0.0.1
        dns-search my-work-isp.net
        dns-nameservers 122.131.5.2 122.131.5.3
        test peer address 10.0.0.10 mac 03:51:C9:D5:AB:20

```

You can add as many such configurations as you want, just adjust them according to your needs. The important line for guessnet is the "test" statements. The "test" statement tells guessnet to check if the host at the given IP has the given MAC address. If this is true, then guessnet has found your network. For these tests, you should choose a host that is always available in the network like your home router, the file server in your university, the big managed switch at your working place etc.

It might be a good idea to make more than one test, e.g. you could test two servers, and if one of the server is down for some reason, the network is still correctly detected. You can do this with two numbered "test" lines:

```

	test1 peer address 192.168.1.1 mac 00:11:09:D2:22:32
	test2 peer address 192.168.1.2 mac cd:12:ac:03:53:12

```

It can be a bit tricky to find the right hosts to test for. In my home network, it doesn't work if I test my router (which is a very strange one anyway), but it works fine if I test for my server or for my desktop machine, which is turned on most of the time. So if you experience that guessnet doesn't correctly detect your network, simply try a different server, a different router etc. Guessnet will actually run all tests in parallel, so it doesn't make the whole procedure take longer if you add some more hosts.

In some cases a host that you test will not respond to an ARP request which doesn't have a source IP (remember, your interface is not yet configured, so your computer has no IP address when these tests are done). In this case, you can just tell guessnet to use a bogus IP address as source address:

```

test peer address 192.168.1.1 mac cd:11:ff:D2:52:32 source 192.168.1.20

```

As a source address you can have: Either the IP address you know that you'll get, or the address of the network (e.g. 192.168.1.0) or an IP address that you know is not used elsewhere in the network.



**Hint**
You propably don't know the MAC addresses of the hosts in your network, but it's easy to find them out. If you want to find out the MAC address of your home router at 192.168.1.1 for example, simply ping this server once:

```

ping -c 1 192.168.1.1

```

Then, run the command

```

arp -a

```

This will print out the ARP table of your laptop. In this table, search for the IP address you justed pinged and you'll find the corresponding MAC address in the same line.



**Step 4: Add a DHCP fallback entry & a unplugged configuration**
It's likely that you will also use your laptop within a new network where you haven't been before, and in such a case it's always a good idea to try to get an IP address via DHCP. I'll call this configuration "unknown", the entry for /etc/network/interfaces is simple:

```

iface unknown inet dhcp

```

Also, if you don't have a cable plugged in at all, the system should know what to do. In this case, we don't assign a IP address to the interface at all:

```

iface disconnected inet static
        test missing-cable

```

One important thing is to remove the line "auto eth0" from /etc/network/interfaces, so that we make sure that eth0 is controlled by guessnet (if you want to control another interface with guessnet, you have to remove the corresponding "auto" line of course)

Your file /etc/network/interfaces should now look something like this:

```

auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

mapping eth0
        script guessnet-ifupdown
        map default: none
        map timeout: 3
        map verbose: true

iface home inet static
        address 192.168.1.20
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-search my-home-isp.net
        dns-nameservers 62.206.1.4 62.206.2.4
        test1 peer address 192.168.1.1 mac 00:11:09:D2:22:32
	test2 peer address 192.168.1.2 mac cd:12:ac:03:53:12

iface work inet static
        address 10.0.0.55
        netmask 255.0.0.0
        gateway 10.0.01
        dns-search my-work-isp.net
        dns-nameservers 122.131.5.2 122.131.5.3
        test peer address 10.0.0.10 mac 03:51:C9:D5:AB:20

iface unknown inet dhcp

iface disconnected inet static
        test missing-cable

```



**Step 5: Configure ifplugd**
Now comes the easy part: We basically just have to tell ifplugd which interfaces it should control and start it. Edit the file /etc/default/ifplugd and add the interface(s) you want to auto-config to the INTERFACES variable. Please also remove the "-q" from the ARGS variable. Running ifplugd --help will tell you what the others args do, they are basically for tweaking the behaviour, but the default behaviour should be fine. Now restart ifplugd:

```

sudo /etc/init.d/ifplugd restart

```

and check if it is running:  

```

ps -e | grep ifplugd

```

Now with ifplugd running & guessnet being configured you should hear a few beeps from your speakers. Ifplugd will make a "light" beep if you plug in the network cable, and you'll hear a second "light" beep if a network has been detected, or if you've got an address via DHCP. If you unplug the network cable, you'll hear a "dark" beep. If you put your laptop to sleep (close the lid) you should also hear a "dark" beep", and you should hear two "light" beeps again when you resume your laptop.

One neat thing of ifplugd is that when you put your laptop to sleep, the network interface is stopped (dark beep). Now, move your laptop to a different network (while it is sleeping), resume it at the new location and ifplugd will start the network again, discover that you're in a different network and re-configure the interface. If you're in a completely new network that you didn't configure, your computer will always try to get an address via DHCP.



**Finished!**
Well I hope it works for you, it has definitely made my mobile life a lot easier. I don't have to fiddle around with the network config anymore, I just plug the cable in and voila I'm done :-)

**Links**
Guessnet: [http://guessnet.alioth.debian.org/](http://guessnet.alioth.debian.org/)

---

### Post by Sokraates on 2006-02-01
Great How-To!

In my case the laptop is either connected to a hub or a cable modem. How do I check for their MAC-addresses? 

AFAIK the address should be displayed on a label on the modem itself, but I don't see any. Guess it has already peeled off. Same goes for the hub.

---

### Post by el3ktro on 2006-02-01
Hi,
I'm glad my how-to was helpful to you. You can find out which MAC your hub/modem has easily:

1. Send a ping to both, e.g. ping 192.168.1.1
2. Then look at the ARP table by running arp -a

The ARP table will tell you which IP addresses in your network have which MAC addresses. ARP is the protocol that guessnet uses to find out in which network it is, via the ARP protcol IP addresses are mapped to hardware (MAC) addresses.

Tom

---

### Post by Sokraates on 2006-02-01
How do I find out which IP-address they have? 

I know the server's IP-address (when using the hub), but not the one of the hub (if there is any). Can I use the server's IP and MAC? If you don't know, I will try sometime. ;)

The same goes for the cable-modem.

---

### Post by zi99y on 2006-02-01
Great howto, I'll try it out when I get a chance. Never heard of these cool tools before..

---

### Post by el3ktro on 2006-02-01
[QUOTE=Sokraates]How do I find out which IP-address they have? 

I know the server's IP-address (when using the hub), but not the one of the hub (if there is any). Can I use the server's IP and MAC? If you don't know, I will try sometime. ;)

The same goes for the cable-modem.[/QUOTE]

Hubs & switched generally don't have an IP address, except managed switches which you might find in large networks. In such a case it would be best to ask the local admin to give you the IP & MAC of this switch & tell them why you need them.

It's best to use the IP & MAC of any local server which you know is always on, or you take the IP of your DSL/Cable router. You can find out their MAC addresses by sending a ping to them from your laptop and by looking at the ARP table of your laptop with arp- a.

If you know te IP address of the server, connect your laptop to the network, send a ping to the server and then enter "arp- a", you'll get a list in which you'll find the server's IP address & it's MAC addres. Simply enter them in /etc/network/interfaces and you're done.

Tom

---

### Post by cbudden on 2006-02-01
GTK-wifi for the wireless part?

---

### Post by el3ktro on 2006-02-01
[QUOTE=cbudden]GTK-wifi for the wireless part?[/QUOTE]
 Please don't ask me this :-k  I have no wireless at all (damn) so i can't tell much about this. I've just read on the hp of guessnet that it supports searching for access point, SSIDs etc., but if you need such an auto-config behaviour for wifi interfaces I'm afraid I can't help you :???: 

Tom

---

### Post by Gandalf on 2006-02-01
For wireless, I suggest using Wifi-radar (apt-get install wifi-radar), it's so easy, lightweight and very helpfull, thats what I use myself

gtkwifi is good too, but i don't want a gnome applet, i'd rather hae gnome-network-manager instead which is wired/wireless but still in development..

---

### Post by Heliode on 2006-02-01
[QUOTE=Sokraates]How do I find out which IP-address they have? 

I know the server's IP-address (when using the hub), but not the one of the hub (if there is any). Can I use the server's IP and MAC? If you don't know, I will try sometime. ;)

The same goes for the cable-modem.[/QUOTE]

What I would do is scan the thing with NMAP. That should give you the MAC-address.

---

### Post by el3ktro on 2006-02-01
[QUOTE=Heliode]What I would do is scan the thing with NMAP. That should give you the MAC-address.[/QUOTE]

This would also work, right. I suggested to ping the host and then look at the arp table with arp -a, this way you don't have to install nmap.

Tom

---

### Post by Sokraates on 2006-02-02
NMAP doesn't help much, or I'm just too stupid to use it right. I'll take a look at the arp-table, when I get around to it.

---

### Post by slakkie on 2007-02-12
Little kick, but I followed the howto and it works for me :)

I got it to work for both fixed and wireless.

It took me a while to get it working with wpa_supplicant and guessnet, but it now works.
You need to start wpa_supplicant before ifplugd.

See this execelent guide (in German) [http://www.aaron-spettl.de/ubuntu/dynamische-netzwerkkonfiguration.php](http://www.aaron-spettl.de/ubuntu/dynamische-netzwerkkonfiguration.php)
I only needed the test criteria for the essid, but it will help everyone (even the non German readers).

```

# Our various networks, both work and home
mapping eth0
  script guessnet-ifupdown
  map default: none
  map verbose: true
  map debug: true
  map work-fixed
  map home-fixed

mapping eth1
  script guessnet-ifupdown
  map default: none
  map verbose: true
  map debug: true
  map work-wifi
  map home-wifi

iface work-fixed inet dhcp
  dns-search euronet.nl
  dns-server 194.134.5.5 194.134.0.97 194.134.5.55
  test peer address 194.134.x.x mac XX:XX:XX:XX:XX:XX source 194.134.XX.XX

iface home-fixed inet static
  address 192.168.1.119
  netmask 255.255.255.0
  gateway 192.168.1.1
  dns-search opperschaap.net euronet.nl
  dns-server 194.134.5.5 194.134.0.97 194.134.5.55
  test peer 192.168.1.1 mac 00:03:c9:73:20:41 source 192.168.1.119

# Wireless fixed thanks to: http://www.aaron-spettl.de/ubuntu/dynamische-netzwerkkonfiguration.php
iface work-wifi inet dhcp
  dns-search euronet.nl
  dns-server 194.134.5.5 194.134.0.97 194.134.5.55
  test wireless essid Work Wireless

iface home-wifi inet static
  address 192.168.1.109
  netmask 255.255.255.0
  gateway 192.168.1.1
  dns-search opperschaap.net euronet.nl
  dns-server 194.134.5.5 194.134.0.97 194.134.5.55
  test wireless essid wnl.opperschaap.net


```

The only thing left now, is that in case of DHCP it does not edit my /etc/resolv.conf.. But that's for the DHCP or it will be a pre/post-up action.

---

### Post by ingo on 2007-02-17
Have any of you gnome people tried installing knetworkmanager? It does all of the above, handles wpa, wpa2, etc by way of a simple click (at least in my case :)) Not sure whether there is gnome equivalent yet...

---

### Post by slakkie on 2007-02-23
I don't see a reason to switch from this configuration to a GUI for my network configuration. This will also work when my PC/laptop will boot without a GUI.

---

### Post by rrwo on 2008-01-08
I've had problems using the mapping keyword for wireless because of wpa_supplicant. I found [this page]("http://manual.sidux.com/ja/internet-connecting-wpa-ja.htm") to be a helpful guide.

First,in the interfaces file, I have
```
auto lo
allow-hotplug eth0 eth1
```
since we want ifplugd to be in charge of putting network devices up or down.

My interfaces has the following for the wireless device:
```

iface eth1 inet manual
  wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
  wpa-roam-default-iface wparoam-unknown
  wpa-mapping-script guessnet-ifupdown
  wpa-map default: guessnet-unknown
  wpa-map0 wpa-home
  wpa-map1 wpa-work

iface wpa-home inet dhcp
  test wireless mac 01:23:45:67:89:AB essid MyHomeSSID
  metric 10
  post-up /etc/network/guessnet-scripts/home

iface wpa-home inet dhcp
  test1 wireless mac 01:23:45:67:89:FF essid MyWorkSSID
  test2 wireless mac 01:23:45:67:89:FE essid MyWorkSSID
  post-up /etc/network/guessnet-scripts/work

iface wparoam-unknown inet dhcp
  post-up /etc/network/guessnet-scripts/unknown

iface guessnet-unknown inet dhcp
  post-up /etc/network/guessnet-scripts/unknown

```

I'm unsure if a separate wparoam-unknown and guessnet-unknown is needed (that's what was in the reference above). I assume they can be the same, but I've not yet tested it.

The metric keyword is used to set the network metric when I'm at home. For the wired connection, I have "metric 1" so that it has priority if I'm connected to both, e.g.
```
iface lan-home inet dhcp
  test peer address  192.168.0.1 mac 01:23:45:67:89:AB
  metric 1
  post-up /etc/network/guessnet-scripts/home

```

The post-up scripts do various configuration tasks like setting the default printer, configuring some network security settings, etc.
(Another page [here]("http://andrewlinux.blogspot.com/") discusses using switchconf for more complex reconfiguration.)

Also, /etc/default/ifplugd is set to the following

```
INTERFACES="eth0 eth1"
HOTPLUG_INTERFACES=""
ARGS_eth0="-q -f -u 0 -d 1 -I"
ARGS_eth1="-q -f  -u 0 -d 5 -I -m wlan"
SUSPEND_ACTION="stop"

```

I have the hibernate package installed, and have /etc/hibernate/common.conf configured with the following lines
```

DownInterfaces eth0 eth1
UpInterfaces auto
RestartServices laptop-mode ifplugd

```

---

