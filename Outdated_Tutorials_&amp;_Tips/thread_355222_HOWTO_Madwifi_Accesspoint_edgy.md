---
title: "HOWTO: Madwifi Accesspoint edgy"
date: 2007-02-06
forum: Outdated Tutorials &amp; Tips
---

### Post by andytof47 on 2007-02-06
Hi All,

Want set up an AP for your home WIFI network? Got an Atheros chipset Wireless Card? Got a Fresh install of edgy?

Yes!!!!!

Good then read on and you'll make an access point out of it in a few minutes
-This howto is my first ever so please be kind - I only want to give back to the ubuntu commnity:)

Coming straight after a fresh load from an edgy 6.10 install CD

also for the very very green - commands are italicized so just copy and paste them:)

open a terminal
1st : [I]sudo apt-get update
[/I]
2nd : *sudo apt-get dist-upgrade    *    
(I can't get the AP up properly unless I do an upgrade first so I recomend you do too)

3rd : Reboot :)

4th : *sudo apt-get install build-essential*

5th : download the current snapshot from here [http://snapshots.madwifi.org/dadwifi-current.tar.gz](http://snapshots.madwifi.org/dadwifi-current.tar.gz)

6th : extract the file to a folder mine is on the desktop so from your home folder cd Desktop then cd to the madwifi folder

7th : *make clean*

8th : *make*

9th : *make install*

10th : choose remove the current module from the system and you have the driver installed good for you!!!!!!

11th : *sudo modprobe ath_pci autocreate=ap*

12th : *sudo gedit /etc/modules*

13th type in *ath_pci autocreate=ap* then save it

14th *sudo gedit /etc/modprobe.d/madwifi*

15th type *options ath_pci autocreate=ap* then save and close

16th *sudo gedit /etc/network/interfaces*

17th *auto ath0*
*iface ath0 inet static*
*address 192.168.3.5*
*netmask 255.255.255.0*
*broadcast 192.168.3.255*
[*wireless-essid WiFiAp*
*wireless mode master* Just change this to suite your network ip addresses

18th setup routing of some sort I use this script for my home network and placed it in
/etc/network/if-up.d    (I got the script from [www.debianadministrator](www.debianadministrator) - simple debian gateway) I name it 00firewall and made it executable and then reboot

[I]#!/bin/sh

PATH=/usr/sbin:/sbin:/bin:/usr/bin

#
# delete all existing rules.
#
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT


# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i ! eth1 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow outgoing connections from the LAN side.
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT

# Masquerade.
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

# Don't forward from the outside to the inside.
iptables -A FORWARD -i eth1 -o eth1 -j REJECT

# Enable routing.
echo 1 > /proc/sys/net/ipv4/ip_forward
[/I] 





19th on a client machine
*iface rausb0 inet static*
*address 192.168.3.5*
*netmask 255.255.255.0*
*broadcast 192.168.3.255*
[*wireless-essid WiFiAp*

20th on the client machine you'll need to setup your isp's DNS settings in the networking panel (can't think of the file right now) because this is a static address setup... Either that or setup a DNS server like bind9 on you AP thats what I did


ping the machine and boingo you should be done

I hope this helps

Please feel free to make suggesstions or even corrections and as for credits???? well I credit myself for doing heaps of reading and re-installing about 10-15 times 

And I credit fairly crappy explanations or complete howto's to the need for writing this one and ironically just as I got to the end of my search for knowledge I found in the forums the very same conlcusion that i came to by doing a search for 

yep you guessed it ath_pci autocreate=ap

It confirmed what I was just about to do so I'm glad the thread was there but it was very obscure.

Cheers All Again I hope this helps

---

### Post by pedalwrench on 2007-02-11
I used these instructions to install Madwifi.
[http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi](http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi)

Seems to work pretty good...I then disable the repo after I installed the madwifi driver.

Also in #4 you missed the word "install"

Thanks for the tutorial

---

### Post by andytof47 on 2007-02-11
> Also in #4 you missed the word "install"

Fixed:popcorn: 


Not a bad link, good to have it here

Cheers

---

