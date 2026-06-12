---
title: "HOWTO: Automatic network configuration"
date: 2005-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by blueplazma on 2005-04-08
HOWTO Whereami
Originally by Reid Gilman
goodstuff AT blueplazma DOT org
8/4/2005


1) What is Whereami?
	[Whereami](http://debiana.net/whereami/) is a very useful little program that "automatically configures your system during boot and whenever a PCMCIA network card is inserted or removed."  It can be used to switch settings and is very useful on laptops that move from trusted networks to untrusted networks.
	This HOWTO will cover setting up a laptop to differentiate a wired, wireless, and un-trusted wireless network.  We will assume that this laptop is normally on a public, unsecured wireless network, but is also used on a home wireless network (which is also unsecured), as well as a home wired network.  eth0 will be an ethernet card, and eth1 will be a wireless card.  This HOWTO was tested on Ubuntu Hoary running on a Dell Inspiron 8600 with an Intel IPW2200(b/g).

2) Where do I get Whereami?
	There are a few ways to get Whereami.  I did this install on Ubuntu, so I used apt-get.  On Ubuntu, simply ```
sudo apt-get install whereami
```  For other distros, visit [the download page](http://debiana.net/whereami/generic/). 

3) How do I configure Whereami?
	Whereami configuration involves two main files: /etc/whereami/detect.conf and /etc/whereami/whereami.conf.  From now on, if I refer to one of these files, I mean for it to be prefaced by /etc/whereami.  Thus, if I say, "Edit whereami.conf..." I mean "Edit /etc/whereami/whereami.conf".  To begin setting up Whereami, cd into the whereami directory from a terminal. ```
cd /etc/whereami 
```
	
	1) detect.conf
		detect.conf is the first of the two extremely important files to make whereami function.  This file does what it sounds like: it detects on which network you are using a variety of tests.  Ubuntu gives you an example detect.conf; I recommend moving it to detect.conf.default and opening a new version like so 
```
sudo mv detect.conf detect.conf.default && sudo gedit detect.conf 
```
	You should now have a nice shiny gedit window with nothing in it.  You should set a "default" location.  For our purposes, it will be "wireless".  Enter the line ```
 default wireless 
``` into your new detect.conf file.
	The next test is to determine if there is an ethernet cable plugged in or not, since that can rule out one possible configuration.  We will use the testmii command to do so.  testmii needs two arguements.  The first is an interface to test, the second a network to enable should it find an ethernet cable.  Since it is looking for an ethernet cable, it will enable the wired network if it finds one.  eth0 is our ethernet card, so enter this line to check for an ethernet cable plugged into eth0
```
testmii eth0 lan
```
	Now let's tell Whereami what to do if an ethernet cable is plugged in.  
```
if lan
	set INTERFACE eth0
	testdhcp 192.168.1.0/24 home-wired
	testdhcp '*.*.*.*' wired
	notat down
else
	notat wired,home-wired
	always set INTERFACE eth1
	always testap scan wlan
fi
```
So, what does all that mean?  Some of it is plain old shell-scripting, but some is not.  "set INTERFACE eth0" tells whereami to perform the following tests on the interface eth0.  testdhcp tells whereami to test for a DHCP assigned IP address on the interface and activate the selected network if it finds one.  "notat down" simply tells Whereami that we have some type of network, since down is going to be our selection when there is absolutely no connectivity.  The last command of interest is "testap scan wlan".  If you haven't guessed yet, this command simply scans for a wireless AP within range and activate the wlan network when it finds one.
	Now, we must determine if we are on our trusted wireless network or not.
```
if wlan
	testssid MyHomeNetwork home-wireless
	testap scan wlan wireless
	always notat wlan
fi
```
	"testssid MyHomeNetwork home-wireless" is our final test.  If it finds an SSID for our trusted network, then it turns on the home-wireless network.  Otherwise, it assumes we have an unknown network.  It shuts off wlan because wlan is just a name to avoid conflict in if statements.

	2) whereami.conf
		Now that we know which network we are at, we need to tell Whereami to do something about it.  whereami.conf does this, and is much more straightforward and self-explanatory than is detect.conf.
	Here is the first section of our whereami.conf.
```

	=rm /etc/network/interfaces.old

+home-wired /etc/init.d/networking restart
+home-wired /etc/init.d/firestarter restart
+home-wired setresolver search <put in your settings here>
```
	There are really three things that need explanation here.  First is the equals sign (=), which means to always perform the command, regardless of which network we were on before.  The plus (+) means to perform this command only if we were not on this network before, and the minus (-) means to perform this command only if we were on this network before, but are NOT anymore.  See the [documentation](http://debiana.net/whereami/actions.html) for specifics. Also, please consider writing small firewall scripts to replace firestarter if you can.  It will give you much better control over your firewall at different locations.  I have done this, and have an /etc/init.d/trusted-network-firewall and /etc/init.d/untrusted-network-firewall script set up.  That is beyond this HOWTO, but worth considering.  Otherwise, the default firestarter setup should be fine for you.

4) How do I make this all work now?
	Whereami should work on reboot, or by running the initscript (/etc/init.d/whereami).  I found that this works well for me.  I hope it works well for you too.  These settings can be kind of difficult, but I found the included documentation to be very sparse, so I hope that this example will help you a bit to get off the ground.  Obviously, whereami can be used for very complex networks including WEP and WPA, but most people do not need an extremely complex setup.

