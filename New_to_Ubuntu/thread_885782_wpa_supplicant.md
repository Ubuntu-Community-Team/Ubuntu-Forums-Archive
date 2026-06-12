---
title: "wpa_supplicant"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by xiaozhu on 2008-08-10
Can Unbuntu install wpa_supplicant? or is it installed by default?

Can someone direct me to more details?

---

### Post by Kevbert on 2008-08-10
wpa supplicant is installed by default on Hardy Heron 8.04 (and Gutsy 7.10).  If you need to check this go to System-Administration-Synaptic Package Manager.  Enter your log-in password when prompted.  Now click on Search and enter wpasupplicant (Hardy Heron) in the box that is displayed and then click on Search in the window that is now displayed. It should be shown with a green coloured box next to it. This means it is installed.

---

### Post by xiaozhu on 2008-08-10
Then how do I get about using wpa supplicant?

Such as entering my details...

I know I need

1) rootcert - I got it
2) The exact guide I need to connect to my wireless point is here: [http://forums.hardwarezone.com.sg/showthread.php?t=1975528](http://forums.hardwarezone.com.sg/showthread.php?t=1975528)

but I don't seemed to understand it and the guide creator isn't clear of Ubuntu anyway.

---

### Post by InfinityCircuit on 2008-08-10
> 
Also, I believe that in using linux, you should know what you are doing, not like unbuntu forums copy and paste shell scripts and don't know what they have messed up their /etc files. I'm not going to just tell you step by step.

What a nice attitude...

Basically, you want to copy the following:

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1 # settings to scan for ssid. Try 0,1,2 each to find the network.

network={
	ssid="SITSDN" # your sch wireless network name
	key_mgmt=IEEE8021X
	eap=PEAP
	phase2="auth=MSCHAPV2"
	identity="NYPSDN\123456X" # change NYPSDN to your own logon domain (in sch lab login the one under the password) and your admin num 
	password="mypassword"	# your password (yes, have to be clear, i can't make it work with hex) 
	ca_cert="/home/rainyrhy/rootca.cer" # go to sch wireless guide, download the cert, place it somewhere and point to it.
	scan_ssid=1 # also try 1 or 0 to find the network.
}
```

into /etc/wpa_supplicant/wpa_supplicant.conf.  Then, you want to execute this command: 

sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd

Do this with a bunch of different iterations on the above file (e.g. different network names or different ap_scan values)

If it finally seems to daemonize without errors, then run:

sudo dhclient wlan0

to get an address.

If this all works you can put those two commands in /etc/rc.local to get it started at boot.

---

### Post by Kevbert on 2008-08-11
You don't need to do anything if you're just trying to connect to a wireless network. Can you see other wireless networks ?  If not, what's the wireless chipset ?  You can get this by going to Accessories-Terminal and entering 
```
lspci
```
Towards the bottom of the page will be the wireless information (broadcom bcm4306, realtek rt8101 for example).
Please also enter
```
iwconfig
```
and post the information here (you can do this by highlighting the text with the mouse then select Edit-Copy from the menus, next open up your next post and press Ctrl+V).

---

