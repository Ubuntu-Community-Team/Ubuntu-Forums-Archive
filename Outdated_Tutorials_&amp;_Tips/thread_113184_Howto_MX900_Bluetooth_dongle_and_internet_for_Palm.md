---
title: "Howto: MX900 Bluetooth dongle and internet for Palm w/ BT"
date: 2006-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by SirKillalot on 2006-01-05
Hi.
This, my very fist howto, describes how to get your Logitech MX900 mouse bluetooth donge work as HID and Bluetooth dongle at once and how you go online with your Palm using that Bluetooth dongle. The problem in Ubuntu is that the MX900 is working EITHER as mouse device OR Bluetooth dongle with the standard configurations. Maybe I should've split that into up two howtos, the Bluetooth howto and the thing with the Palm.. whatever.

**_STEP 1_**
_Getting bluetooth work with MX900._

First you need a working bluez on your PC:

```
sudo apt-get install libbluetooth1 bluez-utils bluez-pin 
```

Check whether bluetooth module is loaded:
```
lsmod | grep bluetooth
```

Now, create a startup script to get your mouse work AND let your dongle work as a dongle!

```
sudo touch /etc/init.d/bluetooth
sudo gedit /etc/init.d/bluetooth
sudo chmod +x /etc/init.d/bluetooth
```

edit it like that:

```
hid2hci
hcid
sdpd
hidd --server
```

You should link that script to the runlevels:
```
sudo update-rc.d bluetooth defaults
```

(If you don't have any of that programs, install them :P. You could try to find them via apt-cache search of apt-file search)

You need to restart your machine in order to get everything work. You can check if everything went ok by searching for a Bluetooth device for example using
```
hcitool scan
```

**_STEP 2_**
_Get your Palm device online_

First you need to edit the private key for Bluetooth pairings of your computer. The file is called /etc/bluetooth/pin.
The standard key is simply '1234'.

Then startup your Palm, go to the Preferences menu and select 'Bluetooth'. Enable your Bluetooth and add your PC as an authorized device. Use the key for the connection you set up the step before on your PC.

Now go to the 'Connections' tab and create a new connection. Call it something like 'Bluetooth PC', Select 'PC' as device to connect to and use 'Bluetooth' as medium. Finally, select your PC in the last control.

Now switch to your desktop back.

Create /etc/ppp/peers/dun:
```
115200
proxyarp
192.168.168.1:192.168.168.50
local
ms-dns 172.16.3.3
noauth
debug
ktune
```
(Thanks to Botsinge)


First get the Bluetooth address of your palm:
```
hcitool scan
```
It should be something like '00:60:57:4C:09:3C'. Don't lose the address, we'll need it now.

Edit your rfcomm configuration file to emulate Bluetooth -> com port.
```
sudo gedit /etc/bluetooth/rfcomm.conf
```

enter:
```
rfcomm0 {
bind yes;
device 00:60:57:4C:09:3C ;
channel 1;
comment "Palm";
}
```

Where '00:60:57:4C:09:3C' is the bluetooth address of your Palm. This step makes rfcomm bind your Palm Bluetooth connectio to the 1st rfcomm channel.

We create a NAT forwarding for your palm to share your internet connection. To get it run every boot, we create a startup script:

```
sudo touch /etc/init.d/btinternet
sudo chmod +x /etc/init.d/btinternet
sudo gedit /etc/initd.d/btinternet
```

paste:

```
dund --listen --msdun --channel 1 192.168.2.101:192.168.2.102

iptables -A INPUT --in-interface ppp0 -d 0.0.0.0/0 -j ACCEPT
iptables -A FORWARD --in-interface ppp0 -j ACCEPT
iptables -A FORWARD --in-interface eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING --out-interface eth0 -j SNAT --to 192.168.0.1

```
where 192.168.0.1 is your local address and eth0 your internet interface. This will create a ppp0 interface just for your Palm. You need to have 'dund' 
installed for that. It should be available in the Ubuntu repos.

Again thanks to Botsinge!

After that, edit the file /etc/default/bluez-utils.
Find the row

```
DUND_ENABLED=0
```

and change it to

```

DUND_ENABLED=1
```


and change the row

```
DUND_OPTIONS="--listen --persist"
```

to

```

DUND_OPTIONS="--listen --persist --msdun call dun"
```

Then, restart bluez-utils:

```
sudo /etc/init.d/bluez-utils restart
```

Okay, that was very much, but I think now it should work. Get your Palm again and go to the 'Network' tab in Preferences. 
Select 'Windows RAS', leave user and password blank and take the connection you set up before.

Now press C O N N E C T.


My whole Bluetooth system is running very fine after working on it for more than a month, because of the lack of information about the MX900 under Linux. I cannot really test if this all will work for a Ubuntu from scratch, it works fine for me, maybe I forgot some steps I made a month ago, but if so, just tell me. I'll try to complete the howto. Hope I could help.

Regards
Caglar

---

### Post by zisper on 2006-04-27
Hi;

     My setup is a bit simpler, I've only got a normal bluetooth dongle that I want to get working with my palm Tungsten.  I've got it working and connecting (VNC on my palm via BT, cool.  Not really quick enough to be all that useful - but still fun!) but I'm having trouble with the forwarding/iptables/internet access.
   When I try to start the /etc/init.d/btinernet script I get the following error:

Bad argument `nat'
Try `iptables -h' or 'iptables --help' for more information.

Any advice?  I don't really know anything about iptables.  Otherwise, great guide.  Never would've got this working myself.

---

### Post by SirKillalot on 2006-05-13
Hello zisper,
There was a typo in the tutorial, you can now change the entry to this:
```

dund --listen --msdun --channel 1 192.168.2.101:192.168.2.102

iptables -A INPUT --in-interface ppp0 -d 0.0.0.0/0 -j ACCEPT
iptables -A FORWARD --in-interface ppp0 -j ACCEPT
iptables -A FORWARD --in-interface eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING --out-interface eth0 -j SNAT --to 192.168.0.1
```

if your internet interface is **eth0**.
This should work for you. Thank you!
Best regards

---

### Post by ihenni on 2006-05-14
I'm trying to use your post with a Zire 72 and using wlan0 as the internet access point.  One big question, am I supposed to change all of the ip addresses to fit mine?  I'm able to connect to the desktop, but not to access the internet.  I don't get any errors, but it simply won't connect.
Any reply would be excellent
thanks,

ihenni


[QUOTE=SirKillalot]Hello zisper,
There was a typo in the tutorial, you can now change the entry to this:
```

dund --listen --msdun --channel 1 192.168.2.101:192.168.2.102

iptables -A INPUT --in-interface ppp0 -d 0.0.0.0/0 -j ACCEPT
iptables -A FORWARD --in-interface ppp0 -j ACCEPT
iptables -A FORWARD --in-interface eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING --out-interface eth0 -j SNAT --to 192.168.0.1
```

if your internet interface is **eth0**.
This should work for you. Thank you!
Best regards[/QUOTE]

---

### Post by nico9julio on 2006-09-29
Excelent! I've tried others before and non worked.
Lol, this doesn't work too... but the only two things I have to change was 

iptables -t nat -A POSTROUTING --out-interface eth1 -j SNAT --to **192.168.1.1**

(To the IP of my router)

And I have to specify the DNS on the palm side connection with the ip of my router again 192.168.1.1 (not my machine 192.168.0.1)

Thnaks
This is the better tutorial ever
8)

---

### Post by illuniel on 2007-12-11
would this apply to gutsy as well?

---