---

### Post by Gandalf on 2005-04-09
> **blueplazma]HOWTO Whereami
Originally by Reid Gilman
goodstuff AT blueplazma DOT org
8/4/2005


1) What is Whereami?
	[Whereami](http://debiana.net/whereami/) is a very useful little program that "automatically configures your system during boot and whenever a PCMCIA network card is inserted or removed."  It can be used to switch settings and is very useful on laptops that move from trusted networks to untrusted networks.
	This HOWTO will cover setting up a laptop to differentiate a wired, wireless, and un-trusted wireless network.  We will assume that this laptop is normally on a public, unsecured wireless network, but is also used on a home wireless network (which is also unsecured), as well as a home wired network.  eth0 will be an ethernet card, and eth1 will be a wireless card.  This HOWTO was tested on Ubuntu Hoary running on a Dell Inspiron 8600 with an Intel IPW2200(b/g).

2) Where do I get Whereami?
	There are a few ways to get Whereami.  I did this install on Ubuntu, so I used apt-get.  On Ubuntu, simply ```
sudo apt-get install whereami
```  For other distros, visit [the download page](http://debiana.net/whereami/generic/). 

3) How do I configure Whereami?
	Whereami configuration involves two main files: /etc/whereami/detect.conf and /etc/whereami/whereami.conf.  From now on, if I refer to one of these files, I mean for it to be prefaced by /etc/whereami.  Thus, if I say, "Edit whereami.conf..." I mean "Edit /etc/whereami/whereami.conf".  To begin setting up Whereami, cd into the whereami directory from a terminal. ```
cd /etc/whereami 
```
	
	1) detect.conf
		detect.conf is the first of the two extremely important files to make whereami function.  This file does what it sounds like: it detects on which network you are using a variety of tests.  Ubuntu gives you an example detect.conf said:**
> documentation[/URL] for specifics. Also, please consider writing small firewall scripts to replace firestarter if you can.  It will give you much better control over your firewall at different locations.  I have done this, and have an /etc/init.d/trusted-network-firewall and /etc/init.d/untrusted-network-firewall script set up.  That is beyond this HOWTO, but worth considering.  Otherwise, the default firestarter setup should be fine for you.

4) How do I make this all work now?
	Whereami should work on reboot, or by running the initscript (/etc/init.d/whereami).  I found that this works well for me.  I hope it works well for you too.  These settings can be kind of difficult, but I found the included documentation to be very sparse, so I hope that this example will help you a bit to get off the ground.  Obviously, whereami can be used for very complex networks including WEP and WPA, but most people do not need an extremely complex setup.
 nice HOWTO, kinda so usefull to me, but can you explain better detect.conf please? because i have a static wired connection and a secures wireless connection, so for the wired, no DHCP and for the wireless, i need to pass a key, how to do that? where to have insfo on that??
thanks

---

### Post by blueplazma on 2005-04-09
[QUOTE=Gandalf]nice HOWTO, kinda so usefull to me, but can you explain better detect.conf please? because i have a static wired connection and a secures wireless connection, so for the wired, no DHCP and for the wireless, i need to pass a key, how to do that? where to have insfo on that??
thanks[/QUOTE]

Hi Gandalf.  I'll assume that eth0 is wired and eth1 wireless.  You'll need to adjust that to your own settings.  If you only want to use one or the other at a time, then try setting up a detect.conf like this:
```

#detect.conf

#use wired by default
default down

#check for an ethernet cable in the wired interface
testmii eth0 wired

if wired #if it finds a cable
     set INTERFACE eth0
     notat down #then there must be some kind of connectivity, let's use it
else
    notat wired #no cable found, must not be wired
    always set INTERFACE eth1
    always testssid <yoursssid> secure-wireless #make sure your ssid is present
fi

```

That code should do fine for detecting if you are at your wired or wireless connection.  To use a WEP key, you need to set up your /etc/network/interfaces to include the proper key information in it.  You could do this by copying /etc/network/interfaces to /etc/network/interfaces.wired and /etc/network/interfaces.wireless .  Then, put your wired interface information in interfaces.wired, and the same for wireless.  Make sure to include information for the loopback in both.  Using whereami.conf, put in a like this:
```

#whereami.conf

=rm /etc/network/interfaces.last

+secure-wireless cp /etc/network/interfaces /etc/network/interfaces.last
+secure-wireless cp /etc/network/interfaces.wireless /etc/network/interfaces
+secure-wireless /etc/init.d/networking restart

+wired cp /etc/network/interfaces /etc/network/interfaces.last
+wired cp /etc/network/interfaces.wired /etc/network/interfaces
+wired /etc/init.d/networking restart

```

This config will basically change your /etc/network/interfaces file to be the appropriate one for the network you are on.  You will need to edit those files yourself to include the proper information, but if you use information that currently allows you to connect, you should be fine.  It worked out pretty well for me.  Good luck.

