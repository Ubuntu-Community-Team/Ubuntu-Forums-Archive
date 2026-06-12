---
title: "HOWTO: Laptop with ethernet and wireless and ifplugd"
date: 2005-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by department27 on 2005-06-23
This is the first HOWTO i've written so be patient with me. ;-)

I have a laptop (dell d600) with both inbuild ethernet and wireless (intel 2200). The thing that I found frustrating is the I could not get Ubuntu to switch between the ethernet and wireless when I plugged out the ethernet. I always had to manually select the wireless. So I downloaded ifplugd which in theory should do this but it never worked for me.

After playing with it for a while I have managed to get it working perfectly, although it does not seem to be the recomended way.

So here goes.

Assumption: 

eth0 = inbuilt ethernet card
eth1 = wireless card

The two packages you need to download are ifplugd and ifmetric.

Once you have these installed you need to change the following files:

/etc/network/interfaces

add up ifmetric eth0 0 & up ifmetric eth1 1

ifmetric assigns a route metric to the interfaces. In my case eth0 is give a lower metric hence is is the primary interface.


Here is mine as an example:

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
up ifmetric eth0 0

iface eth1 inet dhcp
wireless-essid dept27
up ifmetric eth1 1

auto eth0

auto eth1


Now according to the ifplugd blurb you should coment out any auto interfaces that you will put in ifplugd. That does not work. Well it did not work for me at any rate.


Then you edit /etc/default/ifplugd

# This file may be changed either manually or by running dpkg-reconfigure.
#
# N.B.: dpkg-reconfigure deletes everything from this file except for
# the assignments to variables INTERFACES, HOTPLUG_INTERFACES, ARGS and
# SUSPEND_ACTION.  When run it uses the current values of those variables
# as their default values, thus preserving the administrator's changes.
INTERFACES="eth0 eth1"
HOTPLUG_INTERFACES=""
ARGS="-q -f -u0 -d10 -w -I"
SUSPEND_ACTION="stop"

Add eth0 and eth1 to the INTERFACES line as above.

And that is basically it. I also have netapplet running, the one from backports.

What you will find is that when you boot you machine with the ethernet plugged in it will use that as the primary interface. If you unplug the ethernet it will start to use the wireless, and plug it back in it reverts to the ethernet.


Hope this helps someone.

---

### Post by moment on 2005-06-23
This is great! but when I boot my laptop while ethernet is unplugged I have a 30sec delay in configuring networks. Do you know what's that?

---

### Post by department27 on 2005-06-23
Yep that is a problem at the moment. I think it's do do with the dhcp time delay. Not sure how to fix that at present. :-(

---

### Post by Alexander Kirillov on 2005-06-23
[QUOTE=moment]This is great! but when I boot my laptop while ethernet is unplugged I have a 30sec delay in configuring networks. Do you know what's that?[/QUOTE]
 It seems that the problem is caused by "mapping hotplug" lines. These lines are supposed to use hotplug subsystem, bringing up eth0 when the cable is plugged in (thus, in effect, doing exactly the same thing as the solution suggested here). However, it does not seem to work. See some discussion here: 

[http://ubuntuforums.org/showthread.php?t=32361](http://ubuntuforums.org/showthread.php?t=32361)

---

### Post by moment on 2005-06-23
OK I think I've found a way to get around this problem (might not work for others!).

I commented out the hotplug and also the auto lines in the /etc/networking/interfaces and changed the "ARGS" line in /etc/default/ifplugd to this:

ARGS="-q -f -u5 -d10 -w -I -b"

to have a delay of 5s between interface changes.

---

### Post by department27 on 2005-06-23
[QUOTE=moment]OK I think I've found a way to get around this problem (might not work for others!).

I commented out the hotplug and also the auto lines in the /etc/networking/interfaces and changed the "ARGS" line in /etc/default/ifplugd to this:

ARGS="-q -f -u5 -d10 -w -I -b"

to have a delay of 5s between interface changes.[/QUOTE]

Tried that it did not work for me. Did some more playing and found that if you put in static ip address there is no delay. Hence I think it is a DHCP time delay.

---

### Post by Heliode on 2005-06-23
[QUOTE=department27]Tried that it did not work for me. Did some more playing and found that if you put in static ip address there is no delay. Hence I think it is a DHCP time delay.[/QUOTE]

I have the same problem, but only with my wireless interface. Setting a static IP solves the problem, but that's not really an option since I need to use it at school where IP's are dynamically asigned. So if someone could point out how to solve this, or how to change the DHCP timeout, that would be great!

---

### Post by department27 on 2005-06-23
[QUOTE=Heliode]I have the same problem, but only with my wireless interface. Setting a static IP solves the problem, but that's not really an option since I need to use it at school where IP's are dynamically asigned. So if someone could point out how to solve this, or how to change the DHCP timeout, that would be great![/QUOTE]

Ok did some more playing. The is a dhcp conf file in /etc/dhcp3/ called dhcpclient.conf

If you have a look at that you will see that everything is commented out.

So I just uncommented and changed some time values. Here is what I set the values to:

timeout 5;
retry 5;
reboot 5;
select-timeout 5;
initial-interval 2;

Before I found that I had to wait 60 seconds before ubuntu finished configuring network (assume that is the default)
Now it waits 12 seconds.

I think there is a lot more too this config file. Will try to get more info on it, and see if anything else needs changing. 

There was an option which you could pass to dhcp that lets the process carry on to run in the background, but have no idea how to set that.

---

### Post by Heliode on 2005-06-24
[QUOTE=department27]Ok did some more playing. The is a dhcp conf file in /etc/dhcp3/ called dhcpclient.conf

If you have a look at that you will see that everything is commented out.

So I just uncommented and changed some time values. Here is what I set the values to:

timeout 5;
retry 5;
reboot 5;
select-timeout 5;
initial-interval 2;

Before I found that I had to wait 60 seconds before ubuntu finished configuring network (assume that is the default)
Now it waits 12 seconds.

I think there is a lot more too this config file. Will try to get more info on it, and see if anything else needs changing. 

There was an option which you could pass to dhcp that lets the process carry on to run in the background, but have no idea how to set that.[/QUOTE]


worked great for me, thanks a lot! You've saved at least part of my life from certain boredom! ;)

---

### Post by department27 on 2005-06-24
[QUOTE=Heliode]worked great for me, thanks a lot! You've saved at least part of my life from certain boredom! ;)[/QUOTE]

No problem. YOu may find that those values need to be tweak if the dhcp server is overloaded, but they should be OK.

---

