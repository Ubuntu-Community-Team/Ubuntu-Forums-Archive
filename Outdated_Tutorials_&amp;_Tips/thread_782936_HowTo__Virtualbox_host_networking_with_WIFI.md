---
title: "HowTo : Virtualbox host networking with WIFI"
date: 2008-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by bluefrog on 2008-05-05
Virtualbox host networking and WIFI.

[COLOR="Red"][B]Virtualbox > 2.1.4 and Jaunty. Virtualbox does that on its own now. Select host interface (or bridge network in 2.2) and then your wifi card.
No need for this lengthy howto anymore...[/B][/COLOR]

**[SIZE="3"] Scope of this HowTo [/SIZE]**
While being connected to your router (thus the Internet) via your laptop WIFI card, enable host networking on a different subnet by bridging your ethernet card.
Your ethernet card does not have to be physically connected to your network for this to work.

Your Virtualbox machines will be connected to the Internet as well.

The tutorial is constructed as follows:
  similar settings to Vbox > 2.1.0 and Vbox < 2.1.0
  Vbox > 2.1.0
  Vbox < 2.1.0
  Guest configuration

Tested and working with the following:
Virtualbox 1.5.6, 1.6.0, 1.6.2   Ubuntu 8.04 Hardy Heron
Virtualbox 2.0.4, 2.0.6          Ubuntu 8.10 Intrepid Ibex
Virtualbox > 2.1.0               Ubuntu 8.10 Intrepid Ibex

**[SIZE="3"]Pre-requisites[/SIZE]**
One computer with:
ethernet controller eth0
WIFI Controller     eth1 (or wlan0 or whatever you have, change accordingly to your system)
Virtualbox
Internet connection thru eth1 (WIFI)
 
All the bridge creation and host interface creation knowledge comes from Virtualbox help contents. (see chapter Host Interface Networking and bridging on Linux hosts, version 2.0.6 or previous, as of 2.1.0 host networking is "integrated" in VBox)

**[SIZE="3"]HowTo - by example[/SIZE]**
Consider a connection to the internet via eth1 (WIFI) with IP 192.168.1.2 (netmask 255.255.255.0).
The bridge IP address will be 192.168.**0**.2 (same netmask as above - **note the difference of subnet between the wifi and the bridge**).

Bridge br0 will include eth0 (ethernet card) and the host interfaces (tap0, tap1 ... - only for Vbox < 2.1.0)

I will assume that virtualbox is up and running for the user joe. 

[INDENT]**[SIZE="2"]_[COLOR="Red"]Similar settings[/COLOR]_[/SIZE]**[/INDENT]
Install the necessary tools
```
sudo apt-get install bridge-utils 
```

Modify /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
address 192.168.0.2
netmask 255.255.255.0
    bridge_ports eth0
    bridge_maxwait 0

```

Restart networking
```
sudo invoke-rc.d networking restart
```

Enable ip_forwarding: modify /etc/sysctl.conf
```
net.ipv4.ip_forward=1
```

While it is not necessary to create a firewall service to enable masquerading, it will be much easier to activate if you do so. You can use ufw if you prefer.

```
sudo vi /etc/init.d/firewall
#/bin/bash

start() {
	echo "Creating iptables rule"
	iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
}

stop() {
	echo "Flushing iptables"
	iptables -P INPUT ACCEPT
	iptables -P FORWARD ACCEPT
	iptables -P OUTPUT ACCEPT
	iptables -t nat -P PREROUTING ACCEPT
	iptables -t nat -P POSTROUTING ACCEPT
	iptables -t nat -P OUTPUT ACCEPT
	iptables -F
	iptables -t nat -F
	iptables -X
	iptables -t nat -X
}

case $1 in
	start) 	start;;
	stop) 	stop;;
	restart) 	stop
			start;;
	status) /sbin/iptables -L
		/sbin/iptables -t nat -L
		exit 0;;
	*) 	echo "Usage: firewall {start|stop|restart|status}"
		exit 1