---

### Post by Gandalf on 2005-04-12
something weird has happened with me.
i installed whereami on my test installation (it was befor today, just to test everything, all drivers etc.... and install a real distro later to be clean and fresh) whereami worked well on my PC, i have IPCOP router so i was identifying each zone by the MAC address and if not available i was using wireless and beleive was like magic, it was so good but unfortunately on the fresh install, ubuntu just hang on "Configuring Network Interfaces" service, and Ctrl + C to continue but then it's not possible to use network interfaces and ifup -a hang also...
do you know where can i have a log of errors or something like that?

---

### Post by blueplazma on 2005-04-12
If you think whereami is the problem, add this line to your detect.conf:
set DEBUGWHEREAMI 1


If you don't know exactly what the problem is, then you'll need to check out /var/log/syslog and /var/log/messages.  It could be a number of things, but those two are always a good place to start.

---

### Post by Gandalf on 2005-04-12
[QUOTE=blueplazma]If you think whereami is the problem, add this line to your detect.conf:
set DEBUGWHEREAMI 1


If you don't know exactly what the problem is, then you'll need to check out /var/log/syslog and /var/log/messages.  It could be a number of things, but those two are always a good place to start.[/QUOTE]
 i already solved it, and i sent a mail to the author also, i don't know why but for some reason, ifup hangs, i commented this line
```

# Can't use --syslog because syslog starts after the network (bug #160187)
/usr/sbin/whereami --run_from ${SITUATION} --hint ${SITUATION}

```
in /etc/network/if-pre-up.d/whereami file, and it hangs no more working perfect for all my network zones

---

### Post by AndersAA on 2005-04-14
how can I simply configure this to check for two different networks when my wireless is using wpa_supplicant?


I'm thinking something very simple like:

testmmi eth0 lan
testmmi eth1 wireless

if wireless
        set INTERFACE eth1
        testdhcp    '*.*.*.*'    dhcp
else
  if lan
        set INTERFACE eth0
        testdhcp    '*.*.*.*'    dhcp
  fi
fi


and this in whereami:

+lan /sbin/ifup eth0
+wireless /sbin/ifup eth1


can anyone make me some confs that work?  I've been toying with this for a while now and it's somewhat lacking in documentation.

---

### Post by blueplazma on 2005-04-15
[QUOTE=AndersAA]how can I simply configure this to check for two different networks when my wireless is using wpa_supplicant?
 
 
I'm thinking something very simple like:
 
testmmi eth0 lan
testmmi eth1 wireless
 
if wireless
set INTERFACE eth1
testdhcp '*.*.*.*' dhcp
else
if lan
set INTERFACE eth0
testdhcp '*.*.*.*' dhcp
fi
fi
 
 
and this in whereami:
 
+lan /sbin/ifup eth0
+wireless /sbin/ifup eth1
 
 
can anyone make me some confs that work? I've been toying with this for a while now and it's somewhat lacking in documentation.[/QUOTE]
 
Well, be careful with the testmii call, because it will only work with a wired interface.  Something like this may work better.
```

testmii eth0 wired
 
if wired
set INTERFACE eth0
testdhcp '*.*.*.*' dhcp
else
set INTERFACE eth1
testdhcp '*.*.*.*' dhcp
fi
fi

```
 
And for whereami.conf try what you already have.  It should be fine.

---

### Post by AndersAA on 2005-04-15
[QUOTE=blueplazma]Well, be careful with the testmii call, because it will only work with a wired interface.  Something like this may work better.
[/QUOTE]

thanks for the help, and I actually believe wpa_supplicant triggers the wired/not wired when it connects, allowing clients to run dhcp calls properly.  Although it's a while since I've been playing with it ;)

---

### Post by moon2js on 2005-04-16
Could someone explain a bit more how whereami.conf works? Maybe post an example?

---

### Post by blueplazma on 2005-04-17
whereami.conf is the file that determines what actions are taken based on which network you are on as determined in detect.conf. Each line in whereami.conf starts with a +, -, or = sign. A + means the command is performed when moving from another network to the new network; a - means the perform it when moving away, and the equal means to always perform it when using the network. The +/-/= sign must be followed by a network (which must be listed in detect.conf) and then a command. So, a line looks like this
```
*+/-/=<network> <command>*
```

My whereami.conf file looks like this:
```

=home-wired cp /etc/network/interfaces /etc/network/interfaces.old
=home-wired cp /etc/network/interfaces.wired /etc/network/interfaces
=home-wired /etc/init.d/networking restart
=home-wired setresolver search lucifer.blueplazma.org blueplazma.org nameserver 192.168.1.114


=wired cp /etc/network/interfaces /etc/network/interfaces.old
=wired cp /etc/network/interfaces.wired /etc/network/interfaces
=wired /etc/init.d/networking restart
=wired /etc/init.d/firewall-secure

=home-wireless cp /etc/network/interfaces /etc/network/interfaces.old
=home-wireless cp /etc/network/interfaces.home-wireless /etc/network/interfaces
=home-wireless /etc/init.d/networking restart
=home-wireless setresolver search lucifer.blueplazma.org blueplazma.org nameserver 192.168.1.114
=home-wireless /etc/init.d/firewall-home

=wireless cp /etc/network/interfaces /etc/network/interfaces.old
=wireless cp /etc/network/interfaces.dhcp-wireless /etc/network/interfaces
=wireless /etc/init.d/networking restart
=wireless dhclient
=wireless /etc/init.d/firewall-secure


=down cp /etc/network/interfaces /etc/network/interfaces.old
=down cp /etc/network/interfaces.down /etc/network/interfaces
=down /etc/init.d/networking restart

```

