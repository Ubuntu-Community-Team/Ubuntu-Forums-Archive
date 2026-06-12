---
title: "[SOLVED] unable to establish wireless networking"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by IvanIvan on 2008-06-12
Hello!

I'm having some real trouble establishing my wireless networking.
I've read all the sticky posts in Networking section, still no success. :(

Here is my situation. Please read it and help me out.

I have IBM Thinkpad T60p with Intel PRO/Wireless 3945ABG. The card is recognized under:
```
/sys/bus/pci/drivers/iwl3945
```

My /etc/network/interfaces currently looks like this:
```
auto lo
iface lo inet loopback




iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```
and I am connected via UTP to my router (192.168.1.1)

Back in WinXP I had ThinkVantage Access Connections suite which allowed me to manage multiple wired/wireless network profiles with ease, now I want something simillar in Ubuntu. I am **dependant** on this since I move alot and I can't manually configure network each time.

So, what I need is the ability to add/remove wireless profiles with ease.
I have wpa_supplicant and wpa_gui installed however I was unable to configure my wireless settings.

wpa_supplicant.conf should look like this:
```

ap_scan=2

ctrl_interface=/var/run/wpa_supplicant

#this is my home network: WPA2, hidden SSID
network={
    ssid="SSID"
    key_mgmt=WPA-PSK
    proto=WPA2
    pairwise=CCMP
    psk="PSK"
}

#this is my work network: WEP, PEAP-EAP, no hidden SSID
network={
        ssid="SSID"
        scan_ssid=1
        key_mgmt=IEEE8021X
        eap=PEAP
        phase2="auth=MSCHAPV2"
        identity="username"
        password="pass"
}

```

Ok, so I'm sure that that's ok since I generated ti via wpa_supplicant homepage.

[B]how do I set up multiple profiles in /etc/network/interfaces or wpa_gui?
how do I "tell" /etc/network/interfaces to use multiple profiles? will something like this work?[/B]

```
auto lo
iface lo inet loopback

mapping eth0
	script /usr/local/sbin/map-scheme
	map HOME.LAN eth0-home

mapping wlan0
	script/usr/local/sbin/map-scheme
	map HOME.WLAN wlan0-home
	map FERwlan wlan0-ferwlan

iface eth0-home inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

iface wlan0-home inet static
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1

# wpa-conf /etc/wpa_supplicant.conf ---is this right?

#is this OK for a DHCP network?
iface wlan0-ferwlan inet dhcp

auto eth0

auto wlan0
```

