---
title: "Trouble setting up hotspot"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by nevthinking on 2013-01-22
Hi!
I'm an Ubuntu newbie and I was searching for a way to setup hot-spots using Ubuntu like I do with Connectify on windows. I came across this method in xda forums 
[http://forum.xda-developers.com/showthread.php?t=2009381](http://forum.xda-developers.com/showthread.php?t=2009381)
which I used to succesfully run a hotspot in my Ubuntu 12.10 . 

The problem is that now I have switched back to Ubuntu 12.04 preferring the LTS version and now when I try the same method, I am unable to setup the hotspot. 
When I run the final script in console I get a message that says "failed to create listening socket for 127.0.0.1 : Address already in use"

I'm unable to find any workaround and I'm pretty sure that I've followed the exact same procedure as mentioned int the forum. I've even tried removing both the hostapd and dnsmasq and redoing all the steps. Nothing works, please advise.

---

### Post by cepal on 2013-01-23
which final script, please provide exact contents of the script and exact output. Otherwise we can only guess what you're doing.

My first assumption is you're substituting by a wrong NIC device name (lo instead of eth0, eth1 or wlan0 etc. depending on driver used).

You seem to be using hostapd package. Why not checking their website for any guides? [http://w1.fi/](http://w1.fi/)

---

### Post by nevthinking on 2013-01-30
This is what I did:
I installed the hostapd and dnsmasq packages and then stopped the services and prevented them from starting on system start-up.
Then I added the following code and saved it as /etc/hostapd.conf

```
# Define interface
interface=wlan0
# Select driver
driver=nl80211
# Set access point name
ssid=myhotspot
# Set access point harware mode to 802.11g
hw_mode=g
# Set WIFI channel (can be easily changed)
channel=6
# Enable WPA2 only (1 for WPA, 2 for WPA2, 3 for WPA + WPA2)
wpa=2
wpa_passphrase=mypassword
```

Now I added these lines to the file /etc/dnsmasq.conf

```
# Bind to only one interface
bind-interfaces
# Choose interface for binding
interface=wlan0
# Specify range of IP addresses for DHCP leasses
dhcp-range=192.168.150.2,192.168.150.10
```

Now I created a file start.sh and saved the following code into it

```
#!/bin/bash
# Start
# Configure IP address for WLAN
sudo ifconfig wlan0 192.168.150.1
# Start DHCP/DNS server
sudo service dnsmasq restart
# Enable routing
sudo sysctl net.ipv4.ip_forward=1
# Enable NAT
sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
# Run access point daemon
sudo hostapd /etc/hostapd.conf
# Stop
# Disable NAT
sudo iptables -D POSTROUTING -t nat -o ppp0 -j MASQUERADE
# Disable routing
sudo sysctl net.ipv4.ip_forward=0
# Disable DHCP/DNS server
sudo service dnsmasq stop
sudo service hostapd stop

```

I replaced all the ppp0 in the above file with eth0 which is my NIC card name.

To start the hotspot I run the script start.sh upon which I get the following message :

```
 * Restarting DNS forwarder and DHCP server dnsmasq                             
dnsmasq: failed to create listening socket for 127.0.0.1: Address already in use
                                                                         [fail]
net.ipv4.ip_forward = 1
Configuration file: /etc/hostapd.conf

```

I am not able to create a hotspot like I previously did in Ubuntu 12.10 in the same system.

As I tried to rectify errors I found out the names of the NIC in my computer and found that while the above script was running there was a new NIC addition to my list of NIC names which was named "mon.wlan0" which disappeared the moment I killed the script by closing the terminal.

Please reply with a solution.

---

### Post by palangu on 2013-02-02
Hi,
          Same problem when upgrade from 11.10 to 12.04...solved as show in [http://ubuntuforums.org/showpost.php?p=11923702&postcount=40](http://ubuntuforums.org/showpost.php?p=11923702&postcount=40)

---

### Post by nevthinking on 2013-02-04
Thanks palangu ! 
Really appreciate the great help :)

---