As you can see, I have several different networks, and different commands for each one. This file makes whereami very powerful, because just about any command can be executed based on the network whereami detects. For example, it is possible to automatically create a VPN connection with whereami and some knowhow with the VPN connection. I have not tried this, but see no reason why it would not work... If anyone does get it, let me know. I hope this helps you.

---

### Post by NTolerance on 2005-04-19
Will this work if scanning isn't supported by iwconfig?  Even though I have an Orinoco wireless card, which is supposedly the most Linux-compatible card there is, scanning is still not supported through iwconfig even after patching the kernel modules for kismet.  I see the syntax with the word "scan" and I don't want to get into this if it's going to be pointless.

---

### Post by Gandalf on 2005-04-19
[QUOTE=NTolerance]Will this work if scanning isn't supported by iwconfig?  Even though I have an Orinoco wireless card, which is supposedly the most Linux-compatible card there is, scanning is still not supported through iwconfig even after patching the kernel modules for kismet.  I see the syntax with the word "scan" and I don't want to get into this if it's going to be pointless.[/QUOTE]
sudo iwlist eth1 scan work??

---

### Post by NTolerance on 2005-04-19
[QUOTE=Gandalf]sudo iwlist eth1 scan work??[/QUOTE]

```
iwlist eth1 scan
eth1      Interface doesn't support scanning : Operation not supported

```

---

### Post by Gandalf on 2005-04-19
[QUOTE=NTolerance]```
iwlist eth1 scan
eth1      Interface doesn't support scanning : Operation not supported

```[/QUOTE]
 hmmmm i was getting the same thing so i went into System -> Administration -> Networking and i set eth1 to "This devise is configured" activate it and since iwlist works

---

### Post by blueplazma on 2005-04-19
[QUOTE=NTolerance]Will this work if scanning isn't supported by iwconfig? Even though I have an Orinoco wireless card, which is supposedly the most Linux-compatible card there is, scanning is still not supported through iwconfig even after patching the kernel modules for kismet. I see the syntax with the word "scan" and I don't want to get into this if it's going to be pointless.[/QUOTE]

I don't really know about that, sorry.  My suspicion is that it will not.

---

### Post by NTolerance on 2005-04-20
[QUOTE=Gandalf]hmmmm i was getting the same thing so i went into System -> Administration -> Networking and i set eth1 to "This devise is configured" activate it and since iwlist works[/QUOTE]

Are you using an Orinoco card?  I'm using Kubuntu though, so I'm not sure what the equivalent is.

---

### Post by Gandalf on 2005-04-20
[QUOTE=NTolerance]Are you using an Orinoco card?  I'm using Kubuntu though, so I'm not sure what the equivalent is.[/QUOTE]
 no i have ipw2200 but i had the same problem
even iwconfig reports MAC address 000000.... but after this the MAC address was there,
i'm not sure about the equivalent neither

---

### Post by blueplazma on 2005-04-20
[QUOTE=NTolerance]Are you using an Orinoco card?  I'm using Kubuntu though, so I'm not sure what the equivalent is.[/QUOTE]

Try running these commands from a shell.  I'm assuming that your wireless card is eth1.  Change eth1 to whatever the interface actually is.
```

sudo ifconfig eth1 up

```

That should do the same thing as what Gandalf did.

---

### Post by NTolerance on 2005-04-20
[QUOTE=blueplazma]Try running these commands from a shell.  I'm assuming that your wireless card is eth1.  Change eth1 to whatever the interface actually is.
```

sudo ifconfig eth1 up

```

That should do the same thing as what Gandalf did.[/QUOTE]

Still the same - scanning not supported.

---

### Post by blueplazma on 2005-04-22
[QUOTE=NTolerance]Still the same - scanning not supported.[/QUOTE]

You might need to look into the networking forum to see if your specific card is supported under Ubuntu.

---

### Post by ulisse on 2005-05-29
Ok, I've seen how to configure whereami to choose between a static wired connection and a wireless, the choiche is all about the cable, if it is inserted or not.
But I can't figure out how to set it up for two static-ip wired network, with different IP ranges.
I have this IP at home network: 192.168.254.253
and this other at work: 192.168.0.251

How can I determine on wich of the two network I am?

---