esac
exit
```

Make the script executable
```
sudo chmod u+x /etc/init.d/firewall
```

Create links for the service to be started/stopped automatically
```
sudo update-rc.d firewall defaults
```

Start the service to enable masquerading
```
sudo invoke-rc.d firewall start
```

[INDENT]**[SIZE="2"][COLOR="Red"]_VBox 2.1.0_[/COLOR][/SIZE]**[/INDENT]
The configuration is almost over.
You just need to select host interface in the virtual machine settings and choose br0.

[INDENT]**[SIZE="2"][COLOR="Red"]_VBox < 2.1.0_[/COLOR][/SIZE]**[/INDENT]

```
sudo apt-get install uml-utilities
sudo gpasswd -a uml-net $USER
sudo chgrp uml-net /lib/udev/devices/net/tun
sudo chmod g+rw /lib/udev/devices/net/tun

```
(reboot necessary unless someone has another solution. You can change the ownership of /dev/net/tun right away and wait for a later reboot)

[INDENT]**If you want to create a permanent host interface**[/INDENT]
change /etc/network/interfaces to
```
auto lo
iface lo inet loopback

auto tap0
iface tap0 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user joe    ###replace joe with the name of your user member of vboxusers and uml-net groups##

auto br0
iface br0 inet static
address 192.168.0.2
netmask 255.255.255.0
    bridge_ports eth0 tap0 #tap1 tap2 ...
    bridge_maxwait 0

```
Add as many host interfaces (tap1 tap2 ...) as desired on the same principle. If you do so, don't forget to add them to the bridge.

Restart networking
```
sudo invoke-rc.d networking restart
```

Assign tap0 (tap1 ...) as a host interface to your virtual machine.

[INDENT]**I prefer dynamic host interfaces**[/INDENT]
To create dynamic tap interfaces (from the virtualbox help, 6.7.2. Creating interfaces dynamically when a virtual machine starts up):
* create a start up script (wherever you want, just remember where), replace joe with your user member of vboxusers and uml-net groups
```

cat > /home/joe/addtap.sh <<eof
#!/bin/bash

# Create an new TAP interface for the user 'joe' and remember its name.
interface=\`VBoxTunctl -b -u joe\`## replace joe with your user

# If for some reason the interface could not be created, return 1 to
# tell this to VirtualBox.
if [ -z "\$interface" ]; then
exit 1
fi

# Write the name of the interface to the standard output.
echo \$interface

# Bring up the interface.
ifconfig \$interface up

# And add it to the bridge.
brctl addif br0 \$interface
eof

chmod u+x /home/joe/addtap.sh

```

* create an end script
```

cat > /home/joe/deltap.sh <<eof
#!/bin/bash

# Remove the interface from the bridge.  The second script parameter is
# the interface name.
brctl delif br0 \$2

# And use VBoxTunctl to remove the interface.
VBoxTunctl -d \$2
eof

chmod u+x /home/joe/deltap.sh

```

In the virtual machine network settings, do the following changes
attached to: host interface
interface name: (nothing, leave it empty)
setup application: gksudo /home/joe/addtap.sh
terminate application: gksudo /home/joe/deltap.sh

if you wish to avoid typing your password when the tap interface is created, add the following line to your sudoers file
```

sudo visudo
%vboxusers ALL=(ALL) NOPASSWD: /home/joe/addtap.sh, /home/joe/deltap.sh

```

[INDENT]**[SIZE="2"][COLOR="Red"]_Guest configuration_[/COLOR][/SIZE]**[/INDENT]

[SIZE="2"]**1) No DHCP server**[/SIZE]
If you have no dhcp server serving the 192.168.0.0 range, you will need to assign an IP address in the 192.168.0.0 range to your virtual machine once it is started.
```
sudo ifconfig eth0 192.168.0.3
```
 
It will be necessary to add 192.168.0.2 as a default route as well
```
sudo route add default gw 192.168.0.2
```

If you want to make it permanent, edit /etc/network/interfaces of your virtual machine.
```
auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.2
```

**[SIZE="2"]2) DHCP server[/SIZE]**
You have a dhcp server serving on the 192.168.0.0 range 
either locally (laptop):
make sure the "option routers" given by dhcp is the IP of your bridge br0 (192.168.0.2)