please help me out, I need this set up and working. :(

---

### Post by issih on 2008-06-12
I admit I have not played with wpa supplicant, but its obvious to me that the config file you've posted should have various values replaced with the values of your networks..You need to replace ssid with the ssid of the various networks, and enter your username and password etc. You may well have done this and just posted the generic form for security, in which case sorry for wasting your time, but I thought it best to mention it.

As for locations, network manager supports these. Just click on the network manager applet and choose manual configuration, and you will see you can enter different locations to store different network locations.

Hope thats useful

---

### Post by cmnorton on 2008-06-12
I would save /etc/network/interfaces, and start out with this:

# The loopback network interface
auto lo
iface lo inet loopback

Ubuntu network manager works quite well -- at least it has for me -- and you should be able to connect to your wireless router and also connect via ethernet cable using these settings. These settings, I believe, presume that you are getting your ip addresses DHCP.

Manual configuration in Network Manager should be able to handle your problems if you must have static addresses.

This post might be useful to you as well: [http://ubuntuforums.org/showthread.php?t=793865](http://ubuntuforums.org/showthread.php?t=793865)

---

### Post by IvanIvan on 2008-06-12
thanks for your replies, but you weren't helpful. 
I have VERY advanced knowledge of networks but I'm new to Ubuntu, and this problem seems...well...silly, but I'm still unable to resolve it.

I think this should be moved to Networking/Wireless section.

---

### Post by paulderol on 2008-06-12
does nm-applet not let you use roaming mode? how convoluted are your network setups?

---

### Post by ukripper on 2008-06-12
This card works out of the box in ubuntu gutsy and hardy (iwl3945 drivers are used). 
If you have hidden ssid then it won't show up as this driver doesn't like hidden ssids. nm-applet or network manager both can see Access points using this. 

i have tried configuring it manually through interfaces file which doesn't  recognise the drivers. So it is better you use nm-applet or network manager. you can try wicd as well if you wish too.

---

### Post by IvanIvan on 2008-06-12
> **ukripper said:**
> So it is better you use nm-applet or network manager
tried both. 
doesn't work. :(
it just keeps connecting and connecting and connecting...

---

### Post by ukripper on 2008-06-12
> **IvanIvan said:**
> tried both. 
doesn't work. :(
it just keeps connecting and connecting and connecting...

are u using WPA or WPA2?
and what algorthm for encrytpion AES or TKIP 
on your router?

---

### Post by issih on 2008-06-12
Do you have any more luck trying to do each step through the command line?

Bringing up the wireless device through ifconfig:

e.g. sudo ifconfig wlan0 up

Then connecting to the access point with:

e.g. sudo iwconfig wlano essid *your_ssid*

You'll have to work out the wireless encryption key bit yourself from iwconfig's man page as I have no idea what you are running, I would though recommend removing encryption temporarily to aid troubleshooting.

then once thats done check if iwconfig thinks it is associated.

finally can you acquire an ip via dhcp (if using it) with;

e.g. sudo dhclient wlano

With a bit of luck breaking down the steps might let you see where things are going to hell

---

### Post by IvanIvan on 2008-06-12
I managed to set up my profile in /etc/network/interfaces:

```
iface wlan0 inet static
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1
wpa-driver wext
wpa-ssid myssid
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk key
```

I removed my real ssid and key from here. I was able to connect with these settings and save them as a location profile in network manager but...when I tried to switch to wired lan and then back to my profile (to test if this really works), it didn't work.
then I saw /etc/network/interfaces and of course, **network manager didn't save the settings above. :(**
what to do?
AFAIK, this is a known problem on Ubuntu (WPA2 configuration save...)

---

### Post by issih on 2008-06-12
Hmmn thats a pain, good to know the hardware works at least.

You could create two files with the differing setups for /etc/network/interface

one at /etc/network/interfaces

and another at /etc/network/interface_alternate.

and then have a little script to run

ifdown -a (assuming your interfaces are marked auto)
cp /etc/network/interfaces /etc/network/buffer
cp /etc/network/interfaces_alternate /etc/network/interfaces
cp /etc/network/buffer /etc/network/interfaces_alternate
ifup -a

save the script as switchLocation or some such and chmod it to be executable.

Run that as sudo or set up a launcher to run gksudo switch location, and that ought to achieve the same results..sort of.

A better script could pick up an inputted parameter or even present a list of options to select between locations.

---

### Post by IvanIvan on 2008-06-12
thanks for that, but there MUST be a way for this run smoother...

---

### Post by issih on 2008-06-12
Until someone patches the problem with storing wpa2 setup, you probably came up with your best option in your first post really, using the mapping system in /etc/network/interfaces. What you had looks sensible enough, and it would really just be a case of how you implement the script system to provide the switch between the different setups.

The file you suggested looks ok to me in the main, although you will obviously need to update you wlan logical interfaces with your new information on how to get wpa2 working. The mapping looks good though. The mapping on eth0 isn't doing anything at the moment, but leaves you scope to change more easily later on I guess.

As for the script, you could just have it read a state file to determine its location, but thats not really much better than the above in terms of smooth operation, but it potentially could remove the ifup/ifdown elements.

To truly make it simple you could have the script set up to select the interface mapping select based on a simple state file stored somewhere.

Drop a drawer applet into a panel, and add launchers for each location which just echo the appropriate location id into the state file.

You'll probably need to still ifdown ifup the system though, or do /etc/init.d/networking restart

whatever you do is almost bound to need sudo to get the interfaces to reconfigure, so its probably best to have each item in the drawer be a little script echoing to the state file then restarting the networking interfaces. if you then edit the sudoers file so those scripts can be launched by you without a password you can set the launchers in the draw to use sudo and you should be all done.

To change location simply hit the drop down and select your location..all done.

Right royal pain in the ****, but I can't think of anything else to do unless someone knows how to get ubuntu to store those details persistently.

---

### Post by IvanIvan on 2008-06-12
well that sucks. :(
I'm reeeeeally beginning to miss Access Connections. :)

ok, how about I ditch Network Manager and use wpa_supplicant alongside wpa_gui (in which you can nicely change your profiles, etc.)

i'd use network manager ONLY for wired ethernet and wpa_gui for other...

is this feasible?

---

### Post by issih on 2008-06-12
Haven't used wpa myself so I can't say, I can recommend you have a look at wicd however, this is an alternate network manager that a lot of people prefer I'm not entirely sure if its got locations as the only time I tried it I had issues with firefox forever being in "work offline" mode as apparently wicd wasn't sending a dbus message, so it never stayed on my system for long.

Still worth checking out.

---

### Post by IvanIvan on 2008-06-12
this wicd seems to work, however they too have a problem:

> - Why doesn't Wicd reconnect to my hidden network?

This is probably a bug in your wireless driver; sudo iwlist scan in a terminal and see if the network is listed as <hidden>. If it is, then reopen Wicd and press refresh, and the network should be listed. Otherwise, file a bug with the people who make your wireless driver.


but I think I'll manage for now...until they fix the original problem. 

thanks all.

I'll consider this solved.

---

### Post by lswb on 2008-06-15
Just wanted to point out here, NetworkManager does not use the /etc/network/interfaces file and in fact having an entry there for a particular interface will often prevent NetworkManager from trying to manage that interface at all. Start with the blank (except for the lo entry) interfaces file and then try to enter your settings in the NM applet.

IMHO NetworkManager as shipped with 8.04 is not ready for prime time, and some of the wireless drivers shipped with the 8.04 version are missing some functionality compared to those shipped with older versions. OTOH some of the older versions are not recognized by NM.

I've tried various combinations of drivers and NetworkManager, wicd, and even wifi-radar with hardy and so far have been unable to find a method that is not lacking in some respect. I'm using NetworkManager for now and putting up with its quirks, hoping they will be addressed in upgrades, but, wicd has some attractive advantages.

---

### Post by IvanIvan on 2008-06-15
> **lswb said:**
> Just wanted to point out here, NetworkManager does not use the /etc/network/interfaces file and in fact having an entry there for a particular interface will often prevent NetworkManager from trying to manage that interface at all. Start with the blank (except for the lo entry) interfaces file and then try to enter your settings in the NM applet.
hm...didn't know that, thanks for pointing it out. 
Well, I have Wicd working for now so I won't be going back to Network manager (at least until it's "fully functional").

---