### Post by ulisse on 2005-05-31
No matter, I solved using "Divine", it can be configured for many static networks and uses ARP instead of ping to determine on wich network the laptop is (either I completely ignore what it means...).
Divine can be found here: [http://www.fefe.de/divine/](http://www.fefe.de/divine/)

---

### Post by reckless2k2 on 2005-07-08
My eth0 is not a problem no matter where I am but I'm having problems with multiple wireless configurations (home, work, random detect of broadcasting ssid).

#detect.conf

#use wired by default
default down

#check for an ethernet cable in the wired interface
testmii eth0 wired

if wired #if it finds a cable
     set INTERFACE eth0
     notat down #then there must be some kind of connectivity, let's use it
else
    notat wired #no cable found, must not be wired
    always set INTERFACE eth1
    testssid <myhomessid> secure-wireless #make sure your ssid is present
    testssid <myworkssid> work-wireless #make sure your ssid is present
fi

#whereami.conf

=rm /etc/network/interfaces.last

+secure-wireless cp /etc/network/interfaces /etc/network/interfaces.last
+secure-wireless cp /etc/network/interfaces.wireless /etc/network/interfaces
+secure-wireless /etc/init.d/networking restart

+work-wireless cp /etc/network/interfaces /etc/network/interfaces.last
+work-wireless cp /etc/network/interfaces.wireless /etc/network/interfaces
+work-wireless /etc/init.d/networking restart

+wired cp /etc/network/interfaces /etc/network/interfaces.last
+wired cp /etc/network/interfaces.wired /etc/network/interfaces
+wired /etc/init.d/networking restart

As it's set now, even if I'm at home, it will look for my work ssid. If I take out my work profile, then it "stops" at home wireless and works. How can I make it work that at home it'll stop at my home ssid and at work it'll detect my work ssid? 

Also, is there a way to detect nonsecure broadcasting networks and setup like if I were at coffee shop with free wireless?

Thanks.

---

### Post by coaxx on 2005-07-26
blueplazma,

thank You very much for Your good HowTo. 

Next days I will configure settings for my notebook (different wlan places, vpn, wired) and will sho 'em (hopefully working) configs here...

Anybody else having experience with devine??

---

### Post by pestilence4hr on 2005-07-27
[QUOTE=blueplazma]
```

	=rm /etc/network/interfaces.old

+home-wired /etc/init.d/networking restart
+home-wired /etc/init.d/firestarter restart
+home-wired setresolver search <put in your settings here>
```
	There are really three things that need explanation here.  First is the equals sign (=), which means to always perform the command, regardless of which network we were on before.  The plus (+) means to perform this command only if we were not on this network before, and the minus (-) means to perform this command only if we were on this network before, but are NOT anymore.  See the [documentation](http://debiana.net/whereami/actions.html) for specifics. [/QUOTE]

Good post, but I think you might have a typo in here.  According to the page you have linked to:

> 
The 'equals' indicates that this action applies whenever whereami finds that you are in this location, regardless of whether your last location was different.


So, I think what you meant to type above was

```

=any rm /etc/network/interfaces.old

```

Otherwise it will try to execute /etc/network/interfaces.old whenever it is entering or exiting the network "rm".  Is this correct?

---

### Post by reckless2k2 on 2005-08-17
bump...bump...

...I'm begging...

is blueplazma even around anymore to respond? 

in the meantime...I'm just using a custom script connected to Kwifi that I run on KDE startup. Dirty but it works. I'd like to get the whereami to work though.

anyone???

My scripts are in posts above....

---

### Post by pestilence4hr on 2005-08-19
[QUOTE=reckless2k2]
anyone???

My scripts are in posts above....[/QUOTE]

I strongly suggest doing the following:

```
sudo whereami --scriptdebug shutdown
sudo whereami --scriptdebug
```

In between putting whereami into shutdown and running it again, you can also check to make sure the interfaces are down (i.e. ifconfig eth0 down).  Using this debug feature, you should be able to figure out what's going wrong.

---

### Post by mlomker on 2005-09-29
Ran across this post while troubleshooting my detect.conf file.  The version of whereami that I have on Hoary amd64 doesn't accept the following syntax, which I've seen in a variety of places:

```

testdhcp 192.168.1.0/24 home-wired

```

This works:

```

testdhcp '192.168.1.*' home-wired

```

Thought I'd pass that along in case someone else is having trouble with the tests.

---

### Post by foxy123 on 2005-10-07
OK, I tried to configure it but miserably failed. I've got a laptop with wired and wireless connection (Broadcom chip PCMCIA card with ndiswrapper). So I need it to autoconfig three types of networks:

1. Wired unsecure
2. Wireless secure (with WEP)
3. Wireless unsecure and unknown

At home I usually use my unsecure wired connection with a direct cable to my router. However, sometimes I have to go downstairs and use wireless. So I want to plug out the cable, insert the card and get the connection without rebooting and changing anything. 

However, sometimes I have to use laptop out of my home with a unknown wireless unsecure network. So I want to boot the laptop and hook on the network automatically. Yes, I know that I want too much.

So I decided to handle my home connections.

First of all I installed whereami and edited detect.conf file in this way (using this topic):

```
default down
testmii eth0 wired
if wired
set INTERFACE eth0
notat down
else
notat wired
always set INTERFACE wlan0
always testssid connexant secure-wireless
fi

```

then I created to files: 
interfaces.wired
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface

iface eth0 inet dhcp

auto eth0

#iface wlan0 inet dhcp
#wireless-essid conexant
#wireless-key *******************

#auto wlan0

```

and interfaces.wireless
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface

#iface eth0 inet dhcp

#auto eth0

iface wlan0 inet dhcp
wireless-essid conexant
wireless-key *******************
auto wlan0
```

basically I took a 'interfaces' file and commented wired stuff in .wireless and vice versa.

Then I edited by copy and paste from this topic whereami.conf file:

```
=rm /etc/network/interfaces.last
+secure-wireless cp /etc/network/interfaces /etc/network/interfaces.last
+secure-wireless cp /etc/network/interfaces.wireless /etc/network/interfaces
+secure-wireless /etc/init.d/networking restart
+wired cp /etc/network/interfaces /etc/network/interfaces.last
+wired cp /etc/network/interfaces.wired /etc/network/interfaces
+wired /etc/init.d/networking restart
```

well, as aresult nothing worked. I guess I did it too mechanically without really geting into it, but I am not good in it at all. I looks quite logical to me I do not know why it did not work. Any help?

---

### Post by mlomker on 2005-10-07
Try:

```

if wired #if it finds a cable
     notat down #then there must be some kind of connectivity, let's use it
else
    notat wired #no cable found, must not be wired
    testap scan wlan
fi

if wlan
    testap <myhomessid> secure-wireless #make sure your ssid is present
    testap <myworkssid> work-wireless #make sure your ssid is present
fi

```

I'm not sure why you're copying your interfaces file back and forth.  Do you use static addresses at all of those places or is it to configure your WEP settings?

I'm attaching my files so you can see what I do.  My connections do not have encryption but it'd be just as easy to add another line to call wpa_supplicant in non-daemon mode or another iwconfig line to set a WEP key.

---

### Post by foxy123 on 2005-10-08
[QUOTE=mlomker]Try:

```

if wired #if it finds a cable
     notat down #then there must be some kind of connectivity, let's use it
else
    notat wired #no cable found, must not be wired
    testap scan wlan
fi

if wlan
    testap <myhomessid> secure-wireless #make sure your ssid is present
    testap <myworkssid> work-wireless #make sure your ssid is present
fi

```

I'm not sure why you're copying your interfaces file back and forth.  Do you use static addresses at all of those places or is it to configure your WEP settings?

I'm attaching my files so you can see what I do.  My connections do not have encryption but it'd be just as easy to add another line to call wpa_supplicant in non-daemon mode or another iwconfig line to set a WEP key.[/QUOTE]
I've got a static addresses at home (10.0.0.3 for wired and 10.0.0.13 for wireless). For any non-home network I have neither ssid nor address, because it maybe new everytime.

I am not sure what to write in whereami.conf.

---

### Post by mlomker on 2005-10-08
> I've got a static addresses at home (10.0.0.3 for wired and 10.0.0.13 for wireless). For any non-home network I have neither ssid nor address, because it maybe new everytime.

I am not sure what to write in whereami.conf.

You'll want to install the **resolvconf** package and if this is a laptop then you should consider [**ifplugd**]("http://www.ubuntuforums.org/showpost.php?p=368604") and making a few changes to use it.

The whereami package is powerful but that also makes it difficult to configure.  You need to look through **man whereami.conf** and **man detect.conf** to see all of the available tests.

You'll need to plug in your essid and default route, dns server IP's, WEP key, etc.

/etc/network/interfaces
```

auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp
auto eth0

iface wlan0 inet dhcp

```


Detect.conf
```

default nonetwork

# Test for the presence of an ethernet connection plugged into eth0
testmii eth0 lan

if lan
  testping '10.0.0.x','10.0.0.253' wiredhome #the .x is your router's IP
  testdhcp '*.*.*.*'
else
  notat lan
  testap scan wlan
fi

if wlan
  testap homessid
  testap .+ openap
fi

if openap
  testdhcp wlan0,'*.*.*.*'
else
  notat openap
fi

```

Whereami.conf
```

+homessid iwconfig wlan0 essid homeessid
+homessid iwconfig wlan0 key xxxxxx
+homessid ifconfig wlan0 10.0.0.13
+homessid ifconfig wlan0 netmask xxx.xxx.xxx.xxx #probably 255.255.255.0
+homessid route add default gw 10.0.0.x #your router
+homessid setresolver search whatever.com nameserver xxx.xxx.xxx.xxx #your DNS IP

-wlan iwconfig wlan0 down

+nonetwork ifconfig eth0 down 
+nonetwork ifconfig wlan0 down

+openap dhclient wlan0

```

---

### Post by foxy123 on 2005-10-09
Thanks a lot, but I am still stuck... wired works, but wireless does not....

What is 
> +homessid setresolver search whatever.com nameserver xxx.xxx.xxx.xxx #your DNS IP?

EDIT: well it works if I do the routine from whereami.conf manually... something wrong in my conf files I guess. Also it assigned 10.0.0.253 IP to my wired and 10.0.0.14 to my wireless. I guess I have to use static for home and dchp for non-home.

---

### Post by mlomker on 2005-10-09
> EDIT: well it works if I do the routine from whereami.conf manually... something wrong in my conf files I guess. Also it assigned 10.0.0.253 IP to my wired and 10.0.0.14 to my wireless. I guess I have to use static for home and dchp for non-home.

The setresolver command creates the /etc/resolv.conf file for your DNS servers using the resolvconf package.

The script that I offered does use static for at home and dhcp non-home--the ifconfig command sets the .13 address.  There is no mention of .14 in that script so I don't know where you would have gotten it.

If you want any more help then you'll need to post all of your files, the output of ifconfig, detailed explanations of what's happening, etc.

---

### Post by foxy123 on 2005-10-09
[QUOTE=mlomker]The setresolver command creates the /etc/resolv.conf file for your DNS servers using the resolvconf package.

The script that I offered does use static for at home and dhcp non-home--the ifconfig command sets the .13 address.  There is no mention of .14 in that script so I don't know where you would have gotten it.

If you want any more help then you'll need to post all of your files, the output of ifconfig, detailed explanations of what's happening, etc.[/QUOTE]
Thanks, sorry to bother you.

Files, mentions in all the posts:
detect.conf
```
default nonetwork

# Test for the presence of an ethernet connection plugged into eth0
testmii eth0 lan

if lan
  testping '10.0.0.2'wiredhome #the .x is your router's IP (I have removed 10.0.0.253 from here)
  testdhcp '*.*.*.*'
else
  notat lan
  testap scan wlan
fi

if wlan
  testap homessid
  testap .+ openap
fi

if openap
  testdhcp wlan0,'*.*.*.*'
else
  notat openap
fi

```

whereami.conf
```
+conexant iwconfig wlan0 essid conexant
+conexant iwconfig wlan0 key ***************
+conexant ifconfig wlan0 10.0.0.13
+conexant ifconfig wlan0 netmask 255.0.0.0 #probably 255.255.255.0
+conexant route add default gw 10.0.0.2 #your router
#+conexant setresolver search whatever.com nameserver xxx.xxx.xxx.xxx #your DNS IP - I have commented it as I do not know what it is...

-wlan iwconfig wlan0 down

+nonetwork ifconfig eth0 down 
+nonetwork ifconfig wlan0 down

+openap dhclient wlan0

```

/etc/network/interfaces
```
auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map eth0

iface eth0 inet static
address 10.0.0.3
netmask 255.0.0.0
gateway 10.0.0.2


iface wlan0 inet dhcp
wireless-essid conexant
wireless-key ****************

auto wlan0

```

/etc/default/ifplugd
```
INTERFACES="eth0"
HOTPLUG_INTERFACES=""
ARGS_eth0="-qfwI -u0 -d10"
SUSPEND_ACTION="stop"

```
/etc/iftab
```
eth0 mac **:**:**:**:**:**
wlan0 mac **:**:**:**:**:**

```
wpa_supplicant.conf
```
ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="conexant"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="*********************"
}

```

So now if I boot the laptop with Ethernet cable plugged in, it connects to the network. The same if I boot it with PCMCIA card plaugged in. However, if I unplug the cable and insert the card I have to go in Networking and activate wireless card and deactivate ethernet to make wireless work. I cannot test any non-home network at the moment.

---

### Post by mlomker on 2005-10-09
Are you running WPA or WEP?  You have both configured.  You don't want to use wpa_supplicant unless you need it.

> 
if I unplug the cable and insert the card


I don't have a card--my wireless is built-in.  The hotplug process might not be working but I don't know anything about that.  

Is the ethernet built-in and you have a card for the wireless?  If you can then leave the card plugged in until you figure everything else out.  It's too difficult to deal with more than one problem at a time.

---

### Post by xianinc on 2005-12-28
Hey, new guy to the forum here.
I just installed Ubuntu on my Gateway laptop and so far have had good luck with everything.  I installed the whereami package and the other network package (forget the name?), but my wireless connections work great.  

My issue is when booting the laptop, it takes forever on "configuring network interfaces", when I switch from my home access point to my work access point.   
If I change my Interfaces file and reboot, it goes much faster and I can connect just as usual.  I was wondering if making the changes to the detect, interfaces, and whereami files would make my boot sequence faster and automatically log me in the the specified network (home or work primarily).  Of course it would be nice to auto-detect "automatically" an unsecured network (if all other options are unavailable), but I'm not too concerned about that.

I've seen some examples here about one wired connection and one secure/unsecure wireless connection, but I mainly run just a secure wireless connection at home and a secure wireless connection at work.  It's rare that I plug into a wired connection, so I'm not concerned with that in this case.

Let's say my home wireless connection is:
ssid = home1
192.168.0.1 network set for dhcp
wep key = abcdefg

My work wireless connection is:
ssid = work1
192.168.1.1 network set for dhcp
wep key = abcdefg

Can someone post a quick config on which files I should update?
I think I'm on the right track, but want to make sure I don't reboot and kill my laptop :)
Thanks in advance!

---

### Post by xianinc on 2005-12-28
I forgot to add my simple interface file info?
-------------------------------------------------------

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp
	network 192.168.0.0
	broadcast 192.168.0.255
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.0.1

auto eth0

iface wlan0 inet dhcp
wireless-essid home1
wireless-key *****************

auto wlan0
----------------------------------------------------------
thanks again!

---

### Post by mlomker on 2005-12-29
You could remove the entry for your wireless card altogether from the /interfaces file and use whereami to do command-line commands based upon your detection script.  I'll be honest, though, my results have been spotty...some of those detection scripts are rather buggy.

Are you running Breezy with gnome?  If so then you should grab network-manager in Synaptic and configure it...it's designed to do all of that.

---

### Post by xianinc on 2005-12-29
Yea, i'm with you on the "spotty" scripts and how they all tie together.
Especially seeing how everything is working just fine with Breezy right now on my laptop, I'm skeptical to mess with too many "fine tunings".

I've got network-manager installed and it works great for one wireless network, but I haven't messed with adding my works info in there for an auto detection?

So if I remove the entry from my /interfaces file, network-manager should do an auto detect?  I'll mess with it later tonight, but thought I'd throw that question out there.  To make things easier (but less secure, I know) I made my home and work WEP keys the same to try and make my life easier, but not sure if that complicates things?  ;)