or on your ethernet LAN connection:
nothing to do (in that case, your access to the internet will occur thru ethernet most certainly and not thru WIFI)

James Dupin
[https://wiki.ubuntu.com/VirtualboxHostNetworkingAndWIFI](https://wiki.ubuntu.com/VirtualboxHostNetworkingAndWIFI)

---

### Post by areayetee on 2008-06-21
You are my Hero, after many many failed attempts i have my wifi bridged (Ubuntu Hardy Host / Win XP Guest). I can now enjoy my slingplayer goodness from my home network without having to reboot and load up my windows partition. I followed the instructions but then realized that my network did not fit your pre-requisites.
the alias on my devices were different fixed it with info i found on this thread:
[http://ubuntuforums.org/showthread.php?t=496532](http://ubuntuforums.org/showthread.php?t=496532)
that got me in the ball park then i followed your steps for dynamic setup,
then got real frustrated
cause when i set my virtual box settings
"In the virtual machine network settings, do the following changes
attached to: host interface
interface name: (nothing, leave it empty)
setup application: gksudo /home/joe/addtap.sh
terminate application: gksudo /home/joe/deltap.sh"

Vbox wouldn't load 
I was about ready to give up and undo what i had done so far, but i tried changing from "host interface"
to "nat"
Loaded up again.... and bango booya ...bridged network goodness and my slingplayer is now working in virtualbox on my home network....yah
(a bit long winded but im excited to be able to use my favorite windows app again):guitar:

---

### Post by bluefrog on 2008-06-23
You don't need to do all that if you use NAT. NAT is working out of the box with wifi or ethernet. (this how to has a specific use people who need it will recognize)

So basically, if you are using NAT, all you have done following this howto is useless. Would have worked anyway (normally).

You say VBox wouldn't load. What was the error message? Make sure you adapted the commands/lines in script to fit your architecture (example: replace joe with your user name, and adapt the path to where you created the scripts) and make sure your user is a member of the uml-net group (you need to log out/ log in after having added the user to the group) and that the following lines are written as is (VBox machines settings, as if you write gksudo then select the script with the "explorer" button in the settings window, gksudo will disappear.
setup application: gksudo /home/joe/addtap.sh
terminate application: gksudo /home/joe/deltap.sh

---

### Post by lezzard on 2008-07-06
Hi, thanks for the howto :KS, but unfortunately I can't get my VBox to work with a bridged connection... I've followed several tutorials but so far no luck. Here's my setup:

My Box:
-Dell Inspiron 1420N w/Ubuntu Hardy.
-eth0 is wifi / eth1 is wired.
-VirtualBox 1.5.6_OSE hosting a Windows XP VM.

I need to be able to gain direct (or transparent) access to several different LAN networks, each with their own DHCP, DNS and internet gateway. 

It'd be nice if I could bridge both of my ethernet interfaces (wired and wireless) to my VMs, but wireless is definitively a priority.

I followed your tutorial step-by-step, except for "*make sure the gateway given by dhcp is the ip of your bridge br0*". How do I know the IP of my br0 bridge? Do I have to tweak every DHCP I use? (I don't have admin access to some)

Please help me, I'm new to linux and I'm loving it, but I really need to get this right for my work. I really don't wanna install Windoze natively!

Thanks in advance. :KS

---

### Post by bluefrog on 2008-07-08
If you followed that HowTo, you have given br0 an IP, so you know it.

And what is failing if you followed that HowTo? Please give details as of what is the error and if you followed that HowTo concerning that error.

For the rest, I don't understand what you want to do as if there are several dhcp servers (with different subnets of course) on your network(s) how are you going to do to get an IP from a specific server, but well this is your problem. The only thing that would be of some sense to me is for you to assign an IP to each of your virtual machines (inside the virtual machine) so that they can talk on the different subnets you have.

If you read carefully that HowTo, you will see that I do not bridge the wifi interface but only the ethernet interface, but I use the wifi interface to get out of the laptop.
Bridging the wifi interface do not work 99% (or more or less, I don't know) of the time due to wifi card restrictions.

---

### Post by svaens on 2008-07-12
Hi, 
I also am trying to get this to work, and thus far have had little luck (on this machine). 
I went for your preferred method, the dynamic host interface, and so, I modified the /etc/network/interfaces file as specified. 
This is, I believe, where things go wrong for me. 
With this file modified so, I no longer get an address from my dhcp. I found this out when I restarted networking.... 
I wasn't quite sure what was going on (as i am... new to messing about with networking) and so i did the super sure reboot, and the problem still existed. Reverting the interfaces file to its original state and restarting networking fixed my wireless. 

What do you believe may be the problem here? 

Thanks in advance!

sean

p.s. stupid newbie question, but how do I know which interface is my wireless, and which is my ethernet?  By looking at the output from 'ifconfig' and seeing that the eth1 is the more verbose, and knowing that I only ever use wireless, i would have assumed that the eth1 is my WIFI controller, and eth0 is my ethernet.....  This I assume would make a big difference to it working or not? 

Just in case, here is a printout from my ifconfig when all is fresh and as normal: p.s. I think the vm interfaces at the bottom were created by my installation of vmware some time back..... no?

```
sean@svUbuntuX:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:0d:9e:52:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:81:93:eb  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2dff:fe81:93eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2653334 (2.5 MB)  TX bytes:540078 (527.4 KB)
          Interrupt:11 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57430 (56.0 KB)  TX bytes:57430 (56.0 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.241.1  Bcast:192.168.241.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.152.1  Bcast:192.168.152.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sean@svUbuntuX:~$ 
```

---

### Post by zeefux on 2008-07-12
I follow you step "sudo gpasswd -a $USER uml-net" -a is "Command line option 'a' [from -a] is not known" is there any reference ?? to do help.

thanks
Zyke

---

### Post by bluefrog on 2008-07-14
**to Zeefux:** 
sudo gpasswd -a $USER uml-net  works as is on a "normal" ubuntu distro and should work as is on any?/most Linux distro.
gpasswd is a tool to administer the /etc/group file (man gpasswd).
You could use usermod as well but the syntax is usermod -aG group user (failure to write "a" will replace all your groups by the new group, that is why I prefer gpasswd when I explain how to add a user to a group)

**to Svaens:**
Use iwconfig to be sure.
Your vmnet network interfaces come from vmware indeed. They should have been removed when you removed vmware. Don't know if they can disturb what you are trying to do.
In the HowTo I do not do anything about eth0 or eth1 in the file /etc/network/interfaces, so if you touched that file according to the HowTo there is no reason for your card to not getting a dhcp address.
Are you using Ubuntu or Kubuntu? Do you have the network-manager running?

---

### Post by svaens on 2008-07-14
Hi, and thanks for the reply bluefrog!
iwconfig shows my eth1 to be the wireless. 

```
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"HoneyPie"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:E3:6C:1C:7C   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/92  Signal level=-47 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:31
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.
```

I guess that means I need to modify your scripts (and instructions) to swap your usage of eth0 and eth1 ?

As for your comments and questions, 
the vmnet interfaces, they are there because I never did uninstall vmware in any way. I never considered that the existing interfaces that it has left could cause me trouble. I am no expert, but i wouldn't have expected it. If nothing else works, I will remove them. 

It is strange that my network halts with the interfaces file modified... yes. But i did indeed simply copy your text exactly into the file. 
But you do mention eth1 in the file, in the line:
```
bridge_ports eth1
```
Obviously, I do not know enough about it, and I should (and will) try to read up on how this file is used by the networking components. But any hints and help from you would be heartily welcome! ;)

I am using Ubuntu by the way. Hardy 8.04, fully up to date Ubuntu. 
And yes, I would say the network-manager is correctly running... I checked just now and I see the nm-applet in the process list.. (i assume that is it? ). 

Actually, Looking through your HowTo, the interfaces file is the 'Only' place you mention either eth0 or eth1. Not mentioned in the create script at all.....  How is it working? What could be going wrong with my situation?

---

### Post by bluefrog on 2008-07-15
The problem came as you bridged your wifi card.

if eth1 is your wifi card then use this configuration:

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto br0
iface br0 inet static
address 192.168.1.20      ## replace by your preferred IP
netmask 255.255.255.0     ## replace by your preferred subnet mask
    bridge_ports eth0
    bridge_maxwait 0

```

---

### Post by svaens on 2008-07-15
Hi, and thanks again for the reply. 
I am not at home to try this yet, but I shall as soon as I get outta work.

I would like not to have to rely on the good will of fellow Ubuntu users (although the community here are very nice, and have never begrudged any help giving). 

Could you give me a good suggestion as to WHERE I could find a good book, or internet site which explains the sort of things one needs to understand to be able to;

1. understand the use of the linux tools for networking, and
2. understand these networking issues. 

As a bit of a programmer, I know socket work, and have a general understanding of tcp/ip etc, but never got into this kind of scale networking issues. .. so bridges and interfaces, eth0, eth1 are all a bit like black magic to me. Do you have a suggestion? I would like to one day be able to do this for myself, and know why and how. And one day, It could be me helping others, like you have helped me today. 

Thanks again!

---

### Post by svaens on 2008-07-15
Hi again, 

Actually... i really need a book now. The fix didn't fix it. 
I modified the interfaces file to match the suggested code, and promptly restarted the machine. On restart and login, I again had no internet, and could not even contact the router, or ping anything (on the real computer, the host). When I do an ifconfig, I can see there are 'errors' in the TX Packets... not that that means much to me yet... 

Here is the output from two commands, ifconfig, and iwconfig, 
in the hope it might tell you something. 

**ifconfig**
```

br0       Link encap:Ethernet  HWaddr 00:08:0d:9e:52:12  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fe9e:5212/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:14550 (14.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:08:0d:9e:52:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:81:93:eb  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2dff:fe81:93eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:352 (352.0 B)  TX bytes:8216 (8.0 KB)
          Interrupt:11 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33872 (33.0 KB)  TX bytes:33872 (33.0 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.241.1  Bcast:192.168.241.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.152.1  Bcast:192.168.152.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

**iwconfig**
```
eth1      IEEE 802.11b  ESSID:"HoneyPie"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:E3:6C:1C:7C   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/92  Signal level=-53 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:1
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

thanks again for your help!

---

### Post by bluefrog on 2008-07-16
read the HowTo again. Your wifi card and the bridge MUST NOT be on the same subnet otherwise it will not work (as it is not working right now for you).

As apparently your wifi card is in the 192.168.1.x range then your bridge needs to be in the 192.168.0.x range.

Change your bridge IP in /etc/network/interfaces from 192.168.1.20 to 192.168.0.20

---

### Post by svaens on 2008-07-16
hi. 

done that now. 

Progress is made. My host (ubuntu) has a working network and internet. 
However, the guest not. 

Looking at a ifconfig, I can see that the script made the tap0 ok, 
but there are still these errors at the RX and TX packets (see below). 

I will start reading about all this now, and see if it all makes sense to me. However, If you can see what potential problems may be, please let me know. 

p.s. I didn't really understand what you meant by this paragraph:

```
2) DHCP server
You have a dhcp server serving on the 192.168.1.0 range
either locally (laptop):
make sure the gateway given by dhcp is the ip of your bridge br0

or on your ethernet LAN connection:
nothing to do (in that case, your access to the internet will occur thru ethernet most certainly and not thru WIFI)

```

I have DHCP enabled in my router. What do you mean by "make sure the gateway given by dhcp is the ip of your bridge br0"

not only that, but the script doesn't work in the VirtualBox settings. 
It always comes back with **error** (see below). To test anyway, I enter the name of the created tap 'tap0' in the host interface name of the settings for my vm, and start. 
Then the vm starts, but it does not get a network. 


**error**
```
Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).
Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

although it still makes the tap0 interface, and when I run it from the command line, i can see that it prints to standard out the name of the tap interface it just created.

**This is my exact create script, just as yours i think.**
```

#!/bin/bash
echo "Setting up a new TAP interface for the user 'sean'"
interface=`VBoxTunctl -b -u sean`
if [ -z "$interface" ]; then
exit 1
fi
echo $interface
ifconfig $interface up
# And add it to the bridge.
brctl addif br0 $interface

```

thanks again for your patience. 


**ifconfig**
```
br0       Link encap:Ethernet  HWaddr 00:08:0d:9e:52:12  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fe9e:5212/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28556 (27.8 KB)  TX bytes:15332 (14.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:08:0d:9e:52:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:81:93:eb  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2dff:fe81:93eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3049792 (2.9 MB)  TX bytes:1462947 (1.3 MB)
          Interrupt:11 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42882 (41.8 KB)  TX bytes:42882 (41.8 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:c5:40:47:10  
          inet6 addr: fe80::2ff:c5ff:fe40:4710/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:30248 (29.5 KB)  TX bytes:8402 (8.2 KB)
```

---

### Post by svaens on 2008-07-16
hmmm... 

i just did some more reading, and did a brctl showstp
I noticed it lists my eth0 as disabled (state = disabled). 
This can't be good... and while still being ignorant of how all this works,... i wouldn't be surprised if you were to say 'that is the reason! Enable it!'. 

What do you think? How do I enable this thing?

```
eth0 (1)
 port id		8001			
state		       disabled
 designated root	8000.00080d9e5212	
path cost		 100
 designated bridge	8000.00080d9e5212	
message age timer	   0.00
 designated port	8001			
forward delay timer	   0.00
```
 designated cost	   0			
hold timer		   0.00
 flags

---

### Post by svaens on 2008-07-16
Hi. More progress.. 

In light of what I thought I had discovered (from the last post), 
I decided I needed to try and make this eth0 interface seem NOT disabled. 

I didn't know any way to do this besides actually connecting it to the ethernet port of my router, via cable. 

so, connected it, got the green light happening at the base of the connector.. great!

create the tap0 (i still haven't resolved the problem of it not working from VirtualBox), start virtual box with tap0 specified in the 'host interface' settings, 

and it works!!!! My guest now has network. It can even get out to the internet from it. My guest cannot ping by host name (but maybe this is an issue of the dns? ) but it can ping it via the ip address which the dhcp has given it. 

HOWEVER, THIS IS NO SOLUTION!!! 
I do not want to be connected to the router via the cable, just so I can get the host interface working for my virtual machine! I just did this to test the idea. 

Again. How can I get my eth0 working without sticking the cable in?

p.s. while I have the cable in, I am not using it to connect to the network. The wireless is being used for that. In fact, with the current settings of course i cannot actually connect to the network with the cable (eth0).

Thanks and kind regards, 

sean

---

### Post by bluefrog on 2008-07-17
host interface creation problem.
Looks like a permission problem to me even though you apparently did not paste the whole error message which is in the pop up windows.

Check the /dev/net/tun part of the HowTo.

eth0 being disabled with the brctl command is not surprising if the cable is not plugged in.

For the rest read carefully, you have all the answers in the sentences, I cannot explain more than what I did.

example:
"make sure the gateway given by dhcp is the ip of your bridge br0"
dhcp server... either locally or on your ethernet LAN connection

meaning install a dhcp server on your host or assign an IP address in the guest.

---

### Post by svaens on 2008-07-17
Hi, 

**firstly**, you do say explicitly "Your ethernet card does not have to be plugged for this to work.". 

Was I wrong to take this to mean I don't have the cable plugged into the ethernet card for this to work? For if the whole point is to get this working using wireless, it kind of defeats the purpose if i have to have the cable plugged in anyway!

**secondly**, 

Of course I followed your HowTo regarding the permissions. 
> At this stage /dev/net/tun owners should be root.uml-net, change accordingly if this is not the case.
Yes, this was checked, found to be incorrect, and already since days, modified to be as you specified. 

I did think I pasted the whole message in from the pop up box. If I didn't, it was in error. 

**Third**,

you said:
> meaning install a dhcp server on your host or assign an IP address in the guest. 

ok, "assign an IP address in the guest" I understand. 
What do you mean by "install a dhcp server on your host" ? 

My DHCP is provided by my wireless router. I do not want to have to install a second somewhere to get this working. 

As I have said, I have the DHCP enabled, and it works. This shown by the fact that my laptop, my partners laptop, and my guest vm (when I have the cable plugged in) all get an ip address assigned by the DHCP.

so, the question still stands. 
How do I get it working so that my "ethernet card does not have to be plugged" ?

---

### Post by bluefrog on 2008-07-17
you will not be able to use your router's dhcp if you don't plug in the cable, so assign an IP to your guest or install a dhcp3 server on your host if you don't want to assign an IP.

The quickiest and easiest is to assign an IP.

---

### Post by svaens on 2008-07-17
ahh... ok. 

so. If I understand correctly, 

Because for some reason, we cannot bridge the wireless interface, and
the wireless was where I was connecting to dhcp, 
my guest cannot contact dhcp, and therefore cannot be given an IP Address. 
Is this correct?

If this is so, How is it that my guest will get a network at all?

If this networking in the end looks like this:

```

    |---- eth0 (disconnected ethernet)
br0-|
    |---- tap0 

eth1 (WLAN)

```

It kind of looks like that part of my hosts networking that is connected to the network (eth1) is totally isolated from the part that the guest needs to use to connect (tap0). 

Or do I not understand enough.. 

Thanks anyway.

---

### Post by bluefrog on 2008-07-17
hence ip forwarding and iptables masquerade.

for the explanation, if not mistaken (networking is far from being my specialty), when the guest is looking for an internet address it takes the gateway you've given it then on the host it knows (netstat -rn) it has to go thru the wifi interface to get out. ip forwarding and masquerading will help the information to go back to the guest.

Any network knowledgeable person is welcome to correct that explanation.

---

### Post by echo6 on 2008-07-30
I'm getting the following error >  /etc/network/run/ifstate: No such file or directory

Using Ubuntu Hardy.

---

### Post by bluefrog on 2008-08-04
when running what command?

---

### Post by Mgiacchetti on 2008-09-03
I've just upgraded to intrepid ibex and this happens to me as well

/etc/network/run/ifstate: No such file or directory 			 		

That happens about 4 times if i do sudo /etc/init.d/networking restart   with my vbox0 and br0

only twice if i do it without vbox0 and br0

ALSO   if i have vbox0 and br0 in etc/networking/interfaces  i cannot get online.

---

### Post by bluefrog on 2008-09-05
I haven't tested with intrepid and will not be able to do so before some time.

So far this HowTo only applies to hardy.

---

### Post by gidkill on 2008-09-12
[QUOTE=bluefrog;5730927]

...

not only that, but the script doesn't work in the VirtualBox settings. 
It always comes back with **error** (see below). To test anyway, I enter the name of the created tap 'tap0' in the host interface name of the settings for my vm, and start. 
Then the vm starts, but it does not get a network. 


**error**
```
Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).
Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

....

I saw this error too. What caused it was not having the correct path for the scripts. As soon as I fixed the path, it worked. I would think that permissions issues on the path or the file itself would also cause this.

---

### Post by bluefrog on 2008-09-13
sorry, don't know if you ask for help. 
If so then please explain your problem clearly.

several things can prevent the addtap.sh script from working.

- missing gksudo in front of it
- script being in a hidden folder (.folder/addtap.sh)
- wrong permission on /dev/net/tun

---

### Post by bluefrog on 2008-12-23
Version 2.1.0 of Virtualbox makes it very easy to set up "normal" host networking (networking through the ethernet card).

You still need some little tweaks to have host networking, wifi and internet on host and guest.

I have updated the HowTo to reflect the change.

---

### Post by maphilli14 on 2009-04-02
I would like to add to this great guide is around the file:

/etc/init.d/firewall 

Explanation, this creates the 'nat' portions of ip routing such that the guest network 192.168.0.x /24 (255.255.255.0) has connectivity to the rest of the Internet/Network.  Only reason I mention is that it is critical for this to work.  It also means that the line in this file:

	iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

must use the right interface.  In my install eth1 didn't exist it was wlan0.  Check this line to make sure you use the right "Internet" facing network.

HTH,  great guide!

Mike

---