---

### Post by mlomker on 2005-12-29
[QUOTE=xianinc]So if I remove the entry from my /interfaces file, network-manager should do an auto detect? [/QUOTE]

I don't know, but you'll find other threads about it if you search.  I use KDE and network-manager doesn't integrate as well (okay, the icon is ugly/etc) so I don't use it.  I still have a cobbled together whereami setup, but it's a pain to maintain...that's all.

---

### Post by el3ktro on 2006-01-31
I hope somebody can help me here. I have a laptop, which is either at my home network with a static IP (192.168.1.20) or in any other network at work/university with DHCP, or with no network cable plugged in at all.

I'm currently testing laptop-net, which basically works fine but doesn't support ARP so it's useless for me, because I need this to distinct between my home router and my work router which both have 192.168.1.1, but different MACs of course.

So I need a program that shuts down network if I unplug the cable, and when I plug it in it should look via ARP in which network I am and give me either a static IP or use DHCP. It would also be fine if it could execute some scripts after finding the network (mounting drives etc, starting/stopping services.

Any solution for this?

Tom

---

### Post by mlomker on 2006-02-01
[QUOTE=el3ktro]Any solution for this?
[/QUOTE]

Much of the talk in this thread is **whereami** and it does all of that.  It is a pain to configure, that's all.

---

### Post by ali4728 on 2006-04-16
Hi:
I have a static secure (wep) wireless at home and a dhcp secure wireless at college. I have to "vi" into the /etc/network/interfaces file every time I change location to adjust the wireless settings. How can I utilize "whereami" to recognize and start appropriate wireless settings for my needs? Thanks

---

### Post by ncappel1 on 2006-05-09
Will this method work with a non-laptop computer?

---

### Post by el3ktro on 2006-05-09
[QUOTE=ncappel1]Will this method work with a non-laptop computer?[/QUOTE] Of course it will, there's no difference in a laptop computer and a desktop computer, only that the latter is much bigger :-)

Tom

---

### Post by Polick on 2006-05-10
Hey,

Would whereami work if I have 3 possible networks....one is open (i know htat will work), one is WEP (I'm sure I can get that to work), however the last one is LEAP........yeah, thats right my college isn't Linux friendly.  I've been working on trying to get wpa_supplicant to work properly with LEAP but that isn't a winning battle.  I have a script to Load the LEAPNetwork and the one to return to a regular network.   I read through the thread and didnt see anything helping me extermely (please correct me if I'm wrong)  and I'm not exactly sure where everything goes for whereami and how the scripts link to it.  I'm going to play around with it tonight and see what I can come up with.

Cheers,
Curtis

---

### Post by nekr0z on 2006-06-18
I played around with whereami the whole day long, but the thing didn't work for me. so I removed it and installed network-manager back. After this, network-manager doesn't get DHCP correctly, and I have to manually do "sudo dhclient <interface>".

Does anybody have any idea how to fix it? Everything worked ok until I tried whereami...

---

### Post by barries on 2009-07-24
Besides the fact that I'm a BC (before computers) person, I'm very new to ubuntu as well.
I've got an intel quad core processor on a P5K64 WS motherboard running Ubuntu 9.04 with a 1 Terra bite hard disk. I have loaded Sun virtual box and my intention is to run a number of virtual computers (like a server) with metatrader 4 for people trading forex. Will it be possible to use whereami to setup the dual Gb LAN on the motherboard as well as the virtual network cards of the virtual computers?

Thanks
Gideon

---

### Post by barries on 2009-07-24
I realized that some of the virtual computers will be using XP and some of them will use Ubuntu. I will not be able to setup the Xp network cards but only the ubuntu ones???

---

### Post by Rexhunt on 2011-03-15
Hi, i was wondering if there is a way to have the location automatically switch between home and school without having to restart?

I normally only hibernate my laptop at the end of each day and then when I get home I have to turn off the proxy that we use at school. In the "Network Proxy" option thing at the top there is a drop down menu labeled locations. Is there a way to have it automatically change what is in the location box after restoring from hibernation?

Oh and all the networks are protected wireless networks.

Cheers, Rex

---

